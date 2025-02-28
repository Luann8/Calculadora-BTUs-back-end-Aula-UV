# API de Cálculo de Média

## Visão Geral
Esta API permite:
- Registro de usuários
- Login para autenticação
- Cálculo de médias aritméticas para números enviados via payload

## Endpoints

### 1. Registro de Usuário
**POST** `/register`

- **Descrição**: Cria um novo usuário no sistema.
- **Payload:**
  ```json
  {
    "name": "Seu Nome",
    "email": "seuemail@example.com",
    "password": "suaSenha"
  }
  ```
- **Exemplo de Resposta:**
  ```json
  {
    "message": "Usuário registrado com sucesso!"
  }
  ```

### 2. Login
**POST** `/login`

- **Descrição**: Autentica o usuário e retorna um token JWT.
- **Payload:**
  ```json
  {
    "email": "seuemail@example.com",
    "password": "suaSenha"
  }
  ```
- **Exemplo de Resposta:**
  ```json
  {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
  }
  ```

### 3. Cálculo de Média
**POST** `/calculate-average`

- **Descrição**: Calcula a média de uma lista de números enviados.
- **Autenticação:** Token JWT necessário no cabeçalho.
- **Headers:**
  ```json
  {
    "Authorization": "Bearer <seu-token-jwt>"
  }
  ```
- **Payload:**
  ```json
  {
    "numbers": [10, 20, 30, 40]
  }
  ```
- **Exemplo de Resposta:**
  ```json
  {
    "average": 25
  }
  ```

## Erros Comuns

### 1. Registro de Usuário
- **E-mail já cadastrado:**
  ```json
  {
    "error": "E-mail já está em uso."
  }
  ```

### 2. Login
- **Credenciais inválidas:**
  ```json
  {
    "error": "E-mail ou senha inválidos."
  }
  ```

### 3. Cálculo de Média
- **Falta de autenticação:**
  ```json
  {
    "error": "Token de autenticação não fornecido."
  }
  ```
- **Payload inválido:**
  ```json
  {
    "error": "A lista de números é obrigatória."
  }
  ```

## Ambiente
- **Node.js:** Versão mínima 14+
- **Framework:** AdonisJS

## Configuração
1. Clone o repositório:
   ```bash
   git clone <URL_DO_REPOSITORIO>
   ```
2. Instale as dependências:
   ```bash
   npm install
   ```
3. Configure o arquivo `.env` com suas credenciais de banco de dados.
4. Inicie o servidor:
   ```bash
   npm start
   ```
