O Typescript é um superset da linguagem [[Core Javascript]] , fornecendo tipos e uma melhor sintaxe durante o desenvolvimento.

O Typescript é transpilado para Javascript antes de ser enviado ao browser ou destino de execução.

## Comandos

### iniciando projeto node

```bash
  npm init
```

### criando um arquivo dedicado para estágio de desenvolvimento:

```bash
// instalando typescript para desenvolvimento 
npm install typescript -D

// executando codigo typscript
npx tsc src/index.ts

// criando TS config
npx tsc --init
```

### configurações relevantes

```json
{
  "target" : "...", // configura versão do ecmascript
  "rootdir" : "./src", // arquivo fonte do ts
  "outputdir" : "./build" // pastas de saída dos arquivos js
}
```

após configurar o output dir só é necessário transpilar usando
```bash
  npx tsc
```

### Criando script de execução

`package.json`
```json
{
  "scripts" : {
    "start" : "npx tsc && node buid/index.js",
    "test" : "echo \"Error: no test specified\" && exit 1"
  }  
}
```

chamada:

```bash
  npm run start

```

## Async functions

```ts
async function getData(id : number) {
  return "felipe";
}
```

com retorno explicito o retorno desta função é uma `Promise<string>`

```ts
async function getData(id : number) : Promise<string> {
  return "felipe";
}
```

## Structs/Types

```ts
type produto = {
  nome : string,
  preco : number,
  quantidade : number,
}

let garrafa : produto {
  nome : "garrafa",
  preco : 3.50,
  quantidade : 2,
}
```

## Array com MultiTypes

```ts
  let vetor : (string | number) : ["ana", 1, "joão"]
```

## Tuplas

```ts
  let boleto : [string, number] = ["conta de luz", 200.0]
```

## Muti types functions

```ts
function callToPhone(phoneNumber : number | string) {
  return phoneNumber;
}
```

```ts
function callToPhone(phoneNumber : string) : number | string {
  return phoneNumber;
}
```

## Async functions

```ts
async function getData(id : number) {
  return "felipe";
}
```

com retorno explicito o retorno desta função é uma `Promise<string>`

```ts
async function getData(id : number) : Promise<string> {
  return "felipe";
}
```

## Types vs. Interfaces

```ts
type robot = {
  id : number,
  name : string,
}

const bot : robot = {
  id = 1,
  name = "bamobee",
}
```
  
* mais usado no contexto de classes.
* firma contratos a serem cumpridos

```ts
interface robot2 = {
  id : number,
  name : string,
}

const bot2 : robot2 = {
  id = 1,
  name = "bamobee",
}
```