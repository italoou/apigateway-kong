# Kong Api Gateway 

Este repositório tem como objetivo implementar um API Gateway utilizando o Kong para o sistema Vasco Bank, uma aplicação desenvolvida utilizando a arquitetura de microsserviços para a disciplina de TÓPICOS ESPECIAIS EM SISTEMAS DE INFORMAÇÃO DE GESTÃO A (Arquitetura de Microsserviços).

Autor do projeto: Italo Lima

Github: @italoou

## Identificador de Autenticação

Ao subir o Kong, será gerado um identificador para autenticação que pode ser obtido através da requisição para a rota da API, exposta na porta 8001: /consumers/loginserverissuer/jwt. O valor em data.key deve ser adicionado ao header do token JWT com sua chave "kid".

## Instruções de Executar Aplicação
### Produção (configuração com autenticação)

```bash
cd apigateway-kong
cd kong-production
docker-compose up
```
### Desenvolvimento (configuração sem autenticação)

No diretório apigateway-kong, encontra-se um arquivo YAML com um exemplo para o Docker Compose dos serviços, com a porta padrão definida para eles, o nome dos containers e a rede kong-net, necessária para que o Gateway redirecione para os serviços.

No diretório kong-development, você encontrará o arquivo docker-compose.yml e o arquivo kong.yml, arquivo de configuração do kong DBLess, nele está a configuração do API Gateway com uma configuração padrão para acessar os serviços. Mudanças nos nomes dos containers ou portas dos serviços precisarão ser atualizadas nesse arquivo.


```bash
cd apigateway-kong
cd kong-development 
docker-compose up
```

Após executar o comando, os serviços estarão disponíveis para acesso na porta 8002. Caso deseje, essa porta poderá ser modificada no arquivo docker-compose.yml. As rotas de acesso aos serviços podem ser consultadas na tabela em anexo.

Caso deseje, a configuração com autenticação poderá ser ativada apenas removendo os caracteres de comentários do arquivo kong.yml dentro da pasta kong-development e reiniciando o container. Entretanto, será necessário atualizar o valor do "kid" no serviço de autenticação (consultar "Identificador de Autenticação").


## Rotas de Acesso aos Serviços

|Serviço|Rota|Porta Padrão|Nome do Container Padrão|Repositorio|
|-------|----|------------|---------|-----------|
|Seguro|/seguro|7001|ms-insurance-api|
|Emprestimo|/emprestimo|7002|ms-loan-api|
|Financiamento|/financiamento|7003|ms-realstate-financing-api|
|Autenticação|/autenticacao|7004|vasco-bank-autenticacao-api|
|Usuario|/usuario|7005|user-service-api|
|Investimento|/investimento|7006|investiment-service-api|
|Conta|/conta|7007|vasco-bank-conta-api|
|Cartão|/cartao|7008|vasco-bank-cartao-api|
|Pagamento|/pagamento|7009|vasco-bank-pagamento-api|

