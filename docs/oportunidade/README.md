# Oportunidade Resource

Esta API permite o controle total das oportunidade. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/oportunidades/

Parâmetros de listagem:
* Páginação: 
    * &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)
    * &displayLength=x (integer) - Quantidade de objetos por página (máximo 200)
* Status/Fase: &status=x (integer 1 = em andamento, 2 = ganha, 3 = perdida, 4 = descartada)
* Data de criação: 
    * Inicio: &dataInicio=dd/MM/yyyy
    * Fim: &dataFim=dd/MM/yyyy
* Data limite: 
    * Inicio: &dataInicioLimite=dd/MM/yyyy
    * Fim: &dataFimLimite=dd/MM/yyyy
* Data atualização: 
    * Inicio: &dataInicioAtualizacao=dd/MM/yyyy
    * Fim: &dataFimAtualizacao=dd/MM/yyyy
* Responsáveis: &usuariosId=X,Y - onde X e Y = ids do objeto [/usuario](../docs/usuario)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
autor | (object) | Autor da oportunidade
autorAtualizacao | (object) | Quem fez a última atualização
camposPersonalizados | (properties){"campo 1": "valor 1", "campo 2": "valor 2"} | Campos criados para uso no NectarCRM
cliente | (object) | Contato relacionado a venda
codigo | (string)(auto) | Código da oportunidade
dataAtualizacao | (datetime iso8601) | Última data de atualização
dataCriacao | (datetime iso8601) | Data de criação dessa oportunidade
dataLimite | (datetime iso8601) | Data limite de fechamento da oportunidade
etapa | (integer) | Etapa atual do fluxo de venda
id | (long) | Identificador no sistema
isProrrogada | (boolean) | Verdadeiro se estiver prorrogada
nome | (string) | Nome do contato
observacao | (string) | Observação da oportunidade
origem | (object) | Origem da oportunidade
pipeline | (object) | Fluxo de venda / Pipeline
probabilidade | (int) | Probabilidade de fechamento (10, 25, 50, 75, 90 ou 100)
produtos | (array)(object) | Itens e produtos
responsavel | (object) | Quem será responsável por essa oportunidade
status | (integer) | Status da oportunidade (1 = Em andamento, 2 = Ganho, 3 = Perdido, 4 = Cancelado)
temperatura | (string)* | Temperatura da oportunidade medida pela probabilidade de fechamento da oportunidade (Frio: < 25 / Morno: >= 25 e < 50 / Quente: >=50 e < 75 / Muito Quente: >= 75)
valorAvulso | (float) | Valor da venda avulsa
valorMensal | (float) | Valor da venda recorrente (mensal)
valorTotal | (float) | Valor total da venda (todos produtos e descontos)
valorTotalDescontos | (float) | Valor total dos descontos
compromissos | (integer) | Quantidade de compromissos pendentes
tarefas | (integer) | Quantidade de tarefas pendentes

\* readonly

Exemplo
```js
    {
        "nome": "Minha primeira oportunidade do contato 1",
        "observacao": "Uma Observação qualquer",
        "cliente": {
          "id": 141960,
          "nome": "Cliente 1"
        },
	    "dataLimite":"2016-03-11T10:00:00-03:00",
        "produtos": [
            {
                "comissaoPorcentual": false,
                "desconto": 0,
                "descontoPorcentual": false,
                "refId": 8435, //ID do produto cadastrado
                "nome": "Produto 1", //aqui serve o nome ou o código editado na tabela do produto
                "quantidade": 6, //quantidade de produtos
                "recorrencia": 1, //0 = Avulso, 1 = Mensal, 2 = Anual (mensal x 12)
                "valor": 69,
                "valorTotal": 414
            }
        ],
        "pipeline": "Pipeline padrão",
        "probabilidade": 50,
        "etapa": 2, //Etapa 2
        "responsavel": {
          "id": 12,
          "login": "contato1@teste.com.br",  //se nao tiver id, procura por esse
          "nome": "Usuario 1"  //se nao tiver id, procura por esse
        },
        "origem": {
          "id": 1,
          "nome": "Indicação"
        },
        "status": 1, //Em andamento
        "valorAvulso": 500000, //R$ 500.000
        "valorMensal": 1000, //R$ 1.000
        "camposPersonalizados": {
            "Campo 1": "Valor 1",
            "Campo 2": "Valor 2"
        }
    }
```