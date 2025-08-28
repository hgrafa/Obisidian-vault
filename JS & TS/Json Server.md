```bash
npm i json-server -D
```

```json
{
	"transactions" : [
		{
			"id": 1,
			"description": "Desenvolvimento",
			"type": "income",
			"category": "Venda",
			"price": 1400,
			"createdAt": "..."
		}
	]
}
```

## Pegando hoje pelo console

```bash
new Date().toIstoString()
```

## Executando

```bash
npx json-server server.json -p 3333
```