# Lanchonete Cozinha

Microserviço de gestão da fila de produção do sistema de lanchonete.

## Tecnologias

- Java 17
- Spring Boot 3
- Spring JDBC
- Spring Cloud OpenFeign
- MySQL (RDS)
- RabbitMQ (mensageria)
- Docker
- Kubernetes (EKS)

## Funcionalidades

- Gestão da fila de produção
- Atualização de status de preparo
- Comunicação com serviço de Pedidos (Feign)

## Endpoints

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| GET | `/cozinha/fila` | Listar fila de produção |
| POST | `/cozinha/fila/{id}/iniciar` | Iniciar preparo |
| POST | `/cozinha/fila/{id}/pronto` | Marcar como pronto |
| GET | `/actuator/health` | Health check |

## Comunicação

**REST (Síncrono via OpenFeign):**
- Cozinha → Pedidos: Consulta detalhes do pedido

**RabbitMQ (Assíncrono):**
- Consome: `pagamento.events` (PagamentoAprovado)
- Publica: `cozinha.events` (PedidoPronto)

## Executar Localmente

```bash
# Compilar
mvn clean package

# Executar (requer MySQL e RabbitMQ)
java -jar target/cozinha-1.0.0.jar
```

## Testes

```bash
# Executar testes
mvn test

# Gerar relatório de cobertura
mvn jacoco:report
```

## Docker

```bash
# Build
docker build -t lanchonete-cozinha .

# Run
docker run -p 8080:8080 lanchonete-cozinha
```

## Deploy

O deploy é automatizado via GitHub Actions:
- **CI**: Executado em Pull Requests (testes + SonarCloud)
- **CD**: Executado no merge para main (build + deploy no EKS)

## Repositórios Relacionados

- [lanchonete-infra](https://github.com/andersonfer/lanchonete-infra) - Infraestrutura
- [lanchonete-clientes](https://github.com/andersonfer/lanchonete-clientes)
- [lanchonete-pedidos](https://github.com/andersonfer/lanchonete-pedidos)
- [lanchonete-pagamento](https://github.com/andersonfer/lanchonete-pagamento)
