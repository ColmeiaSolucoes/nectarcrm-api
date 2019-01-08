# Campo Personalizado Resource

Esta API permite o controle total das origens de contato. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/campoPersonalizado/
* Alias: /camposPersonalizados, /customField, /customFields

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
ativo | (boolean) | Marca se esse campo está ou não ativo
alias | (string) | Identificador único baseado no nome
id | (long) | Identificador no sistema
mostrarFiltro | (boolean) | Marca se esse campo aparece no filtro das listagens do nectar  
nome | (string) | Nome do campo personalizado
obrigatorio | (string) | Marca se o campo é ou não obrigatório o preenchimento
opcoes | (array)(string) | Opções em lista dos campos quando utilizando campo multi-valorado  
secao | (string) | Seção agrupadora do campo que ele está vinculado  
sequencia | (int) | Ordem do campo na seção que ele está  
relacionado | (string) | A qual página do nectar ele está vinculado (Contato, Oportunidade, Tarefa, Compromisso)
tipo | (int) | Tipo do campo: 0 = Número, 1 = Texto, 2 = Data, 3 = Moeda, 4 = Booleano, 5 = Lista de opções, 6 = Texto, 7 = Radio, 8 = URL, 9 = Contato, 10 = CNAE, 11 = Checkbox  

Exemplo
```js
    [
    {
        "id": 180,
        "nome": "Campo extra 1",
        "alias": "campo_extra_1",
        "tipo": 1,
        "obrigatorio": false,
        "relacionado": "Contato",
        "opcoes": [],
        "sequencia": 1,
        "secao": {
            "id": 1,
            "ativo": true,
            "nome": "Secao dos campos extras"
        },
        "mostrarFiltro": true
    }
    ]
```

## Métodos adicionais

#### /customField/fields/{objectType}

Retorna os campos escolhidos no sistema para a montagem de tela

* ObjectType { 
    1: Contatos,
    2: Oportunidades
}

Schema Info

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
alias | (string) | Identificador único baseado no label
campoPersonalizado | (object[campoPersonalizado]) | Campo personalizado referenciado
id | (long) | Identificador no sistema
label | (string) | Identificador do campo em texto
fieldType | (string) | personalized = Campo personalizado, "default" = Campo do sistema padrão
obrigatorio | (boolean) | Marca se esse campo é ou não obrigatório
property | (int) | Tipo do campo personalizado (0 = Número, 1 = Texto, 2 = Data, 3 = Moeda, 4 = Booleano, 5 = Lista de opções, 6 = Texto, 7 = Radio, 8 = URL, 9 = Contato, 10 = CNAE, 11 = Checkbox)
removable | (bool) | Se o campo pode ou não ser removido da visão
valor | (string) | Conteúdo demonstrativo do campo (caso visto com um contato/oportunidade)

```js

    {
        "campoPersonalizado": {
            "tipo": 1,
            "obrigatorio": false,
            "hidden": false,
            "alias": "1.3.1.2-cnpj_informado",
            "campoPersonalizadoPai": null,
            "id": 29691,
            "label": "1.3.1.2-CNPJ Informado"
        },
        "obrigatorio": false,
        "removable": true,
        "property": 1,
        "valor": null,
        "alias": "1.3.1.2-cnpj_informado",
        "label": "1.3.1.2-CNPJ Informado",
        "id": 29691,
        "fieldType": "personalized"
    }
```