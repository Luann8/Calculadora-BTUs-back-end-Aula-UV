# AdonisJS API - Autenticação e Cálculo de Média

Este projeto é uma API desenvolvida com [AdonisJS](https://adonisjs.com/), que inclui autenticação JWT e cálculo de média de números. Ele protege rotas usando middleware de autenticação.

## Recursos Principais

- Registro de usuários.
- Login com autenticação JWT.
- Rota protegida para cálculo de média.

## Pré-requisitos

- Node.js
- AdonisJS CLI
- Banco de dados configurado (SQLite, MySQL, etc.)

## Instalação

1. Clone o repositório:
   ```bash
   git clone <URL_DO_REPOSITORIO>
   ```

2. Instale as dependências:
   ```bash
   npm install
   ```

3. Configure o ambiente:
   - Renomeie o arquivo `.env.example` para `.env`.
   - Edite o arquivo `.env` com suas configurações de banco de dados e chave JWT:
     ```env
     APP_KEY=uma_chave_aleatoria
     DB_CONNECTION=sqlite
     JWT_SECRET=uma_chave_secreta_para_jwt
     ```

4. Execute as migrações:
   ```bash
   adonis migration:run
   ```

## Uso

### 1. Registrar um Usuário

Endpoint: `POST /register`

- **Corpo da requisição:**
  ```json
  {
    "username": "usuario_exemplo",
    "email": "usuario@example.com",
    "password": "senha123"
  }
  ```

- **Resposta:**
  ```json
  {
    "message": "Usuário registrado com sucesso!",
    "user": {
      "id": 1,
      "email": "usuario@example.com",
      "username": "usuario_exemplo"
    }
  }
  ```

### 2. Fazer Login

Endpoint: `POST /login`

- **Corpo da requisição:**
  ```json
  {
    "email": "usuario@example.com",
    "password": "senha123"
  }
  ```

- **Resposta:**
  ```json
  {
    "message": "Login realizado com sucesso!",
    "token": "SEU_TOKEN_JWT",
    "user": {
      "id": 1,
      "email": "usuario@example.com",
      "username": "usuario_exemplo"
    }
  }
  ```

### 3. Calcular Média (Rota Protegida)

Endpoint: `POST /calculate-average`

- **Cabeçalho da requisição:**
  ```json
  {
    "Authorization": "Bearer SEU_TOKEN_JWT"
  }
  ```

- **Corpo da requisição:**
  ```json
  {
    "numbers": [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
  }
  ```

- **Resposta:**
  ```json
  {
    "message": "A média foi calculada com sucesso!",
    "average": 55
  }
  ```

## Scripts Disponíveis

- **Iniciar o servidor:**
  ```bash
  adonis serve --dev
  ```

- **Rodar migrações:**
  ```bash
  adonis migration:run
  ```

## Estrutura de Pastas

- **Controllers:**
  - `AuthController` - Gerencia login e registro de usuários.
  - `CalculateAverageController` - Gerencia a lógica de cálculo de média.

- **Rotas:**
  - Definidas em `start/routes.js`.

## Notas Adicionais

Certifique-se de incluir o token JWT no cabeçalho `Authorization` para acessar rotas protegidas. Caso contrário, a API retornará erro 401.
