# ProdutoCategoria Resource

Esta API permite o controle total das produtoCategorias de produto. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/produtoCategoria/

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
ativo | (boolean) | Marca se essa categoria de produto está ativa para utilização
descricao | (string) | Descrição da categoria de produto
subcategorias | (array) | Lista das subcategorias de produto
id | (long) | Identificador no sistema
nome | (string) | Nome da categoria de produto

Exemplo
```js
    [
      {
        "ativo": true,
        "descricao": "Serviços de computadores",
        "id": 1,
        "subcategorias":[
            { "nome": "Subcategoria 1", id: 10 }
        ],
        "nome": "IT Serviços",
      }
    ]
```