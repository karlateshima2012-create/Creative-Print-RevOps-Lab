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

## Propriedade 01

| Campo          | Valor                                                                                          |
| -------------- | ---------------------------------------------------------------------------------------------- |
| Nome Exibido   | Company name                                                                                   |
| Nome Interno   | `name`                                                                                         |
| Tipo           | Single-line text                                                                               |
| Origem         | HubSpot (Padrão)                                                                               |
| Grupo          | Identificação                                                                                  |
| Obrigatório    | Sim                                                                                            |
| Valor Padrão   | Não                                                                                            |
| Origem do Dado | Comercial / Formulários / Importação                                                           |
| Responsável    | Comercial                                                                                      |
| Atualização    | Criação da Empresa                                                                             |
| Utilização     | Identificação principal da Empresa                                                             |
| Justificativa  | Identificador principal do objeto Company. Todas as Empresas deverão possuir um nome definido. |

---

## Propriedade 02

| Campo          | Valor                                                                            |
| -------------- | -------------------------------------------------------------------------------- |
| Nome Exibido   | Company domain name                                                              |
| Nome Interno   | `domain`                                                                         |
| Tipo           | Single-line text                                                                 |
| Origem         | HubSpot (Padrão)                                                                 |
| Grupo          | Identificação                                                                    |
| Obrigatório    | Não                                                                              |
| Valor Padrão   | Não                                                                              |
| Origem do Dado | Comercial                                                                        |
| Responsável    | Comercial                                                                        |
| Atualização    | Quando disponível                                                                |
| Utilização     | Deduplicação, integrações futuras e identificação da Empresa                     |
| Justificativa  | Utilizada como um dos identificadores da Empresa quando existir domínio próprio. |

---

## Propriedade 03

| Campo          | Valor                                                                      |
| -------------- | -------------------------------------------------------------------------- |
| Nome Exibido   | Record ID                                                                  |
| Nome Interno   | `hs_object_id`                                                             |
| Tipo           | Número (Sistema)                                                           |
| Origem         | HubSpot (Padrão)                                                           |
| Grupo          | Identificação                                                              |
| Obrigatório    | Sim (Automático)                                                           |
| Valor Padrão   | Gerado pelo HubSpot                                                        |
| Origem do Dado | Sistema                                                                    |
| Responsável    | HubSpot                                                                    |
| Atualização    | Automática                                                                 |
| Utilização     | Integrações, APIs e relacionamento entre sistemas                          |
| Justificativa  | Identificador único da Empresa dentro do HubSpot. Nunca deve ser alterado. |




