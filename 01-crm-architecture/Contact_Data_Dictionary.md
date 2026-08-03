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
