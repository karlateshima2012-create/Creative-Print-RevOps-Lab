# Architecture Decision Log — Creative Print

**Fase:** 10 — Decisões Arquiteturais
**Formato:** ADR simplificado (Decisão / Contexto / Justificativa / Alternativas consideradas)

---

## ADR-001 — HubSpot como fonte única da verdade

**Decisão:** o HubSpot será o sistema central de relacionamento comercial da Creative Print.
**Contexto:** dados hoje espalhados em WhatsApp, Instagram e planilhas soltas.
**Justificativa:** evita dados divergentes entre sistemas e cria um único ponto de verdade para relacionamento comercial.
**Alternativas consideradas:** manter planilhas centralizadas — descartada por não escalar nem suportar automação.

## ADR-002 — Empresa como objeto principal para clientes B2B

**Decisão:** Empresa é a entidade principal para representar clientes; Contato representa indivíduos vinculados a ela.
**Contexto:** maioria dos clientes é pequeno negócio (restaurante, clínica, academia) com múltiplos responsáveis.
**Justificativa:** facilita múltiplos contatos por cliente e evita duplicar dados comerciais (plano, MRR, status) em cada pessoa.
**Alternativas consideradas:** usar apenas Contato como entidade principal — descartada por gerar duplicação de dados comerciais quando há mais de um responsável por conta.

## ADR-003 — Produtos SaaS representados por propriedades + negócios, não por Objeto Personalizado

**Decisão:** CP Agenda e CP Review são representados via properties na Empresa e no Negócio, não como um Objeto Personalizado "Produto SaaS".
**Contexto:** estágio inicial da implantação, plano HubSpot inicial/gratuito.
**Justificativa:** compatível com as limitações do plano atual; menor complexidade de manutenção nesta fase.
**Alternativas consideradas:** criar Objeto Personalizado desde já — descartada por exigir plano pago (Enterprise) sem benefício imediato; fica registrada como evolução futura (ver Roadmap, Módulo 8+).

## ADR-004 — Prefixo `cp_` obrigatório em todas as properties customizadas

**Decisão:** toda property customizada usa nome interno `cp_` + snake_case.
**Contexto:** necessidade de diferenciar propriedades nativas do HubSpot das propriedades específicas da Creative Print.
**Justificativa:** padronização, facilita manutenção, buscas e onboarding de novos administradores do CRM.
**Alternativas consideradas:** nomes sem prefixo — descartada por gerar ambiguidade com propriedades padrão do HubSpot.

## ADR-005 — Pipeline comercial separado do pipeline de Customer Success

**Decisão:** `PIPE - Sales` e `PIPE - Customer Success` são pipelines distintos.
**Contexto:** processos de vendas e de retenção têm etapas, métricas e responsáveis diferentes.
**Justificativa:** evita misturar taxa de conversão comercial com taxa de retenção/expansão — métricas de RevOps exigem essa separação.
**Alternativas consideradas:** pipeline único do lead à renovação — descartada por dificultar leitura de funil e responsabilização por etapa.

## ADR-006 — Tickets modelados desde o Módulo 1, ativados apenas no Módulo 6

**Decisão:** a estrutura de Tickets é definida agora, mas não configurada tecnicamente no HubSpot ainda.
**Contexto:** Customer Success só entra em operação a partir do Módulo 6 do projeto.
**Justificativa:** evita retrabalho de modelagem quando o atendimento for de fato implementado.
**Alternativas consideradas:** deixar para desenhar no Módulo 6 — descartada porque geraria risco de inconsistência com o modelo de dados já definido para Empresa/Contato/Negócio.

## ADR-007 — Cliente com múltiplos produtos (CP Agenda + CP Review) permanece como uma única Empresa

**Decisão:** produto é tratado como atributo do relacionamento (`cp_product` no Negócio, `cp_product_interest` no Contato), não como Empresa separada.
**Contexto:** um mesmo cliente pode contratar mais de um produto SaaS da Creative Print.
**Justificativa:** evita duplicidade de conta e fragmentação de histórico comercial.
**Alternativas consideradas:** uma Empresa por produto contratado — descartada por fragmentar o relacionamento e dificultar visão 360º do cliente.

## ADR-008 — Moeda da conta HubSpot em BRL

**Decisão:** conta HubSpot configurada com moeda Real (BRL) e idioma português.
**Contexto:** operação e cobrança da Creative Print são realizadas no Brasil.
**Justificativa:** consistência de relatórios financeiros e usabilidade para o time local.
**Alternativas consideradas:** nenhuma — decisão direta pela operação local da empresa.
