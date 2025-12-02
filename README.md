# Lanchonete - Cozinha

Microsserviço responsável pela gestão da fila de preparo e atualização de status.

## Tecnologias

- Java 17
- Spring Boot 3
- MySQL (RDS)
- RabbitMQ

## Endpoints

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| GET | /cozinha/fila | Listar fila de pedidos |
| POST | /cozinha/{id}/iniciar | Iniciar preparo do pedido |
| POST | /cozinha/{id}/pronto | Marcar pedido como pronto |

## Executar Localmente

```bash
mvn spring-boot:run
```

## Testes

```bash
mvn test
```

## Cobertura

[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=andersonfer_lanchonete-cozinha&metric=coverage)](https://sonarcloud.io/project/overview?id=andersonfer_lanchonete-cozinha)
