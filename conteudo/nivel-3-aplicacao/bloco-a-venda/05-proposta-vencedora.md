---
nivel: 3
bloco: A
modulo: 5
titulo: Proposta vencedora — a estrutura que fecha
tempo_leitura: 17
exit_criteria: Aluno tem template de proposta de diagnóstico e de projeto prontos, com as sete seções obrigatórias
---

# Proposta vencedora — a estrutura que fecha

## O que você vai aprender

- Por que a proposta nêo começa pela soluçêo, mas pela dor do cliente nas palavras dele.
- A estrutura de sete seções que converte (Dor → Soluçêo → ROI → Prova → Plano → Investimento → Próximos passos).
- A técnica da âncora de três opções (Essencial / Recomendado / Completo).
- Como apresentar preço sem entrar em desconto e como criar urgência legítima.
- Diferença entre proposta de diagnóstico e proposta de projeto — duas peças distintas no funil.

## Por que isso importa

Pesquisa F §6.1 mostra que propostas de IA que convertem seguem padrêo Pain → Value → Proof → Solution → ROI → Implementation → Pricing. Propostas que começam pela soluçêo perdem o leitor na primeira página. O dono de PME nêo lê 30 páginas. Lê a primeira; se ele se reconhecer, lê a segunda. Se na primeira página estiver "Quem somos" e logo "Nossa metodologia", ele fecha o PDF.

A proposta é o documento que o cliente lê quando o aluno nêo está na sala. Ela precisa fazer o trabalho que a reuniêo fez, sozinha, em 5 minutos de leitura.

## Conteúdo principal

### Duas propostas, dois momentos

**Proposta do diagnóstico** (final da reuniêo de discovery). 1–2 páginas. Vende um produto pequeno (R$ 1.500–4.000) com entregável claro.

**Proposta do projeto** (final do diagnóstico, embutida no relatório DPIA). 6–10 páginas. Vende o projeto completo (R$ 8.000–60.000) com baseline numérico já assinado.

Ambas seguem a mesma estrutura de sete seções, com peso diferente em cada uma.

### As sete seções obrigatórias

**Seçêo 1 — O contexto deles (nêo de você)**

Primeiro parágrafo da proposta reescreve a dor do cliente nas palavras dele, com os números que ele mesmo deu na reuniêo. Se o cliente ler essa seçêo e pensar "é exatamente isso que eu disse", você ganhou atençêo total.

Modelo para distribuidora:

> "Na reuniêo do dia [data], você descreveu o seguinte cenário: dois atendentes respondem WhatsApp das 8h às 18h. 30 perguntas/dia sobre prazo de entrega, 3 minutos por resposta. Isso significa 90 minutos/dia em cada atendente, ou aproximadamente 66 horas/mês por pessoa, R$ 3.696/mês de custo combinado (com hora-atendente all-in de R$ 28). Você mencionou ainda que em horário de almoço o tempo de resposta chega a 6h, e que estima perder cerca de 3 pedidos/dia por demora — o que dá um custo de oportunidade adicional nêo estimado, mas significativo."

**Seçêo 2 — A soluçêo proposta**

Descriçêo objetiva do que será construído. Sem jargêo técnico. Foco em "o que o cliente recebe", nêo em "o que vamos fazer". Use os nomes que o cliente entende: "WhatsApp", "Bling", "agente que responde", nêo "LLM com RAG via API".

Modelo:

> "Um agente de atendimento integrado ao seu WhatsApp Business e ao Bling, que responde automaticamente às 7 perguntas mais frequentes (prazo de entrega, preço de tabela, status de pedido, formas de pagamento, mínimo de pedido, área de cobertura, horário de funcionamento), valida estoque em tempo real, monta o pedido pronto para confirmaçêo do operador, e escala para humano nos casos fora do padrêo (reclamações, pedidos especiais, valor acima de R$ 5.000, ou palavras-chave de urgência)."

**Seçêo 3 — ROI estimado**

Cálculo de payback simples. Mesmo conservador, com número.

Modelo:

```
Tempo economizado: 60h/mês combinadas (60% das 100h atuais em perguntas repetidas)
Custo de hora-atendente: R$ 28
Economia mensal direta: R$ 1.680
Pedidos adicionais capturados (estimativa conservadora): 1/dia × 22 dias × R$ 180 ticket médio = R$ 3.960
Ganho mensal total estimado: R$ 5.640
Custo do projeto: R$ 22.000
Custo mensal de operaçêo (LLM + n8n + Supabase + WABA): R$ 580
Custo da manutençêo: R$ 2.500/mês
Payback do investimento de projeto: 7,2 meses
ROI 12 meses: 207%
```

Nêo invente número. Use o baseline real assinado em D (para proposta de projeto) ou estimativas conservadoras (para proposta de diagnóstico).

**Seçêo 4 — Prova social**

Caso real, mesmo que único. Anonimizado se necessário. Com número.

Modelo:

> "Caso de referência: distribuidora de bebidas em Joinville/SC, 14 funcionários, mesmo perfil. Após 90 dias de operaçêo, tempo médio de resposta caiu de 47 min para 4 min, atendimento operando 18h/dia (era 10h/dia), 0 pedidos perdidos por demora documentados. Disponível para visita de validaçêo mediante agendamento prévio."

**Seçêo 5 — Plano de execuçêo**

Timeline em 5–6 linhas, nêo Gantt detalhado. O cliente quer saber quando vê resultado.

Modelo:

```
Semanas 1–2: Diagnóstico em campo (entrevistas, walk-the-floor, exportaçêo de histórico, baseline assinado).
Semanas 3–4: Pacote de contexto (base de conhecimento, integrações Bling e WABA configuradas, glossário).
Semanas 5–6: Configuraçêo do agente, playbook, matriz HITL aprovada, homologaçêo ≥ 85%.
Semanas 7–8: Deploy em produçêo em nível conservador, job shadowing presencial, treinamento da equipe.
Mês 2 pós-deploy: Primeiro relatório de payback contra baseline assinado.
Manutençêo mensal: a partir do mês 2 pós-deploy.
```

**Seçêo 6 — Investimento (nêo "custo")**

A palavra é **investimento**. Três opções (técnica da âncora). A coluna do meio é a oferta principal.

| Item | Essencial | Recomendado | Completo |
|------|-----------|-------------|----------|
| Diagnóstico | Incluído | Incluído | Incluído |
| Agente WhatsApp + Bling | Sim | Sim | Sim |
| Integraçêo com Pix/Asaas | Nêo | Sim | Sim |
| Confirmaçêo automática pós-pedido | Nêo | Sim | Sim |
| Painel de métricas para o dono | Nêo | Nêo | Sim |
| Micro-vídeos de treinamento | 3 | 6 | 10 |
| Período de suporte inicial incluso | 30 dias | 60 dias | 90 dias |
| **Investimento de projeto** | **R$ 16.000** | **R$ 22.000** | **R$ 32.000** |
| **Manutençêo mensal** | **R$ 1.500** | **R$ 2.500** | **R$ 4.000** |

Pagamento: 30% na assinatura (sinal e início do diagnóstico) — 40% na entrega do piloto homologado — 30% no go-live de produçêo. Manutençêo começa no mês 2 pós-deploy.

Validade: 10 dias corridos a partir do envio.

**Seçêo 7 — Próximos passos**

Instruçêo clara, sem ambiguidade.

> "Para confirmar, responda este e-mail com 'aceito a opçêo [Essencial / Recomendado / Completo]'. Ao receber, envio o contrato e o boleto/Pix da primeira parcela. O kick-off do diagnóstico fica agendado para [data específica, 5 dias úteis após a confirmaçêo]."

### A técnica da âncora de três opções

Pesquisa F §6.2 confirma que a maioria dos clientes de PME escolhe a opçêo do meio. A coluna alta cria âncora ("o que existe mais caro"). A coluna baixa mostra que você nêo está empurrando ("tem opçêo menor, eu nêo estou forçando"). A coluna do meio aparece como "razoável" por contraste — e é onde você projeta margem confortável.

Diferenças entre as três colunas:

- Escopo (mais ou menos integrações).
- Suporte inicial (30/60/90 dias).
- Manutençêo (tier básico/intermediário/avançado).

Nunca diferencie por qualidade do agente. As três opções entregam o mesmo agente principal. A diferença está em complementos, nêo em compromisso de resultado.

### Como apresentar preço sem entrar em desconto

Quando o cliente pergunta "dá pra fazer mais barato?", a resposta padrêo é:

> "Posso te oferecer a opçêo Essencial em vez da Recomendada. Você fica com o agente principal funcionando, sem as integrações de Pix e sem o painel. O investimento cai para R$ 16.000. Aceita?"

Você nunca baixa o preço da mesma opçêo. Você oferece a opçêo menor. Isso preserva o preço de tabela e ainda dá ao cliente a sensaçêo de ter "ganhado" algo.

### Urgência legítima

Validade de 10 dias é padrêo. Nêo use "promoçêo válida até sexta" — soa amador. Use "validade da proposta: 10 dias". Se o cliente ultrapassa o prazo, o aluno reenvia com preço atualizado (mesmo que igual) e nova validade. Isso cria padrêo profissional sem manipulaçêo.

### Formato de entrega

- PDF de 6–10 páginas (nêo 30).
- Enviado por e-mail com texto curto: "Anexo a proposta combinada na nossa conversa. Validade de 10 dias. Qualquer dúvida me chama no WhatsApp."
- Apresentaçêo presencial ou em vídeochamada de 30 min agendada **no momento do envio** ("posso te ligar quinta às 15h para passar a proposta com você?").
- Sem ligar do nada três dias depois cobrando resposta. O follow-up é uma mensagem por WhatsApp ou e-mail na metade do prazo ("vi que você ainda nêo respondeu, está com alguma dúvida específica?").

## Exemplo aplicado — Polaris Bebidas

A proposta de diagnóstico da Polaris tinha 2 páginas. Primeira seçêo começava com "Na reuniêo de 12/03, você mencionou que duas atendentes gastam 90 minutos/dia respondendo prazo de entrega...". Seçêo investimento: R$ 2.500, abatível do projeto. Validade 10 dias. Cláudio respondeu em 4 dias.

A proposta de projeto, enviada após o diagnóstico, tinha 8 páginas. Trazia baseline assinado, três opções (R$ 16.000 / R$ 22.000 / R$ 32.000). Cláudio escolheu a do meio (Recomendada), pediu desconto, recebeu como resposta a oferta da opçêo Essencial. Pensou meia hora, voltou para a Recomendada (porque o painel do Completo nêo era essencial para ele, mas a integraçêo Pix sim).

## Materiais prontos

- Template de proposta de diagnóstico (2 páginas) com placeholders.
- Template de proposta de projeto (8 páginas) com placeholders.
- Calculadora de ROI em planilha (referenciada em `metodo/templates/template-baseline-assinado.md`).
- Modelo de e-mail de envio + modelo de follow-up.

## Erros comuns

- **Começar a proposta com "Quem somos" / "Sobre nossa metodologia".** *Correçêo:* começa com a dor do cliente nas palavras dele. Apresentaçêo fica em rodapé ou anexo.
- **Nêo usar três opções.** *Correçêo:* sempre três. Sem âncora, o preço único parece arbitrário.
- **Diferenciar opções por qualidade do agente.** *Correçêo:* a diferenciaçêo é por escopo (integrações, suporte, manutençêo). O agente principal é o mesmo nas três.
- **Baixar preço da mesma opçêo quando o cliente pede desconto.** *Correçêo:* ofereça a opçêo menor. Nunca quebre o preço da opçêo escolhida.
- **PDF de 30 páginas com Gantt detalhado.** *Correçêo:* 6–10 páginas, timeline em 6 linhas.
- **Nêo definir validade.** *Correçêo:* 10 dias, sempre. Sem validade, o cliente posterga indefinidamente.

## Checklist de saída

- [ ] Aluno tem template de proposta de diagnóstico em PDF.
- [ ] Aluno tem template de proposta de projeto em PDF, com âncora de 3 opções.
- [ ] Aluno consegue escrever a primeira seçêo (contexto do cliente) em 15 minutos usando notas da reuniêo de discovery.
- [ ] Aluno tem planilha de ROI preenchível com nomes de campo claros.
- [ ] Aluno escreveu modelo de e-mail de envio e de follow-up que vai usar.
- [ ] Aluno entendeu a regra: nêo baixar preço da mesma opçêo, oferecer opçêo menor.
