# CRM Data Governance

## 1. Entity Identification Strategy

O CRM da Creative Print deverá evitar a criação de registros duplicados.

Para isso, cada Empresa será identificada seguindo a seguinte ordem de prioridade:

| Prioridade | Identificador | Observação |
|------------|---------------|------------|
| 1 | CNPJ | Identificador oficial da empresa. |
| 2 | Domínio do site | Ex.: creativeprintjp.com |
| 3 | Nome da empresa (normalizado) | Removendo diferenças de maiúsculas, espaços e sufixos como LTDA ou ME. |
| 4 | Instagram Username | Utilizado principalmente para pequenos negócios sem site. |
| 5 | E-mail corporativo | Utilizado apenas quando o domínio representar claramente a empresa. |

Nenhum identificador isolado deverá ser considerado suficiente para todos os cenários.

Sempre que houver dúvida, deverá ser realizada validação manual antes da criação de um novo registro.

---

## 2. Regras de Deduplicação
<!-- Regras para fusão e identificação de duplicatas -->

## 3. Política de Nomenclatura
<!-- Padrões e convenções de nomes no CRM -->

## 4. Donos dos Dados (Data Ownership)
<!-- Definição de responsabilidade e propriedade sobre os dados -->

## 5. Qualidade dos Dados (Data Quality)
<!-- Diretrizes para manutenção e integridade dos dados -->

## 6. Campos Obrigatórios
<!-- Regras de obrigatoriedade por objeto/estágio -->

## 7. Regras de Atualização
<!-- Permissões e fluxos para edição de registros -->

## 8. Convenções para Integrações
<!-- Regras para dados recebidos via API, formulários e webhooks -->

## 9. Auditoria e Versionamento das Mudanças
<!-- Histórico e controle de alterações estruturais e críticas -->

---

# Company Object Governance Review

## Objetivo

Esta revisão tem como objetivo validar a arquitetura do objeto **Company** antes da implementação no HubSpot.

A análise busca garantir que cada propriedade criada possua uma finalidade clara e esteja posicionada no objeto correto dentro do CRM.

Os critérios utilizados são:

* evitar duplicidade de informações;
* garantir qualidade dos dados;
* separar responsabilidades entre objetos;
* facilitar automações futuras;
* manter escalabilidade da arquitetura.

---

## Separação de Responsabilidades dos Objetos

| Informação | Objeto correto | Motivo |
| --- | --- | --- |
| Nome da empresa | Company | Identificação da organização |
| Segmento da empresa | Company | Característica permanente |
| Interesse em soluções | Company | Preferência estratégica |
| Origem do lead | Company/Contact | Informação de aquisição |
| Responsável comercial | Company | Gestão de carteira |
| Produto adquirido | Deal | Evento comercial |
| Valor da venda | Deal | Transação financeira |
| Contrato | Deal | Relação comercial |
| Pagamento | Deal/Financeiro | Processo financeiro |
| Chamados | Ticket | Atendimento |
| Satisfação | Company/Contact | Relacionamento pós-venda |

---

## Revisão de Duplicidade

| Propriedades semelhantes | Decisão | Motivo |
| --- | --- | --- |
| Lifecycle Stage x Customer Status | Manter ambas | Possuem objetivos diferentes |
| Original Source x Acquisition Channel | Manter ambas | Uma é técnica e outra estratégica |
| Industry x Business Segment | Manter ambas | Uma é global e outra comercial |
| Number of Employees x Company Size Classification | Manter ambas | Uma é dado base e outra classificação derivada |
| Customer Potential x Commercial Priority | Manter ambas | Uma representa valor e outra ação interna |

---

## Propriedades Removidas do Modelo Inicial

| Propriedade | Motivo da remoção |
| --- | --- |
| Purchase History | Deve ser obtido através dos Deals |
| Products Purchased | Histórico pertence ao relacionamento comercial |
| Payment Status | Processo financeiro |
| Payment Method | Processo financeiro |
| Contract Value | Informação de negociação |
| Newsletter Subscription | Pertence ao Contact |
| Campaign History | Gerenciado pelo Marketing Hub |
| Annual Revenue | Baixa prioridade inicial |

---

## Padrão de Nomenclatura das Propriedades

As propriedades customizadas seguirão um padrão de nomenclatura consistente para facilitar manutenção, integração e governança.

### Regras:

* nomes devem ser escritos em inglês;
* evitar espaços em nomes internos;
* utilizar nomes descritivos;
* evitar abreviações;
* manter compatibilidade com APIs e integrações futuras.

### Exemplo:

- **Nome exibido:** Customer Health Score
- **Nome interno:** `customer_health_score`

---

## Classificação Final do Modelo Company

| Grupo | Quantidade de propriedades aprovadas |
| --- | --- |
| Contact Information | 11 |
| Perfil da Empresa | 5 |
| Informações Comerciais | 9 |
| Produtos e Serviços | 3 |
| Financeiro | 3 |
| Customer Success | 6 |
| Marketing | 8 |

> **Total do Modelo:** 45 propriedades aprovadas.

---

## Decisão Arquitetural Final

O objeto **Company** foi aprovado para implementação no HubSpot.

A arquitetura definida segue os seguintes princípios:

* utilizar propriedades nativas sempre que possível;
* criar propriedades customizadas somente quando houver necessidade de negócio;
* separar informações permanentes da empresa de informações transacionais;
* manter histórico comercial no objeto **Deal**;
* manter atendimento operacional no objeto **Ticket**;
* garantir possibilidade de automação, integração e geração de relatórios futuros.

O modelo está preparado para uma implementação escalável de CRM.

