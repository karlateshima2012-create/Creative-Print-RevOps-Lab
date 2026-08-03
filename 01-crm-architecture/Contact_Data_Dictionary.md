# Contact Data Dictionary

## Objetivo

Este documento define todas as propriedades utilizadas pelo objeto **Contact (Contato)** no CRM da Creative Print.

Cada propriedade possui uma finalidade específica e foi definida para atender aos processos comerciais, de marketing, atendimento e Revenue Operations.

Nenhuma propriedade deverá ser criada diretamente no HubSpot sem estar previamente documentada neste Data Dictionary.

---

# Grupo 1 — Contact Information

## Objetivo

O grupo Contact Information reúne as informações de identificação e contato das pessoas relacionadas às empresas cadastradas no CRM.

Essas propriedades têm como objetivo apoiar:

* identificação única do contato;
* comunicação comercial;
* segmentação;
* automações;
* integrações.

Este grupo deve armazenar apenas informações pertencentes à pessoa, evitando duplicidade com o objeto Company.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| First Name | Identificação | Sim | HubSpot |
| Last Name | Identificação | Sim | HubSpot |
| Email | Contato | Sim | HubSpot |
| Phone Number | Contato | Sim | HubSpot |
| Mobile Phone Number | Contato | Sim | HubSpot |
| Job Title | Profissional | Sim | HubSpot |

---

## Decisões Arquiteturais

### DA-020 — Priorizar propriedades nativas do HubSpot

As informações de identificação e contato utilizarão prioritariamente propriedades nativas do HubSpot.

---

### DA-021 — Evitar duplicidade entre Contact e Company

Informações organizacionais permanecerão no objeto Company.

O objeto Contact armazenará apenas informações pertencentes às pessoas.

---

### DA-022 — Associação nativa entre Company e Contact

O relacionamento entre empresas e pessoas será realizado através das associações nativas do HubSpot, evitando replicação de informações.

---

### DA-023 — Propriedades customizadas somente com finalidade definida

Novas propriedades serão criadas apenas quando houver necessidade comprovada para automações, segmentações, integrações ou relatórios.

---

## Propriedades Aprovadas

| Propriedade | Origem | Tipo |
| --- | --- | --- |
| First Name | HubSpot | Single-line text |
| Last Name | HubSpot | Single-line text |
| Email | HubSpot | Single-line text |
| Phone Number | HubSpot | Phone number |
| Mobile Phone Number | HubSpot | Phone number |
| Job Title | HubSpot | Single-line text |

> **Observação:**
>
> O relacionamento entre Contact e Company será realizado através das **Associações nativas do HubSpot (Associations)**.
>
> As associações não são propriedades e, portanto, não fazem parte do Data Dictionary.

---

# Status do Grupo

**Grupo 1 — Contact Information**

- **Status:** Modelado
- **Propriedades aprovadas:**
  * First Name
  * Last Name
  * Email
  * Phone Number
  * Mobile Phone Number
  * Job Title
- **Decisão arquitetural principal:** As informações de contato utilizarão exclusivamente propriedades nativas do HubSpot, e o vínculo com a empresa será realizado via associações nativas (Associations).

---

# Grupo 2 — About this Contact

## Objetivo

O grupo About this Contact reúne informações relacionadas ao gerenciamento, classificação e acompanhamento do relacionamento com pessoas cadastradas no CRM.

Essas propriedades têm como objetivo apoiar:

* organização da base de contatos;
* acompanhamento do estágio do relacionamento;
* gestão comercial;
* automações futuras;
* segmentações.

Este grupo não deve armazenar informações da empresa, oportunidades comerciais ou histórico de atendimento, pois essas informações pertencem aos objetos Company, Deal e Ticket.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Lifecycle Stage | Classificação do relacionamento | Sim | HubSpot |
| Contact Owner | Gestão comercial | Sim | HubSpot |
| Lead Status | Processo comercial | Sim | HubSpot |
| Create Date | Histórico | Não | HubSpot |
| Last Contacted | Atividade | Não | HubSpot |
| Recent Conversion Date | Marketing | Não inicialmente | HubSpot |
| Contact Priority | Classificação interna | Não inicialmente | Customizada |

---

## Decisões Arquiteturais

### DA-024 — Lifecycle Stage como indicador principal do relacionamento

O Lifecycle Stage será utilizado como referência principal para representar a evolução do contato dentro do funil de relacionamento.

---

### DA-025 — Lead Status complementa o processo comercial

O Lead Status será utilizado para representar a situação operacional do contato durante o processo de qualificação comercial.

---

### DA-026 — Responsabilidade de dados comerciais no objeto correto

Informações relacionadas à empresa permanecerão no objeto Company.

Informações relacionadas a oportunidades comerciais permanecerão no objeto Deal.

O objeto Contact representa exclusivamente pessoas e seu relacionamento individual.

---

## Propriedades Aprovadas

| Propriedade | Origem | Tipo |
| --- | --- | --- |
| Lifecycle Stage | HubSpot | Dropdown select |
| Contact Owner | HubSpot | HubSpot user |
| Lead Status | HubSpot | Dropdown select |

---

## Propriedades Não Utilizadas Inicialmente

| Propriedade | Motivo |
| --- | --- |
| Create Date | Informação automática do sistema |
| Last Contacted | Métrica operacional automática |
| Recent Conversion Date | Sem processo de marketing definido |
| Contact Priority | Sem critério objetivo de classificação |

---

# Status do Grupo

**Grupo 2 — About this Contact**

- **Status:** Modelado
- **Propriedades aprovadas:**
  * Lifecycle Stage
  * Contact Owner
  * Lead Status
- **Decisão arquitetural principal:** O grupo utilizará exclusivamente propriedades nativas do HubSpot para controle de estágio de relacionamento, qualificação comercial e atribuição de proprietário da conta.
