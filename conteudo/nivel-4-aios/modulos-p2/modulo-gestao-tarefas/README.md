# Módulo 12 — Gestêo de Tarefas (Pedidos Soltos → Tarefas Organizadas)

**Versêo:** 0.1 (especificaçêo P2) — maio/2026
**Categoria:** P2 — especificaçêo para V2 da biblioteca
**Pré-requisitos AIOS:** stack canônica + Módulo 6 (Resumo de Reuniêo) dominado (compartilha lógica de extraçêo).

---

## O que faz

Recebe **pedidos soltos** que chegam ao dono ou gestor por múltiplos canais (WhatsApp, e-mail, reuniêo informal, áudio gravado andando), organiza em **tarefas estruturadas**, prioriza por critério configurável (urgência × impacto), e mantém follow-up.

Cobre:

1. **Captura** de pedido via WhatsApp do dono (texto, áudio, encaminhamento).
2. **Extraçêo estruturada** (o quê, para quem, prazo, contexto).
3. **Priorizaçêo** (matriz urgência × impacto + dependências).
4. **Push** para PM (Trello, Asana, Linear, Notion).
5. **Lembrete proativo** de tarefas próximas do prazo.
6. **Resumo diário** ao dono (agenda + tarefas críticas).

Aplica padrêo **Prompt Chaining** (extraçêo + priorizaçêo).

---

## Quando usar

- Dono/gestor de PME que **gerencia tudo de cabeça** — pedidos chegam por todo lado, atrasos viram regra.
- Time pequeno (3-15 pessoas) onde a organizaçêo ainda é informal.
- Existe **algum sistema de PM** ativo (Trello é o mais comum em PME) ou disposiçêo de adotar Trello/Asana.
- Dono aceita usar WhatsApp como input — nêo vai migrar para sistema próprio.
- Verticais ideais: **agência, consultoria, escritório técnico, dono-operador de varejo, pequena software house**.

---

## Stack utilizada

- WhatsApp Cloud API (input do dono).
- Whisper (áudio → texto) ou serviço cloud equivalente.
- n8n.
- Claude Sonnet 4.6 para extraçêo e priorizaçêo.
- API do sistema de PM (Trello, Asana, Linear, Notion).
- Supabase para histórico e métricas.

---

## Arquitetura sumária

```
Dono manda mensagem ou áudio no WhatsApp do bot
       │
       ▼
[Se áudio] → Whisper transcreve
       │
       ▼
[Agente Sonnet] extrai:
   - o quê (descriçêo da tarefa)
   - quem é responsável (ou [INDEFINIDO] → pergunta ao dono)
   - prazo (data ou descriçêo relativa)
   - contexto e dependências
       │
       ▼
[Priorizaçêo] urgência × impacto (configurável)
       │
       ▼
GATE HITL nível 2 (primeiros 30 dias):
   dono confirma extraçêo e prioridade
       │
       ▼
Push para Trello/Asana com etiquetas
       │
       ▼
Cron diário 8h: enviar ao dono
   - tarefas do dia
   - tarefas em atraso
   - alertas de prazo (D-1, D-3)
```

---

## Nível HITL recomendado

| Operaçêo | Nível inicial |
|---|---|
| Captaçêo e extraçêo | 4 |
| Priorizaçêo | 3 (em casos de baixa confiança → escala) |
| Push para PM | 2 (primeiros 30d), depois 3 |
| Lembrete proativo | 4 |
| Resumo diário | 4 |
| **Atribuiçêo a pessoa específica** | **2 — sempre dono confirma** |

---

## Tempo estimado de construçêo (para V2)

| Fase | Dias úteis |
|---|---|
| D | 5–8 |
| P (matriz de prioridade + integraçêo PM + lista de responsáveis) | 7–12 |
| I | 7–10 |
| A | 5–10 |
| **Total** | **24–40 dias** |

Módulo de complexidade média. Bom para implementador que já dominou Módulo 6.

---

## Pré-requisitos

- **Módulo 6 (Resumo de Reuniêo) dominado** — reaproveita lógica de extraçêo de ações.
- Sistema de PM ativo ou disposiçêo para adotar.
- **Matriz de prioridade definida pelo cliente** (nêo pelo implementador).
- Lista de responsáveis com WhatsApp/e-mail para atribuiçêo.
- Dono aceita usar o módulo diariamente — sem uso, módulo morre em 30 dias.

---

## Notas para V2

- Integraçêo com **calendário** para detectar conflitos de prazo.
- Detecçêo de **tarefas duplicadas** (mesmo pedido vindo por canais diferentes).
- Sugestêo proativa: "essa tarefa tem 3 dependências em atraso" — agente reordena.
- Considerar canal Slack como input alternativo ao WhatsApp.

---

*Especificaçêo Módulo Gestêo de Tarefas v0.1 — AIOS Profissional 2027.*
