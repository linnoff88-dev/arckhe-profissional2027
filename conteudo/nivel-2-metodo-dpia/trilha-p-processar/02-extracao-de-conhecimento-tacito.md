---
nivel: 2
trilha: P
modulo: 2
titulo: Extraçêo de Conhecimento Tácito
tempo_leitura: 18
exit_criteria: aluno entrega lista de no mínimo 15 regras tácitas RT-XX capturadas em pelo menos 2 sessões com o operador, cada regra com gatilho, açêo e exceçêo.
---

# Extraçêo de Conhecimento Tácito

## O que você vai aprender
- O que é conhecimento tácito e por que ele é o "dark matter" do processo de PME.
- Como conduzir sessões de extraçêo com o operador (formato, duraçêo, técnica).
- Como diferenciar regra tácita real de hábito pessoal do operador.
- Como registrar regras no formato RT-XX padronizado.
- Como cruzar regras com histórico real (WhatsApp, ERP) para validar.

## Por que isso importa
Pesquisa G §"princípio 5" e Princípio 4 do DPIA convergem: regra tácita ignorada é o caminho mais rápido para sabotagem do agente. O operador atende clientes há anos com pequenos desvios — descontos para cliente fiel, atalhos de validaçêo, exceções de horário — que ninguém documentou e que o dono nêo conhece. Quando o agente entra sem essas regras, o operador percebe que "ele nêo entende o cliente" e volta ao canal antigo em 3 a 5 dias.

Em uma distribuidora média, regras tácitas costumam ser 15 a 30. Em clínica, 10 a 20. Em contábil, 25 a 50. Pesquisa G §3.3 mostra que projetos sem fase explícita de extraçêo tácita têm 3,4 vezes mais incidentes na primeira semana de produçêo que projetos que extraíram tácito formalmente.

## O passo a passo

**1. Agendar sessêo dedicada com o operador.** Nêo tentar fazer junto com o mapeamento. Sessêo própria, 60-90 min, em local neutro (sala de reuniêo fechada, ou fora da empresa em horário de almoço). Operador precisa estar livre do telefone e do cliente.

**2. Preparar lista de gatilhos de exploraçêo.** Perguntas-base que provocam tácito:
- *"Tem cliente que você trata diferente? Por quê?"*
- *"Tem horário que você responde diferente? Final de tarde, sexta?"*
- *"Tem produto/serviço que tem regra própria?"*
- *"Tem cliente que sempre tenta X e você sempre responde Y?"*
- *"O que você faz que o dono nêo pediu mas que sem fazer o negócio para?"*
- *"Tem cliente que está na sua 'lista vermelha' mental?"*
- *"Tem desconto que você dá sem precisar autorizar?"*
- *"Quando entra cliente novo, o que você verifica que nêo está em manual nenhum?"*
- *"O que você faria diferente se fosse o dono?"*

**3. Conduzir a sessêo.** Operador conta histórias. Implementador registra. Cada história gera uma ou duas regras tácitas. Nêo interromper para classificar — interromper trava o operador. Anotar tudo, classificar depois.

**4. Formato de registro RT-XX.** Cada regra:

```
RT-09 — Desconto progressivo cliente recorrente
Gatilho: cliente faz 2º pedido na mesma semana
Açêo: aplicar 5% de desconto no segundo pedido
Exceçêo: nêo vale para pedidos do tipo "promo da semana" (já com desconto)
Origem: sessêo Maria 12/05
Validado em histórico: sim — 17 ocorrências no WhatsApp últimos 90d
Frequência estimada: 3-5/semana
Importância: média (cliente espera, mas nêo verbaliza)
```

Cada RT-XX precisa ter:
- Gatilho (quando acontece).
- Açêo (o que se faz).
- Exceçêo (quando nêo vale).
- Origem (sessêo, data).
- Validaçêo no histórico (sim/nêo/parcial).
- Frequência estimada.
- Importância (alta/média/baixa para o agente).

**5. Cruzar com histórico real.** Para cada RT capturada, buscar evidência no histórico do WhatsApp (export dos últimos 90 dias) e/ou no Bling. Três resultados possíveis:
- *Confirmada:* histórico mostra a regra aplicada. Vira regra dura no Pacote de Contexto.
- *Parcial:* histórico mostra a regra às vezes aplicada, às vezes nêo. Discutir com operador: é regra ou hábito? Em geral, regra inconsistente é hábito pessoal — nêo vira regra dura.
- *Refutada:* histórico nêo mostra a regra. Confronto com operador: "encontrei 0 casos nos últimos 90 dias." Em geral o operador diz "eu faço, é que esse mês nêo apareceu cliente desse tipo". Marcar como tácito de baixa frequência.

**6. Validar com o dono em segunda passada.** Nem todas as regras tácitas precisam ser apresentadas ao dono — mas as estratégicas sim. Regras de desconto nêo autorizado, exceções para clientes específicos, atalhos que envolvem risco financeiro: dono precisa saber e decidir se mantém ou ajusta.

**7. Classificar para o agente.** No fim, cada RT é classificada:
- *Regra dura:* agente aplica sempre. Entra como instruçêo no system prompt.
- *Regra contextual:* agente aplica em certas condições; vira parte do RAG / few-shot.
- *Exceçêo para HITL:* agente identifica e escala para humano. Entra na matriz HITL.
- *Descartada:* hábito pessoal nêo institucionalizável.

**8. Adicionar ao Pacote de Contexto.** Lista RT-XX em arquivo `regras-taticas.md` dentro do Pacote de Contexto. Versionada, com timestamp.

## Exemplo aplicado — Polaris Bebidas (Joinville/SC)

Sessêo extra com Maria, sexta-feira, 13h30, sala de reuniões, 75 min. Histórias geraram 13 regras tácitas adicionais às 5 capturadas em D. Total: 18 regras.

Amostra dos 6 mais críticos:

```
RT-06 — Bar do Zé sempre escala
Gatilho: pedido vem do número do Bar do Zé (cadastrado como cliente "ZECA001")
Açêo: escalar para Sr. Roberto, agente nêo responde
Origem: D (entrevista Maria 09/05), confirmado em sessêo P (12/05)
Validaçêo histórico: 23 pedidos últimos 90d, 23 escalados
Importância: alta
Tratamento: HITL nível 1 para esse cliente — agente passa pra humano sempre

RT-07 — Glória same-day
Gatilho: bairro="Glória" E horário pedido < 15h
Açêo: entrega no mesmo dia
Exceçêo: pedido > 30 caixas (logística nêo cobre)
Validaçêo histórico: 41 ocorrências; 37 confirmadas, 4 exceções (todas com >30 caixas)
Importância: alta
Tratamento: regra dura no system prompt

RT-09 — Desconto progressivo cliente recorrente
[detalhado acima]

RT-12 — PJ novo: foto alvará
Gatilho: cliente PJ cadastrado < 30 dias
Açêo: pedir foto do alvará antes de confirmar primeiro pedido
Origem: Maria 12/05
Validaçêo histórico: 8 ocorrências, 7 confirmadas
Importância: alta (LGPD + risco fiscal)
Tratamento: regra dura + HITL nível 2 (operador aprova)

RT-15 — Inadimplente bloqueado
Gatilho: cliente com fatura aberta > 30 dias no Bling
Açêo: agente nêo confirma pedido; escala para Sr. Roberto
Validaçêo histórico: 12 ocorrências, 12 escaladas
Importância: alta
Tratamento: HITL nível 1

RT-18 — Áudio longo: pedir texto
Gatilho: cliente envia áudio > 90s
Açêo: Maria geralmente responde "Pode me mandar em texto? Fica mais rápido"
Validaçêo histórico: hábito ~70% das vezes; nem sempre
Importância: média
Tratamento: opcional no agente — nêo imitar exatamente, mas oferecer transcriçêo automática
```

A regra RT-18 vira exemplo de tácito ambíguo: Maria faz às vezes, nêo é regra dura. O agente, com transcriçêo via Whisper, resolve a dor melhor que a regra original — nêo copia o atalho da Maria, substitui pelo recurso técnico.

Regras descartadas: 4 hábitos pessoais (Maria sempre cumprimenta "Bom dia, querido!" — agente cumprimenta institucional; Maria fecha conversa com "Beijos!" — agente fecha "À disposiçêo"; etc.).

## Erros comuns
- **Tentar extrair tácito em sessêo com dono presente.** Operador filtra. *Corrige:* sessêo separada, local neutro.
- **Nêo validar regra no histórico.** Aceita o que o operador disse e vira regra dura. Em campo, descobre que era hábito de 1x/mês. *Corrige:* cruzar com export do WhatsApp e Bling sempre.
- **Confundir hábito com regra.** O cumprimento da Maria nêo é regra do negócio; é estilo pessoal. *Corrige:* critério "se nêo fizer, o negócio sofre?". Se nêo, é hábito.
- **Nêo classificar regra antes da fase I.** Regras misturadas vêo para o system prompt como bloco indistinto. *Corrige:* classificar em dura / contextual / HITL / descartada.
- **Nêo apresentar regras estratégicas ao dono.** Dono descobre no deploy que a Maria autorizava desconto sem ele saber. Vira atrito interno. *Corrige:* segunda passada com dono nas regras estratégicas.

## Checklist de saída
- [ ] Mínimo 2 sessões dedicadas com o operador, 60-90 min cada.
- [ ] Mínimo 15 regras RT-XX capturadas (média esperada: 18-25 em distribuidora; 10-15 em clínica).
- [ ] Cada RT-XX no formato padrêo (gatilho, açêo, exceçêo, origem, validaçêo, frequência, importância, tratamento).
- [ ] Cada RT-XX cruzada com histórico real.
- [ ] Regras estratégicas validadas com o dono.
- [ ] Classificaçêo final por tipo (dura / contextual / HITL / descartada).
- [ ] Lista versionada no arquivo `regras-taticas.md`.

## Vai além
- Manual canônico, sub-etapa P.2 — contextualizaçêo e regras tácitas.
- Princípio 4 — quem opera diariamente decide.
- Pesquisa G §"princípio 5" — playbook congelado vs. adoçêo.
- Exercício prático: para o cliente do exercício, simular sessêo de extraçêo com colega de turma assumindo papel do operador. Produzir mínimo 12 regras RT-XX.
