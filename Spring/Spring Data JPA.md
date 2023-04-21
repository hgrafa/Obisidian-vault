O Spring data JPA é uma [[ORM]] (**Object Relational Mapper**)

## Objetivo

- Abstrair a comunicação ente o projeto Spring e o banco de dados, abstraindo o sql que seria gerado pelo caminho.
- Abstrair o uso da própria JPA com Spring Data JPA, usando interfaces Repository que facilitam nosso uso através de **Especificações.**

## Usos interessantes

### Anotation @Embeddable e @Embedded

Quando queremos separar em classes alguns atributos no Java porém no banco de dados queremos manter tudo apenas como uma tabela:

[**Baeldung:** *JPA @Embedded And @Embeddable*](https://www.baeldung.com/jpa-embedded-embeddable)

```java
@Entity
@Table(name = "pessoas")
@Getter @Setter @NoArgsConstructor
public class Pessoa {

	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long id;

	private String nome;

	@Embedded
	private Endereco endereco;
	
}
```

```java
@Embeddable
@Getter @Setter @NoArgsConstructor
public class Endereco {

	private String rua;
	
}
```

### JPA Derived queries

### JPA Native queries
