- Representation State Transfer
- Modelo de arquitetura
- 6 regras

## Regras Rest

1. Modelo de Client-Server
2. Stateless (não armazena estado ou sessão)
3. Cache (possibilidade, não obrigatoriedade)
4. Interface Uniforme
	- Identificação
		- http://localhost:5050/products
		- http://localhost:5050/clients
	- Representação dos recursos
	- Mensagens auto-descritivas
	- [[#HATEOAS]](Hypertext As The Engine Of Application State)
5. Camadas (parte exposta: endpoint)
6. Código sob demanda

## HATEOAS

```json
{
	"id" : 1,
	"user" : "hgrafa",
	"created_at" : "2021-01-10",
	"comments_link" : "api/users/1/comments"
}
```
