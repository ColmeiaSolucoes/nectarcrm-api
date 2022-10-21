# Origem Resource

Esta API permite o controle total das origens de contato. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/origem/

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)
* &nome=x (string) Nome da origem

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
ativo | (boolean) | Marca se essa origem está ativa para utilização
descricao | (string) | Descrição da origem
id | (long) | Identificador no sistema
nome | (string) | Nome da origem

Exemplo
```js
    [
      {
        "ativo": true,
        "descricao": "Evento que realizamos"
        "id": 1,
        "nome": "Eventos",
      }
    ]
```
