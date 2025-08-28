
Framework feito em cima do [[React]]
## Routing

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
	 |📝template.tsx
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
- `loading.tsx`: é uma página que vai ser carregada enquanto o componente desejado está carregando.
- `template.tsx`: Este arquivo é bem similar ao layout, porém ele recarrega a cada troca de página, enquanto que o layout apenas recarrega os componentes de dentro.

## Rotas dinâmicas

```
📂 src
 |📂 app
	 |📂 product
	    |📝 page.tsx
	 |📂 (auth)
		|📂 signin
			|📝 page.tsx
		|📂 signup
		    |📝page.tsx
```

## Evitando roteamento de pastas

Num contexto de login e register, que um layout poderia ser reaproveitado, poderíamos usar uma pasta `auth` para criar este arquivo.

- Problema: rotas ficariam `/auth/sigin` e `/auth/signup`
- Solução: usar a pasta com `(auth)` faz com que o next não considere ela no roteamento.
## Data Fetching

podemos ter componentes assíncronos e o NEXT vai construindo o componente e utilizando o `loading.tsx` como placeholder enquanto o assincronismo executa

```tsx
interface Product {
	id: number;
	name: string;
}

function fetchProducts() {
	return new Promise((resolve) => {
		setTimout(() => {
			resolve([
				{ id: 1, name: "Produto 1"},
				{ id: 2, name: "Produto 2"},
				{ id: 3, name: "Produto 3"}
			]);
		}, 200);
	});
}

export default async function Products() {
	const products = await fetchProducts();

	return (
		<div>
			<ul>
				{products.map(product => (
					<li key={product.id}> {product.name} </li>
				))}
			</ul>
		</div>
	)
}
```