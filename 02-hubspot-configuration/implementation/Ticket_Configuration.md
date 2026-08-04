# Ticket Object Configuration

## Objetivo

Configurar o objeto Ticket para suportar os processos de Customer Success da Creative Print.

O Ticket será utilizado para:
* onboarding de clientes;
* suporte técnico;
* acompanhamento pós-venda;
* Customer Success.

A configuração seguirá a arquitetura aprovada no *Ticket Data Dictionary*.

---

## 1. Configuração do Pipeline

### Pipeline

| Item | Configuração |
| --- | --- |
| Pipeline Name | Customer Success Pipeline |

**Status do Pipeline:** ✅ Configurado

---

## 2. Ticket Pipeline Stages (Ticket Statuses)

Criar/editar as etapas do atendimento:

| Ordem | Stage | Objetivo | Status |
| --- | --- | --- | --- |
| 1 | New | Novo chamado registrado | ✅ Configurado |
| 2 | In Progress | Atendimento em andamento | ✅ Configurado |
| 3 | Waiting on Customer | Aguardando resposta do cliente | ✅ Configurado |
| 4 | Waiting on Us | Aguardando ação interna | ✅ Configurado |
| 5 | Resolved | Problema solucionado | ✅ Configurado |
| 6 | Closed | Atendimento encerrado | ✅ Configurado |

---

## 3. Propriedades Aprovadas

| Propriedade | Grupo HubSpot | Tipo | Ação |
| --- | --- | --- | --- |
| Ticket Name | Ticket Information | Single-line text | ✅ Utilizar |
| Ticket Owner | Ticket Information | HubSpot user | ✅ Utilizar |
| Ticket Status | Ticket Information | Dropdown select | ✅ Utilizar |
| Pipeline | Ticket Information | Pipeline select | ✅ Utilizar |
| Priority | Ticket Information | Dropdown select | ✅ Utilizar |
| Ticket Description | Ticket Information | Multi-line text | ✅ Utilizar |
| Create Date | Ticket Activity | Date | ✅ Utilizar (Nativo) |
| Close Date | Ticket Activity | Date | ✅ Utilizar (Nativo) |
| Last Activity Date | Ticket Activity | Date | ✅ Utilizar (Nativo) |
| Next Activity Date | Ticket Activity | Date | ✅ Utilizar (Nativo) |
| Last Customer Reply Date | Ticket Activity | Date | ✅ Utilizar (Nativo) |
| First Agent Email Response Date | Ticket Activity | Date | ✅ Utilizar (Nativo) |

---

## 4. Validação após Configuração

Checklist de validação técnica:
- [x] Pipeline criado corretamente (`Customer Success Pipeline`).
- [x] 6 estágios revisados e configurados.
- [x] Status de fechamento/resolução validados (`Resolved`, `Closed`).
- [x] Propriedades essenciais de Ticket validadas.
- [ ] Teste de abertura e encerramento de chamado realizado.

---

## 5. Evidências para Portfólio

Diretório de evidências:
`Documentation/evidence/hubspot/ticket/`

Arquivos a salvar:
* `01_customer_success_pipeline.png`
* `02_ticket_stages.png`
* `03_test_ticket_record.png`

---

## Decisões Arquiteturais

### DA-084 — Um único pipeline de Customer Success

O laboratório utilizará um único pipeline para concentrar onboarding, suporte e acompanhamento pós-venda. Novos pipelines somente serão criados caso processos distintos exijam regras, SLAs ou equipes independentes.

---

# Status Ticket Object Configuration

| Item | Status |
| --- | --- |
| Pipeline Customer Success Pipeline | ✅ Completed |
| Ticket Stages | ✅ Completed |
| Core Properties Validation | ✅ Completed |
| Custom Properties Creation | ⬜ Não necessária (v1) |
| Ticket Views | ⬜ Próximo |
| Ticket Automation | ⬜ Futuro |

---

# Status da Implementação Global

| Objeto | Arquitetura | Configuração |
| --- | --- | --- |
| Company | ✅ Concluído | ✅ Completed |
| Contact | ✅ Concluído | ✅ Completed |
| Deal | ✅ Concluído | ✅ Completed (v1) |
| Ticket | ✅ Concluído | ✅ Configurado (v1) |
