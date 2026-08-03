# CRM Automation Architecture

## Objetivo

Este documento define a arquitetura das automações que serão implementadas no CRM.

O objetivo é estabelecer:

* quais eventos geram automações;
* quais objetos participam;
* quais ações devem ser executadas;
* quais regras de negócio devem ser respeitadas.

As automações serão criadas somente após validação dos dados, propriedades e processos relacionados.

---

## 1. Princípios de Automação

### Automação Baseada em Eventos

As automações devem ser acionadas por mudanças reais no processo.

**Exemplos:**
* mudança de estágio do Deal;
* criação de novo cliente;
* alteração de status do Ticket.

**Não utilizar:**
* ❌ automações baseadas apenas em datas sem contexto
* ❌ automações sem objetivo operacional definido

---

### Automação Não Substitui Processo

O Workflow deve executar uma regra existente.

**Exemplo:**
* **Correto:** Quando Deal entrar em Closed Won → criar ações de onboarding.
* **Incorreto:** Criar workflow apenas porque existe uma ferramenta disponível.

---

## 2. Arquitetura de Automação por Objeto

### Company

* **Objetivo:** Gerenciar relacionamento e ciclo do cliente.
* **Possíveis automações:**

| Automação | Gatilho | Ação |
| --- | --- | --- |
| Customer Health Monitoring | Customer Health alterado | Criar alerta |
| Cliente sem acompanhamento | Sem atividade por período definido | Criar tarefa |

---

### Contact

* **Objetivo:** Gerenciar relacionamento individual.
* **Possíveis automações:**

| Automação | Gatilho | Ação |
| --- | --- | --- |
| Novo contato criado | Contact criado | Classificar origem |
| Atualização de dados | Mudança de propriedade | Atualizar segmentação |

---

### Deal

* **Objetivo:** Gerenciar processo comercial.
* **Possíveis automações:**

| Automação | Gatilho | Ação |
| --- | --- | --- |
| Nova oportunidade | Deal criado | Criar tarefa comercial |
| Mudança de estágio | Stage alterado | Atualizar acompanhamento |
| Venda ganha | Closed Won | Iniciar onboarding |

---

### Ticket

* **Objetivo:** Gerenciar atendimento e Customer Success.
* **Possíveis automações:**

| Automação | Gatilho | Ação |
| --- | --- | --- |
| Novo chamado | Ticket criado | Atribuir responsável |
| Prioridade alta | Priority = High | Criar alerta |
| Ticket resolvido | Closed | Registrar acompanhamento |

---

## 3. Automations Roadmap

A implementação seguirá fases.

### Fase 1 — Core CRM Automation
* **Prioridade:** Alta
* **Objetivo:** Garantir disciplina operacional.

| Workflow | Status |
| --- | --- |
| Deal Created → Create Task | Planejado |
| Deal Stage Change Notification | Planejado |
| Ticket Assignment | Planejado |

---

### Fase 2 — Customer Lifecycle Automation
* **Prioridade:** Média
* **Objetivo:** Melhorar relacionamento.

| Workflow | Status |
| --- | --- |
| Customer Onboarding | Planejado |
| Customer Health Monitoring | Planejado |
| Renewal Tracking | Futuro |

---

### Fase 3 — Revenue Operations Automation
* **Prioridade:** Futura
* **Objetivo:** Integração entre Marketing, Vendas e Customer Success.

| Workflow | Status |
| --- | --- |
| Lead Nurturing | Futuro |
| Expansion Opportunities | Futuro |
| Revenue Forecast Alerts | Futuro |

---

## 4. Regras de Governança

### DA-070 — Workflow deve possuir objetivo documentado

Toda automação criada deve possuir:
* objetivo;
* gatilho;
* ação;
* proprietário;
* impacto esperado.

---

### DA-071 — Automação depende da qualidade dos dados

Workflows somente serão criados após validação das propriedades utilizadas.

---

### DA-072 — Evitar excesso de automações

A Creative Print priorizará automações de alto impacto antes de criar fluxos complexos.

---

# Status da Entrega

| Documento | Status |
| --- | --- |
| CRM Strategy | ✅ Concluído |
| Data Governance | ✅ Concluído |
| Data Dictionaries | ✅ Concluído |
| Object Model | ✅ Concluído |
| Associations Model | ✅ Concluído |
| Automation Architecture | ✅ Concluído |
