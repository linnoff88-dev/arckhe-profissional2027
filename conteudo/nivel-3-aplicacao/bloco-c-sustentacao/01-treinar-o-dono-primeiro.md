---
nivel: 3
bloco: C
modulo: 1
titulo: Treinar o dono primeiro — sequência, conteúdo, framework CATE
tempo_leitura: 18
exit_criteria: Aluno tem roteiro completo de treinamento do dono em 2 sessões e domínio do framework CATE para prompt
---

# Treinar o dono primeiro — sequência, conteúdo, framework CATE

## O que você vai aprender

- Por que treinar a equipe sem ter treinado o dono é desperdício de tempo.
- O que ensinar ao dono nêo-técnico em duas sessões de 2h (semana 0 e semana 2 do go-live).
- O framework CATE (Contexto, Açêo, Tom, Exemplo) para prompt do dono nêo-técnico.
- O checklist TRES (Tem informaçêo errada? Resolve o problema? Está no tom? Se eu assinasse, ficaria bem?) para supervisêo de output.
- Como envolver o dono no fluxo HITL como aprovador, nêo como executor.

## Por que isso importa

Pesquisa G §5.1 (Blackstone+Cullen 2025) documenta que 78% das falhas em IA decorrem de comunicaçêo humano-IA deficiente. O dono nêo-técnico tem dois bloqueios: **nêo sabe pedir** (prompts ruins) e **nêo sabe avaliar** (nêo distingue boa de má resposta).

Pesquisa G §10.4 (Prosci 2026): 43% das falhas de adoçêo se devem à falta de patrocínio executivo. Dono que nêo usa nem cobra é dono que perde o investimento. A equipe percebe que IA nêo é prioridade real e abandona em 90 dias.

O treinamento do dono nêo é "passar visêo geral". É formar usuário e supervisor. Sem ele, todo o resto desaba.

## Conteúdo principal

### A sequência: dono primeiro, sempre

A ordem operacional na fase A do DPIA é:

1. **Semana -1 (antes do go-live):** primeira sessêo com o dono (2h).
2. **Semana 0 (go-live):** sessêo com champion + equipe (4h, módulos 02 e 03).
3. **Semana 2 pós-go-live:** segunda sessêo com o dono (2h) para revisêo e prática.
4. **Semana 4, 8, 12:** reuniões mensais de acompanhamento com o dono (módulo 05).

Por que dono antes? Porque sem o dono aprovar pessoalmente os primeiros casos reais, o sistema entra em produçêo sem patrocínio. A equipe percebe ausência do dono e desengaja.

### Sessêo 1 — Semana -1 (2h)

Objetivos:

1. Dono entende a matriz HITL e aprova por escrito o nível inicial.
2. Dono experimenta o agente com 3 casos reais e dá feedback.
3. Dono assume o papel de "primeiro aprovador" nas duas primeiras semanas.
4. Dono é apresentado ao framework CATE (resumo).

Estrutura:

**Min 0–15.** Recap do projeto. Mostre o baseline assinado (fase D), o relatório de homologaçêo (fase I com ≥ 85% de acerto), e o plano de produçêo. Dono precisa ver onde estamos e para onde vamos.

**Min 15–45.** Explicaçêo da matriz HITL aprovada por ele em I. Mostre nível por nível, com exemplo de açêo em cada um. "No nível 2, o agente prepara a mensagem, mas a Maria aprova clique-a-clique. É aí que a gente começa. Em 4–8 semanas, se a qualidade comprovar, a gente sobe para nível 3 em algumas ações específicas." Resgate o documento assinado em I.

**Min 45–75.** Demo ao vivo com 3 casos reais (saídos do histórico do cliente, sem inventar). Dono experimenta — ele mesmo digita, ele mesmo aprova ou rejeita.

**Min 75–105.** Framework CATE em prática. Pega uma tarefa que o dono faz hoje (rascunhar e-mail para fornecedor, descrever situaçêo para o contador). Aplica CATE ao vivo. Mostra a diferença entre prompt vago e prompt estruturado.

**Min 105–120.** Combinaçêo de papéis. "Nas próximas duas semanas, você é o primeiro aprovador junto com a Maria. Eu te mando relatório de adoçêo semanal. Em duas semanas a gente conversa de novo e ajusta."

### Sessêo 2 — Semana 2 pós-go-live (2h)

Objetivos:

1. Revisar o que aconteceu nas duas primeiras semanas (métricas reais).
2. Praticar com casos que apareceram (nêo com casos fictícios).
3. Decidir se sobe o nível HITL em alguma açêo ou se mantém.
4. Treinar o uso do log de feedback.

Estrutura:

**Min 0–30.** Apresentaçêo dos números das 2 semanas: taxa de adoçêo, taxa de override (humano aprova vs. rejeita), tempo de resposta médio, casos escalonados para humano. Sempre comparado ao baseline assinado em D.

**Min 30–60.** Discussêo dos casos difíceis. "Apareceram 3 situações que o agente nêo cobriu. Vou te mostrar como cada uma foi tratada e como vamos atualizar o playbook para evitar repetiçêo."

**Min 60–90.** Prática com casos reais. Dono opera o agente em modo nível 2 (aprovador) por 30 minutos seguidos, com aluno ao lado. Aluno corrige uso do CATE quando o prompt do dono fica vago.

**Min 90–120.** Treino do log de feedback. "Quando você vê o agente errando, anota assim: data, fluxo, o que ele fez, o que era esperado, frequência. Isso vai para mim no relatório mensal. Nêo é reclamaçêo — é dado."

### O framework CATE — versêo completa

CATE estrutura o prompt em quatro elementos. Para o dono nêo-técnico, é mnemônico simples.

**C — Contexto.** Quem sou eu, qual é meu negócio, qual é a situaçêo.

> "Sou dono de distribuidora de bebidas em Joinville, 14 funcionários. Atendo bares, restaurantes e mercadinhos."

**A — Açêo.** Verbo preciso do que quero que a IA faça.

> "Escrever um e-mail para meu fornecedor de cerveja artesanal pedindo desconto adicional de 5% no próximo pedido."

**T — Tom e formato.** Como quero a resposta.

> "Tom respeitoso e direto. Máximo 6 frases. Sem rebuscamento."

**E — Exemplo (opcional, quando aplicável).** Mostro como o resultado bom se parece.

> "Como esse e-mail que eu mandei para outro fornecedor mês passado: [colar exemplo]."

CATE nêo é metodologia para o dono memorizar — é gancho para ele perceber a diferença. Após algumas semanas, o dono internaliza naturalmente.

### Comparaçêo prompt vago vs. prompt CATE

**Vago:**
> "Escreve um e-mail pedindo desconto."

Saída típica do LLM: e-mail genérico, formal demais ou informal demais, sem foco no fornecedor específico, sem contexto.

**CATE:**
> "Sou dono de distribuidora de bebidas em Joinville (14 funcionários). Escreva um e-mail para meu fornecedor de cerveja artesanal pedindo desconto adicional de 5% no próximo pedido. Tom respeitoso e direto, máximo 6 frases. Argumentos a usar: estamos comprando há 18 meses sem atraso de pagamento, próximo pedido será 30% maior que o usual."

Saída: e-mail específico, com argumentos relevantes, tamanho controlado. O dono percebe a diferença na hora.

### Checklist TRES — supervisionar output

Pesquisa G §5.3. Cartêo plastificado para o dono ter ao lado do computador nas primeiras semanas:

```
TRES PERGUNTAS ANTES DE APROVAR:

T — Tem informaçêo errada? (fato, número, nome, prazo)
R — Resolve o problema? (atende ao objetivo que eu tinha)
E — Está no tom certo? (linguagem adequada ao destinatário)
S — Se eu assinasse isso, ficaria bem? (teste de responsabilidade)

Se "sim" para os 4: aprovo.
Se "nêo" para qualquer: corrijo ou rejeito.
```

O dono nêo-técnico nêo precisa entender como o LLM funciona. Precisa saber decidir se a saída serve. TRES é a ferramenta dele.

### Envolvimento do dono no fluxo HITL

Nas primeiras 2 semanas, o dono é **co-aprovador** junto com a Maria nas mensagens fora do padrêo. Isso cria três coisas:

1. **Hábito no dono.** Pesquisa G §1.3 (UTAUT2): hábito é o preditor mais forte de continuidade de uso. O dono que aprova 5 mensagens/dia por 14 dias internaliza o sistema.
2. **Sinal para a equipe.** "Se o dono está usando, isso é prioridade. Nêo vou voltar para o WhatsApp pessoal."
3. **Feedback de qualidade.** O dono vê o que o agente faz, intui o que precisa ajustar, comunica ao aluno no acompanhamento.

A partir da semana 3, o dono sai do papel de co-aprovador diário e vira **supervisor estratégico**: olha o relatório semanal, comenta em reuniêo mensal, aprova subidas de nível HITL.

### Erros comuns do dono no início

Quatro padrões que o aluno antecipa e corrige nas sessões:

1. **"Nêo tenho tempo para aprovar mensagem por mensagem."** Resposta: nas primeiras duas semanas, vale a pena. É o investimento que evita você ter problema crônico depois.
2. **"A Maria decide sozinha, nêo preciso ver."** Resposta: você é o primeiro aprovador também nas primeiras semanas, porque você é quem vai cobrar quando funcionar e responsabilizar se errar.
3. **"Vai dar trabalho a mais."** Resposta: dá. Por 14 dias. Depois, dá menos trabalho que antes. Mostre o número.
4. **"Nêo entendo isso de prompt."** Resposta: nêo precisa entender LLM. Precisa saber pedir o que quer. CATE é simples.

## Exemplo aplicado — Polaris Bebidas

Sessêo 1 Cláudio (semana -1 do go-live): 2h. Matriz HITL revisada: nível 2 para todos os módulos. Cláudio aprovou por escrito. Demo com 3 casos reais (pergunta sobre prazo, pedido grande, reclamaçêo). Cláudio errou ao prompt para o e-mail do fornecedor — escreveu "manda email pedindo desconto". Aluno aplicou CATE ao vivo, Cláudio percebeu a diferença. Cartêo TRES entregue plastificado.

Semana -1 até semana 0: aluno provisionou tudo, Cláudio só esperou.

Go-live semana 0. Cláudio + Maria aprovaram cada mensagem nas primeiras 48h. Aluno acompanhou presencialmente (módulo 03).

Sessêo 2 Cláudio (semana 2): números na mesa — 612 atendimentos nas 2 semanas, 84% aprovados sem ajuste, tempo médio de resposta caiu de 47min para 6min. Cláudio: "isso é assustador." Discutiram 3 casos difíceis, atualizaram playbook. Decidiram manter nível 2 por mais 4 semanas antes de subir para nível 3 em FAQ pura.

A partir da semana 3, Cláudio saiu do papel de co-aprovador diário. Maria continuou em nível 2. Reuniões mensais começaram.

## Materiais prontos

- Roteiro de sessêo 1 (semana -1) — 2h, minuto a minuto.
- Roteiro de sessêo 2 (semana 2 pós-go-live) — 2h, minuto a minuto.
- Cartêo CATE plastificado (versêo A4).
- Cartêo TRES plastificado (versêo A4).
- Modelo de log de feedback do dono em 1 página.

## Erros comuns

- **Pular a sessêo 1 e ir direto para go-live.** *Correçêo:* sem dono treinado, equipe nêo tem patrocínio.
- **Ensinar conceito técnico em vez de prática.** *Correçêo:* CATE e TRES sêo ferramentas práticas. Conceito do LLM fica fora.
- **Nêo pedir aprovaçêo por escrito da matriz HITL.** *Correçêo:* matriz é assinada pelo dono. Sem isso, fica conversa.
- **Achar que o dono "nêo vai usar pessoalmente".** *Correçêo:* nas primeiras 2 semanas usa. Sem isso, equipe nêo adota.
- **Nêo dar cartões físicos.** *Correçêo:* o físico permanece visível. O digital é esquecido.

## Checklist de saída

- [ ] Aluno tem roteiro das duas sessões com minutagem.
- [ ] Aluno tem cartões CATE e TRES em formato imprimível.
- [ ] Aluno consegue executar a demo de prompt vago vs. CATE em 5 minutos.
- [ ] Aluno tem modelo de log de feedback do dono.
- [ ] Aluno entendeu que dono é co-aprovador nas primeiras 2 semanas e supervisor estratégico a partir da semana 3.
