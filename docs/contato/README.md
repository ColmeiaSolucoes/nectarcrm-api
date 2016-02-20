# Contato Resource

Esta API permite o controle total dos contatos (Leads, Suspects, Prospects, Clientes, etc.). Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/contatos/

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema

Propriedade | Tipo | Descricao
------------ | -------------
ativo | (boolean) | Se está ou não ativo no sistema
autor | (object) | Autor do contato
autorAtualizacao | (object) | Quem fez a última atualização
camposPersonalizados | (properties){"campo 1": "valor 1", "campo 2": "valor 2"} | Campos criados para uso no NectarCRM
categoria | (string) | Categoria do contato (se não tiver, será criado)
cnpj | (string) | CNPJ do contato
cnpj | (string) | CPF do contato
constante | (integer) | 0 = Clientes, 1 = Prospects, 2 = Suspects, 3 = Leads, 4 = Contatos relacionados, 5 = Descartados
contatos | (array)(contato) | Contatos relacionados (pessoas)
dataAtualizacao | (datetime) | Última data de atualização
dataCriacao | (datetime) | Data de criação desse contato
emails | (array)["string"] | E-mails do contato
facebook | (string) | Facebook do contato
id | (long) | Identificador do contato no sistema
indicadoPor | (string) | Campo de indicação
linkedin | (string) | Linkedin
nome | (string) | Nome do contato
observacao | (string) | Observação do contato
origem | (string) | Origem do contato (se não tiver, será criado)
razaoSocial | (string) | Razão social do contato
receitaAnual | (string) | Receita anual prevista do contato
responsavel | (string) | Quem será responsável por esse contato
segmento | (string) | Origem do contato (se não tiver, será criado)
sigiloso | (boolean) | Se for sigiloso, apenas você e administradores verão.
site | (string) | Website do contato
skype | (string) | Skype do contato
telefones | (array)["string"] | Telefones do contato
twitter | (string) | Twitter do contato

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
      "description": "0 = CLIENTE, 1 = PROSPECT, 2 = SUSPECT, 3 = LEAD, 4 = CONTATO_RELACIONADO, 5 = DESCARTADO"
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