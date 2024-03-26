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