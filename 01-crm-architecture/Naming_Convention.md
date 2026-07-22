# Naming Convention — Creative Print

**Fase:** 6 — Padronização
**Regra geral:** nada é criado no HubSpot sem seguir esta convenção.

---

## 1. Properties (propriedades customizadas)

**Padrão:** `cp_` + snake_case (nome interno em inglês) | Label visível em português

| Nome interno | Label (PT-BR) | Objeto |
|---|---|---|
| `cp_lead_source` | Origem do Lead | Contato |
| `cp_customer_segment` | Segmento do Cliente | Contato |
| `cp_product_interest` | Produto de Interesse | Contato |
| `cp_customer_status` | Status do Cliente | Contato |
| `cp_segment` | Segmento | Empresa |
| `cp_current_plan` | Plano Atual | Empresa |
| `cp_mrr` | MRR | Empresa |
| `cp_account_status` | Status da Conta | Empresa |
| `cp_customer_since` | Cliente Desde | Empresa |
| `cp_activation_date` | Data de Ativação | Empresa |
| `cp_num_professionals` | Nº de Profissionais | Empresa |
| `cp_monthly_bookings` | Agendamentos/Mês | Empresa |
| `cp_review_campaign_status` | Status da Campanha de Avaliação | Empresa |
| `cp_total_reviews` | Total de Avaliações | Empresa |
| `cp_google_rating` | Nota Google | Empresa |
| `cp_review_link` | Link de Avaliação | Empresa |
| `cp_cancellation_date` | Data de Cancelamento | Empresa |
| `cp_cancellation_reason` | Motivo do Cancelamento | Empresa |
| `cp_product` | Produto | Negócio |
| `cp_deal_source` | Origem do Negócio | Negócio |
| `cp_ticket_type` | Tipo de Ticket | Ticket |

## 2. Grupo de propriedades

Todas as properties customizadas ficam agrupadas em: **Creative Print Information**

## 3. Pipelines

Padrão: `PIPE - <Nome>`

- `PIPE - Sales`
- `PIPE - Customer Success` (ativado no Módulo 6)

## 4. Workflows

Padrão: `WF - <Ação>`

- `WF - Lead Follow Up`
- `WF - Trial Onboarding`
- `WF - Renewal Alert`
- `WF - Cancellation Reason Capture`

## 5. Listas

- Dinâmicas: `LIST - <Critério>` → ex. `LIST - Active Customers`, `LIST - Trial`, `LIST - Cancelados`
- Estáticas: `SLIST - <Critério>` → ex. `SLIST - Evento Julho 2026`

## 6. E-mails de marketing

Padrão: `EM - <Campanha>` → ex. `EM - Boas Vindas Trial`, `EM - Renovação 60 Dias`

## 7. Sequências de vendas

Padrão: `SEQ - <Objetivo>` → ex. `SEQ - Follow Up Proposta`

## 8. Formulários

Padrão: `FORM - <Origem>` → ex. `FORM - Site Landing Page`, `FORM - Instagram Bio Link`

## 9. Dashboards

Padrão: `DASH - <Área>` → ex. `DASH - Vendas`, `DASH - Customer Success`, `DASH - Receita`

## 10. Estágios de pipeline

Texto simples, em português, sem sigla e sem numeração (ex.: `Novo Lead`, não `1 - Novo Lead`), para manter legibilidade em relatórios e dashboards.
