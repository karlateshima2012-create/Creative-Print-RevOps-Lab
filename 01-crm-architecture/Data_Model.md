# Data Model — Creative Print

**Fase:** 5 — Modelagem de Dados
**Nota:** este documento é a versão detalhada de `properties.xlsx`. Toda property aqui listada também está na planilha, pronta para ser criada no HubSpot em Settings → Properties.

---

## 1. Objeto: Contato (Contact)

**Finalidade:** representar uma pessoa física relacionada à Creative Print (responsável por uma Empresa cliente, lead individual, etc.).

| # | Nome interno | Label (PT-BR) | Tipo | Grupo | Obrigatório | Valores/Opções | Quem preenche | Quando atualiza |
|---|---|---|---|---|---|---|---|---|
| 1 | `firstname` | Nome | Texto | Padrão HubSpot | Sim | — | Comercial / Formulário | Na criação |
| 2 | `lastname` | Sobrenome | Texto | Padrão HubSpot | Sim | — | Comercial / Formulário | Na criação |
| 3 | `email` | Email | Email | Padrão HubSpot | Sim | — | Comercial / Formulário | Na criação |
| 4 | `phone` | Telefone | Telefone | Padrão HubSpot | Sim | — | Comercial / Formulário | Na criação |
| 5 | `jobtitle` | Cargo | Texto | Padrão HubSpot | Não | — | Comercial | Durante qualificação |
| 6 | `cp_lead_source` | Origem do Lead | Dropdown | Creative Print Information | Sim | Instagram, WhatsApp, Website, Google, Indicação, Evento, Outro | Comercial | Na criação |
| 7 | `cp_customer_segment` | Segmento do Cliente | Dropdown | Creative Print Information | Sim | Restaurante, Clínica, Academia, Fotógrafo, Loja, Serviços, Outro | Comercial | Durante qualificação |
| 8 | `cp_product_interest` | Produto de Interesse | Multi-checkbox | Creative Print Information | Sim | NFC Products, CP Agenda, CP Review, CP Connect, 3D Printing | Comercial | Durante qualificação |
| 9 | `cp_customer_status` | Status do Cliente | Dropdown | Creative Print Information | Sim | Lead, Prospect, Customer, Inactive | Comercial / CS | A cada mudança de etapa |
| 10 | `createdate` | Data Primeiro Contato | Date | Padrão HubSpot | Sim (automática) | — | Sistema | Na criação |
| 11 | `notes_last_contacted` | Último Contato | Date | Padrão HubSpot | Não (automática) | — | Sistema | A cada interação registrada |
| 12 | `lifecyclestage` | Lifecycle Stage | Dropdown (sistema) | Padrão HubSpot | Sim | Subscriber, Lead, MQL, SQL, Opportunity, Customer, Evangelist | Sistema / Comercial | Conforme jornada (ver Cap. 10 do CRM_Architecture.md) |
| 13 | `company` (associação) | Empresa Associada | Association | Padrão HubSpot | Sim (se B2B) | — | Comercial | Na criação/qualificação |

## 2. Objeto: Empresa (Company)

**Finalidade:** representar a organização cliente — entidade principal para relacionamento B2B.

| # | Nome interno | Label (PT-BR) | Tipo | Grupo | Obrigatório | Valores/Opções | Quem preenche | Quando atualiza |
|---|---|---|---|---|---|---|---|---|
| 1 | `name` | Nome da Empresa | Texto | Padrão HubSpot | Sim | — | Comercial | Na criação |
| 2 | `cp_cnpj` | CNPJ | Texto | Creative Print Information | Não | — | Comercial | Na criação |
| 3 | `city` | Cidade | Texto | Padrão HubSpot | Não | — | Comercial | Na criação |
| 4 | `country` | País | Texto | Padrão HubSpot | Não | — | Comercial | Na criação |
| 5 | `cp_segment` | Segmento | Dropdown | Creative Print Information | Sim | Restaurante, Clínica, Academia, Fotógrafo, Loja, Serviços, Outro | Comercial | Na criação |
| 6 | `numberofemployees` | Nº de Funcionários | Number | Padrão HubSpot | Não | — | Comercial | Na criação |
| 7 | `cp_customer_since` | Cliente Desde | Date | Creative Print Information | Não | — | Sistema (na venda) | Quando negócio é Fechado Ganho |
| 8 | `cp_current_plan` | Plano Atual | Dropdown | Creative Print Information | Sim (se cliente SaaS) | Básico, Pro, Premium | Comercial / CS | Na venda / upgrade / downgrade |
| 9 | `cp_mrr` | MRR | Currency (BRL) | Creative Print Information | Não | — | Comercial / Financeiro | Na venda / mudança de plano |
| 10 | `cp_account_status` | Status da Conta | Dropdown | Creative Print Information | Sim | Trial, Ativo, Inadimplente, Cancelado | CS | A cada mudança de situação |
| 11 | `cp_activation_date` | Data de Ativação | Date | Creative Print Information | Não | — | CS | No onboarding |
| 12 | `cp_num_professionals` | Nº de Profissionais (CP Agenda) | Number | Creative Print Information | Não | — | Integração futura / CS | Periodicamente |
| 13 | `cp_monthly_bookings` | Agendamentos/Mês (CP Agenda) | Number | Creative Print Information | Não | — | Integração futura | Mensal |
| 14 | `cp_review_campaign_status` | Status Campanha CP Review | Dropdown | Creative Print Information | Não | Ativa, Pausada, Não configurada | Integração futura / CS | Conforme uso |
| 15 | `cp_total_reviews` | Total de Avaliações (CP Review) | Number | Creative Print Information | Não | — | Integração futura | Conforme uso |
| 16 | `cp_google_rating` | Nota Google | Number (decimal) | Creative Print Information | Não | — | Integração futura | Periodicamente |
| 17 | `cp_review_link` | Link de Avaliação | Texto | Creative Print Information | Não | — | Integração futura | Na ativação |
| 18 | `cp_cancellation_date` | Data de Cancelamento | Date | Creative Print Information | Não | — | CS | No cancelamento |
| 19 | `cp_cancellation_reason` | Motivo do Cancelamento | Dropdown | Creative Print Information | Não | Preço, Concorrência, Não uso, Insatisfação, Outro | CS | No cancelamento |

## 3. Objeto: Negócio (Deal)

**Finalidade:** representar uma oportunidade comercial em andamento.

| # | Nome interno | Label (PT-BR) | Tipo | Grupo | Obrigatório | Valores/Opções | Quem preenche | Quando atualiza |
|---|---|---|---|---|---|---|---|---|
| 1 | `dealname` | Nome do Negócio | Texto | Padrão HubSpot | Sim | — | Comercial | Na criação |
| 2 | `amount` | Valor | Currency (BRL) | Padrão HubSpot | Sim | — | Comercial | Na proposta |
| 3 | `cp_product` | Produto | Dropdown | Creative Print Information | Sim | NFC Products, CP Agenda, CP Review, CP Connect, 3D Printing | Comercial | Na criação |
| 4 | `pipeline` | Pipeline | Dropdown (sistema) | Padrão HubSpot | Sim | PIPE - Sales, PIPE - Customer Success | Comercial | Na criação |
| 5 | `dealstage` | Estágio | Dropdown (sistema) | Padrão HubSpot | Sim | Ver Cap. 9 do CRM_Architecture.md | Comercial | A cada avanço |
| 6 | `closedate` | Data de Fechamento | Date | Padrão HubSpot | Sim | — | Comercial | Na criação (estimada) / no fechamento (real) |
| 7 | `hubspot_owner_id` | Responsável | Owner | Padrão HubSpot | Sim | — | Comercial | Na criação |
| 8 | `cp_deal_source` | Origem do Negócio | Dropdown | Creative Print Information | Sim | Instagram, WhatsApp, Website, Google, Indicação, Evento, Outro | Comercial | Na criação |
| 9 | `cp_deal_type` | Tipo de Negócio | Dropdown | Creative Print Information | Não | Novo Cliente, Upsell, Renovação | Comercial | Na criação |

## 4. Objeto: Ticket (preparado, ativação no Módulo 6)

**Finalidade:** representar solicitações de suporte e atendimento pós-venda.

| # | Nome interno | Label (PT-BR) | Tipo | Grupo | Obrigatório | Valores/Opções | Quem preenche | Quando atualiza |
|---|---|---|---|---|---|---|---|---|
| 1 | `subject` | Assunto | Texto | Padrão HubSpot | Sim | — | CS / Cliente | Na criação |
| 2 | `cp_ticket_type` | Tipo de Ticket | Dropdown | Creative Print Information | Sim | Dúvida, Bug, Solicitação, Cancelamento | CS | Na criação |
| 3 | `hs_ticket_priority` | Prioridade | Dropdown (sistema) | Padrão HubSpot | Sim | Baixa, Média, Alta, Urgente | CS | Na criação |
| 4 | `hs_pipeline_stage` | Status | Dropdown (sistema) | Padrão HubSpot | Sim | Novo, Em Andamento, Resolvido, Fechado | CS | A cada avanço |
| 5 | `company` (associação) | Empresa Associada | Association | Padrão HubSpot | Sim | — | CS | Na criação |

## 5. Resumo de contagem de propriedades customizadas

| Objeto | Propriedades customizadas (`cp_`) |
|---|---|
| Contato | 4 |
| Empresa | 13 |
| Negócio | 2 |
| Ticket | 1 |
| **Total** | **20** |

Este número é intencionalmente enxuto para o Módulo 1: o princípio arquitetural (Cap. 16 do `CRM_Architecture.md`) é não criar propriedades especulativas — cada property aqui tem uma justificativa e um consumidor claro (relatório, automação ou processo).
