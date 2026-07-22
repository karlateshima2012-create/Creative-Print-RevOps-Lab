# Business Discovery — Creative Print

**Fase:** 1 — Descoberta do Negócio
**Objetivo:** Entender completamente como a Creative Print funciona hoje, antes de desenhar qualquer arquitetura de CRM.

---

## 1. Visão Geral do Negócio

A Creative Print é uma empresa de tecnologia e produtos personalizados que combina fabricação digital, NFC e soluções SaaS para pequenos negócios. Opera em duas frentes:

**1. Produtos físicos personalizados**
- Chaveiros NFC
- Cartões NFC
- Brindes corporativos
- Produtos 3D personalizados

**2. Produtos digitais SaaS**
- CP Agenda — sistema de agendamento para prestadores de serviço (salões, clínicas, academias, fotógrafos)
- CP Review — sistema de captação de avaliações e gestão de reputação no Google
- CP Connect (futuro) — integrações entre canais de atendimento

O objetivo da implantação do HubSpot CRM é transformar a operação comercial da Creative Print em uma operação orientada por dados, criando a base para Marketing Automation, Customer Success e Revenue Operations.

## 2. Como os clientes chegam hoje

| Canal | Descrição |
|---|---|
| Instagram | Direct messages a partir de posts/stories |
| WhatsApp | Contato direto, muitas vezes vindo do Instagram |
| Indicação | Cliente atual indica um novo cliente |

## 3. Como acontece uma venda hoje

O processo é inteiramente manual: o lead entra em contato via Instagram ou WhatsApp, a negociação acontece por mensagem de texto, o pagamento é combinado informalmente e a entrega/ativação do produto é feita sem registro formal em nenhum sistema central.

## 4. Como ocorre o pós-venda hoje

Não existe processo formal de pós-venda. O acompanhamento do cliente depende da memória do time e de mensagens antigas no WhatsApp. Não há onboarding estruturado, nem verificação de uso do produto, nem processo de renovação.

## 5. Ferramentas já utilizadas

| Ferramenta | Uso atual |
|---|---|
| WhatsApp Business | Comunicação com leads e clientes |
| Instagram | Aquisição e primeiro contato |
| CP Agenda | Sistema operacional do produto (uso do cliente final) |
| CP Review | Sistema operacional do produto (uso do cliente final) |
| Planilhas soltas | Controle informal de alguns clientes (não centralizado) |

## 6. Onde ficam armazenados os dados hoje

Os dados comerciais estão fragmentados: histórico de conversas no WhatsApp e Instagram, dados operacionais de uso dentro do CP Agenda e CP Review (isolados por tenant), e informações financeiras em planilhas não integradas. Não existe um único lugar onde se possa responder "quem são meus clientes, o que compraram e quando renovam".

## 7. Quem utiliza essas informações

Hoje, majoritariamente uma pessoa (fundação/comercial) concentra o conhecimento sobre os clientes, o que cria dependência de memória individual e risco de perda de informação.

## 8. Conclusão da Descoberta

A Creative Print tem produtos validados (físicos e SaaS) e canais de aquisição funcionando, mas nenhuma camada de sistema que centralize relacionamento comercial. Esse é exatamente o problema que a arquitetura de CRM definida em `CRM_Architecture.md` foi desenhada para resolver.
