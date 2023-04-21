
```js
  useEffect(() => {
	  fetch('http://localhost:3333/transactions')
		  .then(response => response.json())
		  .then(data => console.log(data))
  })
```

O use `useEffect` não aceita assincronismo diretamente dentro, então pode ser feito da seguinte forma:

```js
useEffect(() => {
  loadTransactions()
}, [])

async function loadTransactions() {
 const response = await 
	 fetch('http://localhost:3333/transactions')
 
 const data = await response.json()

 console.log(data)
}
```

