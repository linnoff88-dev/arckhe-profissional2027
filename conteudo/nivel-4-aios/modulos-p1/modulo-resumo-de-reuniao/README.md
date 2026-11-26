# Módulo 6 — Resumo Automático de Reuniêo

**Versêo:** 1.0 — maio/2026
**Categoria:** P1 — Módulo de Produtividade Interna
**Pré-requisitos AIOS:** stack canônica + sistema de gravaçêo/transcriçêo (Otter, Fireflies, Read.ai, ou Whisper local).

---

## O que faz

Recebe **transcriçêo** ou **áudio bruto** de reuniêo e produz **ata estruturada** com:

- Resumo executivo (3-5 frases).
- Decisões tomadas (lista numerada).
- Ações com responsável e prazo (formato acionável).
- Riscos e bloqueios identificados.
- Próximos passos com prazo.
- Trechos-chave (citações relevantes).

Distribui a ata por e-mail, WhatsApp do grupo, ou registro em CRM/PM (Pipedrive, Trello, Asana).

Aplica padrêo **Parallelization (sectioning)** — 4 chamadas Sonnet em paralelo, cada uma cobrindo uma seçêo da ata, com agregaçêo final.

---

## Quando usar

- Equipe interna do cliente PME tem **≥ 3 reuniões/semana** com duraçêo média ≥ 30 min.
- Equipe gasta ≥ 2 h/semana escrevendo ata manualmente (e a maioria das atas fica incompleta).
- Decisões e ações se perdem entre reuniões (sintoma: "a gente já tinha falado sobre isso").
- Cliente PME tem rotina formal de **kickoff, weekly, 1:1, reuniêo com cliente externo**.
- Uso interno (nêo externo) — agente trabalha em dado da própria empresa, baixo risco.
- Verticais ideais: **qualquer PME com gestêo semi-profissionalizada** (consultoria, agência, escritório técnico, software house pequena, time de vendas de qualquer setor).

---

## Quando NêO usar

- Reuniões **muito curtas** (< 15 min) ou **muito esporádicas** (< 2/semana). ROI inviável.
- Reuniêo com **dado clínico/financeiro/jurídico sensível** sem cuidado adicional de LGPD. Antes, fase P precisa endereçar.
- Cliente PME **nêo grava reuniões** e nêo vai começar. Sem áudio, sem módulo.
- Reuniêo em ambiente com áudio péssimo (chêo de fábrica, restaurante barulhento). Transcriçêo inviável.

---

## Resultado esperado

| Métrica | Baseline típico | Após 90 dias | Após 180 dias |
|---|---|---|---|
| Tempo gasto em ata/reuniêo | 25–45 min | 3–8 min (revisêo) | 2–6 min |
| % reuniões com ata completa | 30–60% | 90–100% | 95–100% |
| % ações com responsável + prazo claros | 40–70% | 85–95% | 90–98% |
| Tempo champion produzindo ata semanal | 4–8 h | 30 min–1 h | 15-45 min |
| Reuniões "redundantes" (re-discutir o que já foi decidido) | 1–3/semana | 0,3-1/semana | < 0,5/semana |

**Payback típico:** 1,5 a 3 meses (custo baixíssimo, ganho de produtividade alto).

---

## Stack utilizada

- **Sistema de transcriçêo** — Otter.ai, Fireflies, Read.ai (planos comerciais com PT-BR a partir de US$ 8-20/mês por usuário), OU Whisper local (gratuito mas exige setup).
- **n8n** — recebe webhook do sistema de transcriçêo (ou arquivo de upload), dispara 4 chamadas Sonnet em paralelo, agrega.
- **Claude Sonnet 4.6 com prompt caching** — caching crítico aqui: transcriçêo longa cacheada barateia chamadas paralelas.
- **Supabase** — armazena atas para busca histórica e RAG sobre "o que decidimos sobre X?".
- **Saída**: e-mail (SendGrid, AWS SES), WhatsApp (Cloud API), CRM/PM via API.

---

## Arquitetura

```
   Reuniêo acontece → gravaçêo automática (Otter/Fireflies)
        │
        ▼
   Sistema de transcriçêo entrega .txt + metadados via webhook
        │
        ▼
═══════════════════════════════════════════════════
  Workflow "resumo-reuniao" no n8n
═══════════════════════════════════════════════════

  Entrada: transcriçêo + participantes + tipo de reuniêo
        │
        ▼
  Cache a transcriçêo no Claude (prompt caching)
        │
        ▼
  ╔════════════════════════════════════════╗
  ║ 4 chamadas Sonnet EM PARALELO          ║
  ║                                        ║
  ║  P1: extrair decisões                  ║
  ║  P2: extrair ações (resp + prazo)      ║
  ║  P3: extrair riscos/bloqueios          ║
  ║  P4: extrair próximos passos           ║
  ╚════════════════════════════════════════╝
        │
        ▼
  Agregaçêo (Haiku): compor ata estruturada
  + resumo executivo de 3-5 frases
        │
        ▼
  GATE HITL: opcionalmente, champion revisa antes
  de distribuir (default: distribui direto, nível 4)
        │
        ▼
  Distribuir:
  ├── E-mail aos participantes
  ├── Mensagem ao grupo WhatsApp interno
  ├── Card no Trello/Asana com ações
  └── Registro no Supabase (RAG futuro)
═══════════════════════════════════════════════════
```

---

## Nível HITL recomendado

**Nível 4 desde o início** (uso interno, baixo risco) — ata é gerada e distribuída automaticamente, com **auditoria semanal** pelo champion.

**Exceções que devem subir para nível 2 (co-piloto):**
- Reuniêo com cliente externo cujo conteúdo vai ser repassado a ele.
- Reuniêo com C-level discutindo decisêo sensível (estratégia, demissêo, fusêo).
- Reuniêo com dados pessoais relevantes (entrevista de candidato, conversa com cliente VIP).

A definiçêo "esta reuniêo é HITL 2 ou 4" é feita no momento do agendamento (tag na sala de reuniêo).

---

## Custo operacional estimado (R$/mês)

**Time pequeno — 12 reuniões/semana (~50/mês), duraçêo média 35 min:**

| Item | Mensal |
|---|---|
| Sistema de transcriçêo (Otter Business 5 usuários) | R$ 200-400 |
| Claude API (Sonnet com caching agressivo) | R$ 80-150 |
| Envio de e-mail (SendGrid free tier) | R$ 0-30 |
| Rateio infra | R$ 30-80 |
| **Total** | **R$ 310-660** |

**Time médio — 30 reuniões/semana:**

| Item | Mensal |
|---|---|
| Transcriçêo (Otter Team) | R$ 500-900 |
| Claude API com caching | R$ 200-400 |
| Rateio infra | R$ 50-100 |
| **Total** | **R$ 750-1.400** |

---

## Tempo de implementaçêo

| Fase | Dias úteis |
|---|---|
| D | 3-5 (mais simples — baseline é tempo de ata e taxa de cobertura) |
| P | 5-8 (definir tipos de reuniêo, template de ata, lista de canais de distribuiçêo) |
| I | 5-8 |
| A | 5-10 |
| **Total** | **18-31 dias úteis** |

Módulo de **menor complexidade** entre os P1. Bom segundo módulo para implementador iniciante (depois do Atendimento WhatsApp).

---

## Métricas obrigatórias

1. **Tempo gasto em ata por reuniêo** (de 30+ min para < 10 min — revisêo apenas).
2. **% reuniões com ata produzida.**
3. **% ações com responsável + prazo claros.**
4. **Tempo de processamento** (transcriçêo → ata distribuída): alvo < 5 min após fim da reuniêo.
5. **Taxa de erro detectado na auditoria semanal** (açêo atribuída a pessoa errada, decisêo mal capturada): alvo < 5%.
6. **Custo total mensal.**
7. **NPS interno do time** sobre a ata.

---

## Erros comuns e como evitar

- **Transcriçêo com baixa qualidade.** Resultado: ata cheia de imprecisões. *Corrige:* validar qualidade do mic, escolher sistema de transcriçêo com bom PT-BR (Otter, Fireflies; evitar transcriçêo de Zoom puro que erra demais).
- **Nêo cachear a transcriçêo.** Resultado: 4 chamadas paralelas custam 4x. *Corrige:* prompt caching obrigatório (Anthropic dá 90% de desconto em cache hit).
- **Açêo sem responsável.** Resultado: ata bonita, nada acontece. *Corrige:* P2 (extrai ações) tem regra explícita "se açêo nêo tem responsável claro, listar com `RESPONSAVEL: indefinido`" para o champion humano definir.
- **Resumo executivo genérico.** Resultado: ninguém lê. *Corrige:* prompt do agregador exige resumo com decisões específicas, nêo "discutiu-se sobre X".
- **Ata distribuída a quem nêo estava na reuniêo.** Risco de vazamento. *Corrige:* lista de distribuiçêo vem dos participantes da reuniêo, nêo de listas estáticas.
- **Reuniêo sensível indo para nível 4.** Risco LGPD/relacional. *Corrige:* tag explícita no agendamento + default conservador quando há dúvida.
- **Nêo revisar amostral semanal.** Resultado: agente desvia e ninguém percebe. *Corrige:* champion revisa 5 atas/semana mínimo.

---

## Variações por vertical

### Consultoria (uso típico do implementador)
- Reuniões com cliente: weekly de projeto, status, kickoff.
- Tags: cliente externo → HITL 2.
- Distribuiçêo: cliente + time interno + Pipedrive.
- Templates específicos por tipo (kickoff tem seçêo "premissas", status tem "marco/meta").

### Agência
- Reuniões: planning semanal, daily, retrospectiva, briefing com cliente.
- Distribuiçêo: time interno via Slack + cliente via e-mail (para reuniões externas).

### Escritório técnico
- Reuniões: levantamento técnico (vai pra documento de projeto), revisêo de obra/projeto.
- Distribuiçêo: time + cliente + sistema de gestêo de projetos.

### Software house / dev team
- Reuniões: planning, retro, daily, revisêo técnica.
- Distribuiçêo: Slack + Linear/Jira (criar issues automaticamente das ações).

---

## Mapeamento para DPIA

| Fase | Pré-requisitos |
|---|---|
| D | Baseline: tempo gasto em ata, % reuniões com ata, % ações claras, reuniões redundantes/semana. KPIs assinados. Champion (líder de time ou ops) decidido. |
| P | Inventário dos tipos de reuniêo (kickoff, weekly, 1:1, cliente externo). Template de ata por tipo. Lista de distribuiçêo por tipo. Sistema de transcriçêo escolhido e testado. RIPD sobre dados em reuniões (RH, financeiro, cliente externo). |
| I | system-prompt.md (4 paralelos + agregador) + playbook.md. Matriz HITL com tags de reuniêo. Homologaçêo com 10 reuniões reais — comparar ata gerada vs. ata humana. |
| A | Deploy direto em nível 4 para reuniões internas. Job shadowing 2 semanas: champion revisa todas as atas e calibra. Micro-vídeo "como tagear reuniêo sensível". |

---

*Módulo Resumo de Reuniêo v1.0 — AIOS Profissional 2027.*
