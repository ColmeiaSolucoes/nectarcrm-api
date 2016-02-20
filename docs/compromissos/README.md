# Compromisso Resource

Esta API permite o controle total das compromisso. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/compromissos/

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
assunto | (string) | Assunto do compromisso
autor | (object) | Autor do contato
autorAtualizacao | (object) | Quem fez a última atualização
camposPersonalizados | (properties){"campo 1": "valor 1", "campo 2": "valor 2"} | Campos criados para uso no NectarCRM
cliente | (object) | Contato relacionado a venda
dataAtualizacao | (datetime) | Última data de atualização
dataCriacao | (datetime) | Data de criação desse contato
dataInicio | (datetime) | Data do inicio do compromisso
dataFim | (datetime) | Data do final do compromisso
descricao | (string) | Descrição do compromisso
diaInteiro | (boolean) | Marca se o compromisso dura o dia inteiro
endereco | (string) | Endereço do compromisso
id | (long) | Identificador no sistema
local | (string) | Local do compromisso
participantes | (array)(object) | Lista dos participantes do compromisso
responsavel | (object) | Quem será responsável por esse contato
status | (integer) | Status da compromisso (1 = Aberto, 2 = Finalizado, 3 = Cancelado)
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
        "dataFim": 1424203259000,
        "dataInicio": 1424080800000,
        "descricao": "Feriado",
        "diaInteiro": false,
        "endereco": "Rua 07, 394  Setor Europa - São Paulo",
        "participantes": [
          {
            "id": 12,
            "login": "usuario1",
            "nome": "Usuario 1",
            "participar": true
          }
        ],
        "responsavel": {
          "id": 12,
          "login": "usuario1",
          "nome": "Usuario 1"
        },
        "status": 1,
        "tipo": "Reunião"
      }
```