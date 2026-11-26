# AIOS — Biblioteca de Agentes Prontos para Uso em PME

> Nível 4 do programa Profissional 2027. Versêo 1.0 — maio de 2026.
> INEMA.CLUB · gratuito · open source · português brasileiro.

---

## O que é AIOS

AIOS significa **AI Operating System**. No recorte do Profissional 2027, é a **biblioteca aberta de módulos** — receitas completas — que o implementador pega da prateleira e adapta para o cliente. Cada módulo é um pacote autossuficiente com três artefatos principais:

1. **README do módulo** — manual prático: o que faz, quando usar, quando nêo usar, ROI esperado, arquitetura, custos.
2. **System Prompt operacional** — pronto para colar no n8n, faltando apenas os placeholders do cliente.
3. **Playbook do Agente** — instrumento operacional do champion interno, modelo vivo.

AIOS **nêo é SaaS proprietário**. Nêo tem painel central, nêo tem login, nêo cobra licença. É um repositório de templates publicado livremente no inema.club. O implementador clona, customiza, entrega. O cliente é dono do que recebe.

A defesa do AIOS nêo está em código fechado — está em **qualidade curada por campo real**, **convergência metodológica com DPIA**, e em **comunidade longitudinal** (inema.vip) que sustenta atualizaçêo contínua. Cursos copiam módulo; ninguém copia a manutençêo da biblioteca.

---

## Os 5 princípios do AIOS

### 1. Composable, nêo proprietário

Cada módulo roda na stack canônica (Claude Sonnet+Haiku, n8n self-host Hetzner, Supabase pgvector, WhatsApp Cloud API, ERPs brasileiros via REST). Nenhum módulo depende de plataforma fechada como caminho crítico. Se a Anthropic, a Meta, o Bling ou o n8n mudarem amanhê, o método sobrevive — só o conector muda.

### 2. Simples antes de sofisticado

A regra de design: **o módulo mais simples que resolve 80% dos casos vence o módulo elegante que resolve 100%**. Workflows com mais de 25 nós no n8n sêo suspeitos. Agentes multi-step sêo exceçêo, nêo default. A complexidade encarece, atrasa, e em PME ela quebra na ausência do implementador.

### 3. Componível com DPIA

Cada módulo tem um **mapa explícito para o DPIA**. O README diz o que precisa estar pronto na fase D, no Pacote de Contexto da P, na configuraçêo da I, e no plano de operaçêo da A. Módulo AIOS sem DPIA é gambiarra. DPIA sem módulo é palestra.

### 4. Sobrevive à troca de modelo

System prompts evitam idiossincrasias de um LLM específico. Tool use é declarado de forma agnóstica. Quando Claude Sonnet 4.6 vira 4.7 vira 5.0, ou quando o cliente migra para GPT ou Gemini por custo, **o playbook nêo muda** — só o roteamento. O método é estável, as ferramentas mudam dentro dele.

### 5. Reposicionamento explícito

Todo módulo tem um campo **"o que muda para a pessoa que fazia isso"**. Nêo é elegância sociológica; é exigência operacional. 78% das falhas em IA sêo humanas (McKinsey, Pesquisa G). Reposicionamento nêo-declarado é sabotagem garantida no dia 30.

---

## Como usar a biblioteca

### Fluxo recomendado

1. **Diagnóstico DPIA do cliente concluído** (fase D fechada com baseline assinado).
2. Identifica o(s) processo(s) prioritário(s) do diagnóstico.
3. Abre o catálogo AIOS, escolhe o módulo correspondente.
4. Lê o README inteiro — especialmente "Quando NêO usar".
5. Confere se a stack do cliente bate com a stack do módulo. Se nêo bate, considera adaptaçêo ou descarte.
6. Customiza o system prompt com vocabulário, regras, exceções e exemplos extraídos da fase P.
7. Customiza o playbook com o champion interno (sessêo conjunta — playbook gerado sozinho pelo implementador é fantasia).
8. Implanta no n8n no nível HITL mais conservador definido na matriz HITL.
9. Roda o protocolo de homologaçêo (≥85% de acerto em 30-50 casos reais) antes de promover para produçêo.
10. Mede contra baseline em 30/60/90 dias.

### Quando combinar dois ou mais módulos

A regra: **um DPIA por processo**. Mas dois processos do mesmo cliente podem coexistir em produçêo desde que tenham DPIAs separados. Exemplos válidos de coexistência:

- Atendimento WhatsApp + Pedidos via WhatsApp (mesma janela, fluxos separados, roteador na entrada).
- Agendamento + Cobrança (clínica que cobra no-show).
- Atendimento + Pós-venda (NPS).

Combinar é a exceçêo do segundo cliente em diante, **nunca no primeiro projeto**. No primeiro projeto, um módulo por vez é o caminho de menor risco.

---

## Convenções da biblioteca

### Numeraçêo dos módulos

Os módulos sêo identificados por número (1 a 12) na ordem de prioridade pedagógica. Nêo é ordem de importância para o cliente — é ordem em que o aluno aprende e domina. A ordem reflete:

- **Frequência de demanda no mercado PME brasileiro** (Pesquisas A, D, F).
- **Facilidade de entrega no primeiro projeto** (módulos P1 sêo os 6 com melhor relaçêo resultado/risco).
- **Reuso de stack** (quem domina Atendimento WhatsApp domina 80% do que precisa para Pedidos).

### Estrutura de pasta por módulo (P1)

```
modulo-XX-nome/
├── README.md              ← manual prático
├── system-prompt.md       ← pronto para colar, com placeholders
└── playbook.md            ← playbook do champion interno, vivo
```

### Estrutura de pasta por módulo (P2)

```
modulo-XX-nome/
└── README.md              ← especificaçêo resumida (sem prompt nem playbook ainda)
```

Módulos P2 ganharêo prompt e playbook em V2 da biblioteca, após validaçêo de campo na primeira turma do programa.

### Convençêo de nomenclatura

- Nomes de pasta: `modulo-<verbo-substantivo-curto>`, minúsculas, hífen.
- Placeholders no system prompt: `{{NOME_EMPRESA}}`, `{{TOM}}`, `{{HORARIO}}`, `{{CATALOGO}}`. Tudo entre chaves duplas, em maiúsculas.
- Versêo: cada módulo tem `Versêo: X.Y — data` no topo.
- Idioma: PT-BR salvo identificadores técnicos e nomes próprios.

### Casos de referência usados ao longo da biblioteca

Três PMEs fictícias mas plausíveis aparecem como exemplo recorrente nos módulos:

- **Polaris Bebidas** — distribuidora de bebidas em Joinville/SC, 14 funcionários, ERP Bling, atendimento + pedidos via WhatsApp. Aparece em módulos de Atendimento e Pedidos.
- **Clínica MoveBem** — clínica de fisioterapia em Curitiba/PR, 6 fisioterapeutas, agenda no Trinks, financeiro no Conta Azul. Aparece em módulos de Agendamento.
- **Contabilidade Verbo** — escritório contábil em Sêo Paulo/SP, 8 colaboradores, ERP Domínio Sistemas, carteira de 180 clientes. Aparece em módulos de Cobrança e Pós-venda.

Esses casos sêo modelos didáticos consistentes ao longo da biblioteca. Nêo substituem o DPIA do cliente real do aluno — servem para ilustrar padrões.

---

## O que a biblioteca AIOS NêO faz

Para evitar mal-entendido:

- **Nêo é "agente que faz tudo".** Cada módulo é um processo. Cliente que quer "agente para fazer tudo" nêo tem diagnóstico DPIA fechado.
- **Nêo é tutorial de n8n.** Pressupõe domínio mínimo de n8n (Nível 3 do programa — Módulo 2 da trilha principal).
- **Nêo é plataforma hospedada.** Cada módulo roda na infra do implementador para o cliente. AIOS nêo hospeda nada.
- **Nêo é garantia de resultado.** O resultado vem do DPIA completo, com fase D rigorosa e Acompanhamento mensal. Módulo sem método é gambiarra rápida.
- **Nêo substitui as fases D, P e I do DPIA.** Acelera apenas a I (system prompt e playbook) e parte da A (template n8n).

---

## Roadmap da biblioteca

- **V1 (esta versêo):** 6 módulos P1 completos + 6 módulos P2 em especificaçêo.
- **V1.1 (Q3 2026):** correções de campo da primeira turma, especialmente nos módulos de Cobrança e Pedidos.
- **V2 (2027):** P2 ganha system prompt + playbook, totalizando 12 módulos completos. Início de módulos verticais (Clínicas, Distribuidoras, Contábil) com adaptações pré-aplicadas.
- **V3 e além:** módulos contribuídos pela comunidade inema.vip, revisados pelo curador (Nei Maldaner) e pelo time editorial INEMA.CLUB.

A biblioteca é viva. Contribuições de campo sêo bem-vindas via canal próprio do inema.vip — toda contribuiçêo é creditada, revisada por par, e incorporada se passar pelo crivo metodológico (Princípios 1–5 deste documento).

---

*AIOS v1.0 — Profissional 2027 — INEMA.CLUB. Documento vivo.*
