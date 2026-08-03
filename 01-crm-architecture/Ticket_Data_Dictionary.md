# Ticket Data Dictionary

## Objetivo

Este documento define todas as propriedades utilizadas pelo objeto **Ticket (Atendimento / Suporte ao Cliente)** no CRM da Creative Print.

Cada propriedade possui uma finalidade específica e foi definida para atender aos processos de Customer Success, atendimento ao cliente, pós-venda e resolução de chamados.

Nenhuma propriedade deverá ser criada diretamente no HubSpot sem estar previamente documentada neste Data Dictionary.

---

# Grupo 1 — Ticket Information

## Objetivo

O grupo Ticket Information reúne informações principais relacionadas às solicitações de atendimento registradas no CRM.

Essas propriedades representam o contexto do chamado, classificação, prioridade e responsabilidade pelo atendimento.

Este grupo não deve armazenar informações comerciais ou financeiras, pois essas informações pertencem ao objeto Deal.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| Ticket Name | Identificação | Sim | HubSpot |
| Ticket Owner | Responsável | Sim | HubSpot |
| Ticket Status | Processo atendimento | Sim | HubSpot |
| Pipeline | Processo atendimento | Sim | HubSpot |
| Ticket Priority | Classificação | Sim | HubSpot |
| Description | Contexto | Sim | HubSpot |
| Category | Classificação | Avaliar | HubSpot |
| Source | Origem atendimento | Avaliar | HubSpot |
| Create Date | Histórico | Não inicialmente | HubSpot |
| Close Date | Resolução | Avaliar | HubSpot |
