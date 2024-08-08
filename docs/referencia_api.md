## Referência da API

Nossa API RESTful permite que você interaja com os recursos da sua loja virtual de forma programática, facilitando a integração com outros sistemas e a automação de tarefas.

### Autenticação

Todas as requisições à API exigem autenticação utilizando tokens de acesso gerados pelo Amazon Cognito. Você pode obter um token de acesso fazendo login na sua conta de usuário e utilizando o endpoint de autenticação do Cognito.

**Exemplo de cabeçalho de autenticação:**

```
Authorization: Bearer SEU_TOKEN_DE_ACESSO
```

### Endpoints

#### Gerenciamento de Produtos

* **`GET /produtos`:** Retorna uma lista de todos os produtos.
* **`GET /produtos/{id}`:** Retorna os detalhes de um produto específico.
* **`POST /produtos`:** Cria um novo produto.
* **`PUT /produtos/{id}`:** Atualiza os detalhes de um produto existente.
* **`DELETE /produtos/{id}`:** Exclui um produto.

#### Gerenciamento de Pedidos

* **`GET /pedidos`:** Retorna uma lista de todos os pedidos.
* **`GET /pedidos/{id}`:** Retorna os detalhes de um pedido específico.
* **`POST /pedidos`:** Cria um novo pedido.
* **`PUT /pedidos/{id}`:** Atualiza o status de um pedido existente.

#### Gerenciamento de Eventos

* **`POST /eventos`:** Cria um novo evento personalizado.

#### Importação de Notas Fiscais

* **`POST /notas_fiscais`:** Importa uma nota fiscal em formato XML.

### Exemplos de Requisição e Resposta

**Exemplo de requisição GET:**

```
GET /produtos/12345
```

**Exemplo de resposta GET:**

```json
{
  "id": "12345",
  "nome": "Camiseta Polo",
  "descricao": "Camiseta polo masculina, 100% algodão.",
  "preco": 49.90,
  "estoque": 50
}
```

**Exemplo de requisição POST:**

```
POST /produtos
Content-Type: application/json

{
  "nome": "Calça Jeans",
  "descricao": "Calça jeans feminina, corte reto.",
  "preco": 89.90,
  "estoque": 30
}
```

**Exemplo de resposta POST:**

```json
{
  "mensagem": "Produto criado com sucesso!",
  "id": "67890"
}
```

### Códigos de Status HTTP

* **200 OK:** A requisição foi bem-sucedida.
* **201 Created:** O recurso foi criado com sucesso.
* **400 Bad Request:** A requisição está malformada ou inválida.
* **401 Unauthorized:** A autenticação é necessária para acessar o recurso.
* **403 Forbidden:** Você não tem permissão para acessar o recurso.
* **404 Not Found:** O recurso não foi encontrado.
* **500 Internal Server Error:** Ocorreu um erro no servidor.

### Erros

Em caso de erro, a API retornará uma resposta JSON com o código de status HTTP correspondente e uma mensagem de erro descritiva.

**Exemplo de resposta de erro:**

```json
{
  "error": "Produto não encontrado"
}
```

### Limites de Taxa

A API possui limites de taxa para evitar o uso excessivo e garantir a disponibilidade para todos os usuários. Se você exceder os limites, receberá uma resposta com o código de status 429 Too Many Requests.

### Versionamento

A API está sujeita a alterações e melhorias. Para garantir a compatibilidade com seus sistemas, recomendamos que você utilize o versionamento da API. A versão atual da API é 1.0.

### Suporte

Se você tiver alguma dúvida ou precisar de ajuda, entre em contato com nossa equipe de suporte.
