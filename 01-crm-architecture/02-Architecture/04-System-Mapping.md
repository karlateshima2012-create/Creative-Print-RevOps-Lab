# System Mapping — CP Agenda & CP Review → HubSpot

**Fase:** 8 — Mapeamento dos Sistemas
**Método:** para cada campo do sistema de origem, responder: Esse dado existe? → Vai para qual objeto do HubSpot? → Qual propriedade? → Atualiza quando?

---

## 1. CP Agenda

### 1.1 Fluxo de dados do sistema

```
Tenant → Cliente → Profissionais → Serviços → Agendamentos → Pagamentos
```

### 1.2 Mapeamento campo a campo

| Campo (CP Agenda) | Existe hoje? | Objeto HubSpot | Property | Atualiza quando |
|---|---|---|---|---|
| Nome do Tenant (negócio do cliente) | Sim | Empresa | `name` | Na criação da conta |
| Responsável pelo Tenant | Sim | Contato | `firstname`/`lastname`/`email` | Na criação da conta |
| Plano contratado | Sim | Empresa | `cp_current_plan` | Na contratação / upgrade / downgrade |
| Valor da mensalidade | Sim | Empresa | `cp_mrr` | Na contratação / mudança de plano |
| Status da assinatura (trial, ativo, inadimplente, cancelado) | Sim | Empresa | `cp_account_status` | Mudança de status no CP Agenda |
| Data de início de uso | Sim | Empresa | `cp_activation_date` | Na ativação |
| Quantidade de profissionais cadastrados | Sim | Empresa | `cp_num_professionals` | Sincronização periódica (integração futura) |
| Quantidade de serviços cadastrados | Sim | — (não mapeado no Módulo 1) | — | Avaliar necessidade no Módulo 8 |
| Quantidade de agendamentos no mês | Sim | Empresa | `cp_monthly_bookings` | Sincronização mensal (integração futura) |
| Pagamentos recebidos | Sim | Negócio (renovação) | `amount`, `closedate` | Na renovação |
| Data de vencimento da assinatura | Sim | Negócio | `closedate` (negócio de renovação criado 60 dias antes) | Gatilho automático (Módulo 5+) |
| Cancelamento | Sim | Empresa | `cp_cancellation_date`, `cp_cancellation_reason` | No cancelamento |

### 1.3 Observação

No Módulo 1 este mapeamento é conceitual — define o destino de cada dado. A integração técnica (API, Zapier ou Make) é construída no Módulo 8.

---

## 2. CP Review

### 2.1 Fluxo de dados do sistema

```
Empresa → Campanhas → Avaliações → Google Rating → Links
```

### 2.2 Mapeamento campo a campo

| Campo (CP Review) | Existe hoje? | Objeto HubSpot | Property | Atualiza quando |
|---|---|---|---|---|
| Empresa cliente | Sim | Empresa | `name` (mesma Empresa do CP Agenda, se aplicável) | Na criação da conta |
| Campanha de avaliação ativa | Sim | Empresa | `cp_review_campaign_status` | Ativação/pausa da campanha |
| Total de avaliações recebidas | Sim | Empresa | `cp_total_reviews` | Sincronização periódica (integração futura) |
| Nota média no Google | Sim | Empresa | `cp_google_rating` | Sincronização periódica (integração futura) |
| Link de avaliação gerado | Sim | Empresa | `cp_review_link` | Na configuração inicial |
| Plano CP Review | Sim | Empresa | `cp_current_plan` (compartilhada com CP Agenda) | Na contratação |

### 2.3 Regra de cliente multi-produto

Se uma Empresa contrata CP Agenda **e** CP Review, ela permanece como uma única Empresa no HubSpot. Os dois produtos ficam registrados como negócios distintos (`cp_product = CP Agenda` e `cp_product = CP Review`) e refletidos em `cp_product_interest` no Contato responsável (ver ADR-007 em `Architecture_Decisions.md`).

---

## 3. Preparação para produtos futuros

| Produto futuro | Status no Módulo 1 |
|---|---|
| CP Connect | Não mapeado — entra como novo valor em `cp_product` quando lançado |
| CP Fidelidade | Não mapeado — roadmap (ver Cap. 15 do `CRM_Architecture.md`) |
| CP Analytics | Não mapeado — roadmap |

A arquitetura foi desenhada (ADR-003, ADR-007) para que novos produtos sejam adicionados como valores de dropdown, sem exigir remodelagem de objetos.
