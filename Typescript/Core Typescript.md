O Typescript é um superset da linguagem [[Core Javascript]] , fornecendo tipos e uma melhor sintaxe durante o desenvolvimento.

O Typescript é transpilado para Javascript antes de ser enviado ao browser ou destino de execução.

## Oriented Object Programming

- [[Javascript differences]]
- [[OOP]]

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
