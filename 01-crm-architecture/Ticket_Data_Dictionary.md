# Ticket Data Dictionary

## Objetivo

Este documento define todas as propriedades utilizadas pelo objeto **Ticket (Atendimento / Suporte ao Cliente)** no CRM da Creative Print.

Cada propriedade possui uma finalidade específica e foi definida para atender aos processos de Customer Success, atendimento ao cliente, pós-venda e resolução de chamados.

Nenhuma propriedade deverá ser criada diretamente no HubSpot sem estar previamente documentada neste Data Dictionary.

---

# Grupo 1 — Ticket Information

## Objetivo

O grupo Ticket Information reúne informações principais relacionadas às solicitações de atendimento registradas no CRM.

Essas propriedades representam o contexto do chamado, classificação, prioridade e responsabilidade pelo atendimento.

Este grupo não deve armazenar informações comerciais ou financeiras, pois essas informações pertencem ao objeto Deal.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Ticket Name | Identificação | Sim | HubSpot |
| Ticket Owner | Responsável | Sim | HubSpot |
| Ticket Status | Processo atendimento | Sim | HubSpot |
| Pipeline | Processo atendimento | Sim | HubSpot |
| Ticket Priority | Classificação | Sim | HubSpot |
| Description | Contexto | Sim | HubSpot |
| Category | Classificação | Avaliar | HubSpot |
| Source | Origem atendimento | Avaliar | HubSpot |
| Create Date | Histórico | Não inicialmente | HubSpot |
| Close Date | Resolução | Avaliar | HubSpot |

---

## Decisões Arquiteturais

### DA-058 — Ticket representa atendimento, não venda

Informações de negociação e receita permanecem no Deal.

---

### DA-059 — Status controla evolução do atendimento

O progresso do chamado será controlado pelo Ticket Status e Pipeline, evitando propriedades duplicadas.

---

### DA-060 — Classificações devem existir somente quando gerarem análise

Category e Source serão adicionados ao processo quando houver volume suficiente para justificar segmentação.

---

## Resultado

### Propriedades Aprovadas

| Propriedade | Origem | Tipo |
| --- | --- | --- |
| Ticket Name | HubSpot | Single-line text |
| Ticket Owner | HubSpot | HubSpot user |
| Ticket Status | HubSpot | Dropdown select |
| Priority | HubSpot | Dropdown select |
| Ticket Description | HubSpot | Multi-line text |

---

### Avaliar Futuramente

| Propriedade | Motivo |
| --- | --- |
| Category | Depende do volume de atendimentos |
| Source | Depende da estratégia de canais |

---

### Não Utilizar Inicialmente

| Propriedade | Motivo |
| --- | --- |
| Create Date | Campo interno do registro |
| Close Date | Não existe e pode ser derivado do processo |

---

# Status do Grupo

**Grupo 1 — Ticket Information**

- **Status:** ✅ Finalizado
- **Propriedades aprovadas:**
  * Ticket Name
  * Ticket Owner
  * Ticket Status
  * Priority
  * Ticket Description
- **Decisão arquitetural principal:** O grupo utilizará propriedades nativas do HubSpot para identificação, atribuição de responsável, status, prioridade e descrição do atendimento.

---

# Status de Implementação dos Grupos do Ticket

| Grupo | Status |
| --- | --- |
| Ticket Information | ✅ Finalizado |
| Ticket Activity | ⬜ Pendente |
| Ticket Metrics | ⬜ Pendente |
