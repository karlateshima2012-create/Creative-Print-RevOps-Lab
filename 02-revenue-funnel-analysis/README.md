<div align="center">

# Case 02 — Revenue Funnel Analysis

### SQL, métricas de receita e dashboard executivo

![SQL](https://img.shields.io/badge/SQL-Revenue%20Analytics-336791?style=flat-square&logo=postgresql&logoColor=white)
![Looker Studio](https://img.shields.io/badge/Looker%20Studio-Dashboard-4285F4?style=flat-square&logo=looker&logoColor=white)
![GA4](https://img.shields.io/badge/GA4-Acquisition-E37400?style=flat-square&logo=googleanalytics&logoColor=white)
![Status](https://img.shields.io/badge/status-planejado-64748B?style=flat-square)

</div>

## Visão do projeto

Neste case, vou construir uma análise completa de funil e receita a partir de um dataset SaaS simulado. O objetivo é demonstrar como transformo dados brutos em perguntas de negócio, consultas SQL, métricas confiáveis e recomendações executivas.

O uso de dados simulados será identificado em todos os artefatos. Não apresentarei os resultados como desempenho real da Creative Print.

## Problema de negócio

Uma operação de receita pode registrar leads, oportunidades, clientes e pagamentos sem conseguir responder perguntas básicas: onde o funil perde conversão, quanto tempo cada etapa leva, quais canais geram receita e onde surgem churn ou retenção.

## O que vou desenvolver

1. **Dataset**
   - modelo de leads, oportunidades, clientes, atividades e receita;
   - dicionário de dados;
   - regras de geração e identificação dos dados simulados.

2. **Data quality**
   - testes de nulos, duplicidades, chaves e formatos;
   - validação de datas, estágios e valores;
   - registro das correções realizadas.

3. **SQL aplicado ao negócio**
   - volume e conversão por etapa;
   - velocity e tempo de ciclo;
   - win rate e receita;
   - aquisição por canal;
   - retenção e churn.

4. **Métricas e visualização**
   - definição dos KPIs e fórmulas;
   - dashboard executivo;
   - leitura crítica dos resultados;
   - recomendações priorizadas.

## Entregáveis

| Entregável | O que demonstrará |
|---|---|
| Dataset SaaS simulado | Modelagem e preparação de dados para análise |
| Data Dictionary | Definições, tipos, chaves e regras de cada campo |
| Data Quality Report | Testes, inconsistências e correções |
| SQL Query Library | Consultas comentadas ligadas a perguntas de negócio |
| Metrics Dictionary | Fórmulas, granularidade e interpretação dos KPIs |
| **Executive Dashboard** | Visualização do funil, receita, retenção e churn |
| **Business Analytics Report** | Diagnóstico, achados, limitações e recomendações |

## Tecnologias planejadas

- **SQL:** consultas de funil, receita, retenção e churn;
- **HubSpot Reports:** comparação com a visão operacional do CRM;
- **Looker Studio:** construção do Executive Dashboard;
- **Google Analytics 4:** contexto de aquisição e comportamento;
- **Excel / Google Sheets:** validação e análise exploratória;
- **GitHub:** versionamento do dataset, queries e documentação.

## Perguntas que o projeto deverá responder

- Em quais etapas ocorre a maior perda de conversão?
- Qual é o tempo médio entre aquisição, oportunidade e fechamento?
- Quais canais geram volume e quais geram receita?
- Como win rate e ciclo de vendas variam entre segmentos?
- Quais sinais ajudam a explicar retenção e churn?
- Que ações devem ser priorizadas a partir dos dados?

## Estrutura

```text
02-revenue-funnel-analysis/
├── dataset/
├── data-quality/
├── sql/
├── metrics/
├── dashboard/
├── findings/
└── README.md
```

As pastas serão adicionadas quando seus primeiros artefatos existirem. Não uso arquivos vazios apenas para simular progresso.

## Competência demonstrável

Ao concluir este case, poderei apresentar uma análise de receita de ponta a ponta: qualidade da base, consultas SQL, definição de KPIs, dashboard e recomendações sustentadas pelos dados.

[← Voltar ao portfólio](../README.md)
