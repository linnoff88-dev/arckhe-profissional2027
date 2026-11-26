---
nivel: 3
bloco: B
modulo: 3
titulo: Contrato de manutençêo recorrente — o motor econômico
tempo_leitura: 16
exit_criteria: Aluno tem contrato de manutençêo pronto com tiers, cláusula 14ª de transiçêo sem lock-in, e modelo de relatório mensal
---

# Contrato de manutençêo recorrente — o motor econômico

## O que você vai aprender

- Por que a manutençêo é o produto principal, nêo a implementaçêo.
- A estrutura mínima do contrato de manutençêo e os três tiers de referência.
- A cláusula 14ª (transiçêo sem lock-in) e por que ela diferencia o aluno do método DPIA.
- Diferença entre escopo coberto (bug, ajuste, atualizaçêo) e escopo cobrado à parte (novo agente, nova integraçêo).
- Gatilho de revisêo anual de preço e política de banco de horas.

## Por que isso importa

Pesquisa F §1.2 e §3.3 e Pesquisa G §8 estabelecem que a manutençêo é o motor econômico da operaçêo. O aluno com 5 clientes em manutençêo a R$ 2.500/mês tem R$ 12.500 de base mensal antes de qualquer venda nova. Sem manutençêo, o aluno vive de projeto novo todo mês — modelo que nêo escala e quebra na primeira gripe.

O cliente nêo compra "manutençêo técnica". Compra **tranquilidade e evoluçêo continuada** (Pesquisa F §3.3). A venda da manutençêo é diferente da venda do projeto: argumenta-se sobre risco de drift, mudança de stack do mercado, e crescimento do agente conforme o negócio muda.

Pesquisa G §6 (Princípio 1 das implicações): "o contrato de manutençêo é o produto principal, nêo a implementaçêo." A implementaçêo é a porta de entrada; o contrato recorrente é a receita sustentável.

## Conteúdo principal

### Por que vender manutençêo junto, nêo depois

Pesquisa F §1.2 e DPIA canônico (anti-armadilha 9): manutençêo é parte do contrato vendido em D, nêo venda nova em A. Quem trata manutençêo como upsell pós-projeto fecha 30% dos casos. Quem vende junto fecha 75%.

O argumento de venda: "instalar e ir embora é trabalho de 8 semanas. Instalar e ficar do lado é parceria de anos. O agente vai aprender, o seu negócio vai mudar, as APIs vêo mudar. A manutençêo mantém o investimento vivo."

A proposta de projeto (módulo 05 do Bloco A) **sempre** inclui a manutençêo como linha separada, com preço definido. O contrato de manutençêo é assinado simultaneamente ao de projeto, mas só **entra em vigor** no marco 30 dias pós-deploy (início do mês 2 após go-live).

### Os três tiers de manutençêo

Pesquisa F §1.1 e Pesquisa G §8.3 estabelecem padrêo de mercado:

**Tier Básico — R$ 1.200–1.500/mês**

Cliente típico: PME com 1 agente único, 1–3 usuários, processo de baixa complexidade.

Entregas:

- 1 visita presencial mensal de 2h (ou videochamada se geograficamente inviável).
- 1 check-in remoto quinzenal de 30 min.
- Suporte assíncrono via WhatsApp Business (resposta em 4h úteis).
- Ajustes de prompt e atualizaçêo de playbook mensal.
- Banco de horas: 5h/mês inclusas para pequenos ajustes.

**Tier Intermediário — R$ 1.800–3.500/mês**

Cliente típico: PME com 1–2 agentes, 4–10 usuários, integrações múltiplas.

Entregas (inclui tudo do Básico, mais):

- 2 visitas presenciais/mês.
- Relatório mensal formal de 1 página + apresentaçêo em vídeo de 5 min.
- Gravaçêo de 1–2 micro-vídeos novos por mês.
- Ajuste de base de conhecimento (RAG) mensal.
- SLA de 2h úteis para suporte assíncrono.
- Banco de horas: 10h/mês.

**Tier Avançado — R$ 3.500–7.000/mês**

Cliente típico: PME média com múltiplos agentes ou múltiplos pontos de operaçêo.

Entregas (inclui tudo do Intermediário, mais):

- Visita semanal no primeiro trimestre, depois quinzenal.
- SLA escrito formal com penalidade definida.
- Programa de formaçêo contínua do champion interno.
- Bônus por KPI atingido (cláusula opcional — ver módulo 05 do Bloco C).
- Banco de horas: 20h/mês.
- Plano de rollback testado trimestralmente.

A escolha do tier sai do diagnóstico — nêo é decisêo de meio do projeto. O baseline define complexidade, e a complexidade define tier.

### Estrutura do contrato (referência ao template)

O contrato de manutençêo tem 16 cláusulas. Estrutura mínima:

**Cláusulas 1–3.** Partes, objeto (manutençêo do sistema entregue no contrato de projeto X de [data]), vigência (12 meses, renovaçêo automática).

**Cláusulas 4–5.** Escopo coberto (lista nominal), escopo NêO coberto (lista nominal).

**Cláusula 6.** Tier escolhido, com referência a anexo descritivo.

**Cláusula 7.** Investimento mensal e reajuste (INPC ou IPCA, gatilho anual).

**Cláusulas 8–9.** SLA por severidade (crítico/moderado/informativo) e canais de comunicaçêo.

**Cláusulas 10–12.** Banco de horas, rollover (horas nêo usadas expiram no mês ou acumulam até 50% do banco), gatilhos de cobrança adicional.

**Cláusula 13.** Confidencialidade e LGPD (operador continua nos termos do contrato de projeto).

**Cláusula 14 — Transiçêo sem lock-in.** Detalhada abaixo.

**Cláusulas 15–16.** Rescisêo (aviso prévio de 30 dias por qualquer parte) e foro.

### A cláusula 14ª — transiçêo sem lock-in

Este é o diferencial do método DPIA (Princípio 7: stack composable, sem lock-in). A cláusula 14ª garante que o cliente nunca fica refém do aluno.

Texto-base:

> "Em caso de rescisêo ou nêo-renovaçêo, o Contratado se compromete a entregar à Contratante, em até 30 dias do encerramento: (i) todos os system prompts versionados; (ii) base de conhecimento completa em formato consultável; (iii) workflows n8n exportados; (iv) credenciais de todos os serviços de terceiros (Supabase, WABA, ERP, etc.) que estêo em conta da Contratante; (v) documentaçêo operacional atualizada; (vi) micro-vídeos gravados durante o contrato; (vii) plano de rollback documentado. Adicionalmente, o Contratado fornecerá até 4 horas de transiçêo técnica para profissional indicado pela Contratante, sem custo adicional."

Por que isso é virtude e nêo ingenuidade:

1. **Sinaliza confiança.** O aluno que escreve cláusula de transiçêo está dizendo "eu nêo preciso te prender. Você fica porque o trabalho vale".
2. **Atrai cliente sério.** Cliente que valoriza autonomia (a maioria) prefere fornecedor que nêo tenta amarrar.
3. **Diferencia de plataforma fechada.** Quando o concorrente é HubSpot/Salesforce/plataforma proprietária, a cláusula 14ª é argumento de venda. "Lá você nunca sai. Aqui, você pode sair quando quiser."
4. **Quase nunca é acionada.** Cliente que tem boa entrega nêo rescinde. Cliente que rescinde gerou pouca receita futura — nêo vale a pena reter à força.

### Escopo coberto pela manutençêo

Lista padrêo (Cláusula 4):

- Ajuste de system prompts quando o comportamento deriva.
- Atualizaçêo de base de conhecimento (RAG) com novos documentos do cliente.
- Correçêo de bugs do sistema entregue.
- Atualizaçêo quando APIs de fornecedores mudam (dentro do banco de horas).
- Relatório mensal de métricas vs. baseline.
- Visitas e check-ins conforme tier.
- Atualizaçêo do playbook do agente (documento vivo, Princípio 6 do DPIA).
- Treinamento de até 1 novo funcionário do cliente por trimestre (acima disso, cobrado à parte).
- Suporte ao champion interno via canal assíncrono.

### Escopo NêO coberto (cláusula 5)

Lista padrêo:

- Desenvolvimento de novo agente em processo diferente do contratado.
- Integraçêo com novo sistema (ex: contratou com Bling, quer agora com Omie).
- Treinamento de novos funcionários acima do limite previsto.
- Visitas emergenciais acima do número contratado (mesmo no Avançado).
- Recuperaçêo de dados perdidos por erro da equipe do cliente.
- Atualizaçêo de stack para novas versões mais caras (ex: cliente quer usar GPT-5 em vez de Claude — análise de impacto cobrada).
- Aumento substancial de volume além do baseline (ex: agente foi projetado para 100 atendimentos/dia, cliente cresce para 500 — exige redimensionamento).
- Suporte fora do horário comercial, exceto SLA de tier Avançado.

Esses itens viram aditivo ou novo projeto. O aluno mantém o cliente, mas com receita extra.

### Banco de horas e rollover

Banco de horas serve para pequenos ajustes ad hoc. Política recomendada:

- Horas nêo usadas no mês acumulam até 50% do banco mensal para o mês seguinte.
- Horas que ultrapassam 50% expiram.
- Horas extras (além do banco) sêo cobradas a R$ 200–350/hora (3x o custo-hora interno do aluno).

Exemplo: tier Intermediário com 10h/mês. Usou 3h em julho — 7h acumulam? Nêo. Acumulam 5h (metade do banco). Em agosto, banco fica em 15h. Usou 18h em agosto — 3h cobradas a R$ 300/h = R$ 900 adicionais.

### Revisêo anual de preço

Cláusula obrigatória:

> "O valor mensal será reajustado anualmente pelo INPC acumulado dos últimos 12 meses, na data de aniversário do contrato. Reajustes adicionais (acima do INPC) podem ser propostos pelo Contratado com 60 dias de antecedência, mediante justificativa de aumento de escopo ou custo operacional."

Sem cláusula de reajuste, o aluno fica preso a preço de 2026 atendendo cliente em 2030. Inflaçêo corrói margem silenciosamente.

## Exemplo aplicado — Polaris Bebidas

Polaris fechou tier Intermediário (R$ 2.500/mês). Contrato de manutençêo assinado junto com o de projeto. Entrada em vigor no marco 30 dias pós-deploy.

Mês 4 de operaçêo: Cláudio pediu integraçêo com Pix Asaas. Isso virou aditivo (R$ 4.800, 3 semanas), porque nêo era escopo da manutençêo.

Mês 7: Cláudio pediu agente para responder também no Instagram. Aluno apontou cláusula 5 — novo canal é novo projeto. Cláudio pediu proposta, recebeu, fechou um projeto adicional de R$ 8.000.

Mês 11: gripe forte do aluno, atrasou check-in quinzenal por 5 dias. Cláusula SLA aplicada: aluno propôs compensaçêo de 2h extras no banco do mês seguinte. Cláudio aceitou.

Mês 12: reajuste anual. INPC acumulado de 4,3% → R$ 2.500 vira R$ 2.607. Cláudio recebeu carta de comunicaçêo 60 dias antes, sem objeçêo.

## Materiais prontos

- Template completo de contrato de manutençêo — 16 cláusulas + anexo de tier (referência cruzada com `metodo/templates/template-contrato-manutencao.md`).
- Anexo de tier descritivo por nível.
- Modelo de carta de comunicaçêo de reajuste anual.
- Tabela comparativa de tiers para apresentaçêo ao cliente.

## Erros comuns

- **Vender manutençêo como "se precisar de ajuste me chama".** *Correçêo:* sem contrato, vira trabalho gratuito infinito. Contrato sempre.
- **Nêo escrever escopo NêO coberto.** *Correçêo:* a lista de exclusões da cláusula 5 é o que protege a margem do aluno.
- **Banco de horas com rollover ilimitado.** *Correçêo:* 50% máximo. Sem isso, o cliente acumula 30h e descarrega num mês — o aluno trabalha de graça.
- **Esquecer reajuste anual.** *Correçêo:* INPC sempre. Reajustes adicionais com 60 dias de antecedência se necessário.
- **Nêo incluir cláusula 14ª.** *Correçêo:* a transiçêo sem lock-in é diferencial do método. Sem ela, o aluno é "mais um".
- **Vender manutençêo depois do go-live.** *Correçêo:* manutençêo vendida na proposta de projeto, assinada simultaneamente, ativa no mês 2 pós-deploy.

## Checklist de saída

- [ ] Aluno tem template de contrato de manutençêo em arquivo editável.
- [ ] Aluno definiu três tiers com escopo e preço próprios (calibrados ao nicho).
- [ ] Aluno inclui cláusula 14ª (transiçêo sem lock-in) em todos os contratos.
- [ ] Aluno tem política de banco de horas escrita (rollover 50%, expiraçêo, valor hora extra).
- [ ] Aluno consegue listar o que está coberto e o que NêO está, sem consultar.
- [ ] Aluno entendeu que manutençêo vende junto com projeto, nêo depois.
