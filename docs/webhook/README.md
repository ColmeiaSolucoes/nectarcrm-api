# Webhook Resource

Esta API permite o controle total dos webhooks. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/webhook/

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
id | (long) | Identificador no sistema
nome | (string) | Nome do webhook
url | (string) | URL do webhook
isAtivo | (boolean) | Ativar/desativar o webhook
contador | (integer) | Quantidade de vezes que o webhook foi disparado com sucesso
eventNumber | (integer) | Número do evento que irá disparar o webhook
authType | (integer) | Tipo de autenticação do webhook
authUser | (string) | Usuário para autenticação do tipo 'SIMPLE'
authPassword | (string) | Senha para autenticação do tipo 'SIMPLE'
tokenBearer | (string) | Token para autenticação do tipo 'BEARER'

Exemplo
```js
    [
      {
        "id": 10060,
        "nome": "Webhook teste",
        "url": "http://requestbin.fullcontact.com/1kvwu001",
        "contador": 12,
        "eventNumber": 1070,
        "authType": 1,
        "authUser": "usuario",
        "authPassword": "czODHGW9Akg=",
        "tokenBearer": "Bearer abcdefgh123"
        "ativo": true
      }
  ]
```