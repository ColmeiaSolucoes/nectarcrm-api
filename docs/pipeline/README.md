# Pipeline Resource

Esta API permite o controle total dos funis de venda/outro tipo. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/pipeline/

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)
* &type=x (integer) Define o filtro de funil (0 = vendas, 1 = qualificação)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
ativo | (boolean) | Marca se esse funil está ativo para utilização
descricao | (string) | Descrição do funil
id | (long) | Identificador no sistema
nome | (string) | Nome do funil
padrao | (boolean) | Determina se esse funil é o padrão do sistema
sequencias | (array) | Etapas do funil
tipo | (int) | Tipo do funil (0 = vendas, 1 = qualificação)

Exemplo
```js
    [
      {
        "ativo": true,
        "descricao": "Funil de vendas do produto X"
        "id": 1,
        "nome": "Funil de venda",
        "padrao": true,
        "sequencias": [
                    {
                        "id": 11,
                        "nome": "Gerar Interesse",
                        "sequencia": 1,
                        "prazo": 3,
                        "gerarProposta": false
                    },
                    {
                        "id": 22,
                        "nome": "Processo de Cadência",
                        "sequencia": 2,
                        "prazo": 2,
                        "gerarProposta": false
                    }
                    ],
        "tipo": 0
      }
    ]
```