# Contact Data Dictionary

## Objetivo

Este documento define todas as propriedades utilizadas pelo objeto **Contact (Contato)** no CRM da Creative Print.

Cada propriedade possui uma finalidade específica e foi definida para atender aos processos comerciais, de marketing, atendimento e Revenue Operations.

Nenhuma propriedade deverá ser criada diretamente no HubSpot sem estar previamente documentada neste Data Dictionary.

---

# Grupo 1 — Contact Information

## Objetivo

O grupo Contact Information reúne as informações de identificação, contato e classificação do ciclo de vida das pessoas relacionadas às empresas cadastradas no CRM.

Essas propriedades têm como objetivo apoiar:

* identificação única do contato;
* comunicação comercial;
* acompanhamento do estágio do relacionamento (Lifecycle Stage);
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
| Lifecycle Stage | Classificação | Sim | HubSpot |

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
| Lifecycle Stage | HubSpot | Dropdown select |

> **Observação:**
>
> O relacionamento entre Contact e Company será realizado através das **Associações nativas do HubSpot (Associations)**.
>
> As associações não são propriedades e, portanto, não fazem parte do Data Dictionary.

---

# Status do Grupo

**Grupo 1 — Contact Information**

- **Status:** ✅ Finalizado
- **Propriedades aprovadas:**
  * First Name
  * Last Name
  * Email
  * Phone Number
  * Mobile Phone Number
  * Job Title
  * Lifecycle Stage
- **Decisão arquitetural principal:** As informações de contato e o estágio do ciclo de vida utilizarão exclusivamente propriedades nativas do HubSpot no grupo Contact Information.

---

# Grupo 2 — Sales Properties

## 1. Objetivo

O grupo Sales Properties reúne informações utilizadas para gestão comercial e acompanhamento da responsabilidade sobre contatos dentro do processo de vendas.

Essas propriedades têm como objetivo apoiar:

* organização da equipe comercial;
* distribuição de responsabilidades;
* acompanhamento de leads;
* gestão do processo comercial.

Este grupo não deve armazenar informações da empresa ou dados de negociação, pois essas informações pertencem aos objetos Company e Deal.

---

## 2. Levantamento das propriedades candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Contact Owner | Gestão comercial | Sim | HubSpot |
| Lead Status | Processo comercial | Sim | HubSpot |
| Sales Activity Date | Atividade comercial | Não inicialmente | HubSpot |
| HubSpot Team | Organização comercial | Não inicialmente | HubSpot |

---

## 3. Análise das propriedades

### Contact Owner

Quem é responsável pelo relacionamento com este contato?

Utilizado para:

* distribuição de contatos;
* acompanhamento comercial;
* gestão de carteira.

**Decisão:** ✅ Utilizar.

---

### Lead Status

Qual é a situação atual do contato no processo comercial?

Utilizado para:

* qualificação;
* acompanhamento de oportunidades;
* automações futuras.

**Decisão:** ✅ Utilizar.

---

### Sales Activity Date

Representa atividades registradas no CRM.

É uma informação operacional gerada pelo HubSpot.

**Decisão:** ❌ Não utilizar inicialmente.

---

### HubSpot Team

Depende da estrutura comercial da organização.

Como a Creative Print ainda não possui uma equipe comercial estruturada no CRM:

**Decisão:** ❌ Não utilizar inicialmente.

---

## 4. Decisões Arquiteturais

### DA-024 — Sales Properties representa gestão comercial

As propriedades deste grupo serão utilizadas para controlar responsabilidade e acompanhamento comercial dos contatos.

---

### DA-025 — Lifecycle Stage permanece no Contact Information

O Lifecycle Stage será tratado como uma classificação geral do relacionamento do contato e permanecerá no grupo nativo Contact Information.

---

### DA-026 — Dados comerciais transacionais pertencem ao Deal

Informações relacionadas a valores, negociações e receita deverão permanecer no objeto Deal.

---

## 5. Resultado

### Propriedades aprovadas

| Propriedade | Origem | Tipo |
| --- | --- | --- |
| Contact Owner | HubSpot | HubSpot user |
| Lead Status | HubSpot | Dropdown select |

---

### Não utilizar inicialmente

| Propriedade | Motivo |
| --- | --- |
| Sales Activity Date | Informação operacional automática |
| HubSpot Team | Estrutura comercial ainda não definida |

---

# Status do Grupo

**Grupo 2 — Sales Properties**

- **Status:** ✅ Finalizado
- **Propriedades aprovadas:**
  * Contact Owner
  * Lead Status
- **Decisão arquitetural principal:** O grupo utilizará propriedades nativas do HubSpot para atribuição de responsabilidade comercial e qualificação operacional de contatos.

---

# Status de Implementação dos Grupos do Contact

| Grupo | Status |
| --- | --- |
| Contact Information | ✅ Finalizado |
| Sales Properties | ✅ Finalizado |
| Social Media Information | ⬜ Pendente |
| Email Information | ⬜ Pendente |
| Marketing Information | ⬜ Pendente |
