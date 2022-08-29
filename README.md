# JSON-SERVER PROJETO FRONTEND M3

## Rotas que não precisam de autenticacão

<br>

### **Cadastrar usuário**

<br>

POST /register

Corpo da mensagem

```javascript
{
	"email": string,
	"password": string,
	"phone": string,
	"avatar": string,
	"social_network": string
}
```

Resposta

```javascript
{
	"accessToken": string,
	"user": {
		"email": string,
	    "phone": string,
	    "avatar": string,
	    "social_network": string,
        "id": number
	}
}
```

<br>

### **Login**

<br>

POST /login

Corpo da mensagem

```javascript
{
	"email": string,
	"password": string,
}
```

Resposta

```javascript
{
	"accessToken": string,
	"user": {
		"email": string,
	    "phone": string,
	    "avatar": string,
	    "social_network": string,
        "id": number
	}
}
```

<br>

### **Listar todos os itens**

<br>

GET /itens

Resposta

```javascript
[
    {
    "status": strinf,
	"image": string,
	"name": string,
	"description": string,
	"userId": number,
	"id": number
    },
    {
    "status": strinf,
	"image": string,
	"name": string,
	"description": string,
	"userId": number,
	"id": number
    },
    ...
]
```

<br>

### **Listar Item específico**

<br>

GET /itens/id

Resposta

```javascript
{
    "status": strinf,
	"image": string,
	"name": string,
	"description": string,
	"userId": number,
	"id": number
}
```

<br>

### **Paginação dos itens**

<br>

GET /itens?\_page={number}&\_limit={number}

<br>

## Rotas que precisam de autenticacão (TOKEN)

<br>

### **Cadastrar um item**

<br>

POST /itens

Corpo da mensagem

```javascript

{
	"status": string,
	"image": string,
	"name": string,
	"description": string,
	"userId": number
}

```

<br>

Obs.: <br>
status: deve ser **"lost"** para item perdido ou **"found"** para item encontrado <br>
name: refere-se ao nome genérico do item

<br>

Resposta

```javascript

{
	"status": string,
	"image": string,
	"name": string,
	"description": string,
	"userId": number,
	"id": number
}

```

<br>

### **Atualizar um item**

<br>

PATCH /itens/id

Corpo da mensagem: keys que podem ser alteradas

```javascript

{
	"status": string,
	"image": string,
	"name": string,
	"description": string,
}

```

<br>

Resposta

```javascript

{
	"status": strinf,
	"image": string,
	"name": string,
	"description": string,
	"userId": number,
	"id": number
}

```

<br>

### **Deletar um item**

<br>

DELETE /itens/id

<br>

### **Deletar um Usuário**

<br>

DELETE /itens/userId

<br>

## Rota para usuário específico (enviar para empresa)

<br>

GET /users/userId

Resposta

```javascript

{
	"email": string,
	"phone": string,
	"avatar": string,
	"social_network": string,
    "id": number
}
```
