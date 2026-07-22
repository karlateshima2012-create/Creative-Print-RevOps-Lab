# Future State — Creative Print

**Fase:** 4 (parte de) — Estado Futuro (To Be)

---

## 1. Arquitetura de aquisição e relacionamento

```
Instagram   Google   Site   WhatsApp   Landing Pages   Indicação
        \      |       |        |            |           /
         \_____|_______|________|____________|__________/
                              ↓
                        HubSpot CRM
                              ↓
                          Pipeline
                              ↓
                            Venda
                              ↓
                         Onboarding
                              ↓
                      Customer Success
                              ↓
                          Renovação
```

## 2. Decisão arquitetural central

O HubSpot será considerado o sistema central de relacionamento comercial da Creative Print. Os sistemas CP Agenda e CP Review continuarão responsáveis pela operação dos produtos (o dia a dia do cliente final dentro de cada SaaS), enquanto o HubSpot será responsável por:

- Aquisição
- Relacionamento
- Vendas
- Comunicação
- Segmentação
- Acompanhamento de receita

## 3. O que muda por área

| Área | Hoje (As Is) | Futuro (To Be) |
|---|---|---|
| Aquisição | Instagram e WhatsApp informais | Múltiplos canais convergindo para o CRM |
| Qualificação | Inexistente | Lifecycle stage (Subscriber → Lead → MQL → SQL) |
| Vendas | Conversa solta, sem etapas | Pipeline com estágios, critérios e responsável |
| Atendimento | Reativo, sem histórico | Tickets com histórico centralizado (Módulo 6) |
| Pós-venda | Inexistente | Pipeline de Customer Success com onboarding e acompanhamento |
| Renovação | Não monitorada | Gatilho automático 60 dias antes do vencimento |
| Relatórios | Inexistentes | Dashboards de vendas, retenção e receita (Módulo 7) |

## 4. Critério de sucesso do Estado Futuro

A arquitetura futura é considerada bem-sucedida quando qualquer pessoa do time consegue, a partir do HubSpot e sem depender de memória individual, responder: quem é o cliente, o que ele contratou, em que etapa do relacionamento está, e quando precisa ser contatado novamente.
