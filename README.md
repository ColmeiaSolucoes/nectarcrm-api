# NectarCRM API

##  Esse é um repositório para auxílio na **API NectarCRM**.
  Colocaremos materiais e webhooks para que a integração seja facilitada.

  **Nota:** Qualquer erro ou sugestão, por favor nos contate.

Esta API permite o controle total dos contatos, oportunidades, tarefas e compromissos. Veja as instruções de como realizar a integração abaixo.
###[Clique aqui para a documentação completa](http://docs.nectarcrm.apiary.io)

## Instruções para realizar a integração

### URL de acesso
https://app.nectarcrm.com.br/crm/api/1/
######Obs: utilize o HTTPS, pois o HTTP ainda funciona vai ser desabilitado em breve

### Requisição HTTP

Seguimos a estrutura padrão do estilo [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer)

- GET: lista ou consulta dados
- POST: criação de dados
- PUT: atualização de dados
- DELETE: remoção de dados

Dica: quando estiver listando, você pode escolher os campos que deseja trazer enviando o parâmetro "attribute" na URL.

Exemplo:
/crm/api/1/oportunidades?attribute=id&attribute=nome
Apenas id e nome virá na listagem.


### Retorno


+ Response (application/json)

    ```js
        {
            "sobre": {
                "versao": "1.0",
                "creditos": "Colmeia Soluções"
            },
            "endpoints": {
                "contatos": {
                    "edicao": {
                        "response": 200,
                        "title": "Edicao de contatos",
                        "method": "PUT",
                        "endpoint": "http://app.nectarcrm.com.br/crm/api/1/contatos/:id"
                    },
                    "listagem": {
                        "response": 200,
                        "title": "Listagem de contatos",
                        "method": "GET",
                        "endpoint": "http://app.nectarcrm.com.br/crm/api/1/contatos"
                    }
                    //...outros métodos abaixo
                }
            }
        }
    ```

## Como autenticar

É necessário passar o token privado de autenticação para conseguir realizar as operações.
Para conseguir esse token, acesse no NectarCRM a seção **Configurações** -> *Integrações*.

![Token Nectar ](http://nectarcrm.com.br/assets/images/screens/screen-token.png?ok)

Com esse token, você acessa, edita e excluir as informações possíveis pela API.

Você pode optar por 2 caminhos:

1. Enviar header na requisição **Access-Token** *SEU_TOKEN*
```
curl http://app.nectarcrm.com.br/crm/api/1/contatos/ -H "Access-Token: c5520d027fd1475b97a7a3aab50886f4"
```

2. Enviar parâmetro na URL de requisição **api_token=** *SEU_TOKEN*
```
curl http://app.nectarcrm.com.br/crm/api/1/contatos/?api_token=c5520d027fd1475b97a7a3aab50886f4
```


## Códigos de respostas

+ 200 (application/json)

        Sucesso

+ 401 (text/json)

        Algum parâmetro enviado errado

+ 404 (text/json)

        Registro não encontrado

+ 500 (text/json)

        Erro do servidor


### Seções disponíveis

Segue as seções que você pode acessar pela API

Principais:

- [/contatos](./docs/contato)
- [/oportunidades](./docs/oportunidade)
- [/compromissos](./docs/compromisso)
- [/tarefas](./docs/tarefa)

Tabelas administrativas
- [/produto](./docs/produto)
- [/tabelaPreco](./docs/tabelaPreco)
- [/lista](./docs/lista)
- [/origem](./docs/origem)
- [/segmento](./docs/segmento)
- [/categoria](./docs/categoria)
- [Tipos - cadastros administrativos](./docs/tipos)

### Header
A requisição deve conter:

- Content-Type: application/json
- Access-Token: SEU_TOKEN_AQUI

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

##Integração RDStation
Para informações de integração com RDStation, [clique aqui](./docs/rdstation)