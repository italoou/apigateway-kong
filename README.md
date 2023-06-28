# Kong Api Gateway 

Este repositório tem como objetivo implementar um api gateway utilizando o kong para o sistema Vasco Bank, uma aplicação desenvolvida utilizando a arquitetura de microserviços para a disciplina de TÓPICOS ESPECIAIS EM SISTEMAS DE INFORMAÇÃO DE GESTÃO A (Arquitetura de Microsserviços)

## Identificador de Autenticação

    Ao subir o kong, será gerado um identificador para autenticação que pode ser obtido através da requisição para a rota da api, exposta na porta 8001, /consumers/loginserverissuer/jwt, o valor em data.key deve ser adicionado ao header do token jwt com sua chave "kid".

## Produção (configuração com autenticação)

>> cd apigateway-kong

>> cd kong-production

>> docker-compose up

    

## Desenvolvimento (configuração sem autenticação)

No diretório apigateway-kong se encontra um arquivo yml com um exemplo para o docker compose dos serviços com a porta padrão definida para eles e a rede kong-net, necessária para que o gateway redirecione para os serviços

No diretório kong-development terá o arquivo docker-compose.yml e o arquivo kong.yml, nele está a configuração do api gateway com uma configuração padrão para acessar os serviços, mudanças nos nomes dos containers ou portas dos serviços precisarão ser atualizadas nesse arquivo.

>> cd apigateway-kong

>> cd kong-development 

>> docker-compose up

Após executado o comando os serviços estarão disponíveis para acesso na porta 8002, caso desejar essa porta poderá ser modificada no arquivo docker-compose.yml, as rotas de acesso aos serviços podem ser consultadas na tabela em anexo

Caso deseje, a configuração com autenticação poderá ser ativada apenas por removendo os caracteres de comentarios do arquivo *kong.yml* dentro da pasta **kong-development**, porém será necessario atualizar o valor do kid no serviço de autenticação (consultar ***Identificador de Autenticação*** ).


# Rotas de Acesso aos Serviços

|Serviço|Rota|Porta Padrão|Diretório|Repositorio|
|-------|----|------------|---------|-----------|
|Seguro|/seguro|7001|ms-insurance|
|Emprestimo|/emprestimo|7002|ms-loan|
|Financiamento|/financiamento|7003|ms-realstate-financing|
|Autenticação|/autenticacao|7004|vasco-bank-autenticacao|
|Usuario|/usuario|7005|user-service|
|Investimento|/investimento|7006|investiment-service|
|Conta|/conta|7007|vasco-bank-conta|
|Cartão|/cartao|7008|vasco-bank-cartao|
|Pagamento|/pagamento|7009|vasco-bank-pagamento|