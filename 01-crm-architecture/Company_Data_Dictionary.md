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

As propriedades da Empresa serão organizadas nos seguintes grupos:

1. Identificação
2. Perfil da Empresa
3. Informações Comerciais
4. Produtos e Serviços
5. Financeiro
6. Customer Success
7. Marketing

Cada grupo será documentado em uma seção específica deste documento.

---

# Grupo 1 — Identificação

## Objetivo

O Grupo **Identificação** reúne todas as informações responsáveis por identificar de forma única uma empresa dentro do CRM.

As propriedades deste grupo não descrevem características comerciais ou operacionais do cliente.

Sua função é permitir:

* identificar corretamente uma empresa;
* evitar registros duplicados;
* facilitar integrações;
* padronizar cadastros;
* garantir rastreabilidade entre sistemas.

---

## Propriedades Candidatas

| Propriedade         | Categoria | Necessária?        | Origem      |
| ------------------- | --------- | ------------------ | ----------- |
| Company Name        | Global    | Sim                | HubSpot     |
| Company Domain      | Global    | Sim                | HubSpot     |
| Website             | Global    | Sim                | HubSpot     |
| Phone Number        | Global    | Sim                | HubSpot     |
| Country             | Global    | Sim                | HubSpot     |
| State/Region        | Global    | Sim                | HubSpot     |
| City                | Global    | Sim                | HubSpot     |
| Record ID           | Global    | Sim                | HubSpot     |
| CNPJ                | Brasil    | Sim                | Customizada |
| Razão Social        | Brasil    | Sim                | Customizada |
| Nome Fantasia       | Brasil    | Sim                | Customizada |
| Inscrição Estadual  | Brasil    | Não (Inicialmente) | Customizada |
| Inscrição Municipal | Brasil    | Não (Inicialmente) | Customizada |
| Instagram Comercial | Brasil    | Sim                | Customizada |
| Facebook            | Global    | Não                | HubSpot     |
| LinkedIn            | Global    | Não                | HubSpot     |

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

A identificação de uma Empresa utilizará uma combinação de propriedades, conforme definido no documento **CRM_Data_Governance.md**, não dependendo de um único identificador.

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

### Razão Social

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Razão Social |
| Objeto | Company |
| Tipo | Texto |
| Categoria | Brasil |
| Origem | Customizada |
| Obrigatória | Sim |

#### Objetivo

Registrar o nome jurídico oficial da empresa.

#### Uso no Negócio

Utilizado para:

* contratos;
* documentos fiscais;
* integrações administrativas.

#### Decisão Arquitetural

Criar propriedade customizada.

Separar nome comercial e nome jurídico evita mistura de informações.

---

### Nome Fantasia

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Nome Fantasia |
| Objeto | Company |
| Tipo | Texto |
| Categoria | Brasil |
| Origem | Customizada |
| Obrigatória | Sim |

#### Objetivo

Registrar o nome comercial oficial quando diferente da razão social.

#### Uso no Negócio

Utilizado para:

* comunicação comercial;
* identificação pública;
* relacionamento com clientes.

#### Decisão Arquitetural

Criar propriedade customizada.

---

### Instagram Comercial

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Instagram Comercial |
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

---

# Grupo 2 — Perfil da Empresa

## Objetivo

O Grupo **Perfil da Empresa** reúne informações estruturais e classificatórias sobre uma organização.

As propriedades deste grupo têm como objetivo permitir compreender o contexto da empresa, seu porte, segmento de atuação e características gerais.

Estas informações devem apoiar:

* segmentação comercial;
* personalização da comunicação;
* análise de mercado;
* criação de relatórios;
* definição de estratégias de relacionamento.

As propriedades deste grupo não devem armazenar informações relacionadas diretamente a oportunidades comerciais, produtos adquiridos ou dados financeiros.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Industry | Global | Sim | HubSpot |
| Company Type | Global | Sim | HubSpot |
| Number of Employees | Global | Sim | HubSpot |
| Annual Revenue | Global | Não inicialmente | HubSpot |
| Business Segment | Brasil | Sim | Customizada |
| Business Model | Brasil | Sim | Customizada |
| Company Size Classification | Customizada | Sim | Customizada |
| Years in Operation | Brasil | Não inicialmente | Customizada |
| Target Market | Customizada | Não inicialmente | Customizada |
| Main Customer Profile | Customizada | Não inicialmente | Customizada |

---

## Decisões Arquiteturais

### DA-005 — Utilização de propriedades globais quando disponíveis

Sempre que uma propriedade padrão do HubSpot atender ao requisito de negócio, ela será utilizada antes da criação de uma propriedade customizada.

Exemplo:

A propriedade **Industry** será utilizada para classificação geral da empresa, evitando a criação de um campo duplicado.

---

### DA-006 — Separação entre classificação global e segmentação comercial

O CRM utilizará propriedades globais do HubSpot para classificações universais e propriedades customizadas para informações específicas do mercado ou estratégia comercial.

Exemplo:

- **Industry** representa a classificação global da empresa.
- **Business Segment** representa a segmentação comercial utilizada pela organização.

---

### DA-007 — Dados calculáveis não serão mantidos manualmente

Propriedades que podem ser derivadas a partir de outros dados não devem depender de preenchimento manual.

Exemplo:

A propriedade **Company Size Classification** será baseada na informação de **Number of Employees** e poderá ser gerada através de automação.

---

### DA-008 — Evitar duplicidade entre propriedades de ciclo de vida

Propriedades relacionadas ao relacionamento da empresa com a organização não devem ser armazenadas neste grupo.

Exemplo:

Informações como:

* cliente ativo;
* oportunidade;
* lead;
* status comercial;

serão tratadas nos grupos apropriados ou através das propriedades padrão do HubSpot.

---

### DA-009 — Criar propriedades somente quando existir finalidade operacional

Uma propriedade somente fará parte do CRM quando possuir pelo menos um dos seguintes objetivos:

* segmentação;
* automação;
* integração;
* relatório;
* apoio à tomada de decisão.

---

## Propriedades Aprovadas

| Propriedade | Decisão | Motivo |
| --- | --- | --- |
| Industry | Aprovada | Classificação global utilizada pelo HubSpot |
| Number of Employees | Aprovada | Permite identificar porte da empresa |
| Business Segment | Aprovada | Necessária para segmentação comercial brasileira |
| Business Model | Aprovada | Permite classificar modelo de atuação |
| Company Size Classification | Aprovada | Facilita relatórios e segmentações |

---

## Propriedades Não Utilizadas Inicialmente

| Propriedade | Decisão | Motivo |
| --- | --- | --- |
| Annual Revenue | Não utilizar inicialmente | Baixa confiabilidade e pouca aplicação operacional no início |
| Years in Operation | Não utilizar inicialmente | Não possui impacto imediato em automações ou relatórios |
| Target Market | Não utilizar inicialmente | Informação pode ser obtida em outros processos comerciais |
| Main Customer Profile | Não utilizar inicialmente | Possui maior relação com estratégia comercial do que cadastro da empresa |

---

# Grupo 3 — Informações Comerciais

## Objetivo

O Grupo **Informações Comerciais** reúne informações relacionadas ao relacionamento comercial entre a empresa e a organização.

As propriedades deste grupo têm como objetivo registrar informações que auxiliam o processo de vendas, acompanhamento de oportunidades, gestão da carteira e análise comercial.

Estas informações devem apoiar:

* gestão do processo comercial;
* segmentação de empresas;
* acompanhamento de oportunidades;
* análise de desempenho de vendas;
* definição de estratégias comerciais.

As propriedades deste grupo não devem armazenar informações relacionadas a produtos específicos, valores financeiros detalhados ou dados de relacionamento após a venda.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Lifecycle Stage | Global | Sim | HubSpot |
| Lead Status | Global | Sim | HubSpot |
| Company Owner | Global | Sim | HubSpot |
| Create Date | Global | Sim | HubSpot |
| Last Activity Date | Global | Sim | HubSpot |
| Original Source | Global | Sim | HubSpot |
| Acquisition Channel | Brasil | Sim | Customizada |
| Sales Territory | Customizada | Não inicialmente | Customizada |
| Customer Potential | Customizada | Sim | Customizada |
| Commercial Priority | Customizada | Sim | Customizada |
| Lead Qualification | Customizada | Não inicialmente | Customizada |
| Relationship Status | Customizada | Não inicialmente | Customizada |

---

## Análise Arquitetural Inicial

### Lifecycle Stage
- **Pergunta Arquitetural:** Precisamos criar um campo próprio para estágio do relacionamento?
- **Resposta:** Não. O HubSpot já possui uma propriedade padrão criada exatamente para controlar a evolução do relacionamento (*Subscriber, Lead, MQL, SQL, Opportunity, Customer*).
- **Decisão:** Utilizar propriedade nativa.

### Lead Status
- **Pergunta:** Como controlar empresas que estão em processo comercial?
- **Resposta:** O HubSpot já possui a propriedade nativa Lead Status (*New, Open, In Progress, Qualified, Unqualified*).
- **Decisão:** Utilizar propriedade nativa.

### Company Owner
- **Finalidade:** Responsável interno pelo relacionamento.
- **Importante para:** Distribuição de carteira, responsabilidade comercial e relatórios.
- **Decisão:** Utilizar propriedade nativa.

### Create Date
- **Finalidade:** Data técnica criada automaticamente pelo HubSpot.
- **Utilizada para:** Análise de aquisição, tempo de relacionamento e relatórios.
- **Decisão:** Utilizar propriedade nativa.

### Last Activity Date
- **Finalidade:** Permite identificar empresas sem interação recente.
- **Uso:** Acompanhamento comercial, identificação de risco e produtividade.
- **Decisão:** Utilizar propriedade nativa.

### Original Source
- **Finalidade:** Registra origem técnica da empresa (*Organic Search, Social Media, Referral, Offline Source*).
- **Decisão:** Utilizar propriedade nativa.

### Acquisition Channel
- **Diferença Estratégica:** Enquanto *Original Source* responde "De onde veio o contato?", *Acquisition Channel* responde "Qual canal estratégico gerou a aquisição?" (Ex.: Campanha Google Ads - Pequenas Empresas).
- **Decisão:** Criar propriedade customizada.

### Customer Potential
- **Finalidade:** Representa potencial comercial futuro (*Baixo, Médio, Alto*).
- **Uso:** Auxiliar a priorização comercial.
- **Decisão:** Criar propriedade customizada.

### Commercial Priority
- **Finalidade:** Representa a prioridade operacional da equipe (*Alta, Média, Baixa*).
- **Diferença:** Potencial = Valor possível; Prioridade = Decisão interna da equipe.
- **Decisão:** Criar propriedade customizada.

---

## Decisões Arquiteturais

### DA-010 — Utilizar propriedades nativas para controle do ciclo comercial

Sempre que o HubSpot possuir uma propriedade padrão relacionada ao processo comercial, ela será utilizada para manter compatibilidade com recursos nativos da plataforma.

Exemplo:

**Lifecycle Stage** e **Lead Status** serão utilizados sem criação de campos equivalentes.

---

### DA-011 — Separação entre origem, aquisição e relacionamento comercial

O CRM deverá diferenciar:

* origem técnica do registro;
* canal estratégico de aquisição;
* estágio do relacionamento comercial.

Essas informações possuem objetivos diferentes e não devem ser agrupadas em uma única propriedade.

---

### DA-012 — Separação entre potencial comercial e prioridade operacional

O potencial comercial representa a oportunidade futura de negócio.

A prioridade comercial representa a decisão interna da equipe sobre onde concentrar esforços.

Essas informações devem permanecer separadas para evitar interpretações incorretas.

---

### DA-013 — Informações comerciais devem apoiar ações

Uma propriedade comercial somente será criada quando puder gerar:

* ação da equipe;
* segmentação;
* automação;
* relatório;
* tomada de decisão.

---

### DA-014 — Evitar armazenar informações de negócio no objeto incorreto

Informações relacionadas a uma negociação específica, como:

* valor da oportunidade;
* produto vendido;
* previsão de fechamento;
* etapa da negociação;

devem pertencer ao objeto **Deal (Negócio)** e não ao objeto **Company (Empresa)**.

---

## Propriedades Aprovadas

| Propriedade | Decisão | Motivo |
| --- | --- | --- |
| Lifecycle Stage | Aprovada | Controle padrão do ciclo de relacionamento HubSpot |
| Lead Status | Aprovada | Controle operacional do processo comercial |
| Company Owner | Aprovada | Define responsável interno |
| Create Date | Aprovada | Controle histórico do registro |
| Last Activity Date | Aprovada | Permite acompanhamento de interação |
| Original Source | Aprovada | Análise de origem dos registros |
| Acquisition Channel | Aprovada | Necessária para análise estratégica de aquisição |
| Customer Potential | Aprovada | Permite priorização de oportunidades futuras |
| Commercial Priority | Aprovada | Auxilia gestão da carteira |

---

## Propriedades Não Utilizadas Inicialmente

| Propriedade | Decisão | Motivo |
| --- | --- | --- |
| Sales Territory | Não utilizar inicialmente | Necessário apenas em operações com equipe comercial regionalizada |
| Lead Qualification | Não utilizar inicialmente | Pode ser tratado através de processos de qualificação e propriedades existentes |
| Relationship Status | Não utilizar inicialmente | Pode gerar conflito com Lifecycle Stage e Customer Status |








