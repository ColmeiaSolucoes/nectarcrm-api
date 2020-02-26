# Qualificação Resource

Esta API permite o controle total das qualificação. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

### End-point principal
/qualificacoes ou /qualificacao

###URL
http://app.nectarcrm.com.br/crm/api/1/qualificacoes/

### Endpoints disponíveis
    Listagem: GET /qualificacoes/

    Inserção: POST /qualificacoes/
    Visualização: GET /qualificacoes/{id}
    Atualização: PUT /qualificacoes/{id}
    Exclusão: DELETE /qualificacoes/
    Procura por e-mail: GET /qualificacoes/email/{email@dominio.*} (use * para busca por like)
    Procura por telefone: GET /qualificacoes/telefone/{6299999999*} (use * para busca por like)
    Procura por ID contato: GET /qualificacoes/contatoId/{contatoId}
    
Parâmetros de listagem:
* Páginação: 
    * &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)
    * &displayLength=x (integer) - Quantidade de objetos por página (máximo 50)
* &status (optional, int) - Status/Fase da qualificação (integer 1 = em andamento, 2 = ganha, 3 = perdida, 4 = descartada)
+ &displayLength (optional, int) - Quantidade de objetos a serem listados (máximo 50)
+ &dataInicio (optional, date) - Data de criação inicial (dd/MM/yyyy)
+ &dataFim (optional, date) - Data de criação final (dd/MM/yyyy)
+ &dataInicioAtualizacao (optional, date) - Data atualização inicial (dd/MM/yyyy)
+ &dataFimAtualizacao (optional, date) - Data atualização final (dd/MM/yyyy)
+ &dataInicioLimite (optional, date) - Data limite inicial (dd/MM/yyyy)
+ &dataFimLimite (optional, date) - Data limite final (dd/MM/yyyy)
+ &nome (optional, string) - Nome ou código da qualificação
+ &secao (optional, int) - Seção do contato (0 = clientes, 1 = prospects, 2 = suspects, 3 = leads, 5 = descartados)
+ &clienteId (optional, int) - id de um [/contato](../contato) contato
+ &usuariosId (optional, array) - X,Y,Z... (array integer) onde X,Y e Z são ids do objeto [/usuario](../usuario)
+ &useAlias (optional, string) - ao filtrar campos personalizados, utiliza o "alias" do campo personalizado ao invés do nome do campo.


    Dica: quando estiver listando, você pode escolher os campos que deseja trazer enviando o parâmetro "attribute" na URL.
    
    Exemplo:
    /crm/api/1/qualificacoes?attribute=id&attribute=nome
    Apenas id e nome virá na listagem.
    
[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
autor | (object) | Autor da qualificação
autorAtualizacao | (object) | Quem fez a última atualização
cliente | (object) | Contato relacionado a venda
codigo | (string)(auto) | Código da qualificação
compromisso | (object) | O agendamento realizado para a qualificação
compromissos | (integer) | Quantidade de compromissos pendentes
dataAtualizacao | (datetime iso8601) | Última data de atualização
dataCriacao | (datetime iso8601) | Data de criação dessa qualificação
dataLimite | (datetime iso8601) | Data limite de fechamento da qualificação
etapa | (integer) | Etapa atual do fluxo de venda
id | (long) | Identificador no sistema
pipeline | (string) | Funil de venda / Pipeline em string (apenas "nome")
funilVenda | (object) | Funil de venda / Pipeline em objeto (com nome e id)
responsavel | (object) | Quem será responsável por essa qualificação
status | (integer) | Status da qualificação (1 = Em andamento, 2 = Agendada, 3 = Qualificada, 4 = Descartada, 5 = Vendida, 6 = Não vendida)
tarefas | (integer) | Quantidade de tarefas pendentes

\* readonly

Exemplo
```js
    {
        "nome": "Minha primeira qualificação do contato 1",
        "cliente": {
          "id": 141960,
          "nome": "Cliente 1"
        },
	    "dataLimite":"2016-03-11T10:00:00-03:00",
        "pipeline": "Pipeline de qualificação",
        "etapa": 2, //Etapa 2
        "responsavel": {
          "id": 12,
          "login": "contato1@teste.com.br",  //se nao tiver id, procura por esse
          "nome": "Usuario 1"  //se nao tiver id, procura por esse
        },
        "status": 1 //Em andamento
    }
```
