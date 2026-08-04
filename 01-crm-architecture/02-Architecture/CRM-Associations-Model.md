# CRM Associations Model

## Objetivo

Este documento define o modelo de relacionamento entre os objetos do CRM.

O objetivo é estabelecer como empresas, contatos, oportunidades e atendimentos serão associados, garantindo:

* histórico completo do relacionamento;
* visão 360º do cliente;
* consistência dos dados;
* suporte para automações e relatórios futuros.

As associações representam conexões entre registros e não devem ser utilizadas para substituir propriedades ou armazenar informações duplicadas.

---

## 1. Arquitetura Geral

A arquitetura do CRM seguirá o modelo:

```text
Company
   |
   ├── Contact
   |
   ├── Deal
   |
   └── Ticket
```

---

## 2. Company → Contact

### Objetivo

A associação Company → Contact representa as pessoas relacionadas a uma organização.

### Cardinalidade

`Company 1:N Contact`

Uma empresa pode possuir múltiplos contatos.

### Exemplo

```text
Empresa ABC
   ├── João Silva (Diretor)
   ├── Maria Souza (Financeiro)
   └── Carlos Lima (Marketing)
```

### Regras

A **Company** deve armazenar:
* dados organizacionais;
* segmento;
* classificação da empresa.

O **Contact** deve armazenar:
* dados pessoais;
* cargo;
* comunicação individual.

**Não duplicar:**
* ❌ segmento no Contact
* ❌ faturamento no Contact
* ❌ informações da empresa no Contact

---

## 3. Company → Deal

### Objetivo

A associação Company → Deal representa o histórico comercial da organização.

### Cardinalidade

`Company 1:N Deal`

Uma empresa pode possuir diversas oportunidades ao longo do relacionamento.

### Exemplo

```text
Empresa ABC
   ├── Deal 001 (Chaveiros NFC)
   ├── Deal 002 (CP Agenda)
   └── Deal 003 (CP Review)
```

### Regras

O **Deal** deve armazenar:
* valor;
* estágio;
* pipeline;
* previsão de fechamento.

A **Company** deve armazenar:
* perfil da organização;
* informações permanentes.

**Não armazenar na Company:**
* ❌ valor de vendas
* ❌ última negociação
* ❌ produtos comprados individualmente

---

## 4. Company → Ticket

### Objetivo

A associação Company → Ticket representa o histórico de atendimento da organização.

### Cardinalidade

`Company 1:N Ticket`

Uma empresa pode possuir múltiplas solicitações.

### Exemplo

```text
Empresa ABC
   ├── Ticket 001 (Problema login)
   ├── Ticket 002 (Alteração cadastro)
   └── Ticket 003 (Dúvida integração)
```

### Regras

O **Ticket** deve armazenar:
* problema;
* status;
* resolução;
* histórico.

A **Company** deve armazenar:
* indicadores consolidados de relacionamento.

**Não armazenar na Company:**
* ❌ chamados individuais
* ❌ problemas específicos

---

## 5. Contact → Deal

### Objetivo

Representar pessoas envolvidas em oportunidades comerciais.

### Cardinalidade

`Contact N:N Deal`

Um Deal pode envolver decisores, compradores e influenciadores.

### Exemplo

```text
Deal CP Agenda
   ├── João (Decisor)
   └── Maria (Financeiro)
```

A associação identifica participação no processo de venda.

**Não criar propriedades customizadas redundantes:**
* ❌ Decision Maker Name
* ❌ Buyer Name

---

## 6. Contact → Ticket

### Objetivo

Representar quem solicitou ou participa de um atendimento.

### Cardinalidade

`Contact N:N Ticket`

Um chamado pode envolver múltiplas pessoas.

---

## 7. Resumo das Associações

| Associação | Tipo | Objetivo |
| --- | --- | --- |
| Company → Contact | 1:N | Relacionar empresa e pessoas |
| Company → Deal | 1:N | Histórico comercial |
| Company → Ticket | 1:N | Histórico atendimento |
| Contact → Deal | N:N | Participantes da negociação |
| Contact → Ticket | N:N | Participantes do atendimento |

---

## Decisões Arquiteturais

### DA-067 — Associações preservam histórico

Registros históricos devem ser mantidos através de associações entre objetos, evitando sobrescrita de informações.

---

### DA-068 — Cada objeto possui responsabilidade própria

Nenhum objeto deve armazenar informações pertencentes a outro objeto.

---

### DA-069 — Associações são fonte para visão 360º

A análise completa do cliente será construída através das relações entre Company, Contact, Deal e Ticket.

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

---

## Referências

- [Data Model](../03-Data-Model/Data-Model.md)
- [CRM Object Model](CRM-Object-Model.md)
- [Company Data Dictionary](../03-Data-Model/Company-Data-Dictionary.md)
- [Contact Data Dictionary](../03-Data-Model/Contact-Data-Dictionary.md)
- [Deal Data Dictionary](../03-Data-Model/Deal-Data-Dictionary.md)
- [Ticket Data Dictionary](../03-Data-Model/Ticket-Data-Dictionary.md)
