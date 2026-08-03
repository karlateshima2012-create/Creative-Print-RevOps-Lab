# CRM Object Model

## Objetivo

Este documento define o modelo de dados do CRM, estabelecendo a responsabilidade de cada objeto, suas propriedades principais e os relacionamentos existentes entre eles.

O objetivo é garantir que cada informação seja armazenada no local correto, evitando duplicidade, inconsistência de dados e dificuldades futuras de automação e análise.

O modelo foi estruturado seguindo princípios de arquitetura de CRM:

* cada objeto possui uma responsabilidade clara;
* informações transacionais não devem ser armazenadas em objetos de cadastro;
* histórico deve ser preservado através de relacionamentos;
* propriedades devem representar o estado atual da informação.

---

## Princípios do Modelo de Objetos

### Separação de responsabilidades

Cada objeto deve armazenar somente informações relacionadas ao seu propósito.

Exemplo:

- **Company** representa uma organização.
- **Deal** representa uma oportunidade comercial.
- **Ticket** representa uma solicitação de atendimento.

### Evitar duplicidade de dados

A mesma informação não deve existir em múltiplos objetos sem necessidade.

Exemplo:

O segmento da empresa deve existir na **Company** e não ser replicado em todos os **Deals**.

### Histórico através de associações

Eventos que acontecem ao longo do tempo devem ser representados através de registros relacionados.

Exemplo:

Uma empresa pode possuir vários **Deals** ao longo dos anos.

### Dados derivados devem ser calculados

Informações que podem ser obtidas através de outros dados não devem ser preenchidas manualmente.

Exemplo:

Receita acumulada deve ser calculada através dos **Deals** fechados.

---

## Arquitetura Geral dos Objetos

O CRM será estruturado utilizando os principais objetos do HubSpot:

```text
Company
  ↓
Representa organizações e empresas.

Contact
  ↓
Representa pessoas relacionadas às empresas.

Deal
  ↓
Representa oportunidades comerciais e transações.

Ticket
  ↓
Representa solicitações de atendimento e suporte.

Activity
  ↓
Representa interações realizadas no relacionamento.
```

---

## Modelo de Relacionamento

```text
                    Company
                       |
        --------------------------------
        |                              |
     Contact                         Deal
        |                              |
        |                              |
     Ticket                    Products / Revenue
```

- **Company** → Multiple Contacts
- **Company** → Multiple Deals
- **Company** → Multiple Tickets

---

## Company Object

### Responsabilidade

O objeto **Company** representa a organização ou empresa dentro do CRM.

Ele deve armazenar informações permanentes ou estratégicas sobre a empresa.

### Deve armazenar:

* identificação da empresa;
* perfil organizacional;
* segmento;
* localização;
* interesses;
* classificação comercial;
* saúde do cliente.

### Não deve armazenar:

* valor de negociação;
* histórico de compras;
* pagamentos;
* contratos;
* chamados específicos.

### Company Property Groups

| Grupo | Objetivo |
| --- | --- |
| Contact Information | Identificar a empresa |
| Perfil da Empresa | Características organizacionais |
| Informações Comerciais | Relacionamento comercial |
| Produtos e Serviços | Interesse em soluções |
| Financeiro | Classificação financeira |
| Customer Success | Saúde e relacionamento |
| Marketing | Segmentação e aquisição |

---

## Contact Object

### Responsabilidade

O objeto **Contact** representa pessoas relacionadas às empresas.

Uma empresa pode possuir diversos contatos com diferentes funções.

### Deve armazenar:

* nome;
* email;
* telefone;
* cargo;
* departamento;
* preferências individuais;
* informações de comunicação.

### Não deve armazenar:

* dados gerais da empresa;
* informações comerciais da organização;
* faturamento;
* produtos adquiridos pela empresa.

---

## Deal Object

### Responsabilidade

O objeto **Deal** representa oportunidades comerciais, negociações e receitas associadas ao processo de venda.

### Deve armazenar:

* oportunidade;
* etapa comercial;
* valor;
* previsão de fechamento;
* produto vendido;
* receita.

### Não deve armazenar:

* características permanentes da empresa;
* perfil organizacional;
* informações de marketing da empresa.

---

## Ticket Object

### Responsabilidade

O objeto **Ticket** representa solicitações, problemas e interações de suporte.

### Deve armazenar:

* chamados;
* solicitações;
* problemas;
* status de atendimento;
* histórico de resolução.

### Não deve armazenar:

* informações comerciais;
* dados financeiros;
* classificação estratégica da empresa.

---

## Associação entre Objetos

| Relação | Tipo | Objetivo |
| --- | --- | --- |
| Company → Contact | Um para muitos | Relacionar pessoas e empresas |
| Company → Deal | Um para muitos | Histórico comercial |
| Company → Ticket | Um para muitos | Histórico de atendimento |
| Contact → Deal | Muitos para muitos | Identificar envolvidos na negociação |
| Contact → Ticket | Muitos para muitos | Identificar solicitantes |

---

## Decisões Arquiteturais

### DA-035 — Company como fonte principal de dados organizacionais

O objeto **Company** será responsável pelas informações permanentes e estratégicas da organização.

### DA-036 — Deal como fonte de dados transacionais

Todas as informações relacionadas a vendas, receitas e negociações deverão permanecer no objeto **Deal**.

### DA-037 — Contact representa pessoas, não empresas

Informações individuais devem pertencer ao **Contact**.

Informações organizacionais devem permanecer na **Company**.

### DA-038 — Histórico deve ser preservado através de associações

O CRM não deverá sobrescrever informações históricas.

Eventos comerciais e atendimento devem ser registrados através de objetos relacionados.

### DA-039 — Arquitetura preparada para automações futuras

A separação correta dos objetos permitirá:

* workflows;
* segmentações;
* relatórios;
* integrações;
* análises de receita.

---

# Status da Entrega

**Entrega 04 — CRM Object Model**

- **Status:** Modelagem inicial concluída
- **Próxima etapa:** Entrega 05 — HubSpot Implementation Plan
- **Objetivo da próxima etapa:** Transformar o modelo arquitetural em plano de configuração dentro do HubSpot.
