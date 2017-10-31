# Categoria Resource

Esta API permite o controle total das categorias de contato. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/categoria/

Parâmetros de categoriagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
ativo | (boolean) | Marca se essa categoria está ativa para utilização
descricao | (string) | Descrição da categoria
id | (long) | Identificador no sistema
isCliente | (boolean) | Define se aparece na seção de clientes na listagem de contatos
isProspect | (boolean) | Define se aparece na seção de prospects na listagem de contatos
isSuspect | (boolean) | Define se aparece na seção de suspects na listagem de contatos
isLead | (boolean) | Define se aparece na seção de leads na listagem de contatos
nome | (string) | Nome da categoria

Exemplo
```js
    [
      {
        "ativo": true,
        "descricao": "Nossos fornecedores"
        "id": 1,
        "isCliente": true,
        "isProspect": true,
        "isSuspect": false,
        "isLead": true,
        "nome": "Fornecedor",
      }
    ]
```