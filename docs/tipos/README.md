# Tipos - cadastros administrativos

Esta API permite o controle de várias cadastros no sistema que tipificam/categorizam outros objetos. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

### URLs disponíveis

##### Tipo de compromisso:
http://app.nectarcrm.com.br/crm/api/1/compromissos/tipos/

##### Tipo de ligação:
http://app.nectarcrm.com.br/crm/api/1/ligacao/tipos/


Parâmetros de origemgem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista todos objetos)

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