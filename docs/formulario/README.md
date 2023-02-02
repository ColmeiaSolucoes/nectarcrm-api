# Formulário Resource

Esta API permite controlar formulários. 
Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/formulario/

### Endpoints disponíveis
    Listagem: GET /formulario/
    Visualização: GET /formulario/{formularioId}

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
autor | (object[[usuario](../usuario)]) | Autor desse formulário
modeloFormulario | (object[modeloFormulario) | Vincula esse formulário a modelo template de formulario
dataCriacao | (date) | Data da criação de formulário
dataAtualizacao | (date) | Data da última atualização
dataPreenchimento | (date) | Data do preenchimento
preenchido | (boolean) | Parâmetro para indicar se o formulário está preenchido
respostas | (properties){"Pergunta 1": "resposta 1", "Pergunta 2": "resposta 2"} | Campos de respostas baseado nas perguntas do modelo de formulário
respostasObject | (object[valorCampoPersonalizado) | Campos de respostas com propriedades da pergunta

Exemplo
```js
    {
        "id": 1,
        "dataCriacao": "2018-04-05T15:44:09-03:00",
        "dataAtualizacao": "2018-08-13T15:01:49-03:00",
        "dataPreenchimento": "2018-08-13T15:01:49-03:00",
        "preenchido": true,
        "autor": {
            "id": 1,
            "login": "user1@domain.com",
            "nome": "User 1",
            "foto": "1-photo.png"
        },
        "autorAtualizacao": {
            "id": 19,
            "login": "user1@domain.com",
            "nome": "User 1",
            "foto": "1-photo.png"
        },
        "modeloFormulario": {
            "id": 1,
            "nome": "First form"
        },
        "respostas": {
            "First question": "true",
            "Second question": "value text"
        },
        "respostasObject": [ {
            "campoPersonalizado" : {
              "id" : 31021,
              "nome" : "Pergunta 1",
              "tipo" : 0,
              "obrigatorio" : false,
              "opcoes" : [ ],
              "opcoesPersonalizadas" : [ ],
              "sequencia" : 1,
              "secao" : {
                "ativo" : true,
                "nome" : "First Form",
                "id" : 2
              },
              "mostrarFiltro" : true,
              "escondido" : true
            },
            "obrigatorioFormulario": true,
            "valor" : "787",
            "id" : 698681
        } ]
    }
```
