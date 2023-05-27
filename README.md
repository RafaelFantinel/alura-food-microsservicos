
![thumbnail-Microsserviços com Java e Spring](https://user-images.githubusercontent.com/66698429/169815319-20640ad4-cda0-4868-9728-d380c5fcc799.png)

# Microsserviços na prática: implementando com Java e Spring

Projetos construídos no curso da alura, que visa implementar um fluxo de pedidos utilizando micros-serviços de

- Pagamentos
- Pedidos
- Gateway
- Eureka server

## O que foi implementado

- Configuração do servidor [Eureka](https://spring.io/projects/spring-cloud-netflix) para registro Service Discovery e Service Registry
- Configuração do [API-GATEWAY](https://spring.io/projects/spring-cloud-gateway) para centralizar as requisições para os microsserviços e LoadBalancer
- Configuração dos micro-serviços de Pagamentos e Pedidos para registro no servidor Eureka
- Configuração do Flyway para migrations no banco de dados
- Uso da biblioteca ModelMapper para mapeamento de DTO para Entidades
- Utilização da arquitetura de software MVC, com a definição organizada por pasta das resposabilidades da classe
- Criação de uma API REST para os microsserviços de Pagamentos e Pedidos
- Utilização do OpenFeign (Spring Cloud) para comunicação síncrona entre serviços de Pagamentos e Pedidos
- Pallback para atualização do estado de um Pedido
- Configuração do [Resilience4J](https://resilience4j.readme.io/docs) para ação de Circuit Breker na rota de confirmarPagamento no serviço de Pagamentos,

## 🚀 Tecnologias

- [Spring Boot](https://spring.io/projects/spring-boot)
- [JDK 17](https://hub.docker.com/r/bellsoft/liberica-openjdk-alpine)
- [Spring Data JPA](https://spring.io/projects/spring-data-jpa)
- [Model-Mapper](http://modelmapper.org/)
- [Lombok](https://projectlombok.org/)
- [MySQL](https://www.mysql.com/)
- [spring-boot-devtools](https://docs.spring.io/spring-boot/docs/current/reference/html/using.html)
- [Maven](https://maven.apache.org/)
- [Flyway](https://flywaydb.org/documentation/concepts/migrations.html)
- [Resilience4J](https://resilience4j.readme.io/docs)
- [Eureka](https://spring.io/projects/spring-cloud-netflix)
- [API-GATEWAY](https://spring.io/projects/spring-cloud-gateway)

## 🛠 Instalando pré-requisitos

### Instalar Java JDK 17 e Maven

Instale JDK e Maven, vamos usar a ferramenta SdkMan

```
# Para instalar SdkMan
curl -s "https://get.sdkman.io" | bash

source "$HOME/.sdkman/bin/sdkman-init.sh"

# Para instalar o Java JDK 17
sdk install java 17.0.1-open

#Para instalar o Maven
sdk install maven
```

### Executando a aplicação

```

  ### Primeiramente suba o banco de dados das aplicações com o comando
  docker-compose up -d

  ### Logo em seguida subas os projetos na seguinte ordem
  - **server**: aplicação onde todos os micros-serviços vão se registrar;
  - **gateway**: aplicação que centraliza a entrada dos micros-serviços e faz o balanceamento de carga;
  - **pagamentos**: microserviço de pagamentos.
  - **pedidos**: microserviço de pedidos.
```

Por fim, as apis ficam disponíveis através da url <http://localhost:8082/nome-do-serviço/endpoint>, exemplo

```
  http://localhost:8082/pedidos-ms/pedidos'
```
