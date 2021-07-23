# Tarefa Resource

Esta API permite o controle total das tarefa. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/tarefas/

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
autor | (object) | Autor do contato
autorAtualizacao | (object) | Quem fez a última atualização
checklist | (object){"id", "nome"} | Checklist da tarefa (cadastrado, se não existir iremos incluir)
cliente | (object) | Contato relacionado a venda
dataAtualizacao | (datetime iso8601) | Última data de atualização
dataCriacao | (datetime iso8601) | Data de criação desse contato
dataLimite | (datetime iso8601) | Data limite para realizar a tarefa
descricao | (string) | Descrição do tarefa
id | (long) | Identificador no sistema
oportunidade | (object) | Oportunidade relacionado a venda
prioridade | (integer) | Prioridade da tarefa (0 = Normal, 1 = Alta, 2 = Altíssima)
responsavel | (object) | Quem será responsável por esse contato
status | (integer) | Status da tarefa (0 = Aberta, 1 = Concluída, 2 = Cancelada, 3 = Em execução)
tipo | (integer) | Tipo da tarefa (0 = comum, 1 = ligação, 2 = notificação, 3 = e-mail, 4 = compromisso)
titulo | (string) | Titulo da tarefa
modeloTarefa | (object) | Quando a tarefa for criada pelo workflow, irá retornar as propriedades do modelo

Quando a tarefa é do tipo ligação:

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
atendida | (boolean) | Se a ligação foi ou não atendida
dataInicio | (datetime iso8601) | Data de início da ligação
dataFim | (datetime iso8601) | Data de finalização da ligação
contatoQuemAtendeu | (object)[contato] | Contato de quem atendeu a ligação
classificacao | (integer) | Classificação da ligação: de 1 a 5
justificativa | (string) | Quando não atendida, pode-se colocar uma justificativa a parte
tipoLigacao | (object) | Tipo da ligação (cadastrada no nectar)
resultadoLigacao | (string) | A descrição da ligação feita pelo responsável da tarefa


Exemplo
```js
    {
        "cliente": {
          "id": 430,
          "nome": "Colmeia Soluções"
        },
	    "dataLimite":"2016-03-30T00:00:00-03:00",
        "descricao": "Tarefa tese descrição",
		"oportunidade": {
			"id": 1,
			"nome": "Oportunidade de venda"
		},
        "prioridade": 2,
        "responsavel": {
          "id": 12,
          "login": "usuario1",
          "nome": "Usuario 1"
        },
        "status": 0, //aberta
        "tipo": 0, //comum
        "titulo": "Teste de tarefa",
	"modeloTarefa": {
    	   "id": 41,
    	   "titulo": "Teste block",
    	   "tarefaTipo": {
      		"id": 1,
      		"nome": "Tarefa",
      		"ativo": true,
      		"natureza": 0
    	    },
    	    "blockFieldsEdit": true
	}
      }
```
