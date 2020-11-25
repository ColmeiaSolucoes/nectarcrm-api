# Compromisso Resource

Esta API permite o controle total das compromisso. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/compromissos/

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
assunto | (string) | Assunto do compromisso
autor | (object) | Autor do compromisso
autorAtualizacao | (object) | Quem fez a última atualização
camposPersonalizados | (properties){"campo 1": "valor 1", "campo 2": "valor 2"} | Campos criados para uso no NectarCRM
cliente | (object) | Contato relacionado a venda
dataAtualizacao | (datetime iso8601) | Última data de atualização
dataCriacao | (datetime iso8601) | Data de criação desse compromisso
dataInicio | (datetime iso8601) | Data do inicio do compromisso
dataFim | (datetime) | Data do final do compromisso
descricao | (string) | Descrição do compromisso
diaInteiro | (boolean) | Marca se o compromisso dura o dia inteiro
endereco | (string) | Endereço do compromisso
id | (long) | Identificador no sistema
local | (string) | Local do compromisso
oportunidade | (object) | Oportunidade relacionado a venda
participantes | (array)(object) | Lista dos participantes do compromisso
responsavel | (object) | Quem será responsável por esse compromisso
status | (integer) | Status da compromisso (0 = Aberto, 1 = Realizado, 2 = Cancelado)
tipo | (object){"id", "nome"} | Tipo do compromisso (cadastrado, se não existir iremos incluir)

Exemplo
```js
    {
        "assunto": "Teste de compromisso",
        "camposPersonalizados": {
            "Campo 1": "Valor 1"
        },
        "cliente": {
          "id": 430,
          "nome": "Colmeia Soluções"
        },
        "dataInicio":"2016-03-30T10:00:00-0300",
        "dataFim":"2016-03-30T12:00:00-0300",
        "descricao": "Feriado",
        "diaInteiro": false,
        "endereco": "Rua 07, 394  Setor Europa - São Paulo",
        "oportunidade": {
          "id": 1,
          "nome": "Oportunidade de venda"
        },
        "participantes": [
            {
              "contato": {
                "id": 12,
                "nome": "José"
              }
            },
            {
              "usuario": {
                "id": 30,
                "login": "usuario@nectar.com.br"
              },
              "participar": true
            },
            {
              "email": "externo@nectar.com.br"
            }
        ],
        "responsavel": {
          "id": 12,
          "login": "usuario1",
          "nome": "Usuario 1"
        },
        "status": 1,
        "tipo": {
            "id": 1,
            "nome": "Reunião"
        }
      }
```
