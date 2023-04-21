
```js
useEffect(() => {
  loadTransactions()
}, [])

async function loadTransactions() {
 const response = await 
	 fetch('http://localhost:3333/transactions')
 
 const data = await response.json()
}
```

## Associando `UseEffect` e `UseState`

```ts
interface Transaction {
	id: number
	description: string
	type: 'income' | 'outcome'
	price: number
	category: string
	createdAt: string
}

const [transactions, setTransactions] = useState<Transaction[]>([])

async function loadTransactions() {
 const response = await 
	 fetch('http://localhost:3333/transactions')
 
 const data = await response.json()

 setTransactions(data)
}

useEffect(() => {
  loadTransactions()
}, [])

// ...
```

```tsx
<tbody>
	{transactions.map(transaction => {
		return (
			<td>{transaction.id}</td>
			<td> {/*...*/} </td>
		)
	})}
</tbody>
```