# Produto Resource

Esta API permite o controle total das produto. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/produto/

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
ativo | (boolean) | Marca se o produto está ou não ativo
categoria | (object) | Categoria do produto
codigo | (string) | Código do produto
comissao | (float) | Define o valor da comissão do produto (0 = não permite)
contador | (integer) | Código automático do produto
descontoMaximo | (integer) | Valor do desconto máximo permitido
descricao | (string) | Descrição do produto
id | (long) | Identificador no sistema
isComissaoPorcentual | (boolean) | Define se o valor do desconto máximo é porcentual ou real
isDescontoPorcentual | (boolean) | Define se o valor do desconto máximo é porcentual ou real
moeda | (string) | Código monetário da moeda (BRL e USD)
possuiEstoque | (boolean) | Define se o produto possui controle de estoque
quantidadeEstoque | (integer) | Define a quantidade do estoque desse produto
recorrencia | (integer) | Recorrência de valor do produto (0 = único, 1 = mensal, 2 = anual)
subcategoria | (object) | SubCategoria do produto
valorBase | (float) | Valor base do produto
valorEditavel | (boolean) | Indica se o valor base do produto é ou não editável

Exemplo
```js
    [
      {
        "ativo": true,
        "categoria": {
          "ativo": true,
          "id": 7,
          "nome": "Categoria de produto 1"
        },
        "codigo": "2.1",
        "comissao": 0,
        "isComissaoPorcentual": true,
        "contador": 128,
        "descontoMaximo": 15,
        "isDescontoPorcentual": true,
        "id": 1,
        "moeda": "BRL",
        "nome": "Nome do produto",
        "permiteDesconto": true,
        "possuiEstoque": false,
        "recorrencia": 1,
        "subCategoria": {
          "ativo": true,
          "id": 2,
          "nome": "Manutenção"
        },
        "valorBase": 150
      }
  ]
```