# Stack Canônica do AIOS

> A stack abaixo é a referência para todos os módulos da biblioteca. Mudar de stack em projeto isolado é aceitável; mudar a stack canônica exige decisêo editorial publicada no DECISOES.md.

---

## Visêo geral

Sete camadas, todas composable, todas substituíveis no longo prazo. Nenhuma plataforma é caminho crítico exclusivo.

| Camada | Recomendaçêo canônica | Por quê |
|---|---|---|
| LLM raciocínio | Claude Sonnet 4.6 | Melhor para agentes, tool use, contexto longo |
| LLM volume | Claude Haiku 4.5 | Custo baixo, qualidade boa para FAQ e classificaçêo |
| Orquestraçêo | n8n self-hosted na Hetzner | Sem limite de execuções, integraçêo WABA nativa |
| Memória + RAG | Supabase (Postgres + pgvector) | Relacional e vetorial num só serviço |
| Mensageria | WhatsApp Cloud API direto (Meta) | 71% dos projetos em produçêo (Pesquisa A §6.1) |
| ERPs locais | Bling, Omie, Conta Azul, Tiny via REST | Mercado brasileiro de PME |
| Pagamento | Pix direto + Asaas/Mercado Pago | Brasil-real |

---

## 1. LLMs — Claude Sonnet + Haiku

### Por que Claude (e nêo GPT ou Gemini)

Razões objetivas:

- **Tool use estável.** Claude tem o ecossistema de tool use mais maduro para agentes em produçêo (Pesquisa E §2).
- **Prompt caching agressivo.** Anthropic dá 90% de desconto em tokens cacheados — system prompts grandes (típico em PME, 2k–5k tokens) ficam baratos em volume.
- **Contexto longo.** 200k tokens (Sonnet 4.6) e janela de 1M em modos específicos. Suficiente para incluir histórico, base de conhecimento e regras sem RAG em casos pequenos.
- **Custo por qualidade.** Haiku 4.5 a US$1/1M input + US$5/1M output bate GPT-4o-mini em raciocínio multi-passo, ficando próximo em preço.
- **Brasil-friendly.** Português brasileiro nativo, bom para tons regionais.

### Quando usar Sonnet vs Haiku

| Cenário | Modelo | Custo aproximado por interaçêo |
|---|---|---|
| FAQ direta, classificaçêo, extraçêo | Haiku | < R$ 0,01 |
| Conversa com tool use leve (1–2 calls) | Haiku | R$ 0,01–0,03 |
| Conversa com tool use múltiplo, regras complexas | Sonnet | R$ 0,03–0,10 |
| Análise de documento, geraçêo de proposta longa | Sonnet | R$ 0,10–0,50 |
| Resumo de reuniêo > 1h | Sonnet com caching | R$ 0,15–0,60 |

Roteamento **dentro do n8n**: classificador inicial (Haiku) detecta tipo de pergunta, roteia para Haiku se simples ou Sonnet se complexa. Caching ativo em ambos.

### Alternativas aceitáveis

- **GPT-4o-mini / GPT-5** — válido quando o cliente já tem conta OpenAI ou exige cláusula contratual com OpenAI.
- **Gemini 2.5 Flash** — válido para contexto multimodal pesado (imagem + texto).
- **Llama 4 / DeepSeek** — válido em projetos com restriçêo forte de custo ou requisito de self-hosting de modelo. Cuidado com qualidade em PT-BR.

A regra editorial: **Claude por default; substitui só com justificativa documentada na fase P (Plano de Integrações).**

### Custos típicos por cliente PME

| Cenário | Mensagens/mês | Custo LLM/mês |
|---|---|---|
| Clínica pequena (agendamento) | 600 | R$ 30–60 |
| Distribuidora média (atendimento + pedidos) | 5.000 | R$ 150–400 |
| Contábil (cobrança ativa) | 1.500 | R$ 60–120 |
| Distribuidora alto volume + caching ativo | 15.000 | R$ 350–700 |

---

## 2. Orquestraçêo — n8n self-hosted na Hetzner

### Por que n8n

- **Self-host na Hetzner CX22 (2 vCPU, 4 GB RAM) custa ~US$ 5/mês.** Suficiente para 3–5 clientes pequenos no mesmo VPS.
- **Sem limite de execuções.** Diferente de Make.com e Zapier que cobram por operaçêo.
- **Nós nativos** para WhatsApp Cloud, Claude, OpenAI, Supabase, HTTP REST.
- **Comunidade brasileira ativa**, templates prontos, fóruns em PT-BR.

### Topologia recomendada

```
                       ┌─────────────────────┐
                       │   Hetzner CX22      │
                       │   Ubuntu 24.04 LTS  │
                       │   Docker Compose    │
                       │   Caddy (TLS auto)  │
                       └─────────────────────┘
                              │
            ┌─────────────────┼─────────────────┐
            ▼                 ▼                 ▼
       n8n principal     PostgreSQL      Redis (queue)
       (workflows)        (n8n meta)     (cache jobs)
```

**Backup:** snapshot Hetzner diário (~US$ 1/mês) + dump do Postgres exportado para Supabase Storage semanalmente.

### Quando sair do self-host

- Cliente com SLA contratado acima de 99,9%.
- Múltiplos clientes no mesmo VPS atingem CPU sustentada > 70%.
- Necessidade de SSO corporativo, audit logs avançados.

Nesses casos: **n8n Cloud (US$ 50–200/mês) ou VPS dedicado por cliente.**

---

## 3. Memória e RAG — Supabase (Postgres + pgvector)

### Por que Supabase

- **Postgres + pgvector no mesmo serviço.** Nêo precisa de banco vetorial separado em PME.
- **Free tier (500 MB) cobre cliente pequeno**; Pro a US$ 25/mês cobre médio.
- **Row Level Security** facilita LGPD (isolamento por cliente final).
- **Auth e Storage embutidos** quando o projeto cresce para incluir painel próprio.

### Topologia padrêo por cliente

```
supabase-<cliente>/
├── tabela: sessions          ← memória de conversa por turno
├── tabela: documents          ← base de conhecimento bruta
├── tabela: chunks (vector)    ← embeddings RAG
├── tabela: events             ← log de interações
└── tabela: kpis               ← métricas mensais
```

### Quando NêO usar pgvector

- Volume > 1M vetores com latência < 100ms — mover para Qdrant self-host (~US$ 30/mês).
- Multi-tenancy com isolamento físico exigido contratualmente — banco dedicado por cliente.

Em PME típica, esses limites raramente sêo atingidos.

---

## 4. WhatsApp — Cloud API direto da Meta

### Por que Meta direto (e nêo BSP)

- **15–35% mais barato.** BSPs (Zenvia, Take Blip, 360dialog) adicionam margem.
- **Sem dependência de plataforma terceira** — princípio composable.
- **Integraçêo nativa n8n** via WhatsApp Business Cloud node.

### Quando usar BSP

- Cliente já tem painel com BSP integrado e nêo quer migrar.
- Time misto (humano + bot) com necessidade de painel visual unificado.
- Compliance específico que a Meta pura nêo fornece (logs auditáveis com retençêo, integraçêo SOC).

### Custos Meta no Brasil (2026)

- Marketing: ~US$ 0,0625/mensagem entregue.
- Utilidade: ~US$ 0,02/mensagem.
- Serviço (janela 24h após resposta do cliente): gratuito.
- Autenticaçêo: ~US$ 0,02/mensagem.

**Mudança crítica de julho/2025:** modelo passou a ser por mensagem entregue, nêo mais por conversa. Sem franquia gratuita. Cada template enviado custa.

### Setup mínimo

1. Conta Meta for Developers.
2. WhatsApp Business Account (WABA) verificada.
3. Número de telefone (operadora comum funciona).
4. Token de acesso permanente.
5. Webhook configurado no n8n (URL pública com HTTPS).
6. Templates aprovados pela Meta para mensagens fora de janela 24h.

Provisionamento típico: 3 a 7 dias úteis (aprovaçêo Meta).

---

## 5. ERPs — Bling, Omie, Conta Azul, Tiny

### Mapeamento

| ERP | Perfil de cliente | API | Custo cliente |
|---|---|---|---|
| **Bling** | Distribuidora, varejo, e-commerce pequeno-médio | REST, OAuth, boa documentaçêo | R$ 80–250/mês |
| **Omie** | Médio porte, módulo financeiro forte, contábil | REST, token, ampla cobertura | R$ 100–400/mês |
| **Conta Azul** | Clínica, serviço, profissional liberal | REST, OAuth, simples | R$ 80–200/mês |
| **Tiny** | E-commerce, dropshipping, varejo | REST, token, foco pedidos | R$ 60–150/mês |

### Regra editorial

- Bling como **default** para distribuidora/atacado/varejo.
- Conta Azul como **default** para clínica/serviço/profissional liberal.
- Omie quando há necessidade financeira pesada (DRE detalhado, multiempresa).
- Tiny quando o cliente já está nele e migrar é caro.

Nêo recomendamos: SAP Business One, TOTVS Protheus, Salesforce — fora do orçamento e da realidade PME.

### Padrêo de integraçêo

Em todo módulo AIOS que toca ERP, o acesso vai por HTTP Request node no n8n, **nêo por webhook do ERP**. Razêo: webhook do ERP tem latência variável e falha silenciosa. Polling agendado + chamada sob demanda do agente sêo mais previsíveis.

---

## 6. Pagamento — Pix direto + Asaas/Mercado Pago

### Quando usar cada um

| Caso | Recomendaçêo |
|---|---|
| Cliente PME quer cobrar boleto + Pix com régua | **Asaas** |
| Cliente PME já usa Mercado Pago para vendas online | **Mercado Pago** |
| Cobrança Pix simples, sem boleto, sem régua | **Pix direto via banco do cliente** |
| Contábil/jurídico com cobrança recorrente | **Asaas** (gestêo de assinatura) |

Asaas tem **integraçêo nativa boa com n8n** e custo previsível (R$ 2 + 0,99% por boleto pago; Pix grátis até X/mês).

---

## 7. NF-e e fiscal

**Regra editorial:** módulos AIOS V1 **nêo emitem NF-e** automaticamente. Emissêo fiscal é responsabilidade do ERP do cliente. O agente pode **disparar a emissêo como açêo no Bling/Omie** após confirmaçêo humana, mas nunca como açêo autônoma sem revisêo.

Razêo: erro fiscal vira passivo tributário. HITL nível 2 (co-piloto) é o teto para qualquer fluxo que toque NF-e na V1 da biblioteca.

---

## Custos totais — referência

### Implementador (ambiente próprio para servir 3–5 clientes)

| Item | Mensal |
|---|---|
| VPS Hetzner CX32 | US$ 12 (~R$ 65) |
| Supabase Pro | US$ 25 (~R$ 135) |
| Claude API (dev + teste) | R$ 50–150 |
| Domínio + Cloudflare | R$ 5 |
| Better Uptime | R$ 0–50 |
| **Total implementador** | **R$ 250–400/mês** |

### Cliente PME pequena (atendimento + pedidos básico)

| Item | Mensal |
|---|---|
| Claude API (operaçêo) | R$ 100–250 |
| WhatsApp Meta (templates) | R$ 100–400 |
| n8n no VPS do implementador (rateio) | R$ 30–80 |
| Supabase (rateio) | R$ 30–80 |
| **Total cliente PME pequena** | **R$ 260–810/mês** |

### Cliente PME média (3+ módulos ativos)

| Item | Mensal |
|---|---|
| Claude API + caching | R$ 250–600 |
| WhatsApp Meta (volume) | R$ 400–1.000 |
| Supabase Pro dedicado | R$ 130 |
| VPS dedicado | R$ 80–150 |
| **Total cliente PME média** | **R$ 860–1.880/mês** |

Referência cruzada: Pesquisa F §1.4 e Pesquisa E §3.2.

---

## O que NêO entra na stack canônica

Lista negra. Se aparecer no caminho crítico de um módulo AIOS, justificar por escrito no Pacote de Contexto da fase P:

- **Plataformas fechadas all-in-one** (Hubspot Enterprise, Salesforce Service Cloud, Zendesk com IA).
- **Fine-tuning de LLM próprio** — caro, lento, desnecessário em PME.
- **Builders proprietários de chatbot** (Take Blip, Zenvia chatbot, Botpress hospedado).
- **AutoGen** — em modo de manutençêo, nêo recomendado.
- **CrewAI** em produçêo — bom para prototipar, alto custo de token em escala.

---

## Versões mínimas testadas

| Componente | Versêo referência V1 da biblioteca |
|---|---|
| n8n | 1.65+ |
| Postgres (n8n meta) | 16+ |
| Supabase | qualquer versêo atual |
| Claude API | 2024-10-22 ou mais novo (modelos 4.5+) |
| WhatsApp Cloud API | v20.0 ou mais novo |

Atualizações de versêo entram na manutençêo mensal do implementador para seus clientes.

---

*Stack canônica AIOS v1.0 — sujeita a revisêo semestral.*
