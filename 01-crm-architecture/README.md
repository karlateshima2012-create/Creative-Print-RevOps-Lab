# 01-crm-architecture — Arquitetura de CRM & Governança

Bem-vindo à pasta de **Arquitetura de CRM & Governança da Creative Print**. Esta pasta centraliza toda a documentação conceitual, modelagem de dados e decisões estratégicas desenvolvidas durante o **Módulo 1 — CRM Architecture**.

---

## 1. Objetivo do Laboratório

Projetar a arquitetura completa de um CRM profissional utilizando o HubSpot como plataforma de referência, estabelecendo uma base sólida, padronizada e governada para futuras implementações de automação, relatórios e processos de Revenue Operations (RevOps).

Os objetivos específicos incluem:
* Definir a estratégia do CRM para os produtos SaaS (CP Agenda, CP Review) e físicos (NFC / 3D);
* Estruturar o modelo de dados e dicionários dos 4 objetos centrais (`Company`, `Contact`, `Deal`, `Ticket`);
* Estabelecer regras rigorosas de governança, qualidade de dados e nomenclatura;
* Projetar as arquiteturas de automação e relatórios executivos;
* Elaborar o plano sequencial de implementação do CRM.

---

## 2. Estrutura

A documentação desta pasta é dividida em 5 pilares fundamentais:

```text
01-crm-architecture/
├── 1. Estratégia & Diagnóstico   (Business Discovery, Current State, Future State, CRM Architecture)
├── 2. Modelagem & Dicionários   (Company Spec, Company/Contact/Deal/Ticket Data Dictionaries, Data Model)
├── 3. Objetos & Relacionamentos (CRM Object Model, Associations Model, System Mapping)
├── 4. Processos & Governança    (Process Design, Data Governance, Quality Framework, Naming, ADRs)
└── 5. Planejamento & Relatórios (Automation Arch, Reporting Arch, Implementation Plan, Closure Report)
```

---

## 3. Documentos (22 Arquivos)

| # | Documento | Pilar / Área | Descrição |
| --- | --- | --- | --- |
| 1 | [CRM_Architecture.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/CRM_Architecture.md) | Estratégia Mestre | Documento executivo e índice mestre da arquitetura CRM. |
| 2 | [Business_Discovery.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/Business_Discovery.md) | Estratégia | Diagnóstico do modelo de negócio, frentes e stakeholders da Creative Print. |
| 3 | [Current_State.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/Current_State.md) | Estratégia | Diagnóstico *As Is* da operação comercial e problemas identificados. |
| 4 | [Future_State.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/Future_State.md) | Estratégia | Visão de futuro *To Be* e resultados esperados do CRM. |
| 5 | [Company_Object_Specification.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/Company_Object_Specification.md) | Modelagem | Especificação detalhada do objeto Company como entidade soberana. |
| 6 | [Company_Data_Dictionary.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/Company_Data_Dictionary.md) | Dicionário de Dados | Dicionário completo de propriedades aprovadas para o objeto Company (8 grupos). |
| 7 | [Contact_Data_Dictionary.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/Contact_Data_Dictionary.md) | Dicionário de Dados | Dicionário de propriedades para o objeto Contact (nativas vs customizadas). |
| 8 | [Deal_Data_Dictionary.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/Deal_Data_Dictionary.md) | Dicionário de Dados | Dicionário de propriedades para o objeto Deal (receita, ciclo de vida e atividades). |
| 9 | [Ticket_Data_Dictionary.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/Ticket_Data_Dictionary.md) | Dicionário de Dados | Dicionário de propriedades para o objeto Ticket (suporte e Customer Success). |
| 10 | [Data_Model.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/Data_Model.md) | Modelagem | Visão geral da estrutura de dados e propriedades do CRM. |
| 11 | [CRM_Object_Model.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/CRM_Object_Model.md) | Objetos | Definição do papel dos 4 objetos centrais e hierarquia visual de relacionamentos. |
| 12 | [CRM_Associations_Model.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/CRM_Associations_Model.md) | Objetos | Regras de associação (`1:N` e `N:N`) entre empresas, contatos, negócios e tickets. |
| 13 | [System_Mapping.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/System_Mapping.md) | Objetos | Mapeamento do ecossistema de sistemas e integrações do CRM. |
| 14 | [Process_Design.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/Process_Design.md) | Governança & Processos | Desenho dos fluxos operacionais de vendas, onboarding e suporte. |
| 15 | [CRM_Data_Governance.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/CRM_Data_Governance.md) | Governança & Processos | Regras de ownership de dados, responsabilidade por objeto e controle de mudanças. |
| 16 | [CRM_Data_Quality_Framework.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/CRM_Data_Quality_Framework.md) | Governança & Processos | 4 dimensões de qualidade de dados (Completude, Precisão, Consistência, Atualização). |
| 17 | [Naming_Convention.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/Naming_Convention.md) | Governança & Processos | Convenção oficial de nomenclatura de propriedades, dropdowns e arquivos. |
| 18 | [Architecture_Decisions.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/Architecture_Decisions.md) | Governança & Processos | Registro e índice categorizado de 87 Decisões Arquiteturais (DAs). |
| 19 | [CRM_Automation_Architecture.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/CRM_Automation_Architecture.md) | Planejamento | Princípios de automação orientada por eventos e roadmap em 3 fases. |
| 20 | [CRM_Reporting_Architecture.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/CRM_Reporting_Architecture.md) | Planejamento | Especificação de 8 KPIs essenciais, fontes de dados e 3 dashboards executivos. |
| 21 | [HubSpot_Implementation_Plan.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/HubSpot_Implementation_Plan.md) | Planejamento | Plano de implementação sequencial em 7 fases para configuração do HubSpot. |
| 22 | [LAB-01_Project_Closure_report.md](file:///Users/karlateshima/Developer/Portifolio/Creative-Print-Revops-Lab/01-crm-architecture/LAB-01_Project_Closure_report.md) | Encerramento | Relatório final de encerramento do Módulo 1 e limitações do escopo. |

---

## 4. Ordem Recomendada de Leitura

Para compreender a arquitetura do projeto de forma sequencial e lógica, recomenda-se a seguinte ordem de leitura:

```text
1. Visão Executiva & Contexto:
   └── CRM_Architecture.md ──► Business_Discovery.md ──► Current_State.md ──► Future_State.md

2. Arquitetura de Objetos & Relacionamentos:
   └── CRM_Object_Model.md ──► CRM_Associations_Model.md ──► System_Mapping.md

3. Dicionários de Dados & Especificações:
   └── Company_Object_Specification.md ──► Company_Data_Dictionary.md ──► Contact_Data_Dictionary.md 
       ──► Deal_Data_Dictionary.md ──► Ticket_Data_Dictionary.md ──► Data_Model.md

4. Governança, Qualidade & Padrões:
   └── CRM_Data_Governance.md ──► CRM_Data_Quality_Framework.md ──► Naming_Convention.md 
       ──► Architecture_Decisions.md ──► Process_Design.md

5. Planejamento Futuro & Encerramento:
   └── CRM_Automation_Architecture.md ──► CRM_Reporting_Architecture.md ──► HubSpot_Implementation_Plan.md 
       ──► LAB-01_Project_Closure_report.md
```

---

## 5. Entregáveis Produzidos

* **22 Documentos de Arquitetura em Markdown** cobrindo estratégia, modelagem, dicionários, governança, automações e relatórios.
* **87 Decisões Arquiteturais (DAs)** registradas e categorizadas no ADR Log.
* **Modelo de Dados Unificado** contemplando os objetos `Company`, `Contact`, `Deal` e `Ticket`.
* **Framework de Governança de Dados** com política de nomes (`cp_`), papéis por objeto e métricas de qualidade.
* **Plano de Implementação em 7 Fases** para guiar a configuração funcional do HubSpot.

---

## 6. Resultado do Laboratório

A pasta `01-crm-architecture/` entrega uma arquitetura conceitual de CRM completa, robusta e escalável para a Creative Print. 

O resultado garante que o HubSpot seja configurado sob critérios rígidos de governança de dados, eliminando suposições, retrabalho e duplicidades antes do início da configuração prática e da implementação de automações no ambiente produtivo.
