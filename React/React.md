- Inicialmente pensado para Single Page Application (SPA's)
- Normalmente usado com Vite.js ou então com algum framework mais opinado como Next
- É uma library, como uma coleção de recursos menos opinados.

## Components

O React também busca a Estilização componentizada para seu código, visando isolar css de cada componente, evitando possíveis sobreescritas de um css global.

## Functional Components

```tsx
export function MyComponent(props) {
	return (
		<div>
			<h1> title </h1>
			<p> lorem ipsum </p>
		</div>
	)
}
```

## Css para componentes

CSS modules
## Css in Js

- Styled Components
- Stiches

## Melhorando a UX

- Loading Skeleton Pages
- Para roteamento de paginas: React Router DOM 
- React Hooks
- [[Context API]]

## Consumindo APIs

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

###  Associando `UseEffect` e `UseState`

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