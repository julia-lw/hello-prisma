# API Endpoints

Base URL:

`http://localhost:3000`

## 1. Buscar post por ID

**GET** `/post/:id`

Busca um post específico pelo seu ID.

### Exemplo

```http
GET http://localhost:3000/post/1
```

### Resposta esperada

```json
{
  "id": 1,
  "title": "Meu primeiro post",
  "content": "Olá, Prisma!",
  "published": false,
  "authorId": 1
}
```

Se o post não existir, a API retorna **404 Not Found**.

---

## 2. Listar posts publicados

**GET** `/feed`

Retorna todos os posts que estão publicados.

### Exemplo

```http
GET http://localhost:3000/feed
```

### Resposta esperada

```json
[
  {
    "id": 1,
    "title": "Meu primeiro post",
    "content": "Olá, Prisma!",
    "published": true,
    "authorId": 1
  }
]
```

---

## 3. Filtrar posts

**GET** `/filtered-posts/:searchString`

Pesquisa posts cujo título ou conteúdo contém o texto informado.

### Exemplo

```http
GET http://localhost:3000/filtered-posts/prisma
```

### Resposta esperada

```json
[
  {
    "id": 1,
    "title": "Meu primeiro post com Prisma",
    "content": "Aprendendo NestJS e Prisma",
    "published": false,
    "authorId": 1
  }
]
```

---

## 4. Criar um post

**POST** `/post`

Cria um novo post associado a um usuário existente através do e-mail do autor.

### Body

```json
{
  "title": "Meu primeiro post",
  "content": "Olá, Prisma!",
  "authorEmail": "daniel@example.com"
}
```

### Exemplo

```http
POST http://localhost:3000/post
Content-Type: application/json
```

### Resposta esperada

```json
{
  "id": 1,
  "title": "Meu primeiro post",
  "content": "Olá, Prisma!",
  "published": false,
  "authorId": 1
}
```

---

## 5. Criar usuário

**POST** `/user`

Cria um novo usuário.

### Body

```json
{
  "email": "daniel@example.com",
  "name": "Daniel"
}
```

### Exemplo

```http
POST http://localhost:3000/user
Content-Type: application/json
```

### Resposta esperada

```json
{
  "id": 1,
  "email": "daniel@example.com",
  "name": "Daniel"
}
```

---

## 6. Publicar post

**PUT** `/publish/:id`

Altera o post para `published: true`.

### Exemplo

```http
PUT http://localhost:3000/publish/1
```

### Resposta esperada

```json
{
  "id": 1,
  "title": "Meu primeiro post",
  "content": "Olá, Prisma!",
  "published": true,
  "authorId": 1
}
```

---

## 7. Excluir post

**DELETE** `/post/:id`

Exclui um post pelo ID.

### Exemplo

```http
DELETE http://localhost:3000/post/1
```

### Resposta esperada

```json
{
  "id": 1,
  "title": "Meu primeiro post",
  "content": "Olá, Prisma!",
  "published": false,
  "authorId": 1
}
```

---

# Resumo

| Método | Endpoint | Descrição |
|---|---|---|
| GET | `/post/:id` | Buscar post por ID |
| GET | `/feed` | Listar posts publicados |
| GET | `/filtered-posts/:searchString` | Filtrar posts |
| POST | `/post` | Criar post |
| POST | `/user` | Criar usuário |
| PUT | `/publish/:id` | Publicar post |
| DELETE | `/post/:id` | Excluir post |

## Fluxo básico de teste

1. Criar um usuário com `POST /user`.
2. Criar um post com `POST /post`, usando o e-mail do usuário.
3. Consultar o post com `GET /post/:id`.
4. Publicar o post com `PUT /publish/:id`.
5. Consultar os posts publicados com `GET /feed`.
6. Pesquisar posts com `GET /filtered-posts/:searchString`.
7. Excluir o post com `DELETE /post/:id`.
