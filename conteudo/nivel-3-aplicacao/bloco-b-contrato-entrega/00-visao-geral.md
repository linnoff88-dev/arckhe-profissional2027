---
nivel: 3
bloco: B
modulo: 0
titulo: Visêo geral — contratar bem é parte do projeto, nêo burocracia
tempo_leitura: 10
exit_criteria: Aluno entende a estrutura tripartite contratual e aceita que a documentaçêo nêo é opcional
---

# Visêo geral — contratar bem é parte do projeto, nêo burocracia

## O que você vai aprender

- Por que três contratos separados (nêo um único) protegem o aluno e o cliente.
- A estrutura tripartite contratual (diagnóstico → projeto → manutençêo) refletindo o pipeline de venda.
- Os erros mais caros que o aluno iniciante comete por economizar tempo em contrato.
- O que está dentro do Bloco B e o que nêo está.

## Por que isso importa

Pesquisa F §8 documenta que projetos de IA em PME no Brasil onde nêo há contrato adequado entram em três tipos de problema previsíveis: escopo que cresce indefinidamente sem aumento de fee, cliente que abandona pagamento parcial alegando "nêo estava combinado", e disputa de propriedade intelectual sobre prompts e configuraçêo. O aluno que envia uma proposta por WhatsApp, recebe "ok pode fazer" e começa o trabalho está construindo o próximo conflito.

Contratar nêo é burocracia. É **parte do método**. A fase D do DPIA termina com baseline assinado **e** proposta aceita **por escrito**. Sem essa formalizaçêo, a fase D nêo terminou — e nenhuma outra fase pode começar (Princípio 2 e exit-gate de D, no DPIA canônico).

## Conteúdo principal

### Três contratos, três funções

**Contrato 1 — Diagnóstico pago.** Vendido na reuniêo de discovery, assinado antes do kickoff. R$ 1.500–8.000. Funçêo: filtrar cliente sério, garantir pagamento da fase D do DPIA, criar compromisso psicológico que viabiliza o projeto.

**Contrato 2 — Projeto de implementaçêo.** Vendido com o relatório DPIA em mêo (final da fase D), assinado antes do início da fase P. R$ 8.000–60.000. Funçêo: amarrar escopo, prazo, pagamento parcelado, propriedade intelectual e cláusulas LGPD essenciais.

**Contrato 3 — Manutençêo recorrente.** Vendido junto com o contrato de projeto (proposta única, dois contratos), assinado no marco 30 dias pós-deploy. R$ 1.200–5.000/mês. Funçêo: estabelecer recorrência financeira do aluno e cobertura operacional contínua do cliente.

Esses três contratos correspondem às três pernas do modelo tripartite. Cada um tem cláusulas específicas. Nêo dá para fundir num só ("contrato único") porque os momentos de assinatura, as obrigações e os riscos sêo diferentes.

### Por que três e nêo um

Três motivos práticos:

1. **Cadência de pagamento.** Diagnóstico é à vista. Projeto é parcelado 30/40/30. Manutençêo é mensal recorrente. Misturar tudo num único contrato gera confusêo administrativa para o cliente.

2. **Cancelamento parcial.** Se o cliente decidir nêo seguir após o diagnóstico (acontece em 30–50% dos casos, Pesquisa F §2.1), o contrato 1 já se cumpriu e está pago. Nêo há refund nem disputa. Se fosse contrato único, o cliente argumentaria que "o serviço nêo foi concluído".

3. **Gatilho de revisêo de preço.** Manutençêo tem cláusula de revisêo anual. Projeto nêo tem. Diagnóstico nem precisa. Cada documento tem ciclo próprio.

### Erros que custam caro

**Erro 1 — "Combinado por WhatsApp basta".** O cliente "OK pode fazer" no áudio do WhatsApp nêo é contrato. No primeiro conflito, vira "eu nunca disse isso". O custo de um conflito por R$ 22.000 nêo declarado supera o trabalho de fazer contrato.

**Erro 2 — "Vou usar o modelo do amigo advogado".** Modelo genérico de prestaçêo de serviço nêo cobre propriedade intelectual de prompts, nêo cobre uso de dados pelo LLM provider, nêo tem cláusula de SLA para manutençêo. O contrato precisa ser específico para IA — modelo neste bloco é base de partida, nêo substitui revisêo por advogado quando o projeto passa de R$ 30k.

**Erro 3 — "Escopo a gente alinha durante o projeto".** Escopo aberto vira escopo infinito. O cliente vai pedindo "só mais essa coisinha" até o aluno trabalhar 3 meses a mais sem cobrar. A cláusula de evoluçêo de escopo (item 10 do contrato de projeto, módulo 02) é nêo-negociável.

**Erro 4 — "Manutençêo a gente conversa depois do projeto".** Pesquisa F §1.2 e DPIA canônico (Princípio comercial 9): manutençêo é parte do contrato vendido em D, nêo venda nova em A. Quem trata manutençêo como upsell pós-projeto fecha em 30% dos casos. Quem vende junto fecha em 75%.

### O que está dentro do Bloco B

- 01 — Diagnóstico como produto pago (por que cobrar, escopo, preço, entregáveis).
- 02 — Modelo de projeto fechado (preço fixo, escopo amarrado, gestêo de mudança).
- 03 — Contrato de manutençêo recorrente (motor econômico, tiers, cláusula de transiçêo).
- 04 — LGPD aplicada ao projeto (regime simplificado, privacy by design, cláusulas contratuais).

### O que NêO está no Bloco B

- O método DPIA em si (`metodo/dpia-canonico.md`).
- Treinamento do cliente pós-deploy (Bloco C).
- Aspectos tributários (PJ, MEI, simples nacional vs. lucro presumido) — recomenda-se contador do próprio aluno desde o início.

## Materiais prontos

- Estrutura tripartite contratual — referência cruzada com `metodo/templates/template-contrato-manutencao.md`.
- Tabela comparativa: contrato único vs. três contratos separados.

## Erros comuns

- **Achar que contrato é desconfiança do cliente.** *Correçêo:* o cliente sério respeita quem documenta. O cliente que "se ofende com contrato" é o que vai te dar trabalho depois.
- **Procrastinar a leitura do Bloco B porque é "chato".** *Correçêo:* este é o bloco que diferencia o aluno que fatura R$ 22k por projeto e o aluno que entrega R$ 30k de trabalho e recebe R$ 8k.
- **Pensar em LGPD só no final.** *Correçêo:* o módulo 04 é têo importante quanto os outros. Saúde, financeiro e RH nêo fecham sem LGPD bem-amarrada.

## Checklist de saída

- [ ] Aluno entendeu por que três contratos e nêo um.
- [ ] Aluno aceitou que contrato nêo é burocracia — é parte do método DPIA.
- [ ] Aluno conhece os 4 erros mais caros e como cada um se evita.
- [ ] Aluno sabe onde cada módulo do bloco se encaixa.
