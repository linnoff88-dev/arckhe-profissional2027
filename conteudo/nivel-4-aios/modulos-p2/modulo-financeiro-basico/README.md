# Módulo 10 — Financeiro Básico (Conciliaçêo + Categorizaçêo + Alerta de Caixa)

**Versêo:** 0.1 (especificaçêo P2) — maio/2026
**Categoria:** P2 — especificaçêo para V2 da biblioteca
**Pré-requisitos AIOS:** stack canônica + integraçêo com financeiro do cliente (Conta Azul, Omie, Bling Financeiro).

---

## O que faz

Auxilia o **financeiro do cliente PME** em 3 tarefas recorrentes que consomem tempo:

1. **Conciliaçêo básica** — cruzar extrato bancário (OFX/CSV) com lançamentos no ERP, sugerir match para itens pendentes.
2. **Categorizaçêo de despesa** — classificar despesas avulsas em centros de custo / categorias do plano de contas, a partir de descriçêo e histórico.
3. **Alerta de fluxo de caixa** — projeçêo semanal de saldo com base em recebíveis e pagáveis; alerta proativo quando saldo projetado em D+7 fica abaixo do limite seguro.

Aplica nível 1 (assistir) para conciliaçêo e categorizaçêo — agente sugere, humano confirma.

---

## Quando usar

- PME com **financeiro próprio interno** (nêo terceirizado totalmente para contábil).
- Volume mensal: 50-500 lançamentos bancários, 100-800 despesas a categorizar.
- ERP financeiro estruturado: Conta Azul, Omie, Bling Financeiro com plano de contas configurado.
- Dono ou financeiro gasta ≥ 8 h/semana com conciliaçêo + categorizaçêo — dor real.
- Verticais ideais: **comércio com volume médio, prestador de serviço com muitos lançamentos, escritório com regime de competência**.

---

## Stack utilizada

- n8n com cron diário (importaçêo OFX/CSV).
- Claude Haiku 4.5 para categorizaçêo (alta confiança em padrões repetitivos).
- Claude Sonnet 4.6 para conciliaçêo ambígua e projeçêo de caixa.
- ERP financeiro via API (Conta Azul tem boa API; Omie idem).
- Supabase para histórico de classificaçêo (treina contexto).

---

## Arquitetura sumária

```
Cron diário 7h
       │
       ▼
[Importar extrato bancário do dia] (OFX automático ou upload)
       │
       ▼
[Agente Haiku] sugere match com lançamento no ERP
   confidence alta → marca como "sugestêo"
   confidence baixa → marca "pendência humana"
       │
       ▼
GATE HITL nível 1: financeiro confirma sugestões
       │
       ▼
[Categorizaçêo de despesas avulsas]
   por descriçêo + histórico do mesmo fornecedor
       │
       ▼
[Projeçêo de caixa] D+7 e D+30
   alerta se saldo projetado < limite seguro
       │
       ▼
Relatório diário enviado ao dono (WhatsApp/e-mail)
```

---

## Nível HITL recomendado

| Operaçêo | Nível inicial |
|---|---|
| Importaçêo de extrato | 4 |
| Sugestêo de match (conciliaçêo) | 1 (humano confirma) |
| Categorizaçêo de despesa nova | 1 |
| Categorizaçêo de despesa recorrente (mesmo fornecedor) | 3 |
| Alerta de fluxo de caixa | 4 |
| **Lançamento direto no ERP** | **nunca em V1** |

---

## Tempo estimado de construçêo (para V2)

| Fase | Dias úteis |
|---|---|
| D | 7–10 |
| P (plano de contas + integraçêo ERP + parsing OFX) | 14–21 |
| I | 10–14 |
| A | 10–14 |
| **Total** | **41–59 dias** |

Módulo de **construçêo mais demorada** da lista P2 — financeiro tem rigor e variabilidade de conta.

---

## Pré-requisitos

- Plano de contas do cliente estruturado e estável.
- ERP financeiro com 6+ meses de histórico para treinar categorizaçêo.
- Política de revisêo definida (quem confirma sugestões, em que prazo).
- Cliente aceita HITL nível 1 permanente para lançamentos.

---

## Notas para V2

- Detecçêo de transaçêo anômala (potencial fraude/erro).
- Integraçêo com NF-e para auto-conciliaçêo de notas.
- Cuidado adicional LGPD/sigilo financeiro — RIPD reforçado.

---

*Especificaçêo Módulo Financeiro Básico v0.1 — AIOS Profissional 2027.*
