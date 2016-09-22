# Segmento Resource

Esta API permite o controle total das segmentos de contato. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/segmento/

Parâmetros de segmentogem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista todos objetos)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
ativo | (boolean) | Marca se essa segmento está ativa para utilização
descricao | (string) | Descrição da segmento
id | (long) | Identificador no sistema
nome | (string) | Nome da segmento

Exemplo
```js
    [
      {
        "ativo": true,
        "descricao": "Evento que realizamos"
        "id": 1,
        "nome": "Eventos",
      }
    ]
```