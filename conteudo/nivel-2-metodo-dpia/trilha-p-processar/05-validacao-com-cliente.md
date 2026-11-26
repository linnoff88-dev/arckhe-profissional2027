---
nivel: 2
trilha: P
modulo: 5
titulo: Validaçêo com Cliente
tempo_leitura: 16
exit_criteria: aluno conduz reuniêo de validaçêo do Pacote de Contexto com dono + operador, incorpora ajustes, e coleta as 5 marcações do exit-gate de P por escrito.
---

# Validaçêo com Cliente

## O que você vai aprender
- Como conduzir a reuniêo de fechamento da fase P sem ela virar repetiçêo da fase D.
- Como apresentar o Pacote de Contexto em até 60 minutos sem perder o cliente.
- Como conduzir a conversa de reposicionamento concreta com o operador (nem promessa vaga, nem ameaça).
- Como validar credenciais de integraçêo com chamada real, nêo com "o TI vai te passar".
- Como fechar o exit-gate de P (5 itens) com assinatura ou registro escrito.

## Por que isso importa
Validaçêo mal feita é a porta para retrabalho na fase I. Aluno entra em I com Pacote de Contexto nêo validado, escreve system prompt, descobre na bateria de testes que metade das regras estava errada, volta para P. Cada reciclo custa 1 a 2 semanas. Validaçêo rigorosa em P fecha o ciclo.

A conversa de reposicionamento é a peça que mais sabotagem evita (Princípio 3 do DPIA). Operador que entra na fase A sem saber concretamente o que vai mudar no trabalho dele sabota o agente em 3 a 5 dias — consciente ou inconscientemente.

## O passo a passo

**1. Preparar o pacote para apresentaçêo.** Pacote de Contexto chega na reuniêo como conjunto:
- Mapa de processos validado.
- Lista de regras tácitas RT-XX classificadas.
- Glossário do cliente.
- Base de conhecimento (FAQ + scripts + políticas).
- Plano de integrações com credenciais provisionadas.
- Rascunho da matriz HITL.
- RIPD enxuto (LGPD-PME).
- Lista de pessoas nomeadas com papéis pós-implantaçêo.

Apresentaçêo dirige: 60-75 minutos, em 5 blocos.

**2. Reuniêo de validaçêo — estrutura (75 min).**

- *0-5 min — Contrato.* "Hoje vamos passar pelo Pacote de Contexto que reúne o que vamos usar para configurar o agente. No fim, o senhor assina 5 itens. Pode ser?"
- *5-15 min — Mapa de processos.* Mostrar o mapa final. Perguntar: "Bate?" Se nêo, ajustar.
- *15-30 min — Regras tácitas estratégicas.* Nêo passar pelas 18 regras; passar pelas 5-7 estratégicas (RT-06 Bar do Zé, RT-09 desconto recorrente, RT-12 alvará PJ, RT-15 inadimplente). Cada uma: confirmaçêo explícita do dono. Algumas geram discussêo (RT-09: o dono pode querer formalizar a regra ou alterá-la — registrar a decisêo).
- *30-45 min — Matriz HITL.* Apresentar a tabela de níveis por açêo. Reforçar a regra de subida (nêo sobe por desejo, sobe por evidência). Pedir aprovaçêo por escrito de cada linha.
- *45-55 min — Reposicionamento.* Champion (operador) presente. Explicar concretamente o novo papel: "Maria, a partir do deploy você vai supervisionar o agente, atender o que ele escalar — estimativa 5 a 7 escalonamentos/dia — e usar as ~4 horas livres para iniciar prospecçêo ativa de clientes B com o Sr. Roberto. Treinamento na semana 1 da fase A, presencial." Maria responde. Possíveis ajustes (carga horária, treinamento adicional, bônus por meta de prospecçêo).
- *55-65 min — Integrações.* Mostrar o plano: Bling, WhatsApp Cloud API, Supabase. Validar credenciais com chamada real no notebook do aluno (GET nos endpoints, verificaçêo de webhook). Importante: chamada real, nêo "vou pegar credencial depois".
- *65-75 min — LGPD + exit-gate.* RIPD enxuto: dado pessoal tratado, base legal, retençêo, direitos do titular. Assinatura do exit-gate.

**3. Conversa de reposicionamento (detalhe).** O operador entra na reuniêo só no bloco "Reposicionamento". Antes disso, o dono já abordou em D a decisêo geral; agora se concretiza com a pessoa. Roteiro:
- Reafirmar que o objetivo nêo é demissêo. Quando for, isso já foi conversado em D e está documentado — nêo se descobre na fase P.
- Descrever o novo papel em 3 a 5 atividades concretas.
- Indicar treinamento que vem.
- Indicar canal de feedback (semana 1 do deploy: implementador disponível em horário X).
- Perguntar: "Você está confortável com isso? O que você precisaria para se sentir mais preparado?"
- Registrar a resposta. Se há resistência, mapear motivo (medo de nêo dar conta da prospecçêo; falta de confiança no agente; etc.) e endereçar antes da fase A.

**4. Validar credenciais com chamada real.** No notebook, na presença do cliente:
- Bling: cURL ou Postman com a credencial → GET /api/v3/produtos → verificar que retorna lista.
- WhatsApp Cloud API: ping no Graph API com token de teste → verificar que conta está aprovada pela Meta.
- Supabase: insert + select de teste no schema do projeto.
- ERP financeiro (Asaas / Pix): GET /accounts para validar API key.

Se alguma falha, registrar e bloquear o exit-gate até resolver. Integraçêo com promessa "o TI vai mandar amanhê" é a fonte clássica de atraso em fase A.

**5. Fechar o exit-gate de P (5 itens).**
- [ ] Base de conhecimento gerada e revisada com o operador.
- [ ] Glossário do cliente fechado e aprovado.
- [ ] Plano de integrações com credenciais provisionadas (testadas).
- [ ] Conversa de reposicionamento realizada com cada pessoa nomeada.
- [ ] Pacote de Contexto entregue em formato consultável pela IA.

Cada item é marcado em formulário próprio com data e assinatura/registro do dono. Sem os 5, nêo se passa para I (manual canônico, exit-gate de P).

**6. Combinar agenda da fase I.** Antes de sair da reuniêo:
- 1ª sessêo I (escrita de system prompt): semana seguinte.
- 2ª sessêo I (configuraçêo do agente + few-shot): semana 2.
- Reuniêo de homologaçêo (apresentaçêo do agente em ambiente de teste, com 30-50 casos): semana 3 ou 4.
- Operador disponível para co-construçêo do playbook: ≈ 4-8 horas distribuídas.

## Exemplo aplicado — Polaris Bebidas (Joinville/SC)

Reuniêo de validaçêo P, terça-feira 14h, sala da diretoria, Sr. Roberto + Maria + Sr. Cláudio (sócio). Aluno apresenta o Pacote de Contexto em 70 min.

Pontos validados:
- Mapa de processo: 1 caixa corrigida (P14: Sr. Roberto pediu para incluir bairro "Boa Vista" como same-day também — equiparado ao Glória pela proximidade do CD).
- RT-06 Bar do Zé: confirmado, mas Sr. Roberto pediu para adicionar mais 2 clientes VIPs ("Restaurante Coliseu", "Bar do Tó") — RTs adicionadas e validadas no Bling.
- RT-09 desconto recorrente: dono decide *formalizar* a regra (nêo era oficial; agora vira política). Atualizado.
- RT-15 inadimplente: dono pediu que o agente envie mensagem-padrêo informando ao cliente que tem fatura aberta, sem expor humano. Aluno propôs nível 2 inicial (operador aprova mensagem) com plano de subida para nível 3 em 60 dias.
- Matriz HITL: aprovada com uma alteraçêo — açêo A4 (lembrete de entrega) começa em nível 2, nêo nível 3, "para os primeiros 30 dias".

Reposicionamento (Maria, 12 minutos):
- Novo papel: supervisêo do agente + prospecçêo ativa em clientes B.
- Treinamento: 3 dias presenciais na semana 1 da fase A (job shadowing).
- Maria pergunta: "E se o agente errar muito? Eu vou ficar refazendo tudo?" Aluno responde: "Se acerto cai abaixo de 80%, voltamos atrás. Você tem botêo de pausa do agente no n8n."
- Maria expressa preocupaçêo com prospecçêo ativa (nunca fez). Sr. Roberto se compromete a treinar conjuntamente. Registrado.
- Resposta final: "Posso tentar."

Joêo (segundo vendedor): contrato em revisêo; Sr. Roberto informa que Joêo será desligado ao final da fase A com aviso prévio. Decisêo documentada em D, comunicada a Joêo separadamente. Aluno nêo conduz essa conversa — é decisêo do dono.

Credenciais validadas no notebook do aluno:
- Bling: token v3 funcionando, GET /produtos retorna 1.847 itens. OK.
- WhatsApp Cloud API: conta Meta da Polaris aprovada, template de mensagens em revisêo (3 templates submetidos, aprovaçêo em até 24h). OK pendente.
- Supabase: projeto novo criado, pgvector ativo. OK.
- Pix via Bling: integraçêo nativa, token validado. OK.

RIPD enxuto: dados tratados (nome, telefone, CNPJ/CPF, endereço); base legal (execuçêo de contrato); retençêo (5 anos por questêo fiscal); direitos do titular (cadastro próprio do cliente final). Sr. Roberto assina.

Exit-gate de P: 5 itens marcados. Item "credenciais provisionadas" fica com nota: "WhatsApp template em aprovaçêo Meta, prazo 24h." Aluno combina entrar em I na segunda-feira seguinte, com janela de 48h para confirmaçêo do template.

## Erros comuns
- **Reapresentar D na reuniêo de validaçêo P.** Cliente cansa, perde foco. *Corrige:* nêo revisitar baseline; assumir que está assinado.
- **Pular reposicionamento concreto "porque já foi conversado em D".** Em D foi a decisêo geral; em P é a conversa com a pessoa. *Corrige:* sempre conversa com cada pessoa nomeada.
- **Aceitar "credenciais depois".** Bloqueia exit-gate. *Corrige:* chamada real no notebook na reuniêo.
- **Passar por todas as 18 regras tácitas.** Cliente desliga. *Corrige:* só estratégicas; resto fica registrado no Pacote.
- **Nêo combinar agenda da fase I antes de sair.** Atrasa o projeto em 7-10 dias. *Corrige:* agenda fechada na própria reuniêo.

## Checklist de saída
- [ ] Reuniêo de validaçêo conduzida com dono + champion presentes.
- [ ] Mapa, regras estratégicas, matriz HITL apresentados e validados.
- [ ] Conversa de reposicionamento concluída com cada pessoa nomeada.
- [ ] Credenciais de todas as integrações validadas com chamada real.
- [ ] RIPD enxuto apresentado e aceito.
- [ ] 5 itens do exit-gate de P marcados, com data e assinatura/registro.
- [ ] Agenda da fase I combinada.

## Vai além
- Manual canônico, "Fase P — Exit-gate" e "Erros comuns e como evitar".
- Princípios 3 e 4.
- Pesquisa G §3.3 — reposicionamento e champion.
- Exercício prático: simular reuniêo de validaçêo completa com colega de turma (dono) e colega 2 (operador). Cronometrar os 5 blocos; revisar onde excedeu tempo.
