## Class

## Interface

## Type

## Enum

## inheritance

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