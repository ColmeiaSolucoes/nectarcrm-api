# Publicação/Feedback Resource

Esta API permite publicar notas/feedbacks nos objetos (contato, oportunidades, tarefas...). 
Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/publicacao/

### Endpoints disponíveis
    Listagem: GET /publicacao/
    Inserção: POST /publicacao/
    Inserção com anexos: POST /publicacao/incluirComAnexos
        Content-Type: multipart/form-data
        Recebe dois parametros: publicacao (String json, como definido no esquema)
                                anexos (lista de arquivos binarios)
    Ex: curl -i -X POST -H "Content-Type: multipart/form-data" -H "Access-Token: token" -F publicacao='{"oportunidade":{"id":2},"assunto":"Exemplo publicacao com anexos","descricao":"Esse é um exemplo de publicacao com anexos"}' -F anexos=@./example.txt  http://app.nectarcrm.com.br/crm/api/1/publicacao/incluirComAnexos
    Visualização: GET /publicacao/{id}
    Incluir comentário: POST /publicacao/{publicacaoId}/comentario 
        BODY { "autor": { "nome": "Teste" }, "descricao": "Teste" }
    Listas comentários: GET /publicacao/{publicacaoId}/comentarios

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
assunto | (string) | Assunto da nota/feedback
automatica | (boolean) | Mostra se é uma publicação automatica (que o sistema criou)
autor | (object[[usuario](../usuario)]) | Autor dessa publicação
compromisso | (object[[compromisso](../compromisso)]) | Vincula essa publicação a compromisso
contato | (object[[contato](../contato)]) | Vincula essa publicação a um contato
dataCriacao | (date) | Data da criação da publicação
dataAtualizacao | (date) | Data da última atualização
descricao | (html) | HTML do que foi escrito
importante | (boolean) | Mostra se é uma publicação marcada como importante
oportunidade | (object[[oportunidade](../oportunidade)]) | Vincula essa publicação a oportunidade
qtdeComentarios | (int) | Mostra a quantidade de comentários feitos nessa publicação
tarefa | (object[[tarefa](../tarefa)]) | Vincula essa publicação a tarefa
anexos | (array[anexoPublicacao]) | Anexos vinculados à Publicação

Exemplo
```js
    [
        {
            "id": 1,
            "autor": {
                "id": 19,
                "login": "login_usuario_teste@dominio.com",
                "nome": "Usuario de teste"
            },
            "dataCriacao": "2016-04-13T19:07:27-03:00",
            "dataAtualizacao": "2016-04-13T19:07:27-03:00",
            "qtdeComentarios": 0,
            "oportunidade": {
                "id": 10,
                "nome": "Oportunidade de empresa 1",
                "cliente": {
                    "id": 20,
                    "nome": "Empresa teste"
                },
                "funilVenda": {},
                "temperatura": "",
                "valorTotalDescontos": 0,
                "origem": {}
            },
            "contato": {
                "id": 20,
                "nome": "Empresa teste"
            },
            "assunto": "Editou uma oportunidade",
            "descricao": "Teste de edição<br>Data de fechamento: 19/04/2016 <i class='icon-long-arrow-right'></i> <a>13/05/2016</a>",
            "anexos": {
                "id":31,
                "nome": "fotoProfile.jpg"
            }
        }
    ]
```
