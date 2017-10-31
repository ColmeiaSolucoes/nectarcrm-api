# Tipos - cadastros administrativos

Esta API permite o controle dos usuários do sistema.

Instruções para realizar a integração:

### URLs disponíveis

##### Usuário:
http://app.nectarcrm.com.br/crm/api/1/usuario/


Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
ativo | (boolean) | Marca se esse usuário está ativa para utilização
dataAtualizacao | (date) | Data da última atualização
dataCriacao | (date) | Data de criação
email | (string) | E-mail de acesso
foto | (string) | Imagem da foto do usuário 
id | (long) | Identificador no sistema
login | (string) | Login utilizado do usuário
nome | (string) | Nome do usuário

Exemplo
```js
    [
      {
        "ativo": true,
        "dataAtualizacao": "2017-10-30T07:13:31-02:00",
        "dataCriacao": "2015-01-19T03:40:25-02:00",
        "email": "email@dominio.com.br",
        "foto": "imagem.png",
        "id": 1,
        "login": "login_do_usuario",
        "nome": "Nome do usuario"
      }
    ]
```