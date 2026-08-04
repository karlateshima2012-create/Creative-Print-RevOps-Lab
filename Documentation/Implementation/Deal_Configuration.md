# Deal Object Configuration

## Objetivo

Configurar o objeto Deal no HubSpot conforme a arquitetura CRM aprovada.

O objetivo é transformar o modelo comercial documentado em uma estrutura funcional para acompanhamento de oportunidades, receita e previsão comercial.

A configuração inclui:
* pipeline comercial;
* etapas de venda;
* propriedades aprovadas;
* governança do processo comercial.

---

## 1. Configuração do Pipeline

* **Pipeline Name:** Sales Pipeline
* **Estratégia:** Single Sales Pipeline

**Motivo:**
O laboratório utilizará inicialmente um único pipeline para centralizar:
* produtos personalizados;
* soluções digitais;
* SaaS.

A separação em múltiplos pipelines será considerada apenas quando houver processos comerciais diferentes.

---

## 2. Deal Stages Configuration

Criar/editar as etapas:

| Ordem | Stage | Probability | Objetivo |
| --- | --- | ---: | --- |
| 1 | New Opportunity | 10% | Nova oportunidade identificada |
| 2 | Qualified Opportunity | 30% | Necessidade validada |
| 3 | Proposal Sent | 50% | Proposta enviada |
| 4 | Negotiation | 80% | Ajustes finais |
| 5 | Closed Won | 100% | Venda concluída |
| 6 | Closed Lost | 0% | Venda perdida |

---

## 3. Ajuste do Pipeline Existente

O HubSpot possui atualmente:

| Stage Atual no HubSpot | Ação Recomendada |
| --- | --- |
| Appointment Scheduled | Remover/Substituir |
| Qualified To Buy | Substituir por Qualified Opportunity |
| Presentation Scheduled | Remover/Substituir |
| Decision Maker Bought-In | Remover/Substituir |
| Contract Sent | Substituir por Negotiation |
| Closed Won | Manter |
| Closed Lost | Manter |

---

## 4. Configuração das Probabilidades

Configurar as probabilidades por estágio:

| Stage | Probability |
| --- | ---: |
| New Opportunity | 10% |
| Qualified Opportunity | 30% |
| Proposal Sent | 50% |
| Negotiation | 80% |
| Closed Won | 100% |
| Closed Lost | 0% |

---

## 5. Deal Properties Configuration — Resultado da Validação

### Propriedades Aprovadas

| Propriedade | Grupo HubSpot | Ação |
| --- | --- | --- |
| Deal Name | Deal Information | ✅ Utilizar |
| Deal Owner | Deal Information | ✅ Utilizar |
| Close Date | Deal Information | ✅ Utilizar |
| Deal Type | Deal Information | ✅ Utilizar |
| Deal Description | Deal Information | ✅ Utilizar |
| Priority | Deal Information | ✅ Utilizar |
| Amount | Deal Revenue | ✅ Utilizar |
| Last Activity Date | Deal Activity | ✅ Utilizar |
| Next Activity Date | Deal Activity | ✅ Utilizar |
| Last Contacted | Deal Activity | ✅ Utilizar |
| Number of Sales Activities | Deal Activity | ✅ Utilizar |

---

### Ajuste no Data Dictionary

* **Substituir:** `Number of Activities`
* **Por:** `Number of Sales Activities`
* **Motivo:** O HubSpot disponibiliza a propriedade nativa `Number of Sales Activities`, que representa o volume de atividades comerciais associadas ao Deal. Não será criada uma propriedade customizada equivalente.

---

### Propriedades Não Utilizadas Inicialmente

| Grupo | Decisão |
| --- | --- |
| Analytics History | Não utilizar inicialmente |
| HubSpot Metrics | Não utilizar inicialmente |
| Predictive Deal Score Feature Properties | Não utilizar |
| Calculated Deal Information | Não utilizar |
| Multi Account Management | Não utilizar |
| Deal Revenue recorrente (ARR/MRR/ACV) | Reservado para evolução SaaS |

---

## 6. Deal Views Configuration

### Views Personalizadas a Criar

| View | Tipo | Filtros / Critérios | Objetivo |
| --- | --- | --- | --- |
| Open Deals | Custom | Deal Stage != Closed Won / Closed Lost | Acompanhar negócios em andamento |
| Closed Won Deals | Custom | Deal Stage = Closed Won | Acompanhar negócios ganhos |
| Closed Lost Deals | Custom | Deal Stage = Closed Lost | Acompanhar negócios perdidos |
| Stale Deals | Custom | Open Deals + Last Activity Date > 14 dias | Identificar negócios sem movimentação |

### Deal Views Created

| View | Purpose |
| --- | --- |
| Open Deals | Active sales opportunities |
| Closed Won Deals | Completed successful sales |

---

## 7. Validação após Configuração

Checklist de validação técnica:
- [x] Pipeline criado corretamente (`Sales Pipeline`).
- [x] Nome das etapas revisado.
- [x] Probabilidades configuradas.
- [x] Core Properties validadas no HubSpot.
- [x] Closed Won funcionando (100%).
- [x] Closed Lost funcionando (0%).
- [x] Ordem das etapas validada.
- [x] Deal Views personalizadas mapeadas (`Open`, `Closed Won`, `Closed Lost`, `Stale`).
- [ ] Teste com Deal fictício realizado.

---

## 8. Evidências para Portfólio

Diretório de evidências:
`Documentation/evidence/hubspot/deal/`

Arquivos a salvar:
* `01_sales_pipeline.png`
* `02_deal_stages.png`
* `03_stage_probability.png`
* `04_deal_views_setup.png`
* `05_test_deal_record.png`

---

## Decisões Arquiteturais

### DA-080 — Pipeline único para fase inicial

O CRM utilizará um pipeline comercial único até que exista necessidade real de segmentação.

---

### DA-081 — Stages representam maturidade da oportunidade

As etapas foram definidas pelo avanço comercial e não pelo tipo de produto.

---

### DA-082 — Configuração segue documentação aprovada

Nenhuma alteração de pipeline deve ocorrer sem atualização do Data Dictionary e Implementation Plan.

---

### DA-083 — Views operacionais focam em ação comercial

Visualizações personalizadas de Deal devem priorizar a identificação rápida de oportunidades abertas, fechadas e estagnadas (`Stale Deals`).

---

# Status Deal Object Configuration

| Item | Details / Views | Status |
| --- | --- | --- |
| Pipeline Sales Pipeline | Single Sales Pipeline | ✅ Completed |
| Deal Stages | 6 Stages | ✅ Completed |
| Probabilities | Configured per stage | ✅ Completed |
| Core Properties Validation | Native Properties | ✅ Completed |
| Custom Properties Creation | Custom Properties | ⬜ Não necessária (v1) |
| All Deals View | Native View | ✅ Completed |
| My Deals View | Native View | ✅ Completed |
| Open Deals View | Custom View | ✅ Completed |
| Closed Won Deals View | Custom View | ✅ Completed |
| Closed Lost Deals View | Custom View | ✅ Completed |
| Stale Deals View | Custom View | ⏳ Fase 2 |
| Deal Automation | Workflows | ⬜ Futuro |

---

# Status da Implementação Global

| Objeto | Arquitetura | Configuração |
| --- | --- | --- |
| Company | ✅ Concluído | ✅ Completed |
| Contact | ✅ Concluído | ✅ Completed |
| Deal | ✅ Concluído | ✅ Completed (v1) |
| Ticket | ✅ Concluído | ⬜ Pending |
