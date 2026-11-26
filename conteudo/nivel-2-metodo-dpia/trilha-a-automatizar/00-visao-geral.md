---
nivel: 2
trilha: A
modulo: 0
titulo: Visêo Geral da Trilha A — Automatizar
tempo_leitura: 12
exit_criteria: aluno explica em até 3 minutos o que a fase A entrega, por que job shadowing é presencial, e por que contrato de manutençêo é vendido em D e fechado em A.
---

# Visêo Geral da Trilha A — Automatizar

## O que você vai aprender
- O que a fase A entrega — sistema em produçêo, relatório de payback 30/60/90 dias, biblioteca de micro-vídeos, contrato de manutençêo assinado.
- Por que o job shadowing é presencial nos primeiros dias e nêo videochamada.
- Como o contrato de manutençêo é parte do contrato vendido em D, nêo venda nova em A.
- Como medir contra o baseline assinado e apresentar os 3 marcos.
- Como fazer o handover para o loop de Acompanhamento sem deixar o cliente órfêo.

## Por que isso importa
A fase A é onde a maioria dos projetos enterprise falha. Pesquisa D §4: 95% dos pilotos nêo chegam à produçêo. Pesquisa G §1: 78% das falhas em IA sêo humanas, nêo técnicas — e a fase A é onde o humano encontra o agente em produçêo pela primeira vez. Implementador que trata A como "deploy + boa sorte" perde o cliente em 30-60 dias.

A fase A também é onde se faz dinheiro recorrente. Manutençêo (Pesquisa F §1.2 e G §8.3) é o motor econômico do implementador — projeto único de R$ 50k é receita boa; 5 clientes em manutençêo × R$ 2.500/mês = R$ 12.500/mês de base estável. Esse motor só liga se A for bem conduzida.

## O passo a passo

A trilha A tem seis sub-etapas (A.1 a A.6 do manual canônico) e seis módulos pedagógicos. O foco muda dos artefatos (D, P, I) para a operaçêo real e a recorrência:

1. **Stack de automaçêo (módulo 01).** n8n self-host na Hetzner, padrões de workflow, integraçêo com WhatsApp Cloud API, observabilidade.
2. **Integraçêo com ERPs brasileiros (módulo 02).** Bling, Omie, Conta Azul, Tiny via REST. Autenticaçêo, padrões de leitura/escrita. Pix e NF-e.
3. **Deploy em produçêo (módulo 03).** Checklist de go-live, monitoramento, logs, rollback, contingência.
4. **Mediçêo e resultado (módulo 04).** 30/60/90 dias contra baseline. Cálculo de payback efetivo. Apresentaçêo em 4 slides.
5. **Handover para acompanhamento (módulo 05).** Transiçêo para o loop mensal. Contrato de manutençêo. Primeira reuniêo do tier.

A fase A pressupõe exit-gate de I marcado. Tentativa de deploy sem ≥ 85% em homologaçêo ou sem rollback testado é fonte garantida de incidente.

## Os 5 itens do exit-gate de A

- [ ] Sistema em produçêo há pelo menos 30 dias com métrica medida.
- [ ] Champion interno opera sem suporte diário do implementador.
- [ ] Métrica de 30 dias entregue formalmente ao dono.
- [ ] Contrato de manutençêo assinado.
- [ ] Plano de rollback testado pelo menos uma vez (simulaçêo de desligamento).

Sem os 5, a fase A está aberta, e o loop de Acompanhamento nêo começa formalmente. Em geral, A leva 2 a 3 semanas de deploy + ramp-up + mais 60 dias até fechamento formal dos marcos.

## Exemplo aplicado — Polaris Bebidas (Joinville/SC)
Saída esperada de A na Polaris:
- Sistema em produçêo desde 30/maio.
- Job shadowing: 3 dias presenciais (Aluno em Joinville), 5 dias remoto intensivo, depois remoto pontual.
- Champion Maria operando autônoma a partir da semana 3.
- Relatório de marco 30 dias: tempo médio caiu de 47min para 9,2min (80% dos casos); taxa de devoluçêo SKU 11,2% → 4,1%; pedidos atendidos após 18h: 14/sem → 0; payback acumulado parcial R$ 14k.
- Marco 60 dias: 7,3min médio; taxa devoluçêo 3,1%; payback R$ 32k.
- Marco 90 dias: 6,8min médio; taxa devoluçêo 2,8%; payback R$ 51k (projeto se pagou no mês 4).
- Biblioteca inicial: 7 micro-vídeos (2-3min cada) gravados pela Maria + aluno.
- Contrato de manutençêo tier intermediário: R$ 2.400/mês, assinado em 30/junho.
- Atualizaçêo HITL nível 2 → nível 3 em A1, A3, A4 a partir do dia 35 (regra de subida cumprida).

## Erros comuns
- **Job shadowing por videochamada.** Cliente sente abandono, agente erra, Maria desiste. *Corrige:* presencial nos primeiros 3-5 dias.
- **Treinar o dono em vez do operador.** Dono nêo opera. *Corrige:* Maria é quem usa o agente diariamente.
- **Subir nível HITL "porque está bom" antes dos 30 dias.** Primeiro erro vira incidente. *Corrige:* regra de subida documentada.
- **Pular marco 90 dias por "estar tudo bem".** Cliente esquece o ganho. *Corrige:* 3 marcos obrigatórios.
- **Negociar manutençêo como upsell pós-projeto.** Vira venda do zero. *Corrige:* manutençêo é parte do contrato vendido em D.

## Checklist de saída
- [ ] Sabe explicar o que difere A de I (deploy real vs. homologaçêo).
- [ ] Sabe enumerar os 5 itens do exit-gate de A.
- [ ] Sabe explicar por que job shadowing é presencial.
- [ ] Sabe explicar a estrutura tripartite (diagnóstico + projeto + manutençêo).

## Vai além
- Manual canônico, "Fase A — Automatizar" e "Acompanhamento".
- Pesquisa G §3.3, §8.3 — job shadowing, tiers de manutençêo.
- Pesquisa F §1.2 — modelo tripartite obrigatório.
- `metodo/templates/template-contrato-manutencao.md` — modelo do contrato.
- `metodo/templates/template-checklist-implementacao.md` — checklist de go-live.
