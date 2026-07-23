# Future State — Arquitetura Comercial

## Arquitetura Futura

### Mapa de Fluxo de Dados e Relacionamento

```mermaid
graph TD
    subgraph Aquisicao [Canais de Aquisição]
        Instagram[Instagram]
        WhatsApp[WhatsApp]
        Google[Google]
        Site[Site]
        Indicacao["Indicação"]
    end

    HubSpot[CRM HubSpot]
    Contato[Contato]
    Empresa[Empresa]
    Negocio["Negócio"]
    Cliente[Cliente]
    CS[Customer Success]
    Retencao["Renovação / Expansão"]

    Aquisicao --> HubSpot
    HubSpot --> Contato
    Contato --> Empresa
    Empresa --> Negocio
    Negocio --> Cliente
    Cliente --> CS
    CS --> Retencao
```

---

## Decisão Arquitetural

O HubSpot será considerado o **sistema central de relacionamento comercial**.

Os sistemas **CP Agenda** e **CP Review** continuarão responsáveis pela operação técnica dos produtos, enquanto o **HubSpot** será o único responsável por:

- **Aquisição**
- **Relacionamento**
- **Vendas**
- **Comunicação**
- **Segmentação**
- **Acompanhamento de Receita**
