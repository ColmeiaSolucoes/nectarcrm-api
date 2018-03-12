# ProdutoSubCategoria Resource

Esta API permite o controle total das produtoSubCategorias de produto. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/produtoSubCategoria/

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
ativo | (boolean) | Marca se essa subCategoria de produto está ativa para utilização
descricao | (string) | Descrição da subCategoria de produto
id | (long) | Identificador no sistema
nome | (string) | Nome da subCategoria de produto

Exemplo
```js
    [
      {
        "ativo": true,
        "cescricao": "Manutenção de computadores",
        "id": 1,
        "nome": "Manutenção de PCs",
      }
    ]
```