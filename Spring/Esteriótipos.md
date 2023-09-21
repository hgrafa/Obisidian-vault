- [[Spring/Controllers|Controllers]]


## Services


## Repositories

O esteriotipo de Repository vem de usar alguma dependencia permitindo um acesso mais rapido  a base de dados.

> Cuidado! Nem sempre este acesso é performático.

Para bancos relacionais temos a [[Spring Data JPA]]

## Migrations

Para enviarmos  scripts ao banco nem sempre é interessante dar esta manutenção diretamente pela JPA, por isso utilizamos a estratégia de **Migrations**. Isto é: 

- Versionamento do banco
- Controle de estado do banco entre possíveis diferentes origens

Dentro do spring boot temos a [[Flyway]]