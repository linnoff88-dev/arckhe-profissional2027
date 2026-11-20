# Profissional 2027

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


Programa gratuito de formaÃ§Ã£o de **Implementadores de SoluÃ§Ãµes de IA** para pequenas e mÃ©dias empresas brasileiras.

ConstruÃ­do pela comunidade [inema.vip](https://inema.vip) e publicado em texto direto e prÃ¡tico na plataforma [inema.club](https://inema.club).

> *"NÃ£o ensinamos a colecionar ferramentas. Formamos profissionais para sair da curiosidade sobre IA e entrar no mercado real: diagnosticar pequenas empresas, vender soluÃ§Ãµes simples, implementar assistentes personalizados e treinar clientes para vender mais, atender melhor e trabalhar com menos burocracia."*

> *"Ferramenta Ã© commodity. Processo Ã© o ativo."*

## Sobre o programa

- **ResponsÃ¡vel e curador:** Nei Maldaner â€” 40 anos de TI, fundador do SISNEMA (100 mil profissionais de TI formados).
- **Modelo:** 100% gratuito, open source. O programa nÃ£o vende; o aluno vende.
- **DistribuiÃ§Ã£o:** comunidade inema.vip + plataforma inema.club + redes sociais (500k seguidores).
- **MÃ©todo:** **DPIA** â€” Diagnosticar â†’ Processar â†’ Instruir â†’ Automatizar, com Acompanhamento como loop externo de manutenÃ§Ã£o.
- **DuraÃ§Ã£o:** 10â€“12 semanas, ~100 horas.
- **ConclusÃ£o (selo prÃ³prio do programa, nÃ£o Ã© a certificaÃ§Ã£o INEMA):** mediante entrega de 1 diagnÃ³stico pago real + 1 piloto em PME real. A certificaÃ§Ã£o INEMA Ã© a do [Profissional 2030](https://eventos.inema.pro/prof2030/).
- **Foco geogrÃ¡fico:** Brasil, portuguÃªs brasileiro.
- **Modelo de relaÃ§Ã£o:** mercado aberto, sem franquia, sem selo restritivo.

## Estrutura do repositÃ³rio

```
.
â”œâ”€â”€ PLANO.md                          Plano-mestre do projeto
â”œâ”€â”€ DECISOES.md                       10 decisÃµes estratÃ©gicas do Nei
â”‚
â”œâ”€â”€ pesquisa/                         FundamentaÃ§Ã£o de mercado
â”‚   â”œâ”€â”€ 00-sintese-transversal.md     Documento-espinha-dorsal
â”‚   â”œâ”€â”€ 01-mercado-pme-brasil.md      Mercado e dor real
â”‚   â”œâ”€â”€ 02-metodos-frameworks.md      Frameworks e design AIOS
â”‚   â”œâ”€â”€ 03-perfis-e-concorrencia.md   Cargos emergentes e concorrentes
â”‚   â”œâ”€â”€ 04-casos-e-falhas.md          Casos reais e padrÃµes de falha
â”‚   â”œâ”€â”€ 05-stack-tecnico.md           Stack canÃ´nica
â”‚   â”œâ”€â”€ 06-comercial-e-vendas.md      Pricing, venda, contratos, LGPD
â”‚   â””â”€â”€ 07-treinamento-cliente.md     AdoÃ§Ã£o e sustentaÃ§Ã£o
â”‚
â”œâ”€â”€ metodo/
â”‚   â”œâ”€â”€ dpia-canonico.md              Manual canÃ´nico do mÃ©todo
â”‚   â””â”€â”€ templates/                    9 templates operacionais
â”‚
â””â”€â”€ conteudo/
    â”œâ”€â”€ nivel-1-manifesto/            6 arquivos â€” manifesto, tese, perfil, oportunidade
    â”œâ”€â”€ nivel-2-metodo-dpia/          24 arquivos â€” 4 trilhas (D, P, I, A) Ã— 6 mÃ³dulos
    â”œâ”€â”€ nivel-3-aplicacao/            18 arquivos â€” venda, contrato, sustentaÃ§Ã£o
    â””â”€â”€ nivel-4-aios/                 29 arquivos â€” biblioteca de mÃ³dulos prontos
```

## Estado atual

| Camada | Status | Arquivos | Palavras |
|--------|--------|---------:|---------:|
| Pesquisa de mercado (7 frentes) | âœ… Completa | 8 | ~55.000 |
| SÃ­ntese transversal | âœ… Completa | 1 | 5.332 |
| DPIA canÃ´nico + templates | âœ… Completo | 10 | ~22.000 |
| NÃ­vel 1 â€” Manifesto | âœ… Completo | 6 | 11.274 |
| NÃ­vel 2 â€” Trilhas DPIA | âœ… Completo | 24 | 34.108 |
| NÃ­vel 3 â€” AplicaÃ§Ã£o | âœ… Completo | 18 | 31.195 |
| NÃ­vel 4 â€” Biblioteca AIOS | âœ… Completo | 29 | ~36.900 |
| **Total** | | **~96** | **~182.000** |

## Stack canÃ´nica do programa

- **LLM:** Claude Sonnet 4.6 (com prompt caching) + Claude Haiku 4.5 para custo.
- **OrquestraÃ§Ã£o:** n8n self-hosted em Hetzner (~US$ 5/mÃªs).
- **MemÃ³ria:** Supabase com pgvector quando necessÃ¡rio.
- **Mensageria:** WhatsApp Cloud API oficial (Meta).
- **ERPs locais:** integraÃ§Ã£o via REST com Bling, Omie, Conta Azul.
- **Pagamentos:** PIX, integraÃ§Ã£o via API.
- **Fiscal:** NF-e/NFS-e via provedores brasileiros.

## PrincÃ­pios

1. **Ferramenta Ã© commodity. Processo Ã© o ativo.**
2. DiagnÃ³stico antes de implementaÃ§Ã£o. Sem baseline assinado, nÃ£o hÃ¡ projeto.
3. Mercado tripartite: diagnÃ³stico pago + projeto fixo + manutenÃ§Ã£o recorrente.
4. Human-in-the-loop em 4 nÃ­veis (Assistir, Co-piloto, Autopiloto-com-exceÃ§Ãµes, AutÃ´nomo).
5. Treinamento do cliente entra no contrato, nÃ£o Ã© venda extra.
6. ClÃ¡usula de transiÃ§Ã£o sem lock-in em todo contrato (princÃ­pio anti-dependÃªncia).
7. Stack componÃ­vel, sobrevive Ã  troca de modelo.

## LicenÃ§a

ConteÃºdo livre para uso, adaptaÃ§Ã£o e redistribuiÃ§Ã£o por qualquer pessoa ou comunidade.

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>