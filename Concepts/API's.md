
Application Programming Interface

[[#Rest API]] é o modelo que seguiremos na construção dessas API's, sendo atualmente o modelo mais popular.

Também é possível que existam requisições do tipo [[RPC]] sendo umas das mais famosas o [[RPC#gRPC]].

## Tecnologias para fazer API's

- Em javascript feitas através do Nest, [[Fastify]] e do [[Express.js]]
- Em Java através do [[Spring boot]]
- Em C# com o [[DotNet API]]
- Em Python com o Rest Framework, Flask e com o Fast API
## Composta por

- Conjunto de especificações de possíveis interações entre aplicações
- Documentação para desenvolvedor
## Boas Práticas

- Utilização dos métodos HTTP
- Utilização dos status adequados
- Padrão de nomenclatura com o verbos HTTP
## Fake API

podemos fazer uma Fake API básica utilizando a dependência Json Server

existem boas APIs para praticar segurança e ou dados mockados como:

- [Real World API](https://realworld-docs.netlify.app/docs/specs/frontend-specs/api/)
- [Json placeholder](https://jsonplaceholder.typicode.com/)
----
# Rest API

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
