# Sistema de Gestão Financeira - API

## Instalação

1. Clone este repositório ou baixe os arquivos
2. Instale as dependências:
```bash
npm install
```

3. Configure o arquivo .env na raiz do projeto:
```env
MONGODB_URI=mongodb://localhost/financas
JWT_SECRET=sua_chave_secreta_aqui
PORT=3000
```

4. Inicie o MongoDB localmente

5. Inicie a API:
```bash
npm start
```

## Rotas da API

### Autenticação
- POST /api/auth/register - Cadastro de usuário
  ```json
  {
    "nome": "Seu Nome",
    "email": "seu@email.com",
    "senha": "sua_senha",
    "salario": 5000
  }
  ```

- POST /api/auth/login - Login
  ```json
  {
    "email": "seu@email.com",
    "senha": "sua_senha"
  }
  ```

### Finanças (requer autenticação)
- POST /api/finances/despesas - Adicionar despesa
  ```json
  {
    "descricao": "Aluguel",
    "valor": 1500,
    "categoria": "Fixa",
    "dataVencimento": "2023-12-10"
  }
  ```

- GET /api/finances/despesas - Listar despesas
- GET /api/finances/balanco - Obter balanço financeiro

## Como usar

1. Primeiro faça o cadastro usando a rota /api/auth/register
2. Faça login usando /api/auth/login
3. Use o token retornado no login em todas as outras requisições no header:
   ```
   Authorization: Bearer seu_token_aqui
   ```

## Testando a API

Você pode usar o Postman ou Insomnia para testar as rotas. Importe a coleção abaixo:

```json
{
  "info": {
    "_postman_id": "seu-id",
    "name": "Sistema Financeiro",
    "schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json"
  },
  "item": [
    {
      "name": "Auth",
      "item": [
        {
          "name": "Register",
          "request": {
            "method": "POST",
            "header": [],
            "url": {
              "raw": "http://localhost:3000/api/auth/register",
              "protocol": "http",
              "host": ["localhost"],
              "port": "3000",
              "path": ["api", "auth", "register"]
            }
          }
        },
        {
          "name": "Login",
          "request": {
            "method": "POST",
            "header": [],
            "url": {
              "raw": "http://localhost:3000/api/auth/login",
              "protocol": "http",
              "host": ["localhost"],
              "port": "3000",
              "path": ["api", "auth", "login"]
            }
          }
        }
      ]
    }
  ]
}
```