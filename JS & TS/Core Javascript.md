- [[Bibliotecas]]
## Event Loop

O event loop fica ouvindo a call stack (pilha de chamadas) das funções abertas.

O event loop é single thread, então fica buscando nesta pilha e distribuindo entre as outras threads disponíveis.

O javascript não é single thread, mas o event loop trabalha como uma distribuidora para outras threads.
## Links

- [[Consumindo API]]
## Promises

## Linters

> Podemos melhorar nosso desenvolvimento javascript com as ferramentas:
### ES Lint

```bash
// instalação
npm i eslint -D

// com typescript
npm install @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-plugin-react -D

// nova config
npx eslint src --ext .tsx

// rocketseat linter

```
### CommitLint

```bash
npm i @commitlint/config-conventional @commitlint -D
```

## Lint Staged + Husky

```bash
npm i lint-staged -D
npm i husky -D
```


[[Core Javascript]]

## Compilers and Bundlers (node e etc)

### Compilers

- Babel: Converte um código que não funciona em todos os browsers para um mais amigável.

### Bundlers

- Can i use
- Webpack
- vite (já tem compiler)

## Nullish Coalescing Operator

```js
const employee = {
	name: "Pedro",
	salary: 0, 
	job: null, 
}

const salario1 = user.salary || "Não se aplica"; // nao se aplica
const salario2 = user.salary ?? "Não se aplica"; // 0

const cargo1 = user.job || "Não se aplica";
const cargo2 = user.job ?? "Não se aplica"

console.log(`Salario: ${salario1}`);
console.log(`Cargo: ${salario2}`);
```

### 🚩 Problema

**falsy values =>** `0`, `''`, `[]`, `false`, `undefined`, `null`

Caso a `age` seja zero, a resposta continuaria dando `'Empty`

### 🟢 Solução

`??` é mais restritivo

```js
document.body.innerText = 'Your age is: ' + (age ?? 'Empty')
```

## Objetos

```js
const user = {
  name: 'Hugo',
  age: 21,
  address: {
    street: 'Rua',
    number: '123'
  }
};

document.body.innerText = ('name' in user) 
// true

document.body.innerText = ('nickname' in user) 
// false
```

## Métodos interessantes

```js
document.body.innerText = Objects.keys(user)
// name, age, address
```

----

```js
document.body.innerText = Objects.values(user)
```

```json
'Hugo', 21, [object Object]
```
------

```js
document.body.innerText = JSON.stringfy(Objects.values(user))
```

```json
[
 'Hugo',
 21,
 {
   "steet" : "Rua",
   "number" : 123
 } 
]
```

## Desestruturação

```js
const {name, responsability: job, nickname = "Newbie"} = empolyee;

console.log(JSON.stringfy({employee, responsability, nickname}))
```

## Rest operator

Resto da desestruturação

```js
const {name, ...rest} = user;

console.log(JSON.stringfy(rest));
```

Em arrays:
```js
const sequence = [1, 1, 2, 3, 5, 8, 13, 25, 34];

const {first, , third, ...rest} = array;
console.log(JSON.stringfy({first, third, rest}));
```

## Short Sintax - "Reestruturação"

```js

const name = "Pedro";
const job = "Developer";

// antes
// const employee = {
//   name: name;
//   job: job;
// }

// melhorado
const empolyee = {name, job}

```

## Optional Chaining - "Ligamentos opicionais"

```js
const empolyee = {
	name: "Pedro";
	job: {
		name: "Developer",
		time: "2 months ago",
		company: {
			name: "Chat SBT",
			createdAt: "2023/03/20"
		}
		
		drinkCoffee(hour) {
			return (hour > 9 && hour < 16 ) ?
				"Coffee time :)" : "Sorry, it's closed :/";
		}
	}
}

// ruim
const companyOfEmployee = employee.job ?
	  employee.job.company ?
		  employee.job.company.name 
		  : "Not on a company"
	  : "Not on a company";

// melhor
const companyOfEmployee = employee.job?.company?.name ?? "Not on a company";

// melhor para funções
const coffeeAction = employee.job?.drinkCoffe?.();

console.log(companyOfEmployee);
```

## Métodos de array

- `map()` vs. `forEach()`
- `filter()`
- `every()`, `some()`, `find()`, `findIndex()`, `reduce()`

## Promisses

```js
const sum = (a, b) => {
	return new Promisse((resolve, reject) => {
		setTimout(() => {
			resolve(a + b);
		}, 2000)
	})
}

sum(4, 5)
	.then(result => console.log(result));
	.catch(error => console.log(error));
```

