
# Projeto Backend - API para Perguntas e Respostas com IA - NLW-Agents - RocketSeat

## Visão Geral

Este backend é uma **API RESTful** construída com **Fastify** e **TypeScript**, integrada com banco de dados **PostgreSQL** e **Drizzle ORM**. Ela foi projetada para receber perguntas, gerar respostas utilizando o modelo de IA **Gemini da Google** e gerenciar dados de salas, perguntas e *chunks* de áudio.

-----

## Tecnologias Utilizadas

  * **Node.js 18+** com TypeScript
  * **Fastify**: Como *framework* HTTP rápido e extensível.
  * **Drizzle ORM**: Para acesso e migração do banco PostgreSQL.
  * **PostgreSQL**: Para armazenamento relacional.
  * **Google Gemini AI**: Para geração de respostas e *embeddings*.
  * **Zod**: Para validação de *schemas* e tipos.
  * **dotenv**: Para gestão de variáveis de ambiente.
  * **Drizzle Seed**: Para populamento inicial do banco.

-----

## Estrutura do Projeto

```
/src
├── /db         # Configuração do banco, schemas e seeders
├── /routes     # Rotas REST organizadas por domínio (salas, perguntas)
├── /services   # Serviços externos (ex: Gemini AI)
├── /plugins    # Plugins Fastify customizados
├── /types      # Tipos TypeScript compartilhados
├── app.ts      # Inicialização do servidor Fastify
└── server.ts   # Entrypoint principal
```

-----

## Como Rodar Localmente

### Pré-requisitos

  * Node.js 18+
  * PostgreSQL rodando e acessível
  * Configurar arquivo `.env` com variáveis:
      * `DATABASE_URL`
      * `GEMINI_API_KEY`

### Passos

1.  **Clone o repositório:**

    ```bash
    git clone <URL_DO_REPOSITORIO_BACKEND>
    cd backend
    ```

2.  **Instale as dependências:**

    ```bash
    npm install
    ```

3.  **Configure o banco de dados** (migrações):

    ```bash
    npx drizzle-kit push
    ```

4.  **Popule o banco** com dados iniciais:

    ```bash
    npm run db:seed
    ```

5.  **Inicie o servidor:**

    ```bash
    npm run dev
    ```

A API estará disponível em `http://localhost:3333`.

-----

## Endpoints Principais

  * `POST /rooms/:roomId/questions`: Cria nova pergunta, gera *embeddings*, consulta *chunks* relevantes e gera resposta com IA.
  * `GET /rooms/:roomId/questions`: Lista perguntas e respostas da sala.
  * `POST /rooms`: Cria nova sala.
  * Outros *endpoints* conforme necessidade (listar salas, etc.).

-----

## Segurança e Boas Práticas

  * Validação rigorosa de entrada com **Zod**.
  * Tratamento robusto de erros com respostas apropriadas.
  * Uso de `async/await` para operações assíncronas claras.
  * Cache e otimizações podem ser implementados para performance.
  * Logs detalhados para monitoramento.

-----

## Testes

Ainda em desenvolvimento, recomenda-se criar testes unitários com **Jest** e integração com **supertest**.

-----

## Deploy

*Deploy* em servidores Node.js ou contêineres Docker, considerando variáveis de ambiente e segurança da API *key* da Gemini.

-----

## Contato

Para suporte e contribuições, favor abrir *issue* ou *pull request*.