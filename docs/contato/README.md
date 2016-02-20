# Contato Resource

Esta API permite o controle total dos contatos (Leads, Suspects, Prospects, Clientes, etc.). Veja as instruções de como realizar a integração abaixo.


Instruções para realizar a integração:

URL para envio dos dados
http://app.nectarcrm.com.br/crm/api/1/

Método
Requisição HTTP:

    - GET: lista ou consulta contato
    - POST: criação do contato
    - PUT: atualização dos dados
    - DELETE: remoção

Header
A requisição deve conter:

- Content-Type: application/json
- Access-Token: SEU_TOKEN_AQUI

[Para mais informações, consulte a documentação clicando aqui](http://docs.nectarcrm.apiary.io)

Schema
```js
{
  "type": "object",
  "properties": {
    "ativo": {
      "id": "ativo",
      "type": "boolean"
    },
    "autor": {
      "id": "autor",
      "type": "object",
      "properties": {
        "id": {
          "type": "integer"
        },
        "login": {
          "type": "string"
        },
        "nome": {
          "type": "string"
        }
      }
    },
    "autorAtualizacao": {
      "type": "object",
      "properties": {
        "id": {
          "id": "id",
          "type": "integer"
        },
        "login": {
          "type": "string"
        },
        "nome": {
          "type": "string"
        }
      }
    },
    "camposPersonalizados": {
      "type": "object",
      "properties": {
        "type": "string, string",
        "description": "label, valor"
      }
    },
    "categoria": {
      "type": "string",
      "description" : "Se não existir, criaremos um novo objeto com esse nome."
    },
    "cnpj": {
      "type": "string"
    },
    "constante": {
      "type": "integer",
      "description": "0 = CLIENTE, 1 = PROSPECT, 2 = SUSPECT, 3 = LEAD, 4 = CONTATO_RELACIONADO, 5 = DESCARTADO",
    },
    "contatos": {
        "type": "array(contato)",
        "description":"Array de objetos do tipo contato (com mesmas propriedades desse schema Contato)"
    },
    "dataAtualizacao": {
      "type": "timestamp"
    },
    "dataCriacao": {
      "type": "auto"
    },
    "emails": {
      "type": "array",
      "items": {
        "type": "string"
      }
    },
    "facebook": {
      "type": "string"
    },
    "id": {
      "type": "integer"
    },
    "indicadoPor": {
      "type": "string"
    },
    "linkedin": {
      "type": "string"
    },
    "nome": {
      "type": "string"
    },
    "observacao": {
      "type": "string"
    },
    "origem": {
      "type": "string",
      "description" : "Se não existir, criaremos um novo objeto com esse nome."
    },
    "razaoSocial": {
      "type": "string"
    },
    "receitaAnual": {
      "type": "currency"
    },
    "responsavel": {
      "type": "object",
      "properties": {
        "id": {
          "type": "integer"
        },
        "login": {
          "type": "string"
        },
        "nome": {
          "type": "string"
        }
      }
    },
    "segmento": {
      "type": "string",
      "description" : "Se não existir, criaremos um novo objeto com esse nome."
    },
    "sigiloso": {
      "type": "boolean",
      "description": "Esconde ele dos demais usuários"
    },
    "site": {
      "type": "string"
    },
    "skype": {
      "type": "string"
    },
    "telefones": {
      "type": "array",
      "items": {
        "type": "string"
      }
    },
    "twitter": {
      "type": "string"
    }
  },
  "required": [
    "ativo",
    "constante",
    "nome"
  ]
}
``