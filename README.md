#AME-FIPE-TRAINING-API

- Qualquer requisição com chamadas duplicadas não deverá duplicar os dados na base
- Requisições com dados duplicados não devem gerar erro
- O banco deverá ser criado utilizando o Flyway
- Utilizar os verbos HTTP de maneira correta

### 1 - Realizar o setup do projeto:
- Crie uma branch com o seu nome. Exemplo: `training-fipe/fulano`
- Realize a criação da base de dados e configure no application.yml a conexação e configuração do JPA e FlyWay. Exemplo config:
  ```
  spring:
    datasource:
      url: jdbc:mysql://localhost:8080/meubd
      username: meu_user
      password: meu_pwd
      driver-class-name: com.mysql.cj.jdbc.Driver
      hikari:
        maximumPoolSize: 4
    flyway:
      url: jdbc:mysql://localhost:8080/meubd
      username: meu_user
      password: meu_pwd
      validateOnMigrate: true
  ```
- Adicionar um base path para a aplicação. Exemplo:
  ```
  spring:
    webflux:
      base-path: /my-app
  ```

### 2 - Criar um endpoint com o verbo GET que diga Ola Mundo utilizando Webflux

### 3 - Deletar o endpoint do exercicio 2

### 4 - Criar um endpoint para manipulação de marcas de carro:
- Receber as marcas de carros e salve as informações no banco:
    
    Exemplo de informações que serão recebidas:
    
    ```
    {
    "key"*: "fiat-6",
    "fipe_name"*: "Fiat",
    "name"*: "FIAT",
    "country": "ITALIA"
    }
    ```
- Possibilitar que as marcas sejam consultadas por nome, país e nome na FIPE

### 5 - Criar um endpoint para manipulação de carros:

- Receber os carros e possibilitar a associação das marcas que foram criadas no exercício anterior:
Exemplo de informações que serão recebidas:
```
{
"key"*: "palio-4826",
"brand_id"*: 6,
"name"*: "Palio 1.0 Celebr. ECONOMY F.Flex 8V 4p",
"fipe_name"*: "Palio 1.0 Celebr. ECONOMY F.Flex 8V 4p",
"category": "SPORT"
}
```

- Possibilitar que os carros sejam consultados por marca, nome, nome na fipe e categoria

### 6 - Adicionar tratativa para campos obrigatórios nos endpoints dos exercicio 4 e 5 (estão com asterisco)

### 7 - Adicionar um AdvisorController para tratativa de erros

`Nos próximos exerccios faremos a integração com a API da tabela FIPE (http://fipeapi.appspot.com/) utilizando o Webclient`

### 8 - Adicionar um endpoint que sincronize as marcas com a tabela FIPE batendo no endpoint disponibilizado na documentação acima, onde o resultado da consulta deverá ser jogado numa fila SQS

### 9 - Criar um listener na API para a fila SQS que consuma as mensagens postadas no exercício 8 e salve os dados na base

### 10 - Realizar a mesma operação feita no exercício 8 e 9 para os carros

### 11 - Remover os listeners da API e migrar o código para uma lambda (utilizar localstack, caso possua a conta labs ou uma conta pessoal fica mais fácil)

### 12 - Adicionar sleuth para trackear as chamadas

### 13 - Realizar os testes unitários da camada de service realizando mock da camada de DAO e de requisições

### 14 - Adicionar documentação na API (Ler docuemntação do springdoc-openapi-webflux)