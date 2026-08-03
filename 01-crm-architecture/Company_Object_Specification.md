# Company Object Specification

## 1. Objetivo

O objeto **Company (Empresa)** representa a organização que mantém ou poderá manter relacionamento comercial com a Creative Print.

Ele será a entidade central do CRM e concentrará as informações estratégicas do cliente durante todo o ciclo de vida do relacionamento.

Toda empresa poderá possuir:

- um ou mais contatos;
- uma ou mais oportunidades de negócio;
- um ou mais tickets de suporte;
- um histórico completo de relacionamento;
- informações comerciais, financeiras e operacionais.

O objetivo deste objeto é fornecer uma visão única e centralizada de cada cliente, evitando duplicidade de informações e permitindo que vendas, marketing e atendimento trabalhem sobre a mesma base de dados.

# Definição

Uma **Empresa (Company)** representa uma pessoa jurídica ou negócio que possui ou poderá possuir relacionamento com a Creative Print.

A Empresa é considerada o cliente principal da organização e funciona como ponto central para associação dos demais objetos do CRM.

Cada Empresa poderá estar relacionada a:

- Contatos (Contacts)
- Negócios (Deals)
- Tickets
- Atividades
- Produtos contratados
- Campanhas de marketing

Exemplos de Empresas no contexto da Creative Print:

- Restaurante
- Clínica
- Barbearia
- Academia
- Loja
- Escritório
- Prestador de Serviços

Em situações específicas de venda para pessoa física, o relacionamento poderá existir apenas através do objeto Contato, sem necessidade de criação de uma Empresa.

# Regras de Criação

## Quando criar uma Empresa

Uma Empresa deverá ser criada quando existir uma oportunidade real de relacionamento comercial com um negócio.

Os principais cenários são:

- Solicitação de orçamento.
- Compra de qualquer produto ou serviço.
- Preenchimento de formulário informando o nome da empresa.
- Contato via WhatsApp representando um negócio.
- Contato via Instagram representando uma empresa.
- Importação de clientes.
- Cadastro manual realizado pela equipe comercial.

---

## Quando NÃO criar uma Empresa

Não criar uma Empresa quando:

- O contato ainda não informou o nome do negócio.
- O contato é apenas um visitante sem intenção comercial.
- O contato é fornecedor (será classificado posteriormente).
- O contato é parceiro (será classificado posteriormente).
- O contato é pessoa física e não representa uma empresa.

Nestes casos, apenas o objeto **Contato (Contact)** será utilizado.

---

## Regra de Duplicidade

Antes da criação de uma nova Empresa, o CRM deverá verificar se ela já existe.

A validação deverá considerar, sempre que possível:

1. Nome da empresa.
2. Domínio do site.
3. CNPJ (quando disponível).

Caso exista uma Empresa cadastrada, um novo registro não deverá ser criado.

---

## Regra de Associação

Sempre que possível, um Contato deverá estar associado a uma Empresa.

Essa associação permitirá manter o histórico completo do relacionamento comercial e evitar duplicidade de informações.

# Responsabilidades

## Objetivo

Definir quem é responsável pela criação, manutenção e qualidade das informações armazenadas no objeto **Empresa (Company)**.

Uma definição clara de responsabilidades garante consistência dos dados, reduz erros operacionais e estabelece uma governança adequada para o CRM.

---

## Responsáveis pelo Objeto

| Responsabilidade                                | Responsável                   |
| ----------------------------------------------- | ----------------------------- |
| Criar uma Empresa                               | Equipe Comercial ou Automação |
| Atualizar informações comerciais                | Equipe Comercial              |
| Atualizar informações cadastrais                | Equipe Comercial              |
| Atualizar informações provenientes dos sistemas | Integrações e Automações      |
| Garantir a qualidade dos dados                  | RevOps                        |
| Resolver registros duplicados                   | RevOps                        |
| Definir novas propriedades                      | RevOps                        |
| Aprovar alterações estruturais                  | RevOps                        |

---

## Fonte Oficial dos Dados

O HubSpot será considerado a **fonte única da verdade (Single Source of Truth)** para todas as informações comerciais relacionadas às Empresas.

Os sistemas da Creative Print (CP Agenda, CP Review e futuras soluções) poderão consultar e atualizar informações específicas, mas o relacionamento comercial será centralizado no HubSpot.

---

## Regras de Atualização

* Informações comerciais deverão ser atualizadas sempre que houver interação relevante com o cliente.
* Alterações realizadas por integrações deverão seguir as regras definidas em **CRM_Data_Governance.md**.
* Nenhuma automação deverá sobrescrever informações preenchidas manualmente sem uma regra previamente documentada.
* Alterações estruturais (novas propriedades, novos grupos ou mudanças de comportamento) deverão ser registradas como uma nova decisão arquitetural (ADR).

---

## Qualidade dos Dados

A qualidade das informações armazenadas no objeto Empresa deverá seguir os seguintes princípios:

* Evitar registros duplicados.
* Evitar propriedades sem finalidade definida.
* Priorizar informações verificadas.
* Manter apenas dados relevantes para o relacionamento comercial.
* Garantir que todas as informações críticas possuam um responsável claramente definido.

# Relacionamentos

## Objetivo

O objeto **Empresa (Company)** será a entidade central do CRM da Creative Print.

Todos os demais objetos deverão estar associados à Empresa sempre que houver um relacionamento comercial B2B.

---

## Estrutura de Relacionamentos

| Objeto            | Relacionamento                                              | Obrigatório | Justificativa                                                       |
| ----------------- | ----------------------------------------------------------- | ----------- | ------------------------------------------------------------------- |
| Contato (Contact) | Uma Empresa pode possuir vários Contatos.                   | Sim         | Uma empresa pode possuir diferentes pessoas de contato.             |
| Negócio (Deal)    | Uma Empresa pode possuir vários Negócios.                   | Sim         | A mesma empresa poderá realizar diversas compras ao longo do tempo. |
| Ticket            | Uma Empresa pode possuir vários Tickets.                    | Sim         | Todo atendimento deverá manter vínculo com o cliente.               |
| Atividades        | Uma Empresa poderá possuir diversas atividades registradas. | Sim         | Centraliza todo o histórico de relacionamento.                      |

---

## Modelo de Relacionamento

```text
Empresa (Company)
│
├── Contatos
│     ├── Proprietário
│     ├── Gerente
│     └── Financeiro
│
├── Negócios
│     ├── Venda de Chaveiros NFC
│     ├── Assinatura CP Agenda
│     └── Renovação CP Review
│
├── Tickets
│     ├── Suporte
│     ├── Dúvidas
│     └── Solicitações
│
└── Atividades
      ├── Ligações
      ├── E-mails
      ├── Reuniões
      └── Tarefas
```

---

## Regras de Associação

* Todo Negócio deverá estar associado a uma Empresa.
* Todo Ticket deverá estar associado a uma Empresa.
* Todo Contato deverá estar associado a uma Empresa, exceto em operações B2C.
* Todas as atividades deverão permanecer vinculadas ao registro da Empresa sempre que possível.

---

## Benefícios da Arquitetura

Essa estrutura proporciona:

* Histórico centralizado de relacionamento.
* Eliminação de duplicidade de informações.
* Melhor segmentação para Marketing.
* Relatórios mais consistentes.
* Escalabilidade para novos produtos e serviços.
* Facilidade para integrações futuras.

## 6. Ciclo de vida
<!-- Quais as etapas de ciclo de vida aplicáveis a uma Empresa -->

## 7. Informações armazenadas
<!-- Quais os grupos de propriedades e principais tipos de dados armazenados neste objeto -->

## 8. Regras arquiteturais
<!-- Restrições, integrações sistêmicas e regras de governança para o objeto Company -->
