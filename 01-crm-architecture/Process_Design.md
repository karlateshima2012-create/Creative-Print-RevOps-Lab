# Business Processes — Creative Print

**Fase:** 7 — Processos

---

## 1. Processo comercial completo

```
Lead
  ↓
Qualificação
  ↓
Diagnóstico
  ↓
Proposta
  ↓
Negociação
  ↓
Venda
  ↓
Onboarding
  ↓
Customer Success
  ↓
Renovação
```

## 2. Detalhamento por etapa

### 2.1 Lead
- **Entrada:** contato capturado por qualquer canal (Instagram, WhatsApp, Site, Indicação)
- **Saída:** primeiro contato humano realizado
- **Responsável:** Comercial
- **Critério:** registro criado como Contato no HubSpot com `cp_lead_source` preenchido

### 2.2 Qualificação
- **Entrada:** primeiro contato realizado
- **Saída:** confirmação de que o lead tem perfil (segmento atende, orçamento plausível)
- **Responsável:** Comercial
- **Critério:** `cp_customer_segment` e `cp_product_interest` preenchidos

### 2.3 Diagnóstico
- **Entrada:** lead qualificado
- **Saída:** necessidade específica mapeada, solução definida
- **Responsável:** Comercial
- **Critério:** Negócio criado no `PIPE - Sales`, estágio "Diagnóstico"

### 2.4 Proposta
- **Entrada:** solução definida
- **Saída:** proposta formal enviada ao cliente
- **Responsável:** Comercial
- **Critério:** Negócio movido para "Proposta Enviada", valor preenchido

### 2.5 Negociação
- **Entrada:** cliente responde à proposta
- **Saída:** condições finais aceitas ou recusadas
- **Responsável:** Comercial
- **Critério:** Negócio em "Negociação"

### 2.6 Venda
- **Entrada:** condições aceitas
- **Saída:** pagamento/contrato confirmado
- **Responsável:** Comercial
- **Critério:** Negócio "Fechado Ganho"; Empresa criada/atualizada com `cp_account_status = Ativo`

### 2.7 Onboarding
- **Entrada:** venda confirmada
- **Saída:** cliente configurado e treinado no produto (CP Agenda/CP Review)
- **Responsável:** Customer Success
- **Critério:** Negócio de CS em "Onboarding" → "Treinamento"

### 2.8 Customer Success
- **Entrada:** cliente treinado, iniciando uso
- **Saída:** cliente ativo, usando o produto de forma recorrente
- **Responsável:** Customer Success
- **Critério:** `cp_monthly_bookings` (CP Agenda) ou `cp_total_reviews` (CP Review) com movimentação recorrente

### 2.9 Renovação
- **Entrada:** 60 dias antes da data de vencimento da assinatura
- **Saída:** renovado ou cancelado
- **Responsável:** Customer Success
- **Critério:** Negócio de renovação criado no `PIPE - Sales`; se cancelado, `cp_cancellation_date` e `cp_cancellation_reason` preenchidos

## 3. Papéis e responsabilidades

| Etapa | Responsável |
|---|---|
| Lead até Venda | Comercial |
| Onboarding até Renovação | Customer Success |
| Definição de propriedades e pipelines | RevOps / Administrador do CRM |
