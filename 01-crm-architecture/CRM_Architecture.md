# CRM Architecture — Creative Print

**Projeto:** Implementação do CRM HubSpot na Creative Print
**Módulo:** 1 — Fundação do CRM
**Autor:** Karla Teshima
**Data:** Julho/2026
**Status:** v1.0 — Arquitetura Conceitual (pré-implementação)

---

## 1. Introdução

### 1.1 Sobre a Creative Print

A Creative Print é uma empresa de tecnologia e produtos personalizados que combina fabricação digital, NFC e soluções SaaS para pequenos e médios negócios. A operação está dividida em duas frentes:

**Produtos físicos personalizados**
- Chaveiros NFC
- Cartões NFC
- Brindes corporativos
- Produtos 3D personalizados

**Produtos digitais SaaS**
- CP Agenda (sistema de agendamento para prestadores de serviço)
- CP Review (sistema de captação de avaliações e reputação no Google)
- CP Connect (produto futuro — integrações e automações entre canais)

### 1.2 Objetivo da implantação

Transformar a operação comercial da Creative Print em uma operação orientada por dados, substituindo processos manuais e dispersos (WhatsApp, Instagram, planilhas soltas) por um sistema único de CRM capaz de sustentar vendas, atendimento, Customer Success e, futuramente, Marketing Automation e RevOps.

### 1.3 Escopo do projeto (Módulo 1)

Este documento cobre exclusivamente a **arquitetura conceitual do CRM**: desenho de objetos, propriedades, relacionamentos, pipelines e convenções — sem execução de configuração avançada no HubSpot. O objetivo é que qualquer consultor HubSpot consiga abrir este documento e implementar o CRM exatamente como projetado.

### 1.4 Produtos envolvidos nesta fase

| Produto | Tipo | Envolvido no Módulo 1 |
|---|---|---|
| CP Agenda | SaaS | Sim — modelagem completa |
| CP Review | SaaS | Sim — modelagem completa |
| CP Connect | SaaS (futuro) | Não — apenas contemplado no roadmap de crescimento |
| Produtos físicos NFC/3D | Físico | Parcial — representados como "Produto de Interesse" |

### 1.5 Estratégia de crescimento

A arquitetura é desenhada para acomodar novos produtos sem necessidade de remodelagem. Hoje a empresa opera CP Agenda e CP Review; o roadmap prevê CP Connect, CP Fidelidade e CP Analytics como extensões do mesmo modelo de dados (ver Capítulo 15 — Roadmap).

---

## 2. Objetivos do CRM

O CRM HubSpot precisa resolver problemas concretos da operação atual da Creative Print, não apenas substituir uma planilha por um sistema.

| Objetivo | Descrição |
|---|---|
| Centralizar clientes | Unificar contatos hoje espalhados em WhatsApp, Instagram e conversas pessoais em uma única base |
| Padronizar vendas | Criar um processo comercial replicável, com etapas, critérios e responsáveis definidos |
| Automatizar processos | Reduzir follow-up manual e tarefas repetitivas (a partir do Módulo 5) |
| Melhorar atendimento | Criar histórico de relacionamento e base para Customer Success |
| Construir base para Marketing Automation | Propriedades e listas segmentadas prontas para campanhas futuras |
| Criar estrutura para RevOps | Dados confiáveis para métricas de receita, previsão e eficiência comercial |

---

## 3. Estado Atual (As Is)

### 3.1 Canais de aquisição hoje

- Instagram (Direct)
- WhatsApp
- Indicação

### 3.2 Fluxo atual do cliente

```
Instagram
   ↓
WhatsApp
   ↓
Conversa Manual
   ↓
Pagamento
   ↓
Entrega
```

### 3.3 Problemas identificados

| Problema | Impacto |
|---|---|
| Contatos espalhados no WhatsApp | Perda de histórico e de contexto do cliente |
| Conversas perdidas | Oportunidades comerciais não fechadas |
| Sem histórico centralizado | Impossível saber o que já foi conversado com cada cliente |
| Não existe pipeline | Sem visibilidade sobre quantas vendas estão "em andamento" |
| Não existe follow-up estruturado | Leads esfriam e são esquecidos |
| Não existe previsão de vendas | Decisões de negócio baseadas em percepção, não em dados |
| Não existe segmentação | Impossível fazer campanhas direcionadas por perfil de cliente |
| Não existe automação | Todo processo depende de esforço manual |
| Dados duplicados | Mesmo cliente registrado de formas diferentes em lugares diferentes |
| Relatórios inexistentes | Sem indicadores de vendas, conversão ou retenção |

Esta seção justifica a totalidade do projeto: cada objetivo do Capítulo 2 responde diretamente a um problema listado aqui.

---

## 4. Estado Futuro (To Be)

### 4.1 Arquitetura de aquisição e relacionamento

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

### 4.2 Papel do HubSpot no ecossistema

O HubSpot será o **sistema central de relacionamento comercial** ("source of truth" de relacionamento). Os sistemas CP Agenda e CP Review continuam sendo os sistemas operacionais dos produtos (onde o cliente final usa o serviço). O HubSpot é responsável por:

- Aquisição de leads
- Relacionamento comercial
- Vendas (pipeline e negociação)
- Comunicação (e-mail, futuramente WhatsApp integrado)
- Segmentação de clientes
- Acompanhamento de receita (MRR, renovações, churn)

Os sistemas de produto (CP Agenda / CP Review) continuam responsáveis pela operação diária do serviço contratado pelo cliente. A integração entre os dois mundos é detalhada nos Capítulos 12 e 13.

---

## 5. Arquitetura Geral — Modelo de Objetos do HubSpot

```
        EMPRESA
           ↓
        CONTATO
           ↓
        NEGÓCIO
           ↓
        TICKET
           ↓
        PRODUTO
           ↓
       ATIVIDADES
```

### 5.1 Contatos (Contact)

Representa uma **pessoa física** relacionada à Creative Print — dono de restaurante, fotógrafo, gerente de clínica, responsável por uma empresa cliente. É o objeto que recebe toda comunicação individual (e-mail, WhatsApp, ligação).

### 5.2 Empresas (Company)

Representa a **organização/negócio** do cliente. Usado principalmente para relacionamentos B2B, já que a maioria dos clientes da Creative Print é um pequeno negócio (restaurante, clínica, academia, loja). É o **objeto principal** para clientes B2B.

### 5.3 Negócios (Deal)

Representa uma **oportunidade comercial** — cada venda potencial (produto físico ou assinatura SaaS) deve ter um negócio associado, percorrendo um pipeline até ser Fechado Ganho ou Fechado Perdido.

### 5.4 Tickets

Representa **solicitações de suporte e atendimento pós-venda**. Não será utilizado ativamente no Módulo 1, mas a estrutura já é definida agora para ser ativado no Módulo 6 (Customer Success), evitando retrabalho.

### 5.5 Produtos (Products)

Representa os itens vendidos — no HubSpot, associados a negócios. Nesta fase (plano gratuito/inicial) os produtos SaaS serão representados por **propriedades + negócios**, não por um objeto personalizado (justificativa completa no Capítulo 14).

### 5.6 Atividades (Activities)

E-mails, ligações, reuniões, tarefas e notas registradas em Contatos, Empresas e Negócios — formam o histórico de relacionamento que hoje não existe.

---

## 6. Modelo de Dados

O detalhamento completo de propriedades (nome interno, tipo, obrigatoriedade, valores e justificativa) está na planilha `02-hubspot-configuration/properties.xlsx` e no documento `Data_Model.md`. Abaixo, o resumo executivo de cada objeto.

### 6.1 Contato — resumo

| Property | Tipo | Obrigatório |
|---|---|---|
| Nome | Texto | Sim |
| Sobrenome | Texto | Sim |
| Email | Email | Sim |
| Telefone | Telefone | Sim |
| Cargo | Texto | Não |
| cp_lead_source (Origem) | Dropdown | Sim |
| cp_customer_segment (Segmento) | Dropdown | Sim |
| cp_product_interest (Produto de Interesse) | Multi-checkbox | Sim |
| cp_customer_status (Status do Cliente) | Dropdown | Sim |
| Data Primeiro Contato | Date | Sim (automática) |
| Último Contato | Date | Não (automática) |

### 6.2 Empresa — resumo

| Property | Tipo | Obrigatório |
|---|---|---|
| Nome da Empresa | Texto | Sim |
| CNPJ | Texto | Não |
| Cidade / País | Texto | Não |
| cp_segment (Segmento) | Dropdown | Sim |
| Número de Funcionários | Number | Não |
| cp_customer_since (Cliente desde) | Date | Não |
| cp_current_plan (Plano Atual) | Dropdown | Sim (se cliente SaaS) |
| cp_mrr (MRR) | Currency | Não |
| cp_account_status (Status) | Dropdown | Sim |

### 6.3 Negócio — resumo

| Property | Tipo | Obrigatório |
|---|---|---|
| Nome do Negócio | Texto | Sim |
| Valor | Currency | Sim |
| cp_product (Produto) | Dropdown | Sim |
| Pipeline | Dropdown (sistema) | Sim |
| Estágio (Stage) | Dropdown (sistema) | Sim |
| Data de Fechamento | Date | Sim |
| Responsável (Deal Owner) | Owner | Sim |
| cp_deal_source (Origem) | Dropdown | Sim |

### 6.4 Ticket — resumo (preparado, não ativado no Módulo 1)

| Property | Tipo | Obrigatório |
|---|---|---|
| Assunto | Texto | Sim |
| cp_ticket_type (Tipo) | Dropdown | Sim |
| Prioridade | Dropdown (sistema) | Sim |
| Status | Dropdown (sistema) | Sim |
| Empresa associada | Association | Sim |

---

## 7. Relacionamentos entre Objetos

```
EMPRESA
   │
   ├──── possui 1..N ────▶ CONTATO
   │
   ├──── possui 1..N ────▶ NEGÓCIO
   │                          │
   │                          └──── refere-se a ────▶ PRODUTO
   │
   └──── possui 0..N ────▶ TICKET (a partir do Módulo 6)

NEGÓCIO ── Fechado Ganho ──▶ ASSINATURA (property em Empresa/Contato)
```

### 7.1 Por que Empresa é o objeto principal

A Creative Print cresce majoritariamente no mercado B2B (restaurantes, clínicas, academias, fotógrafos com CNPJ). Um mesmo cliente empresarial pode ter múltiplos contatos (proprietário, gerente, responsável por marketing). Modelar por Empresa evita duplicação de dados comerciais (plano, MRR, status) e permite que múltiplos contatos se relacionem à mesma conta sem perder o vínculo comercial único.

Exemplo:

```
Empresa: Restaurante ABC
   ├── Contato: Proprietário
   ├── Contato: Gerente
   └── Contato: Marketing
```

### 7.2 Regra de associação

- Todo Contato **deve** estar associado a uma Empresa sempre que representar um cliente B2B.
- Todo Negócio **deve** estar associado a uma Empresa e a pelo menos um Contato (o decisor).
- Clientes pessoa física sem empresa (ex.: fotógrafo autônomo) podem existir apenas como Contato, sem Empresa associada — tratado como exceção documentada, não como regra.

---

## 8. Convenções de Nomenclatura

Padronização obrigatória para qualquer elemento criado no HubSpot, sem exceção.

| Tipo de elemento | Padrão | Exemplo |
|---|---|---|
| Properties customizadas | `cp_` + snake_case | `cp_lead_source`, `cp_mrr`, `cp_customer_status` |
| Grupo de propriedades | Creative Print Information | — |
| Pipelines | `PIPE - <Nome>` | `PIPE - Sales`, `PIPE - Customer Success` |
| Estágios de pipeline | Texto simples, em português, sem sigla | `Novo Lead`, `Proposta Enviada` |
| Workflows | `WF - <Ação>` | `WF - Lead Follow Up`, `WF - Renewal Alert` |
| Listas ativas (dinâmicas) | `LIST - <Critério>` | `LIST - Active Customers` |
| Listas estáticas | `SLIST - <Critério>` | `SLIST - Evento Julho 2026` |
| E-mails de marketing | `EM - <Campanha>` | `EM - Boas Vindas Trial` |
| Sequências de vendas | `SEQ - <Objetivo>` | `SEQ - Follow Up Proposta` |
| Formulários | `FORM - <Origem>` | `FORM - Site Landing Page` |
| Dashboards | `DASH - <Área>` | `DASH - Vendas`, `DASH - Customer Success` |

**Regra geral:** nenhum elemento é criado no HubSpot sem seguir esta tabela. Qualquer exceção deve ser registrada no Capítulo 14 (Decisões Arquiteturais) com justificativa.

---

## 9. Pipeline Comercial (Sales)

`PIPE - Sales`

```
Novo Lead
   ↓
Contato Inicial
   ↓
Diagnóstico
   ↓
Proposta Enviada
   ↓
Negociação
   ↓
Fechado Ganho / Fechado Perdido
```

| Estágio | Critério de Entrada | Critério de Saída |
|---|---|---|
| Novo Lead | Lead capturado por qualquer canal (Instagram, WhatsApp, Site, Indicação) | Primeiro contato realizado pelo time comercial |
| Contato Inicial | Contato realizado, lead confirma interesse | Necessidade do cliente identificada |
| Diagnóstico | Necessidade mapeada | Solução definida e orçamento viável identificado |
| Proposta Enviada | Proposta comercial formal enviada | Cliente responde (positiva, negativa ou pede ajuste) |
| Negociação | Cliente demonstrou interesse real, ajustando condições | Condições finais aceitas ou recusadas |
| Fechado Ganho | Pagamento/contrato confirmado | — (fim do pipeline de vendas) |
| Fechado Perdido | Cliente recusa ou lead esfria sem resposta em 30 dias | — (fim do pipeline de vendas) |

---

## 10. Lifecycle Stage (ciclo de vida do contato)

```
Subscriber → Lead → MQL → SQL → Opportunity → Customer → Evangelist
```

| Etapa | Quando muda |
|---|---|
| Subscriber | Contato se inscreveu em algum canal (newsletter, redes) sem intenção comercial ainda |
| Lead | Demonstrou interesse ativo (respondeu, perguntou preço, pediu contato) |
| MQL (Marketing Qualified Lead) | Engajou com conteúdo/campanha de forma relevante (a partir do Módulo 4, quando Marketing entra em operação) |
| SQL (Sales Qualified Lead) | Comercial validou que o lead tem perfil e necessidade real — corresponde à entrada no estágio "Diagnóstico" do pipeline |
| Opportunity | Negócio criado e ativo no pipeline |
| Customer | Negócio fechado como Ganho |
| Evangelist | Cliente ativo há mais de 6 meses, com indicação registrada ou avaliação positiva |

---

## 11. Pipeline de Customer Success

`PIPE - Customer Success`

```
Onboarding
   ↓
Treinamento
   ↓
Primeiro Resultado
   ↓
Cliente Ativo
   ↓
Expansão
   ↓
Renovação
```

| Estágio | Critério de Entrada | Critério de Saída |
|---|---|---|
| Onboarding | Negócio fechado ganho, acesso ao produto (CP Agenda/CP Review) liberado | Configuração inicial concluída |
| Treinamento | Configuração concluída | Cliente demonstra uso autônomo básico |
| Primeiro Resultado | Cliente usando o produto | Cliente obtém primeiro resultado mensurável (ex.: primeiro agendamento via CP Agenda, primeira avaliação via CP Review) |
| Cliente Ativo | Primeiro resultado alcançado | Uso recorrente e estável do produto |
| Expansão | Identificada oportunidade de upsell/cross-sell | Novo negócio de expansão criado no Sales Pipeline |
| Renovação | Data de renovação se aproximando (60 dias) | Renovado (volta para Cliente Ativo) ou Cancelado |

Este pipeline não será ativado tecnicamente no HubSpot no Módulo 1 — está documentado agora para ser implementado no Módulo 6, evitando retrabalho de modelagem.

---

## 12. Mapeamento de Dados: CP Agenda → HubSpot

### 12.1 Fluxo de dados do sistema

```
Tenant → Cliente → Profissionais → Serviços → Agendamentos → Pagamentos
```

### 12.2 Tabela de mapeamento

| Sistema (CP Agenda) | HubSpot | Objeto/Property | Observação |
|---|---|---|---|
| Tenant | Empresa | Company | Cada tenant do CP Agenda vira uma Empresa no HubSpot |
| Cliente (dono do tenant) | Contato | Contact | Responsável pela conta, associado à Empresa |
| Plano contratado | Property | `cp_current_plan` (Company) | Ex.: Básico, Pro, Premium |
| Mensalidade | Property | `cp_mrr` (Company) | Alimenta métricas de receita recorrente |
| Status da assinatura | Property | `cp_account_status` (Company) | Ativo, Trial, Inadimplente, Cancelado |
| Data de ativação | Property | `cp_activation_date` (Company) | Data em que o tenant começou a usar o produto |
| Quantidade de profissionais cadastrados | Property | `cp_num_professionals` (Company) | Indicador de tamanho de operação do cliente |
| Quantidade de agendamentos/mês | Property | `cp_monthly_bookings` (Company) | Indicador de uso — insumo futuro para Health Score |
| Renovação da assinatura | Deal | Negócio no `PIPE - Sales` (tipo Renovação) | Criado automaticamente 60 dias antes do vencimento (Módulo 5+) |
| Cancelamento | Property | `cp_cancellation_date` + `cp_cancellation_reason` (Company) | Motivo do cancelamento categorizado |

### 12.3 Regra de sincronização (conceitual)

Nesta fase (Módulo 1) o mapeamento é **conceitual** — não há integração técnica ainda. A integração real (API/Zapier/Make) está prevista no roadmap (Módulo 8 — Integrações). O objetivo aqui é garantir que, quando a integração for construída, o destino de cada dado já esteja definido.

---

## 13. Mapeamento de Dados: CP Review → HubSpot

### 13.1 Fluxo de dados do sistema

```
Empresa → Campanhas → Avaliações → Google Rating → Links
```

### 13.2 Tabela de mapeamento

| Sistema (CP Review) | HubSpot | Objeto/Property | Observação |
|---|---|---|---|
| Empresa cliente | Empresa | Company | Mesma Empresa usada para CP Agenda, se o cliente usar os dois produtos |
| Campanha de avaliação ativa | Property | `cp_review_campaign_status` (Company) | Ativa, Pausada, Não configurada |
| Total de avaliações recebidas | Property | `cp_total_reviews` (Company) | Indicador de uso/engajamento |
| Nota média no Google | Property | `cp_google_rating` (Company) | Usado futuramente em relatórios de sucesso do cliente |
| Link de avaliação gerado | Property | `cp_review_link` (Company) | Referência operacional |
| Plano CP Review | Property | `cp_current_plan` (Company) | Mesma property usada pelo CP Agenda — um cliente pode ter os dois produtos, refletido em `cp_product_interest`/negócios distintos |

### 13.3 Observação de modelagem

Um mesmo cliente pode contratar CP Agenda e CP Review simultaneamente. Por isso, o produto é tratado como **atributo do relacionamento** (property `cp_product` no Negócio e `cp_product_interest` no Contato), e não como uma Empresa separada por produto — evitando duplicação de conta.

---

## 14. Decisões Arquiteturais e Justificativas

| Decisão | Justificativa |
|---|---|
| HubSpot será a fonte única da verdade para dados comerciais e de relacionamento | Evita dados divergentes entre WhatsApp, planilhas e sistemas de produto |
| Empresas serão a entidade principal para clientes B2B | Facilita múltiplos contatos por cliente e evita duplicação de dados comerciais (plano, MRR, status) |
| Produtos SaaS (CP Agenda, CP Review) serão representados por propriedades + negócios, não por Objetos Personalizados | Compatível com o plano inicial do HubSpot (gratuito/starter); pode evoluir para Objeto Personalizado quando o volume justificar a complexidade adicional |
| Todas as propriedades customizadas usam o prefixo `cp_` | Padronização, fácil identificação e diferenciação de propriedades nativas do HubSpot |
| Pipeline comercial separado do pipeline de Customer Success | Evita misturar processo de vendas com processo de retenção/atendimento — métricas e responsáveis são diferentes |
| Tickets modelados desde já, mesmo sem uso imediato | Evita retrabalho de modelagem quando o Módulo 6 (Customer Success) for implementado |
| Um mesmo cliente que usa CP Agenda e CP Review é uma única Empresa | Evita duplicação de conta; produto é tratado como atributo do relacionamento, não como entidade separada |
| Não duplicar propriedades entre objetos quando um relacionamento já resolve | Reduz inconsistência — ex.: MRR fica na Empresa, não repetido em cada Contato |
| Evitar campos de texto livre quando existir lista de opções possível | Garante dados estruturados, necessários para segmentação e relatórios futuros |
| Nomenclatura interna de properties em inglês (`cp_lead_source`), labels visíveis em português | Compatibilidade com boas práticas internacionais de HubSpot e clareza para o time local |
| Moeda da conta configurada em BRL (Real) | Operação e cobrança da Creative Print são no Brasil |

---

## 15. Roadmap de Evolução da Arquitetura

| Módulo | Entrega |
|---|---|
| 1 | Arquitetura do CRM (este documento) |
| 2 | CRM configurado no HubSpot (properties, pipelines, contas criadas) |
| 3 | Pipeline Comercial operacional com negócios reais |
| 4 | Marketing (formulários, listas, lifecycle stages ativos) |
| 5 | Automações (workflows de follow-up, renovação, nutrição) |
| 6 | Customer Success (pipeline CS e tickets ativados) |
| 7 | Dashboards e relatórios de receita |
| 8 | Integrações com CP Agenda e CP Review (dados reais fluindo) |
| 9 | IA aplicada (scoring de leads, previsão de churn) |
| 10 | Receita — modelo de forecast e RevOps consolidado |
| 11 | Otimização de processos e arquitetura |
| 12 | Projeto Final — case completo de implementação |

### 15.1 Crescimento sem remodelagem

```
Hoje:        CP Agenda, CP Review
Futuro:      CP Connect, CP Fidelidade, CP Analytics
```

Novos produtos entram como novos valores em `cp_product_interest` / `cp_product` e novas propriedades de conta (seguindo o padrão `cp_`), sem necessidade de recriar objetos, pipelines ou a estrutura de relacionamento Empresa → Contato → Negócio já definida.

---

## 16. Boas Práticas Arquiteturais

- Não duplicar propriedades entre objetos.
- Evitar campos de texto livre quando houver lista de opções possível.
- Padronizar nomenclatura interna em inglês (`cp_`), labels em português.
- Centralizar indivíduos em Contatos.
- Utilizar Empresas como entidade principal para clientes B2B.
- Criar propriedades reutilizáveis entre pipelines quando fizer sentido.
- Manter pipelines separados por processo de negócio (vendas ≠ sucesso do cliente).
- Documentar toda decisão arquitetural relevante no Capítulo 14, no momento em que é tomada — não depois.

---

## 17. Próximas Etapas (Módulo 2)

1. Criar a conta HubSpot (moeda BRL, idioma português).
2. Criar os grupos de propriedades customizadas (`Creative Print Information`).
3. Criar todas as properties listadas em `properties.xlsx`.
4. Construir os pipelines `PIPE - Sales` conforme Capítulo 9.
5. Importar dados existentes (contatos e empresas atuais) usando os templates de `02-hubspot-configuration/import_templates`.
6. Validar a modelagem com uma amostra real de dados.
7. Preparar o terreno para automações (Módulo 5) e Customer Success (Módulo 6).

---

## Anexos

- `properties.xlsx` — especificação completa de propriedades (Contato, Empresa, Negócio, Ticket)
- `pipelines.xlsx` — estágios detalhados do Sales Pipeline e Customer Success Pipeline
- `diagrams/crm_architecture.png` — diagrama oficial de arquitetura de objetos
- `diagrams/customer_journey.png` — diagrama da jornada do cliente (As Is → To Be)
- `diagrams/data_model.png` — diagrama ER simplificado do modelo de dados
- `Business_Discovery.md`, `Current_State.md`, `Future_State.md`, `Data_Model.md`, `Naming_Convention.md`, `Process_Design.md`, `System_Mapping.md`, `Architecture_Decisions.md` — documentos de apoio detalhados por fase
