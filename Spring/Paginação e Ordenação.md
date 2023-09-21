
## Interface `Pageable`:

```java
public Page<PessoaDto> list(Pageable pagination) {
	return pessoaRepository
		.findAll(pagination)
		.map(PessoaDto::new);
} 
```

request:
```
hhtps://localhost:8080/pessoas?size={tamanho}&page={pagina}
```

```
hhtps://localhost:8080/pessoas?size=20&page=2
```

## Valores e Ordenação Default

```java
public Page<PessoaDto> list(
	@PageableDefault(size = 10, sort = {"nome"})
	Pageable pagination
) {
	return pessoaRepository
		.findAll(pagination)
		.map(PessoaDto::new);
}
```

## Ordenando

```
hhtps://localhost:8080/pessoas?sort={atributo}
```

```
hhtps://localhost:8080/pessoas?sort=nome
```

- Ordena de modo ascendente pelo atributo nome.

```
hhtps://localhost:8080/pessoas?sort=nome,desc
```

- Para ordenar de modo decrescente

## Customização de parametros

```java
spring.data.web.pageable.page-parameter=pagina
spring.data.web.pageable.size-parameter=tamanho
spring.data.web.sort.sort-parameter=ordem
```

```
http://localhost:8080/
	medicos?=5
	&pagina=1
	&ordem=email,desc
```