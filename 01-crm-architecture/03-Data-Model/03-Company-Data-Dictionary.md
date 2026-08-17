# Company Data Dictionary

## Objetivo

Este documento define todas as propriedades utilizadas pelo objeto **Company (Empresa)** no CRM da Creative Print.

Cada propriedade possui uma finalidade específica e foi definida para atender aos processos comerciais, de marketing, atendimento e Revenue Operations.

Nenhuma propriedade deverá ser criada diretamente no HubSpot sem estar previamente documentada neste Data Dictionary.

---

> **Decisão Arquitetural 001:**
> Nunca duplicaremos propriedades padrão do HubSpot.
> Sempre que uma propriedade padrão atender ao requisito de negócio, ela será utilizada.

---

> **Decisão Arquitetural 002:**
> Arquitetura de propriedades em camadas: **Base (Global)** vs **Extensão Brasil**.
> 
> ```text
> Arquitetura Base (Global)
> │
> ├── Nome da Empresa
> ├── Domínio
> ├── País
> ├── Estado
> ├── Cidade
> ├── Website
> ├── Telefone
> └── Record ID
> 
> ↓
> 
> Extensão Brasil
> │
> ├── CNPJ
> ├── Razão Social
> ├── Nome Fantasia
> ├── Inscrição Estadual
> ├── Inscrição Municipal
> └── Regime Tributário (futuro, se necessário)
> ```
> 
> *Justificativa:* Garante internacionalização e reutilização da arquitetura. Projetos para empresas globais (EUA, Japão, etc.) utilizam a camada Base sem necessidade da extensão regional.

---

# Estrutura das Propriedades

Cada propriedade será documentada utilizando o padrão abaixo.

| Campo              | Descrição                                                                  |
| ------------------ | -------------------------------------------------------------------------- |
| Nome Exibido       | Nome apresentado aos usuários no HubSpot.                                  |
| Nome Interno       | Nome técnico utilizado pelo HubSpot. Não deverá ser alterado após criação. |
| Grupo              | Grupo funcional da propriedade.                                            |
| Tipo               | Tipo de campo no HubSpot.                                                  |
| Obrigatório        | Define se o preenchimento é obrigatório.                                   |
| Valor Padrão       | Valor inicial, quando aplicável.                                           |
| Valores Permitidos | Opções disponíveis para propriedades do tipo seleção.                      |
| Origem do Dado     | Sistema ou responsável pelo preenchimento.                                 |
| Responsável        | Área responsável pela manutenção da informação.                            |
| Atualização        | Momento em que o campo deverá ser atualizado.                              |
| Utilização         | Onde a propriedade será utilizada (relatórios, filtros, automações etc.).  |
| Justificativa      | Motivo pelo qual a propriedade existe.                                     |

---

# Grupos de Propriedades

As propriedades da Empresa no HubSpot estão organizadas nos seguintes grupos:

1. **Company Information** (Nativo)
2. **Social Media Information** (Nativo)
3. **Sales Properties** (Nativo)
4. **Products & Services** (Customizado)
5. **Customer Success** (Customizado)
6. **Marketing** (Customizado)

*Nota: O grupo **Finance** foi mantido como estrutura arquitetural reservada, porém nenhuma propriedade foi criada na versão inicial do CRM.*

---

# Group 1 — Company Information

## Objetivo

O grupo **Company Information** reúne as propriedades principais de identificação, localização, porte e ciclo de vida da empresa no HubSpot.

---

## Approved Properties

### Company Information

| Property | Origin | HubSpot Group |
| --- | --- | --- |
| Company Name | HubSpot | Company Information |
| Website URL | HubSpot | Company Information |
| Phone Number | HubSpot | Company Information |
| Country/Region | HubSpot | Company Information |
| State/Region | HubSpot | Company Information |
| City | HubSpot | Company Information |
| Record ID | HubSpot | Company Information |
| CNPJ | Custom | Company Information |
| Industry | HubSpot | Company Information |
| Number of Employees | HubSpot | Company Information |
| Business Type | Custom | Company Information |
| Lifecycle Stage | HubSpot | Company Information |

### Social Media Information

| Property | Origin | HubSpot Group |
| --- | --- | --- |
| Facebook Company Page | HubSpot | Social Media Information |
| LinkedIn Company Page | HubSpot | Social Media Information |
| Instagram Company Page | Custom | Social Media Information |

### Sales Properties

| Property | Origin | HubSpot Group |
| --- | --- | --- |
| Lead Status | HubSpot | Sales Properties |
| Company Owner | HubSpot | Sales Properties |

---

## Decisões Arquiteturais

### DA-001 — Priorizar propriedades nativas

Sempre que uma propriedade padrão do HubSpot atender ao requisito de negócio, ela será utilizada.

---

### DA-002 — Arquitetura Global com Extensão Brasil

O CRM utilizará uma arquitetura baseada nas propriedades globais do HubSpot, complementada por propriedades específicas do mercado brasileiro quando agregarem valor ao negócio.

---

### DA-003 — Propriedades somente com finalidade definida

Uma propriedade somente poderá fazer parte do CRM quando possuir pelo menos um dos seguintes objetivos:

* segmentação;
* automação;
* integração;
* relatório;
* apoio à tomada de decisão.

---

### DA-004 — Identificação por múltiplos identificadores

A identificação de uma Empresa utilizará uma combinação de propriedades, conforme definido no documento **CRM-Data-Governance.md**, não dependendo de um único identificador.

---

## Especificação das Propriedades Aprovadas

### Company Name

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Company Name |
| Objeto | Company |
| Tipo | Texto |
| Categoria | Global |
| Origem | HubSpot padrão |
| Obrigatória | Sim |

#### Objetivo

Identificar o nome comercial utilizado pela empresa dentro do CRM.

Esta propriedade representa a identificação principal visual do registro da empresa para usuários internos.

#### Uso no Negócio

Utilizada para:

* identificação rápida do cliente;
* pesquisa dentro do CRM;
* associação com contatos e negócios;
* visualização em pipelines;
* comunicação comercial.

#### Critérios de Preenchimento

Deve ser utilizado o nome pelo qual a empresa é reconhecida comercialmente.

Exemplo:

`Creative Print`

Não utilizar:

`Creative Print LTDA - Empresa de Produtos Personalizados`

Informações jurídicas devem ser armazenadas em propriedades específicas.

#### Decisão Arquitetural

Utilizar propriedade nativa do HubSpot.

Motivo:

A propriedade padrão atende ao requisito de identificação sem necessidade de customização.

---

### Company Domain

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Company Domain |
| Objeto | Company |
| Tipo | Texto |
| Categoria | Global |
| Origem | HubSpot padrão |
| Obrigatória | Sim |

#### Objetivo

Armazenar o domínio principal utilizado pela empresa.

#### Uso no Negócio

Utilizado para:

* identificação automática de empresas;
* associação de contatos;
* enriquecimento de dados;
* redução de duplicidade.

#### Critérios de Preenchimento

Informar somente o domínio.

Correto:

`creativeprintjp.com`

Incorreto:

`https://www.creativeprintjp.com`

#### Decisão Arquitetural

Utilizar propriedade nativa do HubSpot.

O domínio é um identificador global importante para operações futuras de automação e integração.

---

### Website

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Website URL |
| Objeto | Company |
| Tipo | URL |
| Categoria | Global |
| Origem | HubSpot padrão |
| Obrigatória | Sim |

#### Objetivo

Registrar o endereço oficial da presença digital da empresa.

#### Uso no Negócio

Utilizado para:

* análise comercial;
* pesquisa antes de contato;
* enriquecimento de dados;
* segmentação.

#### Critérios de Preenchimento

Aceita:

`https://creativeprintjp.com`

Quando a empresa não possui site:

Deixar vazio

Não substituir por redes sociais.

#### Decisão Arquitetural

Utilizar propriedade nativa do HubSpot.

---

### Phone Number

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Phone Number |
| Objeto | Company |
| Tipo | Telefone |
| Categoria | Global |
| Origem | HubSpot padrão |
| Obrigatória | Sim |

#### Objetivo

Registrar o principal telefone comercial da empresa.

#### Uso no Negócio

Utilizado para:

* contato comercial;
* atendimento;
* integrações com ferramentas de comunicação.

#### Critérios de Preenchimento

Sempre utilizar formato internacional.

Exemplo:

`+55 65 XXXXX-XXXX`

#### Decisão Arquitetural

Utilizar propriedade nativa do HubSpot.

---

### Country

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Country |
| Objeto | Company |
| Tipo | Seleção |
| Categoria | Global |
| Origem | HubSpot padrão |
| Obrigatória | Sim |

#### Objetivo

Identificar o país de operação da empresa.

#### Uso no Negócio

Permite:

* segmentação geográfica;
* relatórios por mercado;
* regras de automação futuras.

#### Critérios de Preenchimento

Utilizar padrão internacional.

Exemplo:

* Brazil
* Japan
* United States

#### Decisão Arquitetural

Utilizar propriedade nativa do HubSpot.

---

### State / Region

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | State/Region |
| Objeto | Company |
| Tipo | Texto |
| Categoria | Global |
| Origem | HubSpot padrão |
| Obrigatória | Sim |

#### Objetivo

Registrar a divisão administrativa ou região da empresa.

#### Uso no Negócio

Utilizada para:

* segmentação regional;
* análise comercial;
* campanhas específicas.

#### Critérios de Preenchimento

Brasil:

* Mato Grosso
* São Paulo
* Paraná

Japão:

* Shiga
* Aichi
* Tokyo

#### Decisão Arquitetural

Utilizar propriedade nativa do HubSpot.

---

### City

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | City |
| Objeto | Company |
| Tipo | Texto |
| Categoria | Global |
| Origem | HubSpot padrão |
| Obrigatória | Sim |

#### Objetivo

Identificar a cidade principal onde a empresa está localizada.

#### Uso no Negócio

Utilizada para:

* segmentação local;
* campanhas regionais;
* análise territorial.

#### Decisão Arquitetural

Utilizar propriedade nativa do HubSpot.

---

### Record ID

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Record ID |
| Objeto | Company |
| Tipo | Sistema |
| Categoria | Global |
| Origem | HubSpot |
| Obrigatória | Sim |

#### Objetivo

Identificador único interno gerado automaticamente pelo HubSpot.

#### Uso no Negócio

Utilizado principalmente para:

* integrações;
* sincronização entre sistemas;
* APIs;
* controle técnico.

#### Decisão Arquitetural

Não permitir edição manual.

O identificador deve permanecer sob controle do sistema.

---

### CNPJ

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | CNPJ |
| Objeto | Company |
| Tipo | Texto |
| Categoria | Brasil |
| Origem | Customizada |
| Obrigatória | Sim |

#### Objetivo

Registrar o identificador fiscal oficial das empresas brasileiras.

#### Uso no Negócio

Utilizado para:

* identificação jurídica;
* evitar duplicidade;
* integrações financeiras;
* validações futuras.

#### Critérios de Preenchimento

Formato recomendado:

`00.000.000/0001-00`

#### Decisão Arquitetural

Criar propriedade customizada.

Motivo:

O HubSpot possui arquitetura global e não possui CNPJ como campo universal obrigatório.

Para operações no Brasil, este dado possui valor estratégico.

---

### Instagram Company Page

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Instagram Company Page |
| Objeto | Company |
| Tipo | URL |
| Categoria | Brasil |
| Origem | Customizada |
| Obrigatória | Sim |

#### Objetivo

Registrar o principal perfil comercial da empresa.

#### Uso no Negócio

Utilizado para:

* pesquisa comercial;
* análise de presença digital;
* campanhas futuras.

#### Decisão Arquitetural

Criar propriedade customizada.

Apesar de existirem redes sociais no HubSpot, Instagram comercial possui relevância específica para pequenos e médios negócios brasileiros.

**Evidência de Configuração:**
![Print 3 — Configuração da propriedade Instagram Company Page](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/Documentation/evidence/hubspot/company/03/03_instagram_company_page_configuration.png)

---

### Facebook Company Page

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Facebook Company Page |
| Objeto | Company |
| Tipo | URL |
| Categoria | Global |
| Origem | HubSpot padrão |
| Obrigatória | Não |

#### Objetivo

Registrar a página institucional/comercial da empresa no Facebook.

#### Uso no Negócio

Utilizado para:

* pesquisa comercial;
* análise de presença digital;
* apoio ao relacionamento e marketing.

#### Decisão Arquitetural

Utilizar propriedade nativa do HubSpot (`facebook_company_page`).

---

# Group 2 — Sales Properties (Nativo)

## Objetivo

O grupo **Sales Properties** reúne as propriedades padrão do HubSpot utilizadas para acompanhamento do status comercial e atribuição de responsabilidades da conta.

---

## Approved Properties

| Property | Origin | HubSpot Group |
| --- | --- | --- |
| Lead Status | HubSpot | Sales Properties |
| Company Owner | HubSpot | Sales Properties |

**Evidência de Configuração:**
![Print — Estrutura do grupo Sales Properties](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/Documentation/evidence/hubspot/company/sales-properties/01_sales_properties_group.png)

---

# Group 3 — Finance

## Objetivo e Decisão Arquitetural

> **Decisão Arquitetural:** Nenhuma propriedade foi aprovada para a versão inicial do CRM. Não existe configuração de propriedades financeiras no HubSpot nesta fase.

---

# Grupo 4 — Products & Services

## Objetivo

O grupo Produtos e Serviços reúne informações relacionadas ao interesse, utilização e relacionamento da empresa com as soluções oferecidas.

Estas propriedades têm como objetivo apoiar:

* segmentação de clientes;
* identificação de oportunidades de expansão;
* personalização de comunicação;
* análise de interesse por solução.

Este grupo não deve armazenar informações transacionais, como quantidade vendida, valor da venda ou histórico de compras.

Essas informações devem permanecer associadas ao objeto Deal.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Products of Interest | Customizada | Sim | Customizada |
| Solutions Used | Customizada | Sim | Customizada |
| Customer Product Category | Customizada | Não inicialmente | Customizada |
| Last Purchased Product | Customizada | Não inicialmente | Customizada |
| Product Adoption Status | Customizada | Não inicialmente | Customizada |

---

## Decisões Arquiteturais

### DA-012 — Separação entre interesse e utilização de produtos

O CRM separa informações de interesse comercial e utilização atual de soluções.

Products of Interest representa intenção ou potencial oportunidade.

Solutions Used representa soluções já utilizadas pela empresa.

---

### DA-013 — Produtos não armazenam histórico de vendas

Informações relacionadas a quantidade vendida, valores e histórico de compras não serão armazenadas no objeto Company.

Esses dados deverão permanecer no objeto Deal.

---

## Propriedades Aprovadas

| Propriedade | Origem | Decisão | Motivo |
| --- | --- | --- | --- |
| Products of Interest | Customizada | ✅ Criar | Identificar produtos e soluções que a empresa demonstrou interesse |
| Solutions Used | Customizada | ✅ Criar | Registrar produtos e soluções atualmente utilizados pela empresa |

---

## Propriedades Não Utilizadas Inicialmente

| Propriedade | Origem | Decisão | Motivo |
| --- | --- | --- | --- |
| Customer Product Category | Customizada | Não utilizar inicialmente | Sobreposição funcional com Products of Interest |
| Last Purchased Product | Customizada | Não utilizar inicialmente | Histórico de compras pertencente ao objeto Deal |
| Product Adoption Status | Customizada | Não utilizar inicialmente | Pode ser acompanhado através do relacionamento e uso das soluções |

---

## Especificação das Propriedades

### Products of Interest

| Campo | Definição |
| --- | --- |
| Property Name | Products of Interest |
| Object | Company |
| Group | Products & Services |
| Type | Multiple checkboxes |
| Origin | Custom |
| Purpose | Identificar produtos e soluções que a empresa demonstrou interesse. |
| Usage | Segmentação comercial, campanhas e análise de oportunidades futuras. |

---

### Solutions Used

| Campo | Definição |
| --- | --- |
| Property Name | Solutions Used |
| Object | Company |
| Group | Products & Services |
| Type | Multiple checkboxes |
| Origin | Custom |
| Purpose | Registrar produtos e soluções atualmente utilizados pela empresa. |
| Usage | Expansão de clientes, cross-sell e análise de relacionamento. |

---

# Status do Grupo

**Grupo 4 — Products & Services**

- **Status:** Modelado e configurado
- **Propriedades aprovadas:**
  * Products of Interest
  * Solutions Used
- **Decisão arquitetural principal:** Informações de interesse permanecem no objeto Company. Informações de compra, contrato e histórico comercial serão controladas através do objeto Deal.

---

# Grupo 5 — Finance

## Objetivo

O grupo Finance reúne informações financeiras estratégicas da empresa que apoiam análises, segmentações e tomada de decisão.

Este grupo não deve armazenar informações transacionais, como valores de negociações, pagamentos, faturas ou receitas provenientes de vendas.

Esses dados deverão permanecer nos objetos apropriados ou em sistemas financeiros integrados.

As propriedades deste grupo têm como objetivo:

* apoiar análises estratégicas;
* auxiliar na qualificação de clientes;
* identificar potencial financeiro da empresa;
* fornecer informações para segmentação e planejamento comercial.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Payment Terms | Customizada | Sim | Customizada |
| Customer Credit Status | Customizada | Não inicialmente | Customizada |
| Financial Risk | Customizada | Não inicialmente | Customizada |
| Currency | HubSpot | Não | HubSpot |
| Annual Revenue | HubSpot | Não inicialmente | HubSpot |

---

## Decisões Arquiteturais

### DA-014 — Dados financeiros transacionais não pertencem ao objeto Company

Informações como faturamento, pagamentos, receitas, condições comerciais específicas e histórico financeiro deverão permanecer nos objetos apropriados ou em sistemas financeiros integrados.

---

### DA-015 — Grupo reservado para evolução futura

O grupo Finance faz parte da arquitetura do CRM, porém nenhuma propriedade será criada nesta primeira versão.

Novas propriedades somente serão adicionadas quando existir um processo operacional que justifique sua utilização.

---

## Propriedades Aprovadas

Nenhuma propriedade foi aprovada para implementação na versão inicial do CRM.

---

## Propriedades Não Utilizadas Inicialmente

| Propriedade | Origem | Decisão | Motivo |
| --- | --- | --- | --- |
| Payment Terms | Customizada | Não utilizar inicialmente | Sem processo financeiro integrado nesta fase |
| Customer Credit Status | Customizada | Não utilizar inicialmente | Análise de crédito realizada em sistema externo |
| Financial Risk | Customizada | Não utilizar inicialmente | Ausência de política formal de risco configurada no CRM |
| Currency | HubSpot | Não utilizar inicialmente | Operação exclusivamente nacional em moeda BRL |
| Annual Revenue | HubSpot | Não utilizar inicialmente | Baixa confiabilidade e pouca aplicação operacional no início |

---

## Especificação

Nenhuma propriedade foi aprovada para implementação na versão inicial do CRM.

---

# Status do Grupo

**Grupo 5 — Finance**

- **Status:** Concluído (Sem propriedades nesta versão)
- **Propriedades aprovadas:** Nenhuma nesta versão
- **Decisão arquitetural principal:** Nenhuma propriedade financeira foi criada nesta primeira fase para evitar complexidade desnecessária e manter a integridade dos dados.

---

# Grupo 6 — Customer Success

## Objetivo

O grupo Customer Success reúne informações utilizadas para acompanhar o relacionamento da empresa com a organização após o processo comercial.

Essas propriedades têm como objetivo apoiar:

* retenção de clientes;
* identificação de oportunidades de expansão;
* monitoramento da saúde do relacionamento;
* priorização de ações de acompanhamento.

Este grupo não deve armazenar informações operacionais de atendimento ou chamados, pois essas informações pertencem ao objeto Ticket.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Customer Health | Customizada | Sim | Customizada |
| Onboarding Status | Customizada | Sim | Customizada |
| Renewal Status | Customizada | Não inicialmente | Customizada |
| Last Success Review | Customizada | Não inicialmente | Customizada |
| Churn Risk | Customizada | Não inicialmente | Customizada |

---

## Decisões Arquiteturais

### DA-016 — Separação entre pós-venda estratégico e operacional

O objeto Company armazenará exclusivamente dados estratégicos do relacionamento pós-venda, como saúde do cliente e status de onboarding.

Atendimentos operacionais, dúvidas e chamados pertencem ao objeto Ticket.

---

### DA-017 — Monitoramento preventivo de saúde do cliente

As propriedades Customer Health e Onboarding Status serão utilizadas para acionar fluxos de acompanhamento preventivo e mitigar riscos de churn.

---

## Propriedades Aprovadas

| Propriedade | Origem | Decisão | Motivo |
| --- | --- | --- | --- |
| Customer Health | Customizada | ✅ Criar | Monitorar a saúde e engajamento da conta no pós-venda |
| Onboarding Status | Customizada | ✅ Criar | Acompanhar a evolução da etapa inicial de implantação/onboarding |

---

## Propriedades Não Utilizadas Inicialmente

| Propriedade | Origem | Decisão | Motivo |
| --- | --- | --- | --- |
| Renewal Status | Customizada | Não utilizar inicialmente | Controle de renovação gerido através dos contratos/Deals |
| Last Success Review | Customizada | Não utilizar inicialmente | Registrado automaticamente via histórico de atividades/reuniões |
| Churn Risk | Customizada | Não utilizar inicialmente | Indicador incorporado nas opções da propriedade Customer Health |

---

## Especificação das Propriedades

| Property | Group | Type |
| --- | --- | --- |
| Customer Health | Customer Success | Dropdown select |
| Onboarding Status | Customer Success | Dropdown select |

---

### Customer Health

| Campo | Definição |
| --- | --- |
| Property Name | Customer Health |
| Object | Company |
| Group | Customer Success |
| Type | Dropdown select |
| Origin | Custom |
| Options | Healthy, Attention, Critical |
| Purpose | Monitorar o nível de saúde do cliente e engajamento com as soluções. |
| Usage | Priorização de atendimento CS, alerta de risco de churn e relatórios de saúde da carteira. |

---

### Onboarding Status

| Campo | Definição |
| --- | --- |
| Property Name | Onboarding Status |
| Object | Company |
| Group | Customer Success |
| Type | Dropdown select |
| Origin | Custom |
| Options | Not Started, In Progress, Completed |
| Purpose | Acompanhar o progresso de implantação/onboarding de novos clientes. |
| Usage | Controle da jornada inicial do cliente e identificação de gargalos na implantação. |

---

# Status do Grupo

**Grupo 6 — Customer Success**

- **Status:** Modelado e configurado
- **Propriedades aprovadas:**
  * Customer Health
  * Onboarding Status
- **Decisão arquitetural principal:** A Company armazenará informações estratégicas de saúde do cliente e onboarding. Atendimentos e solicitações operacionais serão controlados pelo objeto Ticket.

---

# Grupo 7 — Marketing

## Objetivo

O grupo Marketing reúne informações utilizadas para segmentação, campanhas e análise da origem do relacionamento com a empresa.

As propriedades deste grupo têm como objetivo apoiar:

* segmentação de campanhas;
* personalização da comunicação;
* análise de aquisição de clientes;
* automações de marketing.

Este grupo não deve armazenar métricas de campanhas ou atividades de marketing, pois essas informações são registradas automaticamente pelo HubSpot.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Primary Acquisition Channel | Customizada | Sim | Customizada |
| Marketing Consent Status | HubSpot | Não | HubSpot |
| Lead Source Detail | Customizada | Não inicialmente | Customizada |
| Newsletter Subscriber | HubSpot | Não | HubSpot |
| Marketing Qualified | HubSpot | Não | HubSpot |

---

## Decisões Arquiteturais

### DA-018 — Marketing focado em segmentação

As propriedades deste grupo serão utilizadas para segmentação e análise da origem dos clientes.

---

### DA-019 — Funcionalidades nativas têm prioridade

Recursos de consentimento, assinatura de e-mails e métricas de campanhas utilizarão as funcionalidades nativas do HubSpot, evitando duplicidade de informações.

---

## Propriedades Aprovadas

| Propriedade | Origem | Decisão | Motivo |
| --- | --- | --- | --- |
| Primary Acquisition Channel | Customizada | ✅ Criar | Identificar o canal principal de aquisição da empresa para segmentação |

---

## Especificação das Propriedades

| Property | Group | Type |
| --- | --- | --- |
| Primary Acquisition Channel | Marketing | Dropdown select |

---

### Primary Acquisition Channel

| Campo | Definição |
| --- | --- |
| Property Name | Primary Acquisition Channel |
| Object | Company |
| Group | Marketing |
| Type | Dropdown select |
| Origin | Custom |
| Options | Organic Search, Google Ads, Instagram, Facebook, LinkedIn, Referral, WhatsApp, Event, Direct, Other |
| Purpose | Identificar o canal principal de aquisição da empresa. |
| Usage | Segmentação de campanhas, análise de ROI e estratégia de aquisição. |

**Evidência de Configuração:**
![Print — Configuração Primary Acquisition Channel](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/Documentation/evidence/hubspot/company/marketing/01_primary_acquisition_channel_configuration.png)

---

# Status do Grupo

**Grupo 7 — Marketing**

- **Status:** Modelado e configurado
- **Propriedades aprovadas:**
  * Primary Acquisition Channel
- **Decisão arquitetural principal:** O CRM utilizará propriedades nativas do HubSpot para rastreamento e comunicação individual, criando apenas propriedades customizadas estratégicas para a empresa.

















