<div align="center">

# Case 01 — CRM Implementation & Data Quality

### Auditoria, correção, importação e validação de dados reais no HubSpot

![HubSpot](https://img.shields.io/badge/HubSpot-CRM-FF7A59?style=flat-square&logo=hubspot&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-Data%20Quality-217346?style=flat-square&logo=microsoftexcel&logoColor=white)
![Status](https://img.shields.io/badge/status-em%20desenvolvimento-F59E0B?style=flat-square)

</div>

## Visão do projeto

Neste case, trabalho com a operação real da Creative Print para transformar registros dispersos em uma base confiável, padronizada e utilizável no HubSpot.

Meu foco é demonstrar o processo completo de qualidade e migração de dados: entender o negócio, auditar a base, definir regras, mapear campos, corrigir inconsistências, importar e validar os registros sem perder rastreabilidade.

## Problema de negócio

A Creative Print possui clientes e relacionamentos reais, mas as informações foram construídas ao longo da operação sem uma estrutura única de CRM. Isso cria riscos de duplicidade, campos incompletos, associações incorretas e baixa confiabilidade para vendas, marketing e atendimento.

## O que vou desenvolver

1. **Discovery e requisitos**
   - contexto do negócio e objetivos do CRM;
   - diagnóstico do estado atual;
   - definição do estado futuro e critérios de sucesso.

2. **Auditoria e qualidade**
   - inventário e profiling da base;
   - análise de duplicidade, completude, validade e consistência;
   - regras de padronização e deduplicação;
   - plano de correção priorizado.

3. **Field mapping**
   - mapeamento entre origem e destino;
   - revisão dos objetos Company, Contact, Deal e Ticket;
   - propriedades, tipos de campo e regras de preenchimento;
   - associações e identificadores únicos.

4. **Configuração do HubSpot**
   - revisão de propriedades e pipelines;
   - validação das configurações de Deal e Ticket;
   - preparação dos templates de importação.

5. **Importação e validação**
   - execução controlada da importação;
   - verificação das associações;
   - reconciliação entre origem e HubSpot;
   - registro de erros, correções e reprocessamentos.

## Entregáveis

| Entregável | Finalidade | Estado |
|---|---|---|
| Business Discovery e Current/Future State | Traduzir o problema operacional em requisitos de CRM | Disponível |
| Data dictionaries | Definir propriedades, formatos e regras dos quatro objetos | Disponível |
| Governance e Data Quality Framework | Estabelecer padrões de criação, manutenção e controle | Disponível |
| Field Mapping Workbook | Relacionar campos de origem e destino | Em revisão |
| Data Audit Report | Medir completude, validade, consistência e duplicidade | A desenvolver |
| Data Cleaning Plan | Priorizar correções antes da importação | A desenvolver |
| Import Templates | Padronizar Company, Contact e Deal | Disponível |
| Import & Validation Report | Comprovar volume processado, erros e reconciliação | A desenvolver |
| Error & Correction Log | Preservar rastreabilidade das decisões | A desenvolver |
| Evidence Pack | Reunir capturas e validações relevantes do HubSpot | Em desenvolvimento |

## Tecnologias e técnicas

- **HubSpot CRM:** objetos, propriedades, associações, pipelines e importação;
- **Excel / Google Sheets:** profiling, limpeza, deduplicação, mapping e reconciliação;
- **CSV / XLSX:** preparação e controle dos arquivos de carga;
- **GitHub:** versionamento da documentação, artefatos e evidências;
- **Data hygiene:** completude, unicidade, validade, consistência e padronização.

## Evidências que encerrarão o case

O projeto só será considerado concluído quando eu conseguir demonstrar:

- base auditada com critérios documentados;
- correções executadas e justificadas;
- importação concluída sem perda silenciosa de registros;
- associações verificadas no HubSpot;
- comparação entre dados de origem e destino;
- erros e reprocessamentos registrados;
- limitações e próximos passos explicitados.

## Estrutura

```text
01-crm-implementation-data-quality/
├── discovery-and-requirements/
├── data-audit/
├── field-mapping/
├── hubspot-configuration/
├── import-and-validation/
├── evidence/
└── README.md
```

## Competência demonstrável

Ao concluir este case, poderei explicar tecnicamente como auditei uma base real, defini regras de qualidade, preparei uma migração e validei dados no HubSpot mantendo integridade e rastreabilidade.

[← Voltar ao portfólio](../README.md)
