# Deal Data Dictionary

## Objetivo

Este documento define todas as propriedades utilizadas pelo objeto **Deal (Negócio / Oportunidade Comercial)** no CRM da Creative Print.

Cada propriedade possui uma finalidade específica e foi definida para atender aos processos comerciais, de vendas, previsão de receita (forecasting) e Revenue Operations.

Nenhuma propriedade deverá ser criada diretamente no HubSpot sem estar previamente documentada neste Data Dictionary.

---

# Grupo 1 — Deal Information

## Objetivo

O grupo Deal Information reúne informações principais relacionadas às oportunidades comerciais registradas no CRM.

Essas propriedades representam o ciclo de venda, identificação da oportunidade e relacionamento com empresas e contatos.

Este grupo deve armazenar informações sobre a oportunidade comercial, não informações permanentes da empresa ou da pessoa.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Deal Name | Identificação | Sim | HubSpot |
| Deal Owner | Responsabilidade comercial | Sim | HubSpot |
| Pipeline | Processo comercial | Sim | HubSpot |
| Deal Stage | Processo comercial | Sim | HubSpot |
| Amount | Receita | Sim | HubSpot |
| Close Date | Previsão comercial | Sim | HubSpot |
| Create Date | Histórico | Não | HubSpot |
| Deal Type | Classificação | Avaliar | HubSpot |
| Description | Informações adicionais | Não inicialmente | HubSpot |
| Priority | Classificação comercial | Avaliar | Customizada |
| Loss Reason | Análise comercial | Avaliar | Customizada |
| Lead Source | Origem oportunidade | Avaliar | Customizada |

---

## Decisões Arquiteturais

### DA-036 — Pipeline e Deal Stage são configurações comerciais

Pipeline e Deal Stage não serão tratados como propriedades customizadas.

Eles representam a estrutura do processo comercial e devem ser configurados no objeto Deal.

---

### DA-037 — Deal representa transações comerciais

Informações de valor, fechamento e responsabilidade pertencem ao Deal.

Dados permanentes da organização permanecem na Company.

---

## Resultado

### Propriedades Aprovadas

| Propriedade | Origem | Tipo |
| --- | --- | --- |
| Deal Name | HubSpot | Single-line text |
| Deal Owner | HubSpot | HubSpot user |
| Close Date | HubSpot | Date picker |
| Deal Description | HubSpot | Multi-line text |

---

### Avaliar Futuramente

| Propriedade | Motivo |
| --- | --- |
| Deal Type | Depende da estratégia comercial |
| Priority | Necessita critério objetivo |

---

### Não Utilizar Inicialmente

| Propriedade | Motivo |
| --- | --- |
| Loss Reason | Processo de análise de perdas inexistente |
| Lead Source | Origem pertence ao relacionamento, não à oportunidade |

---

# Status do Grupo

**Grupo 1 — Deal Information**

- **Status:** ✅ Finalizado
- **Propriedades aprovadas:**
  * Deal Name
  * Deal Owner
  * Close Date
  * Deal Description
- **Decisão arquitetural principal:** O grupo utilizará propriedades nativas do HubSpot para identificação da oportunidade, atribuição de responsável, previsão de fechamento e descrição complementar.

---

# Status de Implementação dos Grupos do Deal

| Grupo | Status |
| --- | --- |
| Deal Information | ✅ Finalizado |
| Deal Revenue | ✅ Finalizado |
| Deal Activity | ⬜ Pendente |
| Analytics History | ⬜ Pendente |
| Outros grupos técnicos | ⬜ Pendente |

---

# Grupo 2 — Deal Revenue

## Objetivo

O grupo Deal Revenue reúne informações relacionadas ao valor financeiro das oportunidades comerciais registradas no CRM.

Essas propriedades têm como objetivo apoiar:

* previsão de receita;
* análise comercial;
* acompanhamento de contratos;
* relatórios financeiros;
* métricas de crescimento.

Este grupo deve armazenar somente informações financeiras relacionadas à oportunidade comercial. Dados financeiros da empresa ou cliente não pertencem ao objeto Deal.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Amount | Valor da oportunidade | Sim | HubSpot |
| Amount in company currency | Conversão financeira | Não inicialmente | HubSpot |
| Annual Contract Value | Receita anual | Não inicialmente | HubSpot |
| Annual Recurring Revenue | Receita recorrente anual | Avaliar | HubSpot |
| Monthly Recurring Revenue | Receita recorrente mensal | Avaliar | HubSpot |
| Total Contract Value | Valor total do contrato | Avaliar | HubSpot |
| Exchange Rate | Conversão monetária | Não inicialmente | HubSpot |

---

## Decisões Arquiteturais

### DA-038 — Receita pertence ao Deal

Valores financeiros devem permanecer no objeto Deal e nunca serem armazenados em Company ou Contact.

---

### DA-039 — Métricas SaaS somente quando houver processo definido

Indicadores como MRR, ARR e TCV serão utilizados somente quando a operação recorrente estiver estruturada.

---

### DA-040 — Campos calculados não devem ser gerenciados manualmente

Conversões monetárias e cálculos automáticos devem permanecer sob responsabilidade do HubSpot.

---

## Resultado

### Propriedades Aprovadas

| Propriedade | Origem | Tipo |
| --- | --- | --- |
| Amount | HubSpot | Number |

---

### Avaliar Futuramente

| Propriedade | Motivo |
| --- | --- |
| Annual Contract Value | Depende de contratos anuais |
| Annual Recurring Revenue | Depende de modelo SaaS estruturado |
| Monthly Recurring Revenue | Depende de receita recorrente ativa |
| Total Contract Value | Depende de contratos formais |

---

### Não Utilizar Inicialmente

| Propriedade | Motivo |
| --- | --- |
| Amount in company currency | Campo técnico de conversão |
| Exchange Rate | Campo técnico de moeda |

---

# Status do Grupo

**Grupo 2 — Deal Revenue**

- **Status:** ✅ Finalizado
- **Propriedades aprovadas:**
  * Amount
- **Decisão arquitetural principal:** O grupo utilizará a propriedade nativa Amount para controle financeiro da oportunidade. Métricas recorrentes SaaS (ARR/MRR) serão avaliadas futuramente com a maturidade da operação.
