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

# Ciclo de Vida

## Objetivo

Definir a evolução de uma Empresa dentro do CRM utilizando o **Lifecycle Stage** padrão do HubSpot.

O Lifecycle Stage representa a maturidade do relacionamento comercial e será utilizado em segmentações, automações, relatórios e métricas.

---

## Lifecycle Stage

| Estágio                        | Quando entra                                                                  | Quando avança                                              |
| ------------------------------ | ----------------------------------------------------------------------------- | ---------------------------------------------------------- |
| Subscriber                     | A empresa apenas demonstrou interesse em receber conteúdo ou manter contato.  | Quando existir interesse comercial identificado.           |
| Lead                           | A empresa demonstrou interesse em um produto ou serviço.                      | Após qualificação inicial.                                 |
| Marketing Qualified Lead (MQL) | A empresa atende ao perfil de cliente ideal e possui potencial comercial.     | Quando for aceita pela equipe comercial.                   |
| Sales Qualified Lead (SQL)     | A oportunidade foi qualificada pela equipe comercial.                         | Quando existir uma negociação ativa.                       |
| Opportunity                    | Existe uma oportunidade real registrada através de um Negócio (Deal).         | Quando ocorrer a primeira venda.                           |
| Customer                       | A empresa realizou sua primeira compra ou contratação.                        | Permanece enquanto houver relacionamento comercial.        |
| Evangelist                     | Cliente satisfeito que recomenda a Creative Print e gera novas oportunidades. | Mantido enquanto continuar atuando como promotor da marca. |
| Other                          | Empresas que não se enquadram nas categorias anteriores.                      | Conforme necessidade futura.                               |

---

## Regras Gerais

* O Lifecycle Stage deverá evoluir sempre para frente, evitando regressões sempre que possível.
* Alterações automáticas deverão ser documentadas antes da implementação.
* O Lifecycle Stage representa o relacionamento comercial e não o status operacional do cliente.

---

## Observação

Informações como:

* Cliente Ativo
* Cliente Inativo
* Em Onboarding
* Cancelado
* Inadimplente

não pertencem ao Lifecycle Stage.

Essas situações serão controladas por propriedades específicas da Creative Print definidas posteriormente no Data Dictionary.

# Informações Armazenadas

## Objetivo

As informações da Empresa serão organizadas em grupos funcionais.

Essa organização facilitará a configuração das propriedades no HubSpot, a manutenção do CRM e a criação de automações e relatórios.

Cada grupo representa um conjunto de informações com uma finalidade específica.

---

## 1. Contact Information

Armazena os dados básicos que identificam a empresa.

Exemplos:

* Nome da empresa
* Nome fantasia
* CNPJ
* Site
* Instagram
* País
* Estado
* Cidade

---

## 2. Perfil da Empresa

Descreve as características do negócio.

Exemplos:

* Segmento
* Porte
* Número de funcionários
* Tipo de empresa
* Idioma
* Fuso horário

Essas informações serão utilizadas principalmente para segmentação, relatórios e definição do ICP.

---

## 3. Informações Comerciais

Controla o relacionamento comercial com a Creative Print.

Exemplos:

* Origem do Lead
* Responsável Comercial
* Data do Primeiro Contato
* Data da Última Interação
* Próxima Ação
* Prioridade

Esse grupo será utilizado principalmente pelo processo de vendas.

---

## 4. Produtos e Serviços

Registra quais soluções da Creative Print fazem parte do relacionamento da empresa.

Exemplos:

* Cliente de Produtos NFC
* Cliente CP Agenda
* Cliente CP Review
* Cliente CP Connect
* Outros produtos contratados

Essas informações serão utilizadas em segmentações, campanhas e Customer Success.

---

## 5. Financeiro

Armazena indicadores financeiros relacionados ao relacionamento comercial.

Exemplos:

* Data da Primeira Compra
* Data da Última Compra
* Receita Total
* Ticket Médio
* Cliente Recorrente

Esse grupo não substituirá um sistema financeiro, mas fornecerá indicadores para análise comercial.

---

## 6. Customer Success

Controla o relacionamento após a venda.

Exemplos:

* Data de Onboarding
* Onboarding Concluído
* Data da Última Reunião
* Próxima Revisão
* Health Score (futuro)

Essas informações apoiarão o acompanhamento dos clientes ao longo do tempo.

---

## 7. Marketing

Armazena informações utilizadas para campanhas e segmentações.

Exemplos:

* ICP
* Persona
* Origem da Campanha
* Consentimento para Marketing
* Última Campanha Recebida

Esse grupo será utilizado principalmente quando o Marketing Hub passar a fazer parte da operação.

---

## Considerações Arquiteturais

Cada propriedade da Empresa deverá pertencer a apenas um grupo funcional.

Novos grupos somente poderão ser criados quando houver necessidade claramente documentada e aprovada na arquitetura do CRM.

Essa padronização garante consistência, facilita a manutenção do sistema e reduz a criação de propriedades redundantes.

# Regras Arquiteturais

## Objetivo

Estabelecer os princípios que orientam a modelagem do objeto **Empresa (Company)** e garantem a consistência da arquitetura do CRM da Creative Print.

Essas regras deverão ser respeitadas em todas as futuras implementações, integrações e automações.

---

## Princípios Arquiteturais

### 1. A Empresa representa o cliente, não a pessoa.

O objeto Empresa representa o negócio com o qual a Creative Print mantém relacionamento comercial.

As pessoas que trabalham nesse negócio deverão ser cadastradas como Contatos.

---

### 2. Toda informação deverá possuir um único local de armazenamento.

Cada informação deverá existir apenas uma vez dentro do CRM.

Não serão permitidas duplicações de propriedades entre objetos sem necessidade técnica claramente justificada.

---

### 3. O HubSpot será a fonte única da verdade (Single Source of Truth).

Todas as informações comerciais relacionadas às Empresas deverão ser centralizadas no HubSpot.

Os sistemas da Creative Print poderão consumir ou atualizar dados específicos, mas o CRM será o sistema oficial de relacionamento.

---

### 4. Todo relacionamento comercial deverá estar associado a uma Empresa.

Sempre que existir um cliente B2B, os objetos Contato, Negócio, Ticket e Atividades deverão estar vinculados à respectiva Empresa.

---

### 5. O modelo de dados deverá ser escalável.

A arquitetura deverá permitir a inclusão de novos produtos, serviços e processos sem necessidade de remodelar os objetos principais do CRM.

---

### 6. As propriedades deverão representar dados, e não processos.

Uma propriedade deverá armazenar apenas uma informação.

Processos de negócio serão controlados por Pipelines, Lifecycle Stage, Workflows e demais recursos do HubSpot.

---

### 7. Todas as alterações estruturais deverão ser documentadas.

A criação de novas propriedades, grupos, regras de associação ou mudanças na arquitetura deverá ser registrada antes da implementação.

Nenhuma alteração estrutural deverá ser realizada diretamente no HubSpot sem atualização da documentação do projeto.

---

### 8. A simplicidade terá prioridade sobre a complexidade.

Sempre que houver mais de uma solução tecnicamente possível, será adotada aquela que:

* utilizar menos propriedades;
* reduzir duplicidade de informações;
* facilitar a manutenção;
* utilizar recursos nativos do HubSpot;
* preservar a escalabilidade da arquitetura.
