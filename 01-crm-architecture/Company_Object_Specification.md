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

## 4. Responsabilidades
<!-- Quem é responsável por gerenciar, atualizar e manter a qualidade dos dados deste objeto -->

## 5. Relacionamentos
<!-- Como este objeto se relaciona com Contatos, Negócios (Deals), Tickets e outros objetos -->

## 6. Ciclo de vida
<!-- Quais as etapas de ciclo de vida aplicáveis a uma Empresa -->

## 7. Informações armazenadas
<!-- Quais os grupos de propriedades e principais tipos de dados armazenados neste objeto -->

## 8. Regras arquiteturais
<!-- Restrições, integrações sistêmicas e regras de governança para o objeto Company -->
