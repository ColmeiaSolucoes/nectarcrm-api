# Oportunidade Resource

Esta API permite o controle total das oportunidade. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/oportunidades/

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
autor | (object) | Autor do contato
autorAtualizacao | (object) | Quem fez a última atualização
camposPersonalizados | (properties){"campo 1": "valor 1", "campo 2": "valor 2"} | Campos criados para uso no NectarCRM
cliente | (object) | Contato relacionado a venda
codigo | (string)(auto) | Código da oportunidade
dataAtualizacao | (datetime) | Última data de atualização
dataCriacao | (datetime) | Data de criação desse contato
dataLimite | (datetime) | Data limite de fechamento da oportunidade
etapa | (integer) | Etapa atual do fluxo de venda
id | (long) | Identificador do contato no sistema
isProrrogada | (boolean) | Verdadeiro se estiver prorrogada
produtos | (array)(object) | Itens e produtos
nome | (string) | Nome do contato
observacao | (string) | Observação do contato
pipeline | (object) | Fluxo de venda / Pipeline
probabilidade | (int) | Probabilidade de fechamento (10, 25, 50, 75, 90 ou 100)
responsavel | (string) | Quem será responsável por esse contato
status | (integer) | Status da oportunidade (1 = Em andamento, 2 = Ganho, 3 = Perdido, 4 = Cancelado
valorAvulso | (float) | Valor da venda avulsa
valorMensal | (float) | Valor da venda recorrente (mensal)

Exemplo
```js
    {
        "nome": "Minha primeira oportunidade do contato 1",
        "observacao": "Uma Observação qualquer",
        "cliente": {
          "id": 141960
        },
        "dataLimite": 1455760800000,
        "produtos": [{ "nome": "Primeiro item", "valor": 10000 }],
        "pipeline": "Pipeline padrão",
        "probabilidade": 50,
        "etapa": 2,
        "responsavel": {
          "id": 19
        },
        "status": 1,
        "valorAvulso": 500000,
        "valorMensal": 1000,
        "camposPersonalizados": {
            "Campo 1": "Valor 1",
            "Campo 2": "Valor 2"
        }
    }
```