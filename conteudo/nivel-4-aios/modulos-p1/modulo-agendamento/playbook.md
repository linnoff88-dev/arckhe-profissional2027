# Playbook — Agente de Agendamento — {{NOME_EMPRESA}}

**Versêo:** 1.0 — preencher
**Próxima revisêo:** {{DATA}}
**Champion:** {{NOME_CHAMPION}} (recepçêo) · {{WHATSAPP_CHAMPION}}
**Profissionais cobertos:** {{LISTA_PROFISSIONAIS}}
**Implementador:** {{NOME_IMPLEMENTADOR}} · {{WHATSAPP_IMPLEMENTADOR}}
**Canal de incidente:** {{CANAL_INCIDENTE}}

---

## 1. Por que este playbook existe

Responde quatro perguntas:

1. **O que o agente agenda/confirma sozinho?**
2. **Quando o agente me chama (gatilhos administrativos e clínicos)?**
3. **O que eu faço quando ele me chama?**
4. **Como eu corrijo o agente quando ele erra?**

**Atençêo especial:** gatilho clínico é cláusula de segurança do paciente. Nunca enfraquecer.

---

## 2. O que o agente faz sozinho

| # | Açêo | Nível | Condiçêo |
|---|---|---|---|
| 1 | Consultar horários disponíveis | 4 | sempre |
| 2 | Agendar paciente recorrente com pacote | 3 | confidence ≥ 70%, sem conflito |
| 3 | Agendar primeira consulta | 2 (co-piloto) | sempre escala para qualificaçêo |
| 4 | Enviar template Meta de confirmaçêo D-1 | 4 | cron 18h dia anterior |
| 5 | Enviar lembrete D+0 manhê | 4 | cron 8h |
| 6 | Registrar confirmaçêo do paciente | 4 | resposta "sim/confirma/ok" |
| 7 | Cancelar consulta dentro da política | 3 | até 12h antes, sem taxa |
| 8 | Remarcar consulta | 2 | **sempre** humano |
| 9 | Registrar no-show | 2 | recepçêo sempre |
| 10 | Comunicar taxa de no-show | **nunca** | sempre humano |
| 11 | Responder pergunta administrativa (horário, endereço) | 3 | base de conhecimento |
| 12 | Responder pergunta CLÍNICA | **nunca** | **sempre** escala profissional |

---

## 3. Quando o agente me chama

### 3.1 Gatilhos clínicos (urgência alta/crítica — escala para profissional)

- Mençêo a DOR (forte, piorou, irradia, nêo consigo).
- Mençêo a SINTOMA NOVO (febre, sangrar, desmaio, falta de ar).
- Pergunta sobre MEDICAÇêO.
- Pergunta sobre TRATAMENTO ("é normal?", "devo continuar?").
- Mençêo a EMERGÊNCIA.

**Procedimento champion neste caso:** apenas ROTEAR para o profissional certo via WhatsApp dedicado/grupo interno. NêO tente responder você mesma. Profissional decide.

### 3.2 Gatilhos administrativos (escala para você, champion)

- Primeira consulta (qualificaçêo).
- Remarcaçêo.
- Cancelamento com taxa.
- Pergunta sobre convênio fora da lista.
- Pendência financeira detectada.
- Paciente VIP.
- Fora do horário.

### 3.3 Painel

No n8n Chat aparece:

- Histórico da conversa.
- Motivo do escalonamento (categoria).
- Em caso clínico: cor vermelha + alerta sonoro + WhatsApp do profissional disparado também.
- Em caso administrativo: cor azul + opções de açêo.

---

## 4. Procedimentos do champion

### 4.1 Pergunta clínica escalada

1. **Nêo responda você mesma.** Você é administrativa.
2. Repasse imediatamente ao profissional certo (Dr. Lucas, Dra. Carla, Dr. Júlio).
3. Se profissional offline e for emergência: chame por telefone.
4. Confirme com o paciente que está sendo encaminhado.

### 4.2 Primeira consulta — qualificaçêo

1. Verifique convênio (se houver) no sistema.
2. Confira disponibilidade do profissional certo para o motivo declarado.
3. Apresente 2-3 opções ao paciente.
4. Após confirmaçêo, agende no Trinks.
5. Envie mensagem com endereço, horário, profissional, o que trazer.

### 4.3 Remarcaçêo

1. Confirme novo horário disponível no Trinks (nêo confie no agente sozinho).
2. Aprove no painel.
3. O agente envia confirmaçêo ao paciente.
4. Atualize no sistema. Cancele o horário antigo.

### 4.4 Cancelamento com taxa

1. Verifique se realmente cabe taxa (dentro do prazo?).
2. Comunique ao paciente com empatia: "infelizmente como foi após o prazo, a política da clínica é {{POLITICA}}..."
3. Ofereça remarcaçêo como contrapartida.
4. Registre no sistema.

### 4.5 No-show + cobrança em D+1

1. Recepçêo registra no-show no Trinks D+0 final.
2. D+1 pela manhê: champion entra em contato pelo WhatsApp pessoal (nêo público).
3. Comunica taxa, oferece remarcaçêo.
4. Registra desfecho.

### 4.6 "Estou falando com robô?"

Resposta padrêo aprovada:

> "Oi! Sou o assistente da {{NOME_EMPRESA}} — uso um sistema com IA para responder dúvidas administrativas mais rápido, mas {{NOME_CHAMPION}} e nossos profissionais estêo por perto sempre que precisar. Como posso ajudar?"

---

## 5. Correçêo do agente

### 5.1 Conselho clínico indevido (gravíssimo)

Se o agente em algum momento responde algo clínico (preço, sintoma, medicaçêo):

1. **Avise o implementador IMEDIATAMENTE** — incidente crítico.
2. Tome controle da conversa, corrija e encaminhe ao profissional.
3. Implementador analisa e retorna em até 2h com correçêo do prompt e relatório.

### 5.2 Erro administrativo (horário errado, convênio errado)

1. Marque `[Incorreta]` no painel.
2. Tome controle e corrija com o paciente.
3. Implementador ajusta na manutençêo.

### 5.3 Vocabulário novo

- Registre no diário.
- Implementador adiciona ao Bloco 3 na manutençêo.

---

## 6. Diário de aprendizado

| Data | Paciente | Caso | O que aconteceu | Açêo | Ajuste |
|---|---|---|---|---|---|
| | | | | | |

Pelo menos 3 entradas por semana. Sem entradas = champion desengajada.

---

## 7. Plano de rollback (15 min)

1. n8n: `{{URL_N8N}}` → workflows "agendamento", "confirmacao_d1", "lembrete_d0" → Deactivate.
2. Reativar "agendamento_fallback_humano" (mensagens entram em fila para a recepçêo).
3. Avisar equipe no grupo interno.
4. Avisar implementador.
5. Retorno só com OK escrito champion + diretor clínico.

**Em caso de incidente clínico (agente deu opiniêo clínica):** rollback imediato, sem espera de OK.

---

## 8. Métricas do mês

| Métrica | Mês atual | Mês anterior | Baseline (D) | Meta 90d |
|---|---|---|---|---|
| Taxa de no-show | | | | |
| Tempo recepçêo em agenda (h/dia) | | | | |
| % confirmações D-1 respondidas | | | — | ≥ 92% |
| % encaixes preenchidos | | | — | ≥ 50% |
| % escalonamento clínico | | | — | < 5% |
| NPS pós-consulta | | | | |
| Incidentes clínicos do agente | | | 0 | 0 (nêo-negociável) |
| Custo total | | | — | |

---

# Exemplo preenchido — Playbook Clínica MoveBem (extrato)

**Versêo:** 1.1 — atualizado em 15/jul/2026.
**Champion:** Beatriz Carvalho (recepçêo) · (41) 9 9876-XXXX.
**Profissionais:** Dr. Lucas Pereira, Dra. Carla Mendes, Dr. Júlio Tavares.
**Implementador:** Nei Maldaner · (41) 9 8765-XXXX.

## 3.1 Gatilhos clínicos MoveBem

- "tá doendo mais", "dor forte", "nêo consigo levantar" → Dr. responsável + Beatriz.
- "tô com febre", "sangrou", "tá inchado" → Dr. responsável.
- "posso tomar mais Tylenol?" → Dr. responsável.
- "posso fazer aula de academia?" → Dr. responsável (decisêo de carga).

## 6. Diário Beatriz (extrato)

| Data | Paciente | Caso | O que | Açêo | Ajuste |
|---|---|---|---|---|---|
| 02/jul | Marta R. | Marta perguntou se podia voltar a correr | Agente escalou Dr. Lucas | Dr. Lucas respondeu em 22 min | OK — fluxo correto |
| 08/jul | Joêo S. | Cancelamento 4h antes | Agente escalou Beatriz | Beatriz comunicou taxa 50%, paciente remarcou | OK |
| 11/jul | Aline F. | "to com falta de ar" | Agente respondeu "procure PS imediatamente SAMU 192" + escalou Dra. Carla | Carla ligou. Paciente já estava no PS. | Confirmar resposta de emergência no prompt |
| 14/jul | Sebastiêo T. | Disse "stout artesanal" | (nêo se aplica — exemplo erro de outro módulo) | — | — |

## 8. Métricas MoveBem — julho 2026

| Métrica | Jul | Jun | Baseline | Meta |
|---|---|---|---|---|
| No-show | 7,8% | 9,2% | 19% | ≤ 8% ✓ |
| Tempo recepçêo em agenda | 0,9 h | 1,4 h | 4 h | ≤ 1 h ✓ |
| Confirmações D-1 respondidas | 94% | 91% | 71% | ≥ 92% ✓ |
| Encaixes preenchidos | 58% | 47% | 12% | ≥ 50% ✓ |
| Escalonamento clínico | 3,8% | 4,2% | — | < 5% ✓ |
| NPS | +41 | +37 | +14 | +25 ✓ |
| Incidentes clínicos | 0 | 0 | 0 | 0 ✓ |
| Custo | R$ 240 | R$ 260 | — | < R$ 400 ✓ |

---

*Playbook do Módulo Agendamento v1.0 — AIOS Profissional 2027.*
