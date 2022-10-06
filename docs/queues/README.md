# Queues Resource

Esta API permite realizar a listagem e inclusão de novas filas no NectarCRM.

Lembrando, somente usuários ADMIN têm permissão para alterar os objetos. As listagens e consultas são para todos.

Instruções para realizar a integração:

URL
https://app.nectarcrm.com.br/crm/api/1/queues/

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

### Endpoints disponíveis
    Listagem: GET /queues/
    Consultar por ID: GET /queues/{id}
    Visualizar próximo da fila sem rotacionar: GET /queues/next-preview/{queue-id}
    Salvar: POST /queues/
    Atualizar: PUT /queues/
    Remover: DELETE /queues/{queue-id}

Parâmetros de listagem:
* &name=x (integer) Nome desejado para buscar uma fila (iniciando com);

Exemplo de requisição: `https://app.nectarcrm.com.br/crm/api/1/queues`

Propriedade | Tipo            | Descricao
------------ |-----------------| -------------
name | (string)        | Nome da fila (obrigatório)
description | (string)        | Descrição da fila
dataCriacao | (date)          | Data de criação
dataAtualizacao | (date)          | Data de atualização
author | (object)        | Autor da fila
updateAuthor | (object)        | Autor da atualização
users | (array)(object) | Usuários presentes na fila (obrigatório ao menos 1)
strategy | (integer)       | Constante para a estratégia da fila (atualmente somente FIFO - 0)

-----

Exemplo de retorno
```json
{
  "id": 12,
  "name": "Vendedores",
  "description": "Minha fila de vendedores",
  "dataCriacao": "2022-08-02T19:35:56.567Z",
  "dataAtualizacao": "2022-08-22T18:32:32.180Z",
  "author": {
    "id": 2,
    "login": "rafael.marques@nectarcrm.com.br",
    "nome": "Rafael Marques"
  },
  "updateAuthor": {
    "id": 2,
    "login": "rafael.marques@nectarcrm.com.br",
    "nome": "Rafael Marques"
  },
  "users": [
    {
      "id": 16,
      "user": {
        "id": 2,
        "login": "rafael.marques@nectarcrm.com.br",
        "nome": "Rafael Marques"
      },
      "position": 1
    },
    {
      "id": 15,
      "user": {
        "id": 9,
        "login": "usuario1@nectarcrm.com.br",
        "nome": "Usuário 1"
      },
      "position": 2
    },
    {
      "id": 14,
      "user": {
        "id": 7,
        "login": "usuario2@nectarcrm.com.br",
        "nome": "Usuário 2"
      },
      "position": 0
    }
  ],
  "strategy": 0
}
```

--------

As filas podem ser utilizadas nas criações de Contato, Oportunidades e Leadboard. O próximo usuário da fila será utilizado como responsável do objeto. Exemplos:

Contato:
```
{
  "nome": "Rafael teste fila 7",
  "queue": {
    "id": 12
  }
}
```

Oportunidade:
```
{
  "nome": "Oportunidade Do José",
  "cliente": {
    "id": 298
  },
  "funilDeVenda": {
    "id": 20
  },
  "queue": {
    "id": 12
  }
}
```

Leadboard:
```
{
  "cliente": {
    "nome": "Cliente para qualificar"
  },
  "queue": {
    "id": 12
  }
}
```
