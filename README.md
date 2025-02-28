# API de Cálculo de BTUs para Ar-Condicionado

## Visão Geral
Esta API permite:
- Registro de usuários
- Login para autenticação
- Cálculo de BTUs necessários para climatização de ambientes

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

### 3. Cálculo de BTUs
**POST** `/calculate-btus`

- **Descrição**: Calcula a quantidade de BTUs necessária para climatização de um ambiente.
- **Autenticação:** Token JWT necessário no cabeçalho.
- **Headers:**
  ```json
  {
    "Authorization": "Bearer <seu-token-jwt>"
  }
  ```

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

### 3. Cálculo de BTUs
- **Falta de autenticação:**
  ```json
  {
    "error": "Token de autenticação não fornecido."
  }
  ```
- **Payload inválido:**
  ```json
  {
    "error": "Os campos 'room_area', 'number_of_people' e 'sun_exposure' são obrigatórios."
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

## Testes
Para executar testes unitários:
```bash
npm test
