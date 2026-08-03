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





