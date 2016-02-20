# NectarCRM API

##  Esse é um repositório para auxílio na **API NectarCRM**.
  Colocaremos materiais e webhooks para que a integração seja facilitada.

  **Nota:** Qualquer erro ou sugestão, por favor nos contate.

Esta API permite o controle total dos contatos, oportunidades, tarefas e comprimissos. Veja as instruções de como realizar a integração abaixo.
[Clique aqui para a documentação completa](http://docs.nectarcrm.apiary.io)

## Instruções para realizar a integração

### URL de acesso
http://app.nectarcrm.com.br/crm/api/1/

### Requisição HTTP

Seguimos a estrutura padrão do estilo [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer)

- GET: lista ou consulta dados
- POST: criação de dados
- PUT: atualização de dados
- DELETE: remoção de dados

### Seções disponíveis

Segue as seções que você pode acessar pela API

- [/contatos](./docs/contato)
- [/oportunidades](./docs/oportunidade)
- [/compromissos](./docs/compromisso)
- [/tarefas](./docs/tarefa)

### Header
A requisição deve conter:

- Content-Type: application/json
- Access-Token: SEU_TOKEN_AQUI

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)
