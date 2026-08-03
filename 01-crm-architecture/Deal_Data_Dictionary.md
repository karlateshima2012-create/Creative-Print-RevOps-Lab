# Deal Data Dictionary

## Objetivo

Este documento define todas as propriedades utilizadas pelo objeto **Deal (Negócio / Oportunidade Comercial)** no CRM da Creative Print.

Cada propriedade possui uma finalidade específica e foi definida para atender aos processos comerciais, de vendas, previsão de receita (forecasting) e Revenue Operations.

Nenhuma propriedade deverá ser criada diretamente no HubSpot sem estar previamente documentada neste Data Dictionary.

---

# Grupo 1 — Deal Information

## Objetivo

O grupo Deal Information reúne informações principais relacionadas às oportunidades comerciais registradas no CRM.

Essas propriedades representam o ciclo de venda, identificação da oportunidade e relacionamento com empresas e contatos.

Este grupo deve armazenar informações sobre a oportunidade comercial, não informações permanentes da empresa ou da pessoa.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Deal Name | Identificação | Sim | HubSpot |
| Deal Owner | Responsabilidade comercial | Sim | HubSpot |
| Pipeline | Processo comercial | Sim | HubSpot |
| Deal Stage | Processo comercial | Sim | HubSpot |
| Amount | Receita | Sim | HubSpot |
| Close Date | Previsão comercial | Sim | HubSpot |
| Create Date | Histórico | Não | HubSpot |
| Deal Type | Classificação | Avaliar | HubSpot |
| Description | Informações adicionais | Não inicialmente | HubSpot |
| Priority | Classificação comercial | Avaliar | Customizada |
| Loss Reason | Análise comercial | Avaliar | Customizada |
| Lead Source | Origem oportunidade | Avaliar | Customizada |

---

## Decisões Arquiteturais

### DA-036 — Pipeline e Deal Stage são configurações comerciais

Pipeline e Deal Stage não serão tratados como propriedades customizadas.

Eles representam a estrutura do processo comercial e devem ser configurados no objeto Deal.

---

### DA-037 — Deal representa transações comerciais

Informações de valor, fechamento e responsabilidade pertencem ao Deal.

Dados permanentes da organização permanecem na Company.
