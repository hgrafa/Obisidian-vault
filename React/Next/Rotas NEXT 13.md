## Novo diretório App

Agora o padrão no next é chamar o arquivo principal de `page.tsx`

```
📂 src
 |- 📂 app
	 | - 📂 dashboard
	    | - page.tsx
	 | - head.tsx
	 | - layout.tsx
	 | - page.tsx
 |- 📂 pages
	 |- 📂 api
		 hello.ts
```

### Outros arquivos

```
📂 src
 |📂 app
	 |📂 dashboard
	    |📝 page.tsx
	 |📂 (auth)
		|📂 signin
			|📝 page.tsx
		|📂 signup
		    |📝page.tsx
		|📝layout.tsx
		|📝loading.tsx
	 |📝head.tsx
	 |📝layout.tsx
	 |📝page.tsx
 |📂 pages
	 |📂 api
		|📝hello.ts
```

- `layout.tsx` : similar ao antigo `_app.tsx`, definindo coisas que vão se repetir em todas as paginas.
	- Não precisa recarregar entre paginas diferentes.
	- Pode ser usado dentro de um conjunto de rotas específico, como um layout que deve ser repetido em todo contexto de autenticação por exemplo.
	- O Next vai concatenar o layout
- `head.tsx`: este arquivo existe na raiz da `src/app` mas pode ser inserido dentro de qualquer contexto para adicionar e concatenar coisas ao head da pagina quando carregada.
- `loading.tsx`: 
## Evitando roteamento de pastas

Num contexto de login e register, que um layout poderia ser reaproveitado, poderíamos usar uma pasta `auth` para criar este arquivo.

- Problema: rotas ficariam `/auth/sigin` e `/auth/signup`
- Solução: usar a pasta com `(auth)` faz com que o next não considere ela no roteamento.