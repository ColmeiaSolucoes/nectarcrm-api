# Oportunidade Resource

Esta API permite o controle total das oportunidade. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/oportunidades/

### Outros endpoints disponíveis
    Listagem: GET /oportunidades/

    Inserção: POST /oportunidades/
    Visualização: GET /oportunidades/{id}
    Atualização: PUT /oportunidades/{id}
    Exclusão: DELETE /oportunidades/
    Procura por e-mail: GET /oportunidades/email/{email@dominio.*} (use * para busca por like)
    Procura por telefone: GET /oportunidades/telefone/{6299999999*} (use * para busca por like)
    Procura por ID contato: GET /oportunidades/contatoId/{contatoId}
    Estatísticas por oportunidade: GET /oportunidades/statistics/{oportunidadeId}
    Estatísticas por funil e etapa: GET /oportunidades/statistics/pipe/{pipelineId}
    Estatísticas total por funil: GET /oportunidades/statistics/total/{pipelineId}
    Próxima atividade: /oportunidades/{oportunidadeId}/proximaAtividade

_Obs: Por padrão o endpoit de listagem (GET diretamente no http://app.nectarcrm.com.br/crm/api/1/oportunidades) retorna somente oportunidade em andamento (status = 1)._
    
Parâmetros de listagem:
* Páginação: 
    * &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)
    * &displayLength=x (integer) - Quantidade de objetos por página (máximo 50)
* &status (optional, int) - Status/Fase da oportunidade (integer 1 = em andamento, 2 = ganha, 3 = perdida, 4 = descartada)
+ &displayLength (optional, int) - Quantidade de objetos a serem listados (máximo 50)
+ &dataInicio (optional, date) - Data de criação inicial (dd/MM/yyyy)
+ &dataFim (optional, date) - Data de criação final (dd/MM/yyyy)
+ &dataInicioAtualizacao (optional, date) - Data atualização inicial (dd/MM/yyyy)
+ &dataFimAtualizacao (optional, date) - Data atualização final (dd/MM/yyyy)
+ &dataInicioLimite (optional, date) - Data limite inicial (dd/MM/yyyy)
+ &dataFimLimite (optional, date) - Data limite final (dd/MM/yyyy)
+ &dataInicioConclusao (optional, date) - Data conclusão inicial (dd/MM/yyyy)
+ &dataFimConclusao (optional, date) - Data conclusão final (dd/MM/yyyy)
+ &nome (optional, string) - Nome ou código da oportunidade
+ &secao (optional, int) - Seção do contato (0 = clientes, 1 = prospects, 2 = suspects, 3 = leads, 5 = descartados)
+ &clienteId (optional, int) - id de um [/contato](../contato) contato
+ &pipelineId (optional, int) - id de um funil de venda
+ &sequenciaAtual (optional, int) - número da etapa no funil (1...1000 - etapa do funil, 1002 - Ganha, 1003 - Perdida, 1004 - Descartada, 1005 - Prorrogada)
+ &categoriasId (optional, array[int]) - X,Y,Z... onde X,Y e Z são ids do objeto [/categoria](../categoria) de contato
+ &produtosIds (optional, array[int]) - X,Y,Z... onde X,Y e Z são ids do objeto [/produto](../produto)
+ &categoriasProdutoIds (optional, array[int]) - X,Y,Z... onde X,Y e Z são ids do objeto Categoria de Produto
+ &subcategoriasProdutoIds (optional, array[int]) - X,Y,Z... onde X,Y e Z são ids do objeto SubCategoria de Produto
+ &listasIds (optional, array[int]) - X,Y,Z... onde X,Y e Z são ids do objeto [/lista](../lista)
+ &origensId (optional, array[int]) - X,Y,Z... onde X,Y e Z são ids do objeto [/origem](../origem)
+ &origensContatoId (optional, array[int]) - X,Y,Z... onde X,Y e Z são ids do objeto [/origem](../origem) do contato
+ &segmentosId (optional, array[int]) - X,Y,Z... onde X,Y e Z são ids do objeto [/segmento](../segmento)
+ &usuariosId (optional, array) - X,Y,Z... (array integer) onde X,Y e Z são ids do objeto [/usuario](../usuario)
+ &camposPersonalizados (optional, json) - filtro de campos personalizados
+ &useAlias (optional, string) - ao filtrar campos personalizados, utiliza o "alias" do campo personalizado ao invés do nome do campo.


    Dica: quando estiver listando, você pode escolher os campos que deseja trazer enviando o parâmetro "attribute" na URL.
    
    Exemplo:
    /crm/api/1/oportunidades?attribute=id&attribute=nome
    Apenas id e nome virá na listagem.
    
[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
autor | (object) | Autor da oportunidade (Objeto com a propriedade id)
autorAtualizacao | (object) | Quem fez a última atualização (Objeto com a propriedade id)
camposPersonalizados | (properties){"campo 1": "valor 1", "campo 2": "valor 2"} | Campos criados para uso no NectarCRM
cliente | (object) | Contato relacionado a venda
contato | (object) | Pessoa (contato) relacionado a venda
codigo | (string)(auto) | Código da oportunidade
dataAtualizacao | (datetime iso8601) | Última data de atualização
dataCriacao | (datetime iso8601) | Data de criação dessa oportunidade
dataLimite | (datetime iso8601) | Data limite de fechamento da oportunidade
etapa | (integer) | Etapa atual do fluxo de venda
id | (long) | Identificador no sistema
isProrrogada | (boolean) | Verdadeiro se estiver prorrogada
justificativas | (array)(object) | Justificativas de conclusão de oportunidade
nome | (string) | Nome do contato
observacao | (string) | Observação da oportunidade
origem | (object) | Origem da oportunidade
pipeline | (string) | Funil de venda / Pipeline em string (apenas "nome")
funilVenda | (object) | Funil de venda / Pipeline em objeto (com nome e id)
probabilidade | (int) | Probabilidade de fechamento (10, 25, 50, 75, 90 ou 100)
produtos | (array)(object) | Itens e produtos
responsavel | (object) | Quem será responsável por essa oportunidade
status | (integer) | Status da oportunidade (1 = Em andamento, 2 = Ganha, 3 = Perdida, 4 = Cancelada, 5 = Prorrogada)
temperatura | (string)* | Temperatura da oportunidade medida pela probabilidade de fechamento da oportunidade (Frio: < 25 / Morno: >= 25 e < 50 / Quente: >=50 e < 75 / Muito Quente: >= 75) _esse campo é somente leitura seu valor é alterado através da propabilidade_
valorAvulso | (float) | Valor da venda avulsa
valorMensal | (float) | Valor da venda recorrente (mensal)
valorTotal | (float) | Valor total da venda (todos produtos e descontos)
valorTotalDescontos | (float) | Valor total dos descontos
compromissos | (integer) | Quantidade de compromissos pendentes
tarefas | (integer) | Quantidade de tarefas pendentes
bloquearProposta | (boolean) | Status do bloqueio para geração de proposta da oportunidade
bloquearConclusao | (boolean) | Status do bloqueio para conclusão da oportunidade
corresponsaveis | (array)(object) | Usuários corresponsáveis da oportunidade
equipesCorresponsaveis | (array)(object) | Equipes corresponsáveis da oportunidade
motivoDescarte | (object) | Motivo de descarte da oportunidade
vendaBase | (boolean) | Campo indicando se a venda foi realizada na base

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
        "contato": {
          "id": 141961,
          "nome": "Pessoa do cliente 1"
        },
        "autor":{
          "id": 12,
	  "login": "contato1@teste.com.br",  //se nao tiver id, procura por esse
          "nome": "Usuario 1"  //se nao tiver id, procura por esse
        },
        "justificativas": [
            { 
                "id": 10,
                "nome": "Justificativa 1"
            },
            { 
                "nome": "Justificativa sem ID passado buscamos pelo nome"
            }
        ],
	    "dataLimite":"2016-03-11T10:00:00-03:00",
        "produtos": [
            {
                "isComissaoPorcentual": false,
                "desconto": 0,
                "isDescontoPorcentual": false,
		"acrescimo": 10,
		"acrescimoPercentual": false,
                "refId": 8435, //ID do produto cadastrado
                "nome": "Produto 1", //aqui serve o nome ou o código editado na tabela do produto
                "quantidade": 6, //quantidade de produtos
                "recorrencia": 1, //0 = Avulso, 1 = Mensal, 2 = Anual (mensal x 12)
		"sequencia": 0, //quando quiser ordenar os produtos dentro da oportunidade, utilizar os numeros sequenciais para cada item (0,1,2...)
                "valorUnitario": 69,
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
        },
        "bloquearProposta": false,
        "bloquearConclusao": false,
	"corresponsaveis": [
    	    {
     	        "id": 94,
      	        "login": "usuario-coresp@teste.com.br",
      	        "nome": "Usuario Corresponsavel"
    	    }
  	],
        "equipesCorresponsaveis": [
            {
                "id": 9,
                "nome": "Equipe X"
            }
        ],
	"motivoDescarte": {
	     "id": 15,
             "nome": "Lead não qualificado"
	},
	"vendaBase": true 
    }
```
