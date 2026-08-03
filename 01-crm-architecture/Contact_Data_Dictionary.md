# Contact Data Dictionary

## Objetivo

Este documento define todas as propriedades utilizadas pelo objeto **Contact (Contato)** no CRM da Creative Print.

Cada propriedade possui uma finalidade específica e foi definida para atender aos processos comerciais, de marketing, atendimento e Revenue Operations.

Nenhuma propriedade deverá ser criada diretamente no HubSpot sem estar previamente documentada neste Data Dictionary.

---

# Grupo 1 — Contact Information

## Objetivo

O grupo Contact Information reúne as informações de identificação e contato das pessoas relacionadas às empresas cadastradas no CRM.

Essas propriedades têm como objetivo apoiar:

* identificação única do contato;
* comunicação comercial;
* segmentação;
* automações;
* integrações.

Este grupo deve armazenar apenas informações pertencentes à pessoa, evitando duplicidade com o objeto Company.

---

## Propriedades Candidatas

| Propriedade | Categoria | Necessária? | Origem |
| --- | --- | --- | --- |
| First Name | Identificação | Sim | HubSpot |
| Last Name | Identificação | Sim | HubSpot |
| Email | Contato | Sim | HubSpot |
| Phone Number | Contato | Sim | HubSpot |
| Mobile Phone Number | Contato | Sim | HubSpot |
| Job Title | Profissional | Sim | HubSpot |
