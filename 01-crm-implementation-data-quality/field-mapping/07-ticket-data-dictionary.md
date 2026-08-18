# Ticket Data Dictionary

## Objetivo

Este documento define todas as propriedades utilizadas pelo objeto **Ticket (Atendimento / Suporte ao Cliente)** no CRM da Creative Print.

Cada propriedade possui uma finalidade específica e foi definida para atender aos processos de Customer Success, atendimento ao cliente, pós-venda e resolução de chamados.

Nenhuma propriedade deverá ser criada diretamente no HubSpot sem estar previamente documentada neste Data Dictionary.

---

# Grupo 1 — Ticket Information

## Objetivo

O grupo Ticket Information reúne as propriedades responsáveis pela identificação, classificação e gerenciamento operacional dos tickets.

Essas propriedades permitem:
* identificar o ticket;
* definir responsáveis;
* classificar solicitações;
* organizar o atendimento;
* controlar o fluxo de Customer Success.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Ticket Name | Nativa | Sim | HubSpot |
| Ticket Owner | Nativa | Sim | HubSpot |
| Ticket Status | Nativa | Sim | HubSpot |
| Pipeline | Nativa | Sim | HubSpot |
| Priority | Nativa | Sim | HubSpot |
| Ticket Description | Nativa | Sim | HubSpot |
| Category | Nativa | Sim | HubSpot |
| Source | Nativa | Sim | HubSpot |

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

### DA-084 — Ticket Information utilizará propriedades nativas

O grupo utilizará exclusivamente propriedades nativas do HubSpot na versão inicial.

---

### DA-085 — Não criar propriedades duplicadas

Informações operacionais de identificação do ticket permanecerão nas propriedades padrão do HubSpot.

---

## Resultado

### Propriedades Aprovadas

| Propriedade | Origem | Tipo |
| --- | --- | --- |
| Ticket Name | HubSpot | Single-line text |
| Ticket Owner | HubSpot | HubSpot User |
| Ticket Status | HubSpot | Dropdown |
| Pipeline | HubSpot | Dropdown |
| Priority | HubSpot | Dropdown |
| Ticket Description | HubSpot | Multi-line text |
| Category | HubSpot | Dropdown |
| Source | HubSpot | Dropdown |

---

# Status do Grupo

**Grupo 1 — Ticket Information**

- **Status:** ✅ Finalizado
- **Propriedades aprovadas:**
  * Ticket Name
  * Ticket Owner
  * Ticket Status
  * Pipeline
  * Priority
  * Ticket Description
  * Category
  * Source
- **Decisão arquitetural principal:** O grupo utilizará 8 propriedades nativas do HubSpot para identificação, atribuição de responsável, status, pipeline, prioridade, descrição, categoria e origem do atendimento.

---

# Grupo 2 — Ticket Activity

## Objetivo

O grupo Ticket Activity reúne propriedades utilizadas para acompanhar a evolução operacional do ticket e medir indicadores de atendimento.

Essas propriedades apoiam:
* acompanhamento da execução;
* medição de SLA;
* produtividade;
* Customer Success.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Create Date | Nativa | Sim | HubSpot |
| Close Date | Nativa | Sim | HubSpot |
| Last Activity Date | Nativa | Sim | HubSpot |
| Last Contacted Date | Nativa | Sim | HubSpot |
| Next Activity Date | Nativa | Sim | HubSpot |
| Number of Sales Activities | Nativa | Sim | HubSpot |
| Time to Close | Nativa | Sim | HubSpot |
| Last CSAT Survey Rating | Nativa | Sim | HubSpot |
| Last CSAT Survey Date | Nativa | Sim | HubSpot |
| Last NPS Survey Comment | Nativa | Sim | HubSpot |

---

## Decisões Arquiteturais

### DA-061 — Métricas de atendimento devem ser derivadas

Tempo de resposta e resolução devem ser utilizados através das métricas nativas do HubSpot, evitando criação manual de campos.

---

### DA-062 — Customer Feedback será evoluído posteriormente

CSAT e NPS serão utilizados quando existir processo estruturado de Customer Success.

---

### DA-086 — Indicadores operacionais permanecerão nativos

Todos os indicadores de atividade e SLA utilizarão propriedades nativas do HubSpot.

---

### DA-087 — Customer Success utilizará métricas automáticas

Sempre que possível, métricas de CSAT, NPS e tempo de atendimento serão obtidas das propriedades automáticas da plataforma, evitando cálculos ou campos manuais.

---

## Resultado

### Propriedades Aprovadas

| Propriedade | Origem | Tipo |
| --- | --- | --- |
| Create Date | HubSpot | Date |
| Close Date | HubSpot | Date |
| Last Activity Date | HubSpot | Date |
| Last Contacted Date | HubSpot | Date |
| Next Activity Date | HubSpot | Date |
| Number of Sales Activities | HubSpot | Number |
| Time to Close | HubSpot | Calculation |
| Last CSAT Survey Rating | HubSpot | Rollup |
| Last CSAT Survey Date | HubSpot | Rollup |
| Last NPS Survey Comment | HubSpot | Rollup |

---

# Status do Grupo

**Grupo 2 — Ticket Activity**

- **Status:** ✅ Finalizado
- **Propriedades aprovadas:**
  * Create Date
  * Close Date
  * Last Activity Date
  * Last Contacted Date
  * Next Activity Date
  * Number of Sales Activities
  * Time to Close
  * Last CSAT Survey Rating
  * Last CSAT Survey Date
  * Last NPS Survey Comment
- **Decisão arquitetural principal:** O grupo utilizará 10 propriedades nativas do HubSpot para controle de datas, contagem de atividades, cálculo de SLA de fechamento e métricas de satisfação (CSAT/NPS).

---

# Grupo 3 — Ticket AI Enrichment

## Objetivo

O grupo Ticket AI Enrichment reúne propriedades geradas automaticamente por recursos de inteligência artificial do HubSpot para identificar sinais positivos e negativos durante interações de atendimento.

Essas propriedades têm como objetivo auxiliar análises de experiência do cliente, mas não substituem classificações operacionais ou processos definidos de Customer Success.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| CX Negative Signals | Análise de sentimento | Não inicialmente | HubSpot AI |
| CX Positive Signals | Análise de sentimento | Não inicialmente | HubSpot AI |

---

## Decisões Arquiteturais

### DA-063 — IA complementa processos existentes

Recursos de inteligência artificial devem apoiar decisões de Customer Success, mas não substituir dados estruturados de relacionamento.

---

### DA-064 — Dados gerados por IA entram somente quando houver uso operacional

Propriedades automáticas devem ser utilizadas apenas quando gerarem ações concretas dentro do processo.

---

## Resultado

### Propriedades Aprovadas

| Propriedade | Origem | Tipo |
| --- | --- | --- |
| Nenhuma | — | — |

---

### Avaliar Futuramente

| Propriedade | Motivo |
| --- | --- |
| CX Negative Signals | Pode apoiar prevenção de churn |
| CX Positive Signals | Pode apoiar análise de satisfação |

---

# Status do Grupo

**Grupo 3 — Ticket AI Enrichment**

- **Status:** ✅ Finalizado (sem propriedades aprovadas)
- **Propriedades aprovadas:** Nenhuma nesta versão
- **Decisão arquitetural principal:** Sinais de IA serão avaliados no futuro para prevenção de churn e análise de satisfação, sem operacionalização na v1.

---

# Grupo 4 — Ticket Stage Properties

## Objetivo

O grupo Ticket Stage Properties representa propriedades relacionadas às etapas do processo de atendimento no HubSpot.

Este grupo não possui propriedades disponíveis no ambiente atual e não será utilizado como parte do modelo de dados do CRM.

O controle de evolução dos chamados será realizado através da configuração do Pipeline e Ticket Status.

---

## Propriedades Candidatas

Nenhuma propriedade encontrada.

---

## Análise

Não existem propriedades configuráveis neste grupo.

A governança do processo de atendimento será realizada por:
* Pipeline de Tickets;
* Ticket Status;
* responsáveis pelo atendimento;
* métricas de atividade.

**Decisão:** ✅ Não criar propriedades neste grupo.

---

## Resultado

### Propriedades Aprovadas

| Propriedade | Origem | Tipo |
| --- | --- | --- |
| Nenhuma | — | — |

---

## Decisões Arquiteturais

### DA-065 — Etapas do atendimento serão controladas pelo Pipeline

O avanço dos tickets será definido pela configuração do processo, não pela criação de propriedades adicionais.

---

### DA-066 — Evitar propriedades sem função operacional

Grupos vazios ou técnicos não devem receber campos apenas para completar a estrutura do CRM.

---

# Status Final — Ticket Data Dictionary

| Grupo | Status |
| --- | --- |
| Ticket Information | ✅ Finalizado |
| Ticket Activity | ✅ Finalizado |
| Ticket AI Enrichment | ✅ Finalizado |
| Ticket Stage Properties | ✅ Finalizado |

---

# Propriedades Finais Aprovadas do Objeto Ticket

| Propriedade | Grupo |
| --- | --- |
| Ticket Name | Ticket Information |
| Ticket Owner | Ticket Information |
| Ticket Status | Ticket Information |
| Pipeline | Ticket Information |
| Priority | Ticket Information |
| Ticket Description | Ticket Information |
| Category | Ticket Information |
| Source | Ticket Information |
| Create Date | Ticket Activity |
| Close Date | Ticket Activity |
| Last Activity Date | Ticket Activity |
| Next Activity Date | Ticket Activity |
| Last Customer Reply Date | Ticket Activity |
| First Agent Email Response Date | Ticket Activity |
