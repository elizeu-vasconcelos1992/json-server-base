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

### Listar todos os usuários

<br>

GET /users

Resposta

```javascript

{
	"email": string,
	"phone": string,
	"avatar": string,
	"social_network": string,
	"id": number
},
{
	"email": string,
	"phone": string,
	"avatar": string,
	"social_network": string,
	"id": number
},
...
```

<br>

### Listar usuário específico

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

### **Listar item específico**

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

### **Listar todas as reinvidicações**

<br>

GET /claim

Resposta

```javascript
[
	{
	"user_required": {
		"email": string,
		"phone": string,
		"social_network": string,
		"item": {
					"status": string,
					"image": string,
					"name": string,
					"description": string,
					"userId": number,
					"id": number
				}
				},
	"user_applicant": {
		"email": string,
		"phone": string,
		"social_network": string,
		"description": string,
		"image": string
	},
	"userId": number,
	"id": number
	},
	{
	"user_required": {
		"email": string,
		"phone": string,
		"social_network": string,
		"item": {
					"status": string,
					"image": string,
					"name": string,
					"description": string,
					"userId": number,
					"id": number
				}
				},
	"user_applicant": {
		"email": string,
		"phone": string,
		"social_network": string,
		"description": string,
		"image": string
	},
	"userId": number,
	"id": number
	},
	...

]
```

<br>

### **Listar reivindicação específica**

<br>

GET /claim/id

Resposta

```javascript

{
	"user_required": {
		"email": string,
		"phone": string,
		"social_network": string,
		"item": {
					"status": string,
					"image": string,
					"name": string,
					"description": string,
					"userId": number,
					"id": number
				}
				},
	"user_applicant": {
		"email": string,
		"phone": string,
		"social_network": string,
		"description": string,
		"image": string
	},
	"userId": number,
	"id": number
}
```

<br>

### **Paginação dos itens**

<br>

GET /itens?\_page={number}&\_limit={number}

<br>

### **Listar todos os itens um usuário**

GET /users/{userId}?\_embed=itens

<br>

### **Listar todas reivindicações de um usuário**

GET /users/{userId}?\_embed=claim

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

### **Reivindicar um item**

<br>

POST /claim

```javascript

{
	"user_required": {
		"email": string,
		"phone": string,
		"social_network": string,
		"item": {
					"status": string,
					"image": string,
					"name": string,
					"description": string,
					"userId": number,
					"id": number
				}
				},
	"user_applicant": {
		"email": string,
		"phone": string,
		"social_network": string,
		"description": string,
		"image": string
	},
	"userId": number
}

```

<br>

Obs.: <br>

"user_required": refere-se as informações do usuário que cadastrou (postou) o item <br>
"user_applicant": refere-se as informações do usuário que reivindicou o item (logado)<br>
"userId": refere-se ao id do "user_applicant" <br>

<br>

Resposta

```javascript

{
	"user_required": {
		"email": string,
		"phone": string,
		"social_network": string,
		"item": {
					"status": string,
					"image": string,
					"name": string,
					"description": string,
					"userId": number,
					"id": number
				}
				},
	"user_applicant": {
		"email": string,
		"phone": string,
		"social_network": string,
		"description": string,
		"image": string
	},
	"userId": number,
	"id": number
}

```

<br>

### **Deletar um item**

<br>

DELETE /itens/id

<br>

### **Deletar uma reivindicação**

<br>

DELETE /claim/id

<br>

### **Deletar um Usuário**

<br>

DELETE /itens/userId

<br>
