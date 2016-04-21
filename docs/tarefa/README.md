# Tarefa Resource

Esta API permite o controle total das tarefa. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/tarefas/

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista todos objetos)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
autor | (object) | Autor do contato
autorAtualizacao | (object) | Quem fez a última atualização
cliente | (object) | Contato relacionado a venda
dataAtualizacao | (datetime iso8601) | Última data de atualização
dataCriacao | (datetime iso8601) | Data de criação desse contato
dataLimite | (datetime iso8601) | Data limite para realizar a tarefa
descricao | (string) | Descrição do tarefa
id | (long) | Identificador no sistema
prioridade | (integer) | Prioridade da tarefa (0 = Normal, 1 = Alta, 2 = Altíssima)
responsavel | (object) | Quem será responsável por esse contato
status | (integer) | Status da tarefa (0 = Aberta, 1 = Concluída, 2 = Cancelada, 3 = Em execução)
tipo | (object){"id", "nome"} | Tipo do tarefa (cadastrado, se não existir iremos incluir)
titulo | (string) | Titulo da tarefa

Exemplo
```js
    {
        "cliente": {
          "id": 430,
          "nome": "Colmeia Soluções"
        },
	    "dataLimite":"2016-03-30T00:00:00-03:00",
        "descricao": "Tarefa tese descrição",
        "prioridade": 2,
        "responsavel": {
          "id": 12,
          "login": "usuario1",
          "nome": "Usuario 1"
        },
        "status": 0, //aberta
        "tipo": "Reunião",
        "titulo": "Teste de tarefa"
      }
```