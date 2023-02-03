
Application Programming Interface

[[Rest]] é o modelo que seguiremos na construção dessas API's, sendo atualmente o modelo mais popular.

Também é possível que existam requisições do tipo [[RPC]] sendo umas das mais famosas o [[RPC#gRPC]].

## Tecnologias para fazer API's

- Em [[Node.js]] feitas com [[Express.js]]
- Em Java através do [[Spring boot]]

## Composta por

- Conjunto de especificações de possíveis interações entre aplicações
- Documentação para desenvolvedor

## Boas Práticas

- Utilização dos métodos HTTP
- Utilização dos status adequados
- Padrão de nomenclatura com o verbos HTTP

## Métodos de Requisições - HTTP

- GET - leitura
- POST - Criação
- PUT - Atualização
- DELETE - deleção
- PATCH - Atualização Parcial (pode ser com PUT também)

## HTTP Codes

- **1XX**: Informativo - aceita ou continua em andamento
- **2XX**: Confirmação 
	- **200**: Bem sucedida
	- **201**: Created, geralmente usado para POST após uma inserção
- **3XX**: Redirecionamento
	- **301**: Moved Permanently
	- **302**: Moved
- **4XX**: Erro do Cliente
	- **401**: Bad Request
	- **402**: Unauthorized
	- **403**: Forbidden
	- **404**: Not Found
	- **422**: Unprocessable Entity
- **5XX**: Erro no servidor
	- **500**: Internal Server Error
	- **502**: Bad Gateway

## Parâmetros

- Header Params
- Query Params
- Route Params
- Body Params