O Typescript é um superset da linguagem [[Core Javascript]] , fornecendo tipos e uma melhor sintaxe durante o desenvolvimento.

O [[Core Typescript]] é transpilado para [[Core Javascript]] antes de ser enviado ao browser ou destino de execução.

## Oriented Object Programming

- [[Javascript differences]]
- [[Typescript/Class]]
- [[Typescript/Interface]]
- [[Typescript/Type]]

## Comandos

### iniciando projeto node

```bash
  npm init
```

### criando um arquivo dedicado para estágio de desenvolvimento:

```bash
  npm install typescript -D
```

### executando

```bash
  npx tsc src/index.ts
```

### Criando TS config

```bash
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
