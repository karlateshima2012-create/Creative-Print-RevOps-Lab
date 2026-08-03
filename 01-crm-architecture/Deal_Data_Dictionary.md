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

---

# Grupo 3 — Deal Activity

## Objetivo

O grupo Deal Activity reúne informações relacionadas ao histórico de interações, engajamento e acompanhamento de tarefas operacionais associadas às oportunidades comerciais.

Essas propriedades têm como objetivo apoiar:

* visibilidade sobre o andamento do negócio;
* acompanhamento da produtividade comercial;
* prevenção de estagnação de oportunidades no funil.

Informações operacionais geradas automaticamente pelo sistema não devem ser atualizadas manualmente pelos usuários.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem | Grupo |
| --- | --- | --- | --- | --- |
| Last Activity Date | Histórico de interação | Sim | HubSpot | Deal Activity |
| Next Activity Date | Próxima ação comercial | Sim | HubSpot | Deal Activity |
| Number of Sales Activities | Volume de atividades | Não inicialmente | HubSpot | Deal Activity |
| Last Contacted | Último contato realizado | Avaliar | HubSpot | Deal Activity |
| Next Step | Próxima etapa comercial | Não existe | — | — |
| Notes Last Updated | Histórico | Não existe | — | — |
| Created By User ID | Auditoria | Não existe | — | — |
| Updated By User ID | Auditoria | Não existe | — | — |

---

## Decisões Arquiteturais

### DA-041 — Atividades não substituem dados comerciais

Informações de interação representam o histórico operacional da venda e não devem substituir propriedades estruturadas do Deal.

---

### DA-042 — Métricas automáticas não devem ser recriadas

Indicadores gerados pelo HubSpot devem ser utilizados diretamente, evitando criação de campos duplicados.

---

## Resultado

### Propriedades Aprovadas

| Propriedade | Origem | Tipo |
| --- | --- | --- |
| Last Activity Date | HubSpot | Date |
| Next Activity Date | HubSpot | Date |

---

### Avaliar Futuramente

| Propriedade | Motivo |
| --- | --- |
| Number of Sales Activities | Pode ser útil para métricas comerciais |

---

### Não Utilizar Inicialmente

| Propriedade | Motivo |
| --- | --- |
| Last Contacted | Duplicidade conceitual com Last Activity Date |
| Next Step | Não existe no ambiente |
| Notes Last Updated | Não existe no ambiente |
| Created By User ID | Auditoria técnica |
| Updated By User ID | Auditoria técnica |

---

# Status do Grupo

**Grupo 3 — Deal Activity**

- **Status:** ✅ Finalizado
- **Propriedades aprovadas:**
  * Last Activity Date
  * Next Activity Date
- **Decisão arquitetural principal:** O grupo utilizará as propriedades nativas de controle de atividades automáticas do HubSpot para monitorar a frequência de contato e próximos passos comerciais.

---

# Status de Implementação dos Grupos do Deal

| Grupo | Status |
| --- | --- |
| Deal Information | ✅ Finalizado |
| Deal Revenue | ✅ Finalizado |
| Deal Activity | ✅ Finalizado |
| Analytics History | ⏳ Em andamento |
| Professional Services Information | ⬜ Pendente |
| HubSpot Metrics | ⬜ Pendente |
| Outros grupos técnicos | ⬜ Pendente |

---

# Grupo 4 — Analytics History

## Objetivo

O grupo Analytics History reúne informações históricas de origem de tráfego associadas aos registros de Deal.

Essas propriedades são geradas automaticamente pelo HubSpot para rastrear a origem dos registros e apoiar análises de aquisição.

Este grupo não deve ser utilizado para armazenar informações comerciais inseridas manualmente pela equipe.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Latest Traffic Source | Origem de aquisição | Não inicialmente | HubSpot |
| Latest Traffic Source Data 1 | Detalhamento de origem | Não inicialmente | HubSpot |
| Latest Traffic Source Data 2 | Detalhamento de origem | Não inicialmente | HubSpot |
| Latest Traffic Source Timestamp | Data de aquisição | Não inicialmente | HubSpot |
| Original Traffic Source | Origem inicial | Não inicialmente | HubSpot |
| Original Traffic Source Drill-Down 1 | Detalhamento de origem | Não inicialmente | HubSpot |
| Original Traffic Source Drill-Down 2 | Detalhamento de origem | Não inicialmente | HubSpot |

---

## Decisões Arquiteturais

### DA-043 — Dados de aquisição pertencem ao contexto de Marketing

Informações de origem de tráfego devem permanecer associadas ao processo de aquisição de contatos, evitando replicação desnecessária no objeto Deal.

---

### DA-044 — Propriedades técnicas do HubSpot não devem ser operacionalizadas

Campos criados automaticamente pela plataforma serão utilizados apenas quando houver necessidade analítica específica.

---

## Resultado

### Propriedades Aprovadas

| Propriedade | Origem | Tipo |
| --- | --- | --- |
| Nenhuma | — | — |

---

### Não Utilizar Inicialmente

| Propriedade | Motivo |
| --- | --- |
| Latest Traffic Source | Informação de marketing, não comercial |
| Latest Traffic Source Data 1 | Campo técnico automático |
| Latest Traffic Source Data 2 | Campo técnico automático |
| Latest Traffic Source Timestamp | Campo técnico automático |
| Original Traffic Source | Evitar duplicidade com Contact |
| Original Traffic Source Drill-Down 1 | Campo técnico automático |
| Original Traffic Source Drill-Down 2 | Campo técnico automático |

---

# Status do Grupo

**Grupo 4 — Analytics History**

- **Status:** ✅ Finalizado (sem propriedades aprovadas)
- **Propriedades aprovadas:** Nenhuma nesta versão
- **Decisão arquitetural principal:** Informações de origem de tráfego pertencem ao contexto de Marketing e aquisição de contatos, não sendo operacionalizadas no objeto Deal nesta fase.

------

# Grupo 5 — Professional Services Information

## Objetivo

O grupo Professional Services Information reúne informações relacionadas à execução de projetos ou serviços associados às oportunidades comerciais.

Essas propriedades podem apoiar processos que envolvem escopo, prazo, complexidade e entrega de serviços.

No cenário atual da Creative Print, esse grupo não representa o processo comercial principal, pois a maior parte das vendas envolve produtos personalizados e soluções digitais padronizadas.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Complexidade do projeto | Classificação do projeto | Não inicialmente | Customizada |
| Prazo estimado | Planejamento de entrega | Não inicialmente | Customizada |
| Serviços inclusos | Escopo comercial | Não inicialmente | Customizada |
| Tamanho do projeto | Classificação do projeto | Não inicialmente | Customizada |

---

## Decisões Arquiteturais

### DA-045 — Dados de projeto não devem contaminar o processo comercial

Informações de execução devem ser adicionadas somente quando existir um processo formal de serviços/projetos.

---

### DA-046 — Propriedades devem refletir processos existentes

Campos sem utilização operacional definida não devem ser criados ou utilizados apenas para completar o CRM.

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
| Serviços inclusos | Pode ser útil para soluções digitais e projetos futuros |

---

### Não Utilizar Inicialmente

| Propriedade | Motivo |
| --- | --- |
| Complexidade do projeto | Sem necessidade no processo atual |
| Prazo estimado | Não existe processo formal de projetos |
| Tamanho do projeto | Pode duplicar análise pelo valor do Deal |

---

# Status do Grupo

**Grupo 5 — Professional Services Information**

- **Status:** ✅ Finalizado (sem propriedades aprovadas)
- **Propriedades aprovadas:** Nenhuma nesta versão
- **Decisão arquitetural principal:** Propriedades de execução de serviços não serão criadas na v1 para manter o CRM enxuto e alinhado aos processos reais da empresa.

---

# Status de Implementação dos Grupos do Deal

| Grupo | Status |
| --- | --- |
| Deal Information | ✅ Finalizado |
| Deal Revenue | ✅ Finalizado |
| Deal Activity | ✅ Finalizado |
| Analytics History | ✅ Finalizado (sem propriedades aprovadas) |
| Professional Services Information | ✅ Finalizado (sem propriedades aprovadas) |
| HubSpot Metrics | ⬜ Pendente |
