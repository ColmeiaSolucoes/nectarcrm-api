# Tipos - cadastros administrativos

Esta API permite o controle dos usuários do sistema.

Instruções para realizar a integração:

### URLs disponíveis

##### Usuário:
http://app.nectarcrm.com.br/crm/api/1/usuario/


Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)

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
        "descricao": "Uma descricao qualquer"
        "id": 1,
        "nome": "Tipo de teste",
      }
    ]
```