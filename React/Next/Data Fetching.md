## No Next 13 + App Routing

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