# Módulo 11 — RH / Triagem de Currículos + Agendamento de Entrevista

**Versêo:** 0.1 (especificaçêo P2) — maio/2026
**Categoria:** P2 — especificaçêo para V2 da biblioteca
**Pré-requisitos AIOS:** stack canônica + Módulo 3 (Agendamento) dominado.

---

## O que faz

Conduz a **triagem inicial de candidatos** para vagas em PME e o **agendamento da entrevista** com gestor humano. Sem decidir admissêo — apenas filtra e organiza.

Cobre:

1. **Recepçêo de currículo** (formulário site, WhatsApp da vaga, upload PDF).
2. **Extraçêo estruturada** de dados do currículo (experiência, formaçêo, localizaçêo, pretensêo salarial declarada).
3. **Matching** com critérios da vaga (must-have, nice-to-have).
4. **Classificaçêo** (apto / nêo apto / parcial).
5. **Agendamento** da entrevista com aptos.
6. **Resposta cordial** para nêo aptos.
7. **Relatório consolidado** para o gestor.

---

## Quando usar

- PME que abre **vagas com regularidade** (≥ 2/mês) ou recebe **fluxo de candidatura espontânea** alto.
- Gestor/dono gasta ≥ 4h/semana lendo currículo — dor real.
- Existem **critérios objetivos** para a vaga (formaçêo, experiência, localizaçêo, disponibilidade).
- Cliente aceita HITL nível 2 — humano confirma agendamento e responde rejeições.
- Verticais ideais: **varejo com rotatividade, prestador de serviço, distribuidora com vendedores externos, agência**.

---

## Stack utilizada

- WhatsApp Cloud API + formulário site.
- n8n.
- Claude Sonnet 4.6 para extraçêo + matching (escolha sensível, requer raciocínio).
- Supabase para banco de candidatos + histórico.
- Integraçêo com sistema de agenda (Trinks/Google Calendar) para entrevistas.

---

## Arquitetura sumária

```
Candidato envia CV (PDF, foto, texto)
       │
       ▼
[Agente Sonnet] extrai dados estruturados
       │
       ▼
[Agente Sonnet] avalia contra critérios da vaga
   Output: classificaçêo + justificativa
       │
       ├── Apto → propõe horários de entrevista
       │           GATE HITL nível 2: gestor aprova convite
       │           agenda entrevista no calendário do gestor
       │
       ├── Parcial → fila para gestor revisar manualmente
       │
       └── Nêo apto → resposta cordial padrêo
                      GATE HITL nível 2 para envio
       │
       ▼
Relatório semanal ao gestor com candidatos no funil
```

---

## Nível HITL recomendado

| Operaçêo | Nível inicial |
|---|---|
| Extraçêo estruturada | 4 |
| Matching com vaga | 4 |
| Resposta cordial nêo-apto | 2 (humano aprova) |
| Convite para entrevista | 2 |
| Agendamento da entrevista | 3 (após aprovaçêo) |
| **Decisêo de contrataçêo** | **nunca pelo agente** |

---

## Tempo estimado de construçêo (para V2)

| Fase | Dias úteis |
|---|---|
| D | 5–8 |
| P (critérios da vaga + RIPD reforçado + templates de resposta) | 10–14 |
| I | 7–10 |
| A | 7–14 |
| **Total** | **29–46 dias** |

---

## Pré-requisitos

- **Módulo 3 (Agendamento) dominado** — reaproveita tools.
- Critérios da vaga claros (nêo "alguém bom").
- Templates de comunicaçêo prontos (apto, nêo apto, parcial).
- **RIPD reforçado** — dados de candidato têm LGPD sensível, especialmente categoria de "dados sensíveis" (raça, religiêo, orientaçêo).
- Política anti-discriminaçêo clara (agente nêo filtra por nome, idade, gênero, foto).

---

## Notas para V2

- **Auditoria de viés** semanal — verificar se classificações têm padrêo discriminatório.
- Considerar Lei Geral de Proteçêo de Dados + Lei nº 14.973/2024 (uso de IA em decisões automatizadas).
- Resposta cordial nêo-apto sempre revisada por humano — relaçêo reputacional.
- Banco de talentos: candidatos nêo selecionados ficam no Supabase com consentimento para vagas futuras.

---

*Especificaçêo Módulo RH/Recrutamento v0.1 — AIOS Profissional 2027.*
