# CRM Data Quality Framework

## Objetivo

Este documento define as regras e práticas para manter a qualidade dos dados dentro do CRM.

O objetivo é garantir:

* dados completos;
* informações confiáveis;
* padronização dos registros;
* melhor utilização de automações e relatórios;
* redução de inconsistências operacionais.

A qualidade dos dados será tratada como um processo contínuo de governança.

---

## 1. Princípios de Qualidade de Dados

### Dados Devem Possuir Proprietário

Cada informação crítica deve possuir responsabilidade definida.

| Dado | Responsável |
| --- | --- |
| Empresa | Comercial |
| Contato | Comercial/Marketing |
| Deal | Vendas |
| Ticket | Customer Success |

---

### Dados Devem Possuir Origem Definida

Cada propriedade deve responder:
* Quem cria?
* Quando é atualizado?
* Qual processo utiliza?

| Propriedade | Origem |
| --- | --- |
| Amount | Comercial |
| Lifecycle Stage | Processo CRM |
| Ticket Status | Atendimento |

---

### Evitar Duplicidade

Não criar propriedades que representam a mesma informação.

* **Incorreto:** Ter `Company Size`, `Number of Employees` e `Company Category` quando todos representam tamanho.
* **Correto:** Manter `Number of Employees` como fonte principal.

---

## 2. Data Quality Dimensions

### 2.1 Completeness — Completude
* **Pergunta:** Os dados obrigatórios estão preenchidos?
* **Exemplos:**
  - **Company:** Company Name, Industry, Business Type.
  - **Deal:** Amount, Close Date, Deal Stage.
  - **Ticket:** Ticket Status, Owner, Description.

---

### 2.2 Accuracy — Precisão
* **Pergunta:** A informação representa a realidade?
* **Exemplo:** Deal em *Closed Won* sem valor (`Amount`) preenchido gera dado inconsistente e relatórios incorretos.

---

### 2.3 Consistency — Consistência
* **Pergunta:** O mesmo conceito possui o mesmo padrão?
* **Exemplo:** Evitar misturar `Cliente`, `client` e `Customer`. Padronizar como `Customer`.

---

### 2.4 Timeliness — Atualização
* **Pergunta:** O dado está atualizado?
* **Exemplo:** Deal parado em *Negotiation* por 90 dias deve acionar um alerta operacional.

---

## 3. Data Quality Rules

### Company

| Regra | Objetivo |
| --- | --- |
| Toda Company deve possuir nome | Identificação |
| Evitar empresas duplicadas | Integridade |
| Industry deve seguir lista padronizada | Segmentação |

---

### Contact

| Regra | Objetivo |
| --- | --- |
| Email deve ser único | Evitar duplicidade |
| Contact deve estar associado à Company quando aplicável | Relacionamento |

---

### Deal

| Regra | Objetivo |
| --- | --- |
| Deal deve possuir Owner | Responsabilidade |
| Deal acima de Proposal Sent deve possuir Amount | Previsão |
| Closed Won deve possuir Close Date | Receita correta |

---

### Ticket

| Regra | Objetivo |
| --- | --- |
| Todo Ticket deve possuir Owner | Responsabilidade |
| Todo Ticket deve possuir Status | Controle operacional |
| Tickets fechados devem possuir histórico | Auditoria |

---

## 4. Data Quality Monitoring

### Indicadores

| Métrica | Objetivo |
| --- | --- |
| % registros completos | Qualidade |
| Registros sem Owner | Responsabilidade |
| Deals sem Amount | Receita |
| Tickets sem classificação | Atendimento |

---

## 5. Governança de Mudanças

Toda alteração no CRM deve passar por avaliação.

Antes de criar uma nova propriedade, responder:
1. Já existe propriedade semelhante?
2. Qual objeto é responsável?
3. Quem utiliza essa informação?
4. Qual automação ou relatório depende dela?

---

## Decisões Arquiteturais

### DA-076 — Qualidade de dados é responsabilidade contínua

A governança não termina após a configuração inicial do CRM.

---

### DA-077 — Propriedades devem possuir finalidade definida

Nenhum campo deve existir sem processo, usuário ou decisão associada.

---

### DA-078 — Padronização é prioridade sobre quantidade de dados

Um CRM simples com dados confiáveis é superior a um CRM complexo com dados inconsistentes.

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
| CRM Data Quality Framework | ✅ Concluído |
