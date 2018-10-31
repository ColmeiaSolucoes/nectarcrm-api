# Grupo Resource

Esta API permite o controle total das equipes. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/equipe/

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
ativo | (boolean) | Marca se essa equipe está ativa para utilização
descricao | (string) | Descrição da equipe
id | (long) | Identificador no sistema
padrao | (boolean) | Define se a equipe é padrão
nome | (string) | Nome da Equipe

Exemplo
```js
    [
      {
        "ativo": true,
        "descricao": "Nossos desenvolvedores"
        "id": 1,
        "padrao": true,
        "nome": "Desenvolvedores",
      }
    ]
```