# Oportunidade Resource

Esta API permite o controle total das oportunidade. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/oportunidades/

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema
```js
{
  "type": "object",
  "properties": {
    "autor": {
      "type": "object",
      "properties": {
        "id": {
          "type": "integer"
        },
        "nome": {
          "type": "string"
        }
      }
    },
    "codigo": {
      "type": "string"
    },
    "dataLimite": {
      "type": "timestamp"
    },
    "etapa": {
      "type": "integer"
    },
    "id": {
      "type": "integer"
    },
    "itens": {
      "id": "itens",
      "type": "array",
      "items": [{
        "id": {
            "type": "integer"
        },
        "nome": {
            "type": "string"
        }
        "valor": {
            "type": "float"
        }
      }]
    },
    "nome": {
      "type": "string"
    },
    "observacao": {
      "type": "string"
    },
    "pipeline": {
      "type": "string"
    },
    "probabilidade": {
      "type": "integer"
    },
    "responsavel": {
      "type": "object",
      "properties": {
        "id": {
          "id": "id",
          "type": "integer"
        },
        "nome": {
          "id": "nome",
          "type": "string"
        }
      }
    },
    "status": {
      "id": "status",
      "type": "integer",
      "description": "1 = EM ANDAMENTO, 2 = GANHO, 3 = PERDIDO, 4 = CANCELADO"
    },
    "valorAvulso": {
      "type": "float"
    },
    "valorMensal": {
      "type": "float"
    },
    "camposPersonalizados": {
      "type": "object",
      "properties": {}
    },
    "cliente": {
      "id": "cliente",
      "type": "object",
      "properties": {
        "id": {
          "type": "long"
        }
      }
    }
  },
  "required": [
    "nome",
    "cliente"
  ]
}
``