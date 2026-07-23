# Data Model — Contatos & Propriedades

## Propriedades Padrão (HubSpot Standard Properties)

Estas são as propriedades nativas do HubSpot que serão adotadas no modelo de dados:

| Campo / Nome Interno | Uso / Descrição |
| :--- | :--- |
| **Nome** (*firstname* / *lastname*) | Identificação principal do contato comercial |
| **Email** (*email*) | Canal principal de comunicação digital e chave primária |
| **Telefone** (*phone* / *mobilephone*) | Contato direto via WhatsApp |
| **Cargo** (*jobtitle*) | Função do profissional na empresa (ex: Gerente, Proprietário) |
| **Empresa** (*associatedcompanyid*) | Associação e relacionamento com o objeto Empresa |

---

# Propriedades Customizadas

## Grupo: `Creative Print Information`

Para enriquecer nossa base de contatos, criaremos o grupo de propriedades **Creative Print Information** com as seguintes definições customizadas:

### 1. Lead Source
* **Tipo:** Dropdown (Seleção Única)
* **Valores:**
  - Instagram
  - WhatsApp
  - Website
  - Google
  - Indicação
  - Evento
  - Outro
* **Motivo:** Permite mensurar a eficácia de cada canal de aquisição na geração de novas oportunidades comerciais.

### 2. Customer Segment
* **Tipo:** Dropdown (Seleção Única)
* **Valores:**
  - Restaurante
  - Clínica
  - Academia
  - Fotógrafo
  - Loja
  - Serviços
  - Outro
* **Motivo:** Permite a segmentação futura de leads em campanhas de marketing direcionadas (e-mail, anúncios segmentados).

### 3. Product Interest
* **Tipo:** Multiple Checkbox (Seleção Múltipla)
* **Valores:**
  - NFC Products
  - CP Agenda
  - CP Review
  - CP Connect
  - 3D Printing
* **Motivo:** Uma pessoa pode demonstrar interesse em múltiplas soluções físicas e digitais simultaneamente.

### 4. Customer Status
* **Tipo:** Dropdown (Seleção Única)
* **Valores:**
  - Lead
  - Prospect
  - Customer
  - Inactive
* **Motivo:** Controla o estágio atual do ciclo de relacionamento com o cliente.
