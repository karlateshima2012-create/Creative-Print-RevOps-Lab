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

1. Contact Information
2. Perfil da Empresa
3. Informações Comerciais
4. Produtos e Serviços
5. Financeiro
6. Customer Success
7. Marketing

Cada grupo será documentado em uma seção específica deste documento.

---

# Group 1 — Contact Information

## Objetivo

The Contact Information group contains the core company data used to identify, locate and uniquely register an organization within the CRM.

These properties represent stable business information and support integrations, commercial processes and operational activities throughout the customer lifecycle.

---

## Approved Properties

### Company Information

| Property | Origin |
| --- | --- |
| Company Name | HubSpot |
| Website URL | HubSpot |
| Phone Number | HubSpot |
| Country/Region | HubSpot |
| State/Region | HubSpot |
| City | HubSpot |
| Record ID | HubSpot |
| CNPJ | Custom |

### Social Media Information

| Property | Origin |
| --- | --- |
| Facebook Company Page | HubSpot |
| LinkedIn Company Page | HubSpot |
| Instagram Company Page | Custom |


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

# Grupo 2 — Perfil da Empresa

## Objetivo

O grupo Perfil da Empresa reúne informações responsáveis por descrever as características organizacionais da empresa dentro do CRM.

Essas propriedades têm como objetivo permitir:

* segmentação de empresas;
* classificação de clientes;
* personalização de abordagens comerciais;
* criação de relatórios estratégicos;
* análise da carteira de empresas.

Este grupo não deve armazenar informações de negociação, receita ou histórico de relacionamento, pois esses dados pertencem aos objetos e grupos específicos correspondentes.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Industry | Global | Sim | HubSpot |
| Company Size | Global | Sim | HubSpot |
| Number of Employees | Global | Sim | HubSpot |
| Annual Revenue | Global | Não inicialmente | HubSpot |
| Business Type | Customizada | Sim | Customizada |
| Customer Segment | Customizada | Sim | Customizada |
| Market Segment | Customizada | Sim | Customizada |
| Business Model | Customizada | Não inicialmente | Customizada |
| Company Description | Global | Não inicialmente | HubSpot |

---

## Decisões Arquiteturais

### DA-005 — Utilizar propriedades nativas para classificação organizacional

Propriedades padrão do HubSpot serão utilizadas quando atenderem aos objetivos de segmentação e análise da empresa.

---

### DA-006 — Evitar duplicidade entre tamanho da empresa e segmentação

A classificação de porte será realizada utilizando Company Size e Number of Employees, evitando a criação de campos redundantes.

---

### DA-007 — Criar segmentações estratégicas somente quando agregarem valor

Novas propriedades de segmentação serão criadas apenas quando forem necessárias para filtros, automações ou relatórios.

---

### DA-008 — Separar características da empresa de informações comerciais

Dados relacionados ao perfil organizacional permanecerão no objeto Company.

Informações de vendas, negociação e receita serão tratadas no grupo Informações Comerciais.

---

### DA-009 — Business Type como classificação organizacional

A propriedade Business Type será utilizada para classificar o modelo de atuação da empresa.

Esta informação tem como objetivo apoiar segmentação comercial, personalização de abordagem e análises futuras.

A propriedade não substitui Industry, pois Industry representa o setor de atuação enquanto Business Type representa o formato operacional da empresa.

**Evidências de Configuração:**
![Print 1 — Configuração Business Type](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/Documentation/evidence/hubspot/company/profile/01_business_type_configuration.png)
![Print 2 — Opções Dropdown Business Type](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/Documentation/evidence/hubspot/company/profile/02_dropdown_options.png)

---

## Propriedades Aprovadas

| Propriedade | Origem | Decisão | Motivo |
| --- | --- | --- | --- |
| Industry | HubSpot | ✅ Utilizar | Classificação setorizada global nativa do HubSpot |
| Number of Employees | HubSpot | ✅ Utilizar | Identificação do porte estrutural por contagem de funcionários |
| Business Type | Customizada | ✅ Criar | Classificação do formato/modelo operacional da empresa |

---

## Propriedades Não Utilizadas Inicialmente

| Propriedade | Origem | Decisão | Motivo |
| --- | --- | --- | --- |
| Company Size | HubSpot | Não utilizar inicialmente | Subsequente ao Number of Employees |
| Annual Revenue | HubSpot | Não utilizar inicialmente | Baixa confiabilidade e pouca aplicação operacional no início |
| Customer Segment | Customizada | Não utilizar inicialmente | Não possui processo estruturado de coleta definido |
| Market Segment | Customizada | Não utilizar inicialmente | Pode ser derivado da combinação de Industry e Business Type |
| Business Model | Customizada | Não utilizar inicialmente | Consolidado dentro das opções da propriedade Business Type |
| Company Description | HubSpot | Não utilizar inicialmente | Campo de texto livre sem utilização para automação/relatório |

---

# Grupo 3 — Informações Comerciais

## Objetivo

O grupo Informações Comerciais reúne informações relacionadas ao relacionamento comercial entre a empresa e a organização.

As propriedades deste grupo têm como objetivo apoiar:

* qualificação comercial;
* priorização de oportunidades;
* segmentação da carteira;
* planejamento de abordagem;
* análises do processo comercial.

Este grupo não deve armazenar informações transacionais, como valores de venda, produtos vendidos ou histórico de negociações, pois essas informações pertencem ao objeto Deal.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Lead Status | Global | Sim | HubSpot |
| Lifecycle Stage | Global | Sim | HubSpot |
| Owner | Global | Sim | HubSpot |
| Relationship Status | Customizada | Sim | Customizada |
| Customer Tier | Customizada | Não inicialmente | Customizada |
| Sales Priority | Customizada | Não inicialmente | Customizada |
| Acquisition Channel | Customizada | Não inicialmente | Customizada |
| Last Contact Date | Global | Não | HubSpot |
| Next Activity Date | Global | Não | HubSpot |

---

## Decisões Arquiteturais

### DA-010 — Utilizar propriedades comerciais nativas do HubSpot

As propriedades comerciais existentes no HubSpot serão utilizadas para controlar ciclo de vida, status comercial e responsável pela conta.

Novas propriedades não serão criadas quando houver sobreposição funcional com campos nativos.

---

### DA-011 — Evitar duplicidade de status comercial

O CRM não utilizará propriedades customizadas equivalentes a Lifecycle Stage ou Lead Status para evitar divergência de informação.

---

## Propriedades Aprovadas

| Propriedade | Origem | Decisão | Motivo |
| --- | --- | --- | --- |
| Lifecycle Stage | HubSpot | ✅ Utilizar | Controle nativo do ciclo de relacionamento com a empresa |
| Lead Status | HubSpot | ✅ Utilizar | Controle operacional do processo comercial e qualificação |
| Company Owner | HubSpot | ✅ Utilizar | Atribuição de responsabilidade interna pela conta |

---

## Propriedades Não Utilizadas Inicialmente

| Propriedade | Origem | Decisão | Motivo |
| --- | --- | --- | --- |
| Relationship Status | Customizada | Não utilizar inicialmente | Sobreposição funcional com Lifecycle Stage e Lead Status |
| Customer Tier | Customizada | Não utilizar inicialmente | Necessita de regras de negócio de classificação de carteira consolidadas |
| Sales Priority | Customizada | Não utilizar inicialmente | Pode ser gerenciado no objeto Deal durante as oportunidades |
| Acquisition Channel | Customizada | Não utilizar inicialmente | Rastreamento técnico coberto pelo Original Source nativo |
| Last Contact Date | HubSpot | Não utilizar inicialmente | Atualizado automaticamente por interações/atividades nativas |
| Next Activity Date | HubSpot | Não utilizar inicialmente | Gerenciado nativamente por tarefas e compromissos |

---

## Especificação das Propriedades Aprovadas

### Lifecycle Stage

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Lifecycle Stage |
| Objeto | Company |
| Tipo | Dropdown |
| Categoria | Global |
| Origem | HubSpot padrão |
| Obrigatória | Sim |

#### Objetivo

Controlar a evolução do relacionamento da empresa dentro do ciclo de vida comercial.

A propriedade representa o estágio geral em que a empresa se encontra dentro da jornada de relacionamento.

#### Uso no Negócio

Utilizada para:

* segmentação de empresas;
* automações de marketing e vendas;
* relatórios de conversão;
* análise do funil comercial.

#### Critérios de Preenchimento

Valores padrão do HubSpot:

* Subscriber
* Lead
* Marketing Qualified Lead
* Sales Qualified Lead
* Opportunity
* Customer
* Evangelist
* Other

A definição dos valores utilizados deve seguir o processo comercial adotado pela organização.

#### Decisão Arquitetural

Utilizar propriedade nativa do HubSpot.

**Motivo:** A propriedade atende ao controle do ciclo de relacionamento e possui integração direta com ferramentas nativas da plataforma.

---

### Lead Status

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Lead Status |
| Objeto | Company |
| Tipo | Dropdown |
| Categoria | Global |
| Origem | HubSpot padrão |
| Obrigatória | Sim |

#### Objetivo

Controlar a situação operacional de uma empresa dentro do processo comercial.

Diferente do Lifecycle Stage, esta propriedade representa o acompanhamento diário realizado pela equipe comercial.

#### Uso no Negócio

Utilizada para:

* organizar tarefas comerciais;
* acompanhar leads em andamento;
* identificar empresas sem evolução;
* gerar relatórios operacionais.

#### Critérios de Preenchimento

Exemplo de valores:

* New
* Open
* In Progress
* Connected
* Qualified
* Unqualified
* Attempted to Contact

Os valores podem ser adaptados conforme o processo comercial definido.

#### Decisão Arquitetural

Utilizar propriedade nativa do HubSpot.

**Motivo:** Evita criação de campos equivalentes e mantém compatibilidade com recursos comerciais da plataforma.

---

### Company Owner

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Company Owner |
| Objeto | Company |
| Tipo | Usuário |
| Categoria | Global |
| Origem | HubSpot padrão |
| Obrigatória | Sim |

#### Objetivo

Identificar o responsável interno pelo relacionamento com a empresa.

#### Uso no Negócio

Utilizada para:

* distribuição de carteira;
* gestão de responsabilidades;
* relatórios por vendedor;
* acompanhamento de atendimento.

#### Critérios de Preenchimento

Cada empresa deve possuir um responsável definido quando entrar no processo comercial.

#### Decisão Arquitetural

Utilizar propriedade nativa do HubSpot.

**Motivo:** É integrada ao gerenciamento de usuários e permissões da plataforma.

---

### Create Date

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Create Date |
| Objeto | Company |
| Tipo | Data |
| Categoria | Global |
| Origem | HubSpot padrão |
| Obrigatória | Sim |

#### Objetivo

Registrar automaticamente a data em que o registro da empresa foi criado no CRM.

#### Uso no Negócio

Utilizada para:

* análise de crescimento da base;
* relatórios históricos;
* cálculo de tempo no CRM.

#### Critérios de Preenchimento

Preenchimento automático pelo sistema. Não deve ser alterada manualmente.

#### Decisão Arquitetural

Utilizar propriedade nativa do HubSpot.

---

### Last Activity Date

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Last Activity Date |
| Objeto | Company |
| Tipo | Data |
| Categoria | Global |
| Origem | HubSpot padrão |
| Obrigatória | Sim |

#### Objetivo

Registrar a última interação realizada com a empresa.

#### Uso no Negócio

Utilizada para:

* identificar empresas sem contato;
* criar alertas comerciais;
* analisar produtividade.

#### Critérios de Preenchimento

Atualizada automaticamente através das atividades registradas no CRM (ligações, reuniões, e-mails, tarefas).

#### Decisão Arquitetural

Utilizar propriedade nativa do HubSpot.

---

### Original Source

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Original Source |
| Objeto | Company |
| Tipo | Dropdown |
| Categoria | Global |
| Origem | HubSpot padrão |
| Obrigatória | Sim |

#### Objetivo

Identificar o primeiro canal pelo qual a empresa entrou no CRM.

#### Uso no Negócio

Utilizada para:

* análise de aquisição;
* atribuição de marketing;
* relatórios de origem.

#### Critérios de Preenchimento

Valores controlados pelo HubSpot (*Organic Search, Paid Search, Social Media, Referral, Offline Sources*).

#### Decisão Arquitetural

Utilizar propriedade nativa do HubSpot.

---

### Acquisition Channel

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Acquisition Channel |
| Objeto | Company |
| Tipo | Dropdown |
| Categoria | Brasil |
| Origem | Customizada |
| Obrigatória | Sim |

#### Objetivo

Registrar o canal estratégico responsável pela aquisição da empresa.

#### Uso no Negócio

Utilizada para:

* análise de estratégia comercial;
* comparação de canais;
* planejamento de investimentos.

#### Critérios de Preenchimento

Exemplo de valores:

* Indicação
* Google Ads
* Instagram
* Evento
* Prospecção ativa
* Parceiro comercial

#### Decisão Arquitetural

Criar propriedade customizada.

**Motivo:** A propriedade complementa Original Source com uma visão estratégica de negócio.

---

### Customer Potential

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Customer Potential |
| Objeto | Company |
| Tipo | Dropdown |
| Categoria | Customizada |
| Origem | Brasil |
| Obrigatória | Sim |

#### Objetivo

Classificar o potencial comercial futuro da empresa.

#### Uso no Negócio

Utilizada para:

* priorização comercial;
* segmentação da carteira;
* definição de estratégias de abordagem.

#### Critérios de Preenchimento

Valores sugeridos:

* Alto
* Médio
* Baixo

Critérios devem ser definidos pela estratégia comercial.

#### Decisão Arquitetural

Criar propriedade customizada.

**Motivo:** Representa uma avaliação estratégica interna que não existe como propriedade padrão do HubSpot.

---

### Commercial Priority

#### Informações Gerais

| Campo | Definição |
| --- | --- |
| Nome da Propriedade | Commercial Priority |
| Objeto | Company |
| Tipo | Dropdown |
| Categoria | Customizada |
| Origem | Brasil |
| Obrigatória | Sim |

#### Objetivo

Definir a prioridade operacional de acompanhamento da empresa pela equipe comercial.

#### Uso no Negócio

Utilizada para:

* organização da carteira;
* definição de foco comercial;
* criação de listas prioritárias.

#### Critérios de Preenchimento

Valores sugeridos:

* Alta
* Média
* Baixa

#### Decisão Arquitetural

Criar propriedade customizada.

**Motivo:** A prioridade operacional depende da estratégia interna da empresa e não deve ser confundida com potencial comercial.

---

# Status do Grupo

**Grupo 3 — Informações Comerciais**

- **Status:** Modelagem concluída
- **Próxima etapa:** Configuração no HubSpot após conclusão da modelagem completa dos grupos de Company.

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

### DA-025 — Separação entre relacionamento e atendimento

Informações relacionadas à saúde do cliente permanecerão no objeto **Company**.

Informações relacionadas a solicitações, problemas e atendimentos específicos serão controladas pelo objeto **Ticket**.

---

### DA-026 — Customer Success possui visão diferente de Sales

O estágio comercial e a saúde do cliente possuem objetivos diferentes.

- **Lifecycle Stage** controla evolução comercial.
- **Customer Status** controla relacionamento após aquisição.

---

### DA-027 — Saúde do cliente deve permitir ação

Uma propriedade de Customer Success somente será criada quando permitir:

* retenção;
* expansão;
* priorização;
* prevenção de churn.

---

### DA-028 — Evitar criar métricas sem processo definido

Indicadores como:

* NPS;
* satisfação;
* feedback;

somente serão adicionados quando existir um processo estruturado de coleta e utilização.

---

### DA-029 — Informações recorrentes dependem do modelo de negócio

Campos relacionados a renovação, contratos e recorrência somente serão utilizados quando houver necessidade operacional real.

---

## Propriedades Aprovadas

| Propriedade | Decisão | Motivo |
| --- | --- | --- |
| Customer Status | Aprovada | Controla situação atual do cliente |
| Customer Health Score | Aprovada | Permite acompanhamento de saúde |
| Customer Tier | Aprovada | Permite diferenciação estratégica |
| Last Customer Interaction | Aprovada | Permite acompanhamento de relacionamento |
| Churn Risk Level | Aprovada | Permite prevenção de perda |
| Expansion Opportunity | Aprovada | Identifica oportunidades de crescimento |

---

## Propriedades Não Utilizadas Inicialmente

| Propriedade | Decisão | Motivo |
| --- | --- | --- |
| Renewal Date | Não utilizar inicialmente | Depende de modelo de contrato recorrente |
| Support Level | Não utilizar inicialmente | Depende de estrutura de atendimento |
| Customer Feedback Score | Não utilizar inicialmente | Necessita processo de coleta |
| NPS Score | Não utilizar inicialmente | Necessita metodologia implantada |

---

# Status do Grupo

**Grupo 6 — Customer Success**

- **Status:** Modelagem arquitetural concluída
- **Decisão arquitetural principal:** A Company armazenará informações estratégicas de relacionamento e saúde do cliente. Atendimentos e solicitações operacionais serão controlados pelo objeto Ticket.

---

# Grupo 7 — Marketing

## Objetivo

O Grupo **Marketing** reúne informações relacionadas à origem, segmentação e relacionamento da empresa com ações de marketing.

As propriedades deste grupo têm como objetivo permitir uma comunicação mais personalizada, análise de campanhas e criação de estratégias de relacionamento.

Estas informações devem apoiar:

* segmentação de campanhas;
* análise de aquisição;
* personalização de comunicação;
* nutrição de leads;
* análise de desempenho de marketing.

Informações técnicas capturadas automaticamente pelo HubSpot devem utilizar propriedades nativas da plataforma.

Propriedades customizadas devem existir somente quando adicionarem uma visão estratégica específica do negócio.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Original Source | Global | Sim | HubSpot |
| Latest Source | Global | Sim | HubSpot |
| First Conversion | Global | Sim | HubSpot |
| Campaign | Global | Sim | HubSpot |
| Marketing Segment | Customizada | Sim | Customizada |
| Persona | Customizada | Sim | Customizada |
| Content Interest | Customizada | Sim | Customizada |
| Communication Preference | Customizada | Sim | Customizada |
| Marketing Qualified Status | Customizada | Não inicialmente | Customizada |
| Newsletter Subscription | Customizada | Não inicialmente | Customizada |
| Campaign History | Customizada | Não utilizar | Customizada |
| Engagement Score | Customizada | Não inicialmente | Customizada |

---

## Decisões Arquiteturais

### DA-030 — Priorizar propriedades nativas de Marketing Hub

Informações capturadas automaticamente pelo HubSpot devem utilizar propriedades padrão da plataforma.

Não serão criadas propriedades duplicadas para substituir funcionalidades existentes.

---

### DA-031 — Separar dados técnicos e dados estratégicos

O CRM diferenciará:

- dados técnicos de origem e rastreamento;
- classificações estratégicas utilizadas pelo negócio.

Exemplo:

- **Original Source** representa rastreamento técnico.
- **Marketing Segment** representa estratégia comercial.

---

### DA-032 — Dados de comunicação pertencem ao nível correto

Preferências de comunicação devem ser avaliadas conforme o objeto correto.

Quando a informação depender de uma pessoa específica, ela deverá pertencer ao objeto **Contact**.

Quando representar uma característica da empresa, poderá pertencer ao objeto **Company**.

---

### DA-033 — Evitar armazenar histórico em propriedades

Histórico de campanhas, interações e conversões deve ser obtido através dos recursos nativos do HubSpot.

Propriedades da **Company** devem representar o estado atual da empresa.

---

### DA-034 — Segmentação deve gerar ação

Uma propriedade de marketing somente será criada quando permitir:

* campanhas;
* personalização;
* automação;
* análise;
* tomada de decisão.

---

## Propriedades Aprovadas

| Propriedade | Decisão | Motivo |
| --- | --- | --- |
| Original Source | Aprovada | Rastreamento nativo de origem |
| Latest Source | Aprovada | Análise de último canal de interação |
| First Conversion | Aprovada | Controle da primeira conversão |
| Campaign | Aprovada | Associação com campanhas |
| Marketing Segment | Aprovada | Segmentação estratégica |
| Persona | Aprovada | Classificação de perfil |
| Content Interest | Aprovada | Personalização de comunicação |
| Communication Preference | Aprovada | Adequação do relacionamento |

---

## Propriedades Não Utilizadas Inicialmente

| Propriedade | Decisão | Motivo |
| --- | --- | --- |
| Marketing Qualified Status | Não utilizar inicialmente | Pode conflitar com Lifecycle Stage |
| Newsletter Subscription | Não utilizar inicialmente | Deve pertencer ao Contact |
| Campaign History | Não utilizar | Histórico deve ser gerenciado pelo HubSpot |
| Engagement Score | Não utilizar inicialmente | Deve ser calculado automaticamente |

---

# Status do Grupo

**Grupo 7 — Marketing**

- **Status:** Modelagem arquitetural concluída
- **Decisão arquitetural principal:** O CRM utilizará propriedades nativas do HubSpot para rastreamento automático e propriedades customizadas apenas para segmentações estratégicas do negócio.

















