# Tabela de preço Resource

Esta API permite o controle total das tabelas de preço de produto. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/tabelaPreco/

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
ativo | (boolean) | Marca se essa tabela está ativa para utilização
dataCriacao | (date) | Data de criação dessa tabela
dataExpiracao | (datetime) | Data de expiração dessa tabela (ficará inativa após essa data)
descricao | (string) | Descrição do produto
id | (long) | Identificador no sistema
nome | (string) | Nome da tabela
produtos | (array)(object) | Traz os produtos adicionados nessa tabela em uma array
quantidadeProdutos | (integer) | Informa quantos produtos essa tabela possui

Exemplo
```js
    [
      {
        "ativo": true,
        "id": 14,
        "produtos": [
          {
            "ativo": true,
            "categoria": {
              "ativo": true,
              "id": 7,
              "nome": "Categoria de produto 1"
            },
            "codigo": "2.1",
            "comissao": 0,
            "comissaoPorcentual": true,
            "contador": 128,
            "descontoMaximo": 15,
            "descontoPorcentual": true,
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
          ],
        "nome": "Tabela NectarCRM 2016/02",
        "quantidadeProdutos": 9
      }
    ]
```