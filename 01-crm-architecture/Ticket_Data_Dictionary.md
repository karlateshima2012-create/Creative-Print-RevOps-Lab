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

O grupo Ticket Activity reúne propriedades relacionadas ao histórico de movimentação, interação e desempenho dos chamados.

Essas propriedades permitem acompanhar:

* tempo de resolução;
* velocidade de atendimento;
* histórico de interações;
* qualidade do suporte.

A maioria dessas informações é gerada automaticamente pelo HubSpot e não deve ser preenchida manualmente.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Create Date | Data de criação | Sim | HubSpot |
| Close Date | Data de fechamento | Sim | HubSpot |
| Last Modified Date | Histórico | Não inicialmente | HubSpot |
| Last Activity Date | Histórico de interação | Sim | HubSpot |
| Next Activity Date | Próxima ação | Sim | HubSpot |
| Last Customer Reply Date | Resposta do cliente | Sim | HubSpot |
| First Agent Email Response Date | Primeiro atendimento | Sim | HubSpot |
| Time to First Agent Email Reply | SLA atendimento | Avaliar | HubSpot |
| Time to Close | SLA resolução | Avaliar | HubSpot |
| Ticket Reopen Date | Reabertura | Não inicialmente | HubSpot |
| Last Closed Date | Histórico | Não inicialmente | HubSpot |
| Owner Assigned Date | Responsabilidade | Não inicialmente | HubSpot |
| Number of Times Contacted | Métrica interação | Não inicialmente | HubSpot |
| Number of Sales Activities | Métrica atividade | Não inicialmente | HubSpot |
| Last CSAT Survey Rating | Satisfação cliente | Avaliar | HubSpot |
| Last CSAT Survey Date | Pesquisa satisfação | Avaliar | HubSpot |
| Last CSAT Survey Comment | Feedback cliente | Avaliar | HubSpot |
| Last NPS Survey Comment | Feedback cliente | Avaliar | HubSpot |
| Portal-wide Snooze | Controle interno | Não | HubSpot |

---

## Decisões Arquiteturais

### DA-061 — Métricas de atendimento devem ser derivadas

Tempo de resposta e resolução devem ser utilizados através das métricas nativas do HubSpot, evitando criação manual de campos.

---

### DA-062 — Customer Feedback será evoluído posteriormente

CSAT e NPS serão utilizados quando existir processo estruturado de Customer Success.

---

## Resultado

### Propriedades Aprovadas

| Propriedade | Origem | Tipo |
| --- | --- | --- |
| Create Date | HubSpot | Date |
| Close Date | HubSpot | Date |
| Last Activity Date | HubSpot | Date |
| Next Activity Date | HubSpot | Date |
| Last Customer Reply Date | HubSpot | Date |
| First Agent Email Response Date | HubSpot | Date |

---

### Avaliar Futuramente

| Propriedade | Motivo |
| --- | --- |
| Time to First Agent Email Reply | SLA |
| Time to Close | SLA |
| Last CSAT Survey Rating | Customer Success |
| Last CSAT Survey Date | Customer Success |
| Last CSAT Survey Comment | Feedback |
| Last NPS Survey Comment | Feedback |

---

### Não Utilizar Inicialmente

| Propriedade | Motivo |
| --- | --- |
| Last Modified Date | Campo técnico de controle |
| Ticket Reopen Date | Histórico estendido |
| Last Closed Date | Histórico estendido |
| Owner Assigned Date | Histórico estendido |
| Number of Times Contacted | Métrica derivada em relatórios |
| Number of Sales Activities | Métrica derivada em relatórios |
| Portal-wide Snooze | Controle interno do HubSpot |

---

# Status do Grupo

**Grupo 2 — Ticket Activity**

- **Status:** ✅ Finalizado
- **Propriedades aprovadas:**
  * Create Date
  * Close Date
  * Last Activity Date
  * Next Activity Date
  * Last Customer Reply Date
  * First Agent Email Response Date
- **Decisão arquitetural principal:** O grupo utilizará as propriedades de data de atendimento do HubSpot para controle de ciclo de vida e tempo de resposta.

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
