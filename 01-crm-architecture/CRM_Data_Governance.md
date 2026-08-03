# CRM Data Governance

## 1. Entity Identification Strategy

O CRM da Creative Print deverá evitar a criação de registros duplicados.

Para isso, cada Empresa será identificada seguindo a seguinte ordem de prioridade:

| Prioridade | Identificador | Observação |
|------------|---------------|------------|
| 1 | CNPJ | Identificador oficial da empresa. |
| 2 | Domínio do site | Ex.: creativeprintjp.com |
| 3 | Nome da empresa (normalizado) | Removendo diferenças de maiúsculas, espaços e sufixos como LTDA ou ME. |
| 4 | Instagram comercial | Utilizado principalmente para pequenos negócios sem site. |
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
