# Webhook Resource

Esta API permite o controle total dos webhooks. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
https://app.nectarcrm.com.br/crm/api/1/webhook/

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)


Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
id | (long) | _(Somente leitura)_ Identificador no sistema
**nome** | (string) | Nome do webhook **(Obrigatorio)**
**url** | (string) | URL do webhook **(Obrigatorio)**
isAtivo | (boolean) | Ativar/desativar o webhook
contador | (integer) | _(Somente leitura)_ Quantidade de vezes que o webhook foi disparado com sucesso
**[eventNumber](events.md)** | (integer) | Número do evento que irá disparar o webhook **(Obrigatorio)**
authType | (integer) | Tipo de autenticação do webhook
authUser | (string) | Usuário para autenticação do tipo 'SIMPLE'
authPassword | (string) | Senha para autenticação do tipo 'SIMPLE'
tokenBearer | (string) | Token para autenticação do tipo 'BEARER'

#### _Campos somente leitura são relevantes somente nas consultas_

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