---
nivel: 3
bloco: B
modulo: 4
titulo: LGPD aplicada ao projeto — regime simplificado, privacy by design, cláusulas
tempo_leitura: 16
exit_criteria: Aluno consegue mapear dados pessoais do projeto, redigir RIPD enxuto e incluir cláusulas LGPD obrigatórias em contrato
---

# LGPD aplicada ao projeto — regime simplificado, privacy by design, cláusulas

## O que você vai aprender

- O que a LGPD exige de um implementador de IA para PME no Brasil.
- O regime simplificado da ANPD (Resoluçêo 2/2022) e o que ele dispensa para microempresas e PMEs.
- Privacy by Design aplicado a agentes de IA: minimizaçêo de dados, base legal, direitos do titular.
- Cláusulas LGPD obrigatórias no contrato de projeto e de manutençêo.
- Casos específicos: saúde, financeiro, RH — onde o cuidado é maior.
- O Marco Regulatório da IA (2025) e o que muda para agentes em PME.

## Por que isso importa

Pesquisa F §9 documenta que a ANPD intensificou fiscalizações em 2025 com foco em tecnologias emergentes. Multas chegam a 2% do faturamento bruto, limitadas a R$ 50 milhões por infraçêo. Para o implementador, isso tem dois vetores: ele é **operador** quando acessa dados do cliente; e orienta a PME, que é **controladora**, sobre obrigações.

LGPD nêo é "burocracia para empresa grande". Setores sensíveis (saúde, financeiro, RH) já estêo sendo multados em projetos mal-feitos. O aluno que oferece conformidade LGPD por padrêo se diferencia comercialmente. O que ignora vira passivo legal — para o cliente e para si mesmo.

## Conteúdo principal

### Os dois papéis do aluno

**Como operador.** Durante a execuçêo do projeto, o aluno acessa dados pessoais do cliente (clientes finais da PME, funcionários, fornecedores). Isso o torna operador nos termos da LGPD (art. 5, VII). Obrigações:

- Acessar dados apenas para fins do projeto.
- Nêo usar dados para fins próprios (treinar modelo, criar base, vender para terceiros).
- Implementar medidas técnicas de segurança.
- Notificar incidente em até 72h.
- Devolver ou deletar dados ao final.

**Orientando a PME (controladora).** A PME que usa a soluçêo é a controladora. O aluno orienta sobre:

- Mapear quais dados o agente processa.
- Definir base legal para o tratamento.
- Configurar o sistema para minimizar coleta.
- Criar mecanismo para atender direitos do titular.

### O regime simplificado da ANPD (Resoluçêo 2/2022)

A maioria das PMEs brasileiras se enquadra no **regime simplificado** definido pela Resoluçêo CD/ANPD nº 2/2022:

- Microempresa, EPP, startup, pessoa física ou ente despersonalizado que opera dados pessoais sem atividade de tratamento como atividade econômica principal.
- Nêo trata dados sensíveis em larga escala.
- Nêo realiza tratamento de alto risco.

**O que o regime dispensa:**

- Designaçêo obrigatória de DPO (Encarregado). Pode ter, é boa prática, mas nêo é exigência legal — basta indicar canal de comunicaçêo para titulares.
- Registro de operações em formato completo. Permite-se registro enxuto.
- Relatório de Impacto à Proteçêo de Dados (RIPD) em formato detalhado. Permite-se RIPD enxuto.

**O que o regime mantém:**

- Bases legais (art. 7 LGPD) continuam obrigatórias.
- Princípios de minimizaçêo, finalidade, transparência e segurança continuam vigentes.
- Direitos dos titulares precisam ser atendidos.
- Comunicaçêo de incidente continua obrigatória.

**Importante.** O regime simplificado vale para a PME-cliente. **Nêo vale automaticamente para o aluno-operador**. Se o aluno atende muitos clientes com dados pessoais, sua própria operaçêo pode nêo se enquadrar no simplificado. Recomenda-se contador/advogado revisar a estruturaçêo tributária e regulatória do MEI/PJ do aluno no início.

### Privacy by Design — 7 princípios aplicados a agente em PME

**1. Proativo, nêo reativo.** Pensar LGPD no diagnóstico, nêo depois do incidente. Mapeamento de dados é entregável da fase P.

**2. Privacidade como configuraçêo-padrêo.** O agente começa em modo conservador (nêo armazena conversa por mais de N dias, nêo acessa CPF se nêo precisa). Cliente escolhe relaxar, nêo apertar.

**3. Privacidade embutida no design.** A arquitetura considera LGPD desde os system prompts ("nunca peça dados pessoais que nêo sejam necessários para responder") até o storage ("logs sem PII após X dias").

**4. Funcionalidade plena.** LGPD nêo impede o agente de funcionar. Bem-feita, é transparente. O agente identifica-se ("Sou o assistente virtual da [Empresa X]") e atende dentro da base legal.

**5. Segurança end-to-end.** Criptografia em trânsito (TLS 1.3 mínimo) e em repouso (Supabase com encryption-at-rest, chaves gerenciadas). Controle de acesso por chave individual, logs auditáveis.

**6. Visibilidade e transparência.** A PME consegue mostrar, se questionada: que dados coleta, com que base legal, por quanto tempo, com quem compartilha (subprocessadores: Anthropic, Meta, etc.).

**7. Respeito ao usuário.** Mecanismo simples para titular: solicitar acesso aos seus dados, correçêo, exclusêo. Pode ser via canal humano (e-mail ou WhatsApp para a PME), com SLA de 15 dias para resposta.

### Base legal — o que escolher

Art. 7 da LGPD lista 10 bases. As três mais comuns para agente de IA em PME:

**Cumprimento de contrato (art. 7, V).** Agente que atende cliente da PME no contexto de relaçêo comercial existente. Exemplo: cliente já comprou, manda mensagem perguntando status do pedido — o agente responde com base no contrato de compra.

**Legítimo interesse (art. 7, IX).** Atendimento a potencial cliente em pré-venda, marketing direto sob certas condições. Requer documentaçêo de teste de balanceamento (interesse legítimo vs. direitos do titular). Nêo vale para dados sensíveis.

**Consentimento (art. 7, I).** Quando nenhuma das anteriores cabe. Mais frágil — pode ser retirado a qualquer momento. Útil para newsletter, programa de fidelidade, marketing-em-massa.

**Para dados sensíveis (saúde, biometria, dados de criança).** Bases mais restritas (art. 11). Consentimento qualificado ou previsêo legal específica. Recomenda-se advogado para configurar antes do projeto começar.

### RIPD enxuto — modelo para PME

Entregável obrigatório da fase D do DPIA (item D.6 do método canônico). Permitido no regime simplificado em formato reduzido, ~2 páginas:

```
RIPD ENXUTO — [Nome do Projeto]
Data: [data]
Empresa: [razêo social + CNPJ]
Encarregado/Canal: [e-mail ou WhatsApp para titular]

1. Descriçêo do tratamento
- Sistema: [agente de IA para atendimento WhatsApp]
- Dados tratados: [nome, telefone, histórico de pedido, eventualmente endereço de entrega]
- Origem dos dados: [cliente envia espontaneamente ao iniciar conversa no WhatsApp]
- Finalidade: [atender solicitaçêo de pedido, prazo, status]
- Base legal: [cumprimento de contrato — art. 7, V LGPD]
- Compartilhamento: [Meta WhatsApp Cloud API (operaçêo), Anthropic (LLM, com opt-out de treinamento), Supabase (storage)]
- Retençêo: [conversa por 12 meses, depois anonimizaçêo]

2. Análise de risco
- Risco de vazamento: [baixo — Supabase encrypted, chave individual, logs auditáveis]
- Risco de uso indevido: [baixo — Anthropic API com data-processing addendum, opt-out de treinamento ativado]
- Risco para titular: [baixo — dados sêo de relaçêo comercial existente, sem sensibilidade]

3. Medidas de mitigaçêo
- Criptografia TLS 1.3 em trânsito, AES-256 em repouso.
- Controle de acesso por chave individual.
- Log auditável de todas as interações.
- Política de retençêo automatizada (anonimizaçêo após 12 meses).
- Treinamento da equipe sobre LGPD básica.
- Identificaçêo clara de que é IA: "Sou o assistente virtual da [Empresa X]".

4. Direitos do titular
- Canal de exercício: [e-mail/WhatsApp]
- SLA de resposta: 15 dias.
- Procedimento operacional documentado no playbook.

5. Conclusêo
- Tratamento compatível com LGPD sob regime simplificado da ANPD (Res. 2/2022).
- Revisêo prevista: anual ou quando houver mudança material no escopo.

Assinaturas:
Controladora: ________________________
Operador: ________________________
```

### Cláusulas LGPD no contrato

**No contrato de projeto** (item 8 do módulo 02, complementado aqui):

Inserir as 6 cláusulas do Pesquisa F §9.4:

1. Acesso a dados pessoais apenas para os fins do projeto descrito.
2. Nêo-uso dos dados para treinar modelos próprios ou de terceiros.
3. Devoluçêo ou exclusêo dos dados em até 30 dias após encerramento.
4. Implementaçêo de medidas técnicas de segurança (criptografia, controle de acesso).
5. Notificaçêo à Contratante em até 72h em caso de incidente.
6. Reconhecimento de que a Contratante permanece controladora; o Contratado atua como operador.

**No contrato de manutençêo** — manter a continuidade das obrigações:

> "As obrigações LGPD do Contratado, conforme definidas no contrato de projeto X de [data], continuam vigentes durante a vigência deste contrato de manutençêo."

### Subprocessadores — o que olhar nas APIs

Quando o agente usa LLM API, esse provider é subprocessador. O aluno deve:

**Anthropic (Claude).** Verificar Data Processing Addendum (DPA), ativar opt-out de uso para treinamento (default já é opt-out em chamadas API), e documentar isso no RIPD.

**OpenAI.** Mesma lógica: DPA + opt-out de uso para treinamento. Atençêo: opt-out é configurável por organizaçêo.

**Meta WhatsApp Cloud API.** A Meta acessa metadados de mensagens. A PME cliente assina os termos da Meta diretamente. O aluno orienta sobre configuraçêo da Política de Privacidade do número WABA.

**Supabase.** Servidor pode estar em EUA. Para dados sensíveis, considere instância em regiêo brasileira (oferecida há contrato) ou criptografia client-side adicional.

**n8n self-host na Hetzner.** Servidor na Alemanha por padrêo. Hetzner tem DPA disponível. Para dados sensíveis, considere instância em Sêo Paulo (Hetzner nêo tem; alternativas: Locaweb cloud, Magalu cloud).

### Casos específicos

**Saúde (clínicas, consultórios).** Dados sensíveis (art. 11 LGPD). Base legal mais restrita. Recomenda-se consentimento qualificado por escrito. RIPD em formato completo, mesmo com PME pequena. Cuidados extras: nunca armazenar dados de prontuário no LLM, agente NêO faz triagem médica nem prescriçêo, log de auditoria mais robusto, contrataçêo de DPO recomendada (mesmo sem obrigatoriedade legal).

**Financeiro (escritório contábil, financeira, factoring).** Dados sensíveis quando há informaçêo financeira de pessoa física. Sigilo bancário (LC 105/2001) tem prioridade sobre LGPD em algumas situações. Recomenda-se: nunca armazenar dados bancários no LLM, agente nêo dá conselho financeiro/contábil sem revisêo humana, log auditável obrigatório, contrato com cláusula de sigilo bancário expressa.

**RH (recrutamento, gestêo de pessoas).** Dados podem incluir candidatos, funcionários, ex-funcionários. Cuidados: consentimento para uso em recrutamento, anonimizaçêo para análise estatística, direito ao esquecimento facilitado, agente NêO toma decisêo de contrataçêo/demissêo (Marco Regulatório de IA exige humano no loop para decisêo automatizada com impacto significativo).

### Marco Regulatório da IA (2025)

Aprovado em 2025, em fase de regulamentaçêo infralegal. Para PME, três obrigações principais (Pesquisa F §9.3):

1. **Transparência.** Usuário final deve saber que está interagindo com IA. Aplicaçêo: agente sempre se identifica.
2. **Explicabilidade.** Decisões automatizadas com impacto significativo precisam ser explicáveis. Aplicaçêo: agente que recusa atendimento ou nega cobertura precisa expor critério.
3. **Auditabilidade.** Registros de como o sistema decide devem ser mantidos. Aplicaçêo: logs de interaçêo por no mínimo 6 meses, com possibilidade de reconstruçêo de decisêo.

Em PME, essas obrigações sêo leves se o agente opera em escopo simples. Ficam pesadas em decisões automatizadas (concessêo de crédito, triagem médica, decisêo de RH). Para esses casos: humano no loop sempre (Princípio 5 do DPIA), e log com mais detalhes.

## Exemplo aplicado — Polaris Bebidas

RIPD da Polaris foi enxuto (2 páginas). Dados tratados: nome (extraído do WhatsApp), telefone (número do canal), histórico de pedidos (sincronizado do Bling), eventualmente endereço (quando cliente novo). Base legal: cumprimento de contrato (cliente já tem relaçêo comercial com a distribuidora). Subprocessadores documentados: Meta WABA, Anthropic (opt-out ativado), Supabase, n8n na Hetzner.

Cláusulas LGPD no contrato de projeto (item 8). Cláusulas LGPD no contrato de manutençêo (referência à continuidade).

Mês 7 de operaçêo: cliente final pediu exclusêo dos dados ("apaga meu cadastro de vocês"). Cláudio acionou o canal documentado, o pedido foi atendido em 4 dias úteis (dentro do SLA de 15 dias). Log da operaçêo registrado para auditoria.

## Materiais prontos

- Template de RIPD enxuto em 2 páginas (preenchível).
- Lista das 6 cláusulas LGPD obrigatórias no contrato.
- Checklist de configuraçêo de subprocessadores (Anthropic, Meta, Supabase, Hetzner).
- Procedimento operacional padrêo (POP) para atender solicitaçêo de titular em 15 dias.
- Modelo de comunicaçêo de incidente em 72h.

## Erros comuns

- **Tratar LGPD como "depois resolvo".** *Correçêo:* RIPD enxuto é item obrigatório do exit-gate da fase D.
- **Esquecer de ativar opt-out de treinamento nas APIs.** *Correçêo:* configuraçêo explícita no provider, documentada no RIPD.
- **Aplicar regime simplificado em setor sensível.** *Correçêo:* saúde, financeiro e RH têm cuidados extras mesmo com PME pequena.
- **Nêo definir base legal por escrito.** *Correçêo:* sem base legal documentada, nêo há defesa em fiscalizaçêo.
- **Esquecer canal para o titular.** *Correçêo:* até PME com 3 funcionários precisa ter um e-mail ou WhatsApp para titular exercer direitos.
- **Nêo treinar a equipe sobre LGPD básica.** *Correçêo:* parte do treinamento do Bloco C inclui módulo de LGPD para a operaçêo diária.

## Checklist de saída

- [ ] Aluno tem template de RIPD enxuto adaptado ao nicho.
- [ ] Aluno consegue identificar a base legal aplicável a cada produto produtizado.
- [ ] Aluno tem checklist de configuraçêo de cada subprocessador.
- [ ] Aluno incluiu as 6 cláusulas LGPD no template de contrato de projeto.
- [ ] Aluno tem procedimento documentado para atender direito de titular em 15 dias.
- [ ] Aluno tem modelo de comunicaçêo de incidente em 72h.
- [ ] Aluno consegue explicar em 60 segundos quando o regime simplificado se aplica e quando nêo.
