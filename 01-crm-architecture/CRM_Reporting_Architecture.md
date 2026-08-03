# CRM Reporting Architecture

## Objetivo

Este documento define a arquitetura de relatórios e indicadores que serão utilizados para acompanhar o desempenho do CRM.

O objetivo é estabelecer:

* quais métricas devem ser acompanhadas;
* quais objetos são fonte dos dados;
* quais decisões os indicadores devem apoiar;
* como medir eficiência comercial e relacionamento com clientes.

Os dashboards serão configurados somente após validação da estrutura de dados e processos.

---

## 1. Princípios de Reporting

### Métricas Devem Apoiar Decisões

Relatórios não devem existir apenas para visualização.

Cada indicador deve responder:
* Qual decisão ele suporta?
* Quem utiliza essa informação?
* Qual ação pode ser tomada?

---

### Dados Devem Possuir uma Única Fonte

**Exemplo — Receita comercial:**
* **Fonte correta:** ✅ Deal
* **Não utilizar:** ❌ Company / ❌ Contact

---

### Evitar Métricas sem Ação

Não criar dashboards apenas com:
* quantidade de registros;
* campos preenchidos;
* informações sem impacto operacional.

---

## 2. Reporting Architecture por Área

### Sales Reporting

* **Objeto principal:** Deal
* **Objetivo:** Acompanhar desempenho comercial e previsibilidade de receita.

#### KPI 1 — Pipeline Value
* **Pergunta:** Qual o valor total das oportunidades abertas?
* **Fonte:** Deal Amount
* **Visualização:** Pipeline Report

#### KPI 2 — Deal Conversion Rate
* **Pergunta:** Qual percentual das oportunidades vira venda?
* **Fonte:** Deal Stage
* **Métrica:** Closed Won / Total Deals

#### KPI 3 — Sales Cycle Length
* **Pergunta:** Quanto tempo uma oportunidade leva para fechar?
* **Fonte:** Deal Create Date + Close Date

#### KPI 4 — Revenue Won
* **Pergunta:** Quanto foi vendido?
* **Fonte:** Deal Amount
* **Filtro:** Closed Won

---

### Customer Success Reporting

* **Objetos principais:** Company, Ticket
* **Objetivo:** Acompanhar relacionamento após venda.

#### KPI 5 — Customer Health
* **Pergunta:** Qual a saúde da carteira?
* **Fonte:** Company (`Customer Health`)

#### KPI 6 — Ticket Resolution Time
* **Pergunta:** Quanto tempo leva para resolver chamados?
* **Fonte:** Ticket
* **Métrica:** Create Date → Close Date

#### KPI 7 — Ticket Volume
* **Pergunta:** Qual volume de solicitações?
* **Fonte:** Ticket

---

### Marketing Reporting

* **Objetos principais:** Contact, Company
* **Objetivo:** Entender origem e qualidade dos leads.

#### KPI 8 — Lead Source Performance
* **Pergunta:** Quais canais geram oportunidades?
* **Fonte:** Contact Original Traffic Source
* **Relacionamento:** Contact → Deal

---

## 3. Dashboard Architecture

### Dashboard 1 — Executive Overview
* **Usuário:** Gestão
* **Objetivo:** Visão geral do negócio.

| KPI | Fonte |
| --- | --- |
| Revenue Won | Deal |
| Open Pipeline | Deal |
| Conversion Rate | Deal |
| Active Customers | Company |
| Open Tickets | Ticket |

---

### Dashboard 2 — Sales Performance
* **Usuário:** Comercial

| KPI | Fonte |
| --- | --- |
| Pipeline Value | Deal |
| Deals by Stage | Deal |
| Closed Won | Deal |
| Sales Cycle | Deal |
| Lost Deals | Deal |

---

### Dashboard 3 — Customer Success
* **Usuário:** Atendimento

| KPI | Fonte |
| --- | --- |
| Open Tickets | Ticket |
| Resolution Time | Ticket |
| Customer Health | Company |
| CSAT/NPS | Ticket |

---

## 4. Reporting Roadmap

### Fase 1 — Core CRM Metrics
* **Prioridade:** Alta
* **Criar:** Pipeline, Receita, Conversão, Tickets.

---

### Fase 2 — Customer Success Metrics
* **Prioridade:** Média
* **Criar:** Health Score, SLA, Satisfação.

---

### Fase 3 — Revenue Operations Analytics
* **Prioridade:** Futura
* **Criar:** CAC, LTV, Expansão, Churn.

---

## Decisões Arquiteturais

### DA-073 — Relatórios devem utilizar fonte oficial do dado

Cada métrica deve possuir um objeto responsável pela informação.

---

### DA-074 — Dashboards serão criados após validação do CRM

Relatórios dependem da qualidade das propriedades, associações e processos.

---

### DA-075 — Métricas avançadas serão adicionadas conforme maturidade

Indicadores como LTV, CAC e Churn serão implementados quando houver volume suficiente de dados.

---

# Status da Entrega

| Documento | Status |
| --- | --- |
| CRM Strategy | ✅ Concluído |
| Data Governance | ✅ Concluído |
| Company Data Dictionary | ✅ Concluído |
| Contact Data Dictionary | ✅ Concluído |
| Deal Data Dictionary | ✅ Concluído |
| Ticket Data Dictionary | ✅ Concluído |
| CRM Object Model | ✅ Concluído |
| CRM Associations Model | ✅ Concluído |
| CRM Automation Architecture | ✅ Concluído |
| CRM Reporting Architecture | ✅ Concluído |
