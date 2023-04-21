
[[Core Javascript]]
[[Core Typescript]]

## Compilers and Bundlers

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

const salario1 = user.salary || "Não se aplica";
const salario2 = user.salary ?? "Não se aplica"

const cargo1 = user.job || "Não se aplica";
const cargo2 = user.job ?? "Não se aplica"

console.log(`Salario: ${salario1}`);
console.log(`Cargo: ${salario2}`);
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

const 

sum(4, 5)
	.then(result => console.log(result));
	.catch(error => console.log(error));
```

