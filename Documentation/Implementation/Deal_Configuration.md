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

## 5. Validação após Configuração

Checklist de validação técnica:
- [ ] Pipeline criado corretamente (`Sales Pipeline`).
- [ ] Nome das etapas revisado.
- [ ] Probabilidades configuradas.
- [ ] Closed Won funcionando (100%).
- [ ] Closed Lost funcionando (0%).
- [ ] Ordem das etapas validada.
- [ ] Teste com Deal fictício realizado.

---

## 6. Evidências para Portfólio

Diretório de evidências:
`Documentation/evidence/hubspot/deal/`

Arquivos a salvar:
* `01_sales_pipeline.png`
* `02_deal_stages.png`
* `03_stage_probability.png`
* `04_test_deal_record.png`

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

# Status da Implementação

| Objeto | Arquitetura | Configuração |
| --- | --- | --- |
| Company | ✅ Concluído | ✅ Concluído |
| Contact | ✅ Concluído | ✅ Concluído |
| Deal | ✅ Concluído | ⬜ Iniciando |
| Ticket | ✅ Concluído | ⬜ Pendente |
