# 🌍 API de Tradução Universal (Express.js)

Esta é uma API robusta desenvolvida em **Node.js** com o framework **Express.js** que atua como um middleware inteligente para o serviço de tradução **MyMemory**. O projeto foi desenhado seguindo as melhores práticas de arquitetura modular (MVC) e tratamento de erros.

## 🚀 Funcionalidades
- Tradução de textos entre mais de 140 idiomas.
- Arquitetura baseada em **Services** e **Controllers**.
- Validação de entrada de dados (Prevenção de erros).
- Tratamento de erros HTTP customizado (ex: erro 502 para falhas externas).

---

## 📁 Estrutura de Pastas e Arquivos

```text
api-traducao/
├── src/
│   ├── config/           # Configurações globais (variáveis de ambiente)
│   ├── controllers/      # Gerencia as requisições e envia as respostas
│   │   └── translate.controller.js
│   ├── routes/           # Define os caminhos (endpoints) da API
│   │   └── translate.route.js
│   ├── services/         # Lógica de integração com a API externa (Axios)
│   │   └── translation.service.js
│   └── server.js         # Inicialização do servidor Express
├── .env                  # Porta do servidor e configurações sensíveis
├── package.json          # Manifesto do projeto e dependências
└── README.md             # Documentação técnica
```

---

## Detalhes das Camadas:

- >**src/server.js:** O ponto de entrada da aplicação. Configura middlewares como CORS e express.json().

- >**src/routes/:** Camada que define os caminhos. Mantém o código limpo ao separar as URLs da lógica de execução.

- >**src/controllers/:** Onde as regras de negócio de entrada são aplicadas. Verifica se os dados enviados pelo usuário são válidos.

- >**src/services/:** Camada isolada para comunicação com APIs de terceiros. Garante que a aplicação seja fácil de manter.

---

**1. ⚙️ Instalação e Execução**
Instalar dependências:
```bash
npm install
```
**2. Configurar o ambiente:**
Crie um ficheiro .env na raiz com:
```bash
Snippet de códigoPORT=3000
```
**3. Executar o servidor:**
```bash
# Para desenvolvimento (reinicio automático)
npm run dev

# Para produção
node src/server.js
```
---

## 🛣️ Documentação da Rota

**Traduzir Texto**

**Endpoint:** *POST /translate*

**Content-Type:** *application/json*

**Corpo da Requisição:**


| Campo | Tipo | Obrigatório | Descrição |
| :--- | :--- | :--- | :--- |
| `text` | String | **Sim** | O conteúdo a ser traduzido (Máximo de 500 caracteres). |
| `to` | String | **Sim** | Código do idioma de destino (ex: `en`, `es`, `fr`). |
| `from` | String | Não | Código do idioma de origem (Padrão: `pt`). |
 

**Exemplo de Request:**

```json
{
  "text": "Estou desenvolvendo uma API de tradução",
  "from": "pt",
  "to": "en"
}
```

**Exemplo de Response (Sucesso):**

```json
{
  "status": "success",
  "data": {
    "original": "Estou desenvolvendo uma API de tradução",
    "translated": "I am developing a translation API",
    "source_lang": "pt",
    "target_lang": "en"
  }
}
```
---

 ### 🌍 Tabela de Idiomas Suportados (ISO 639-1)

Utilize os códigos abaixo para os campos `from` e `to` na sua requisição:

| Idioma | Código | Idioma | Código |
| :--- | :--- | :--- | :--- |
| **Português** | `pt` | **Inglês** | `en` |
| **Espanhol** | `es` | **Francês** | `fr` |
| **Alemão** | `de` | **Italiano** | `it` |
| **Chinês** | `zh` | **Japonês** | `ja` |
| **Russo** | `ru` | **Árabe** | `ar` |

---

## ⚠️ Limites e Observações
**Cota Gratuita:** O serviço MyMemory permite até 1.000 palavras por dia no modo anônimo.

**Tamanho do Texto:** O sistema foi validado para frases curtas (máx. 500 caracteres).

**Status 502:** Se a API externa falhar, retornamos o status 502 Bad Gateway, indicando que o erro não é do nosso código, mas da dependência externa.

**CORS:** A API está preparada para ser consumida por qualquer Frontend (Web ou Mobile).

---

## 👨‍💻 Autor
**Moisés Hoque**
*Software Developer & Entrepreneur*

---
