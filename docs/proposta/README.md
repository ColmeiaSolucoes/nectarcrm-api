# Proposta Resource

Esta API permite o controle das propostas das oportunidades. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/proposta/

Parâmetros de listagem:
* &status=x (integer) filtra os status da proposta
* &page=x (integer) Organiza a listagem de objetos por páginas

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

# Endpoint para consultar propostas de uma determinada oportunidade

URL
http://app.nectarcrm.com.br/crm/api/1/proposta/opportunity/{id_oportunidade}

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
id | (long) | Identificador no sistema
status | (integer) | Código do status da proposta
versao | (integer) | Versão da proposta na oportunidade
numero | (integer) | Número identificador da proposta
codigo | (string) | Código da proposta gerada
publicUrl | (string) | Url pública para download da proposta
dataProposta | (date) | Data de geração da proposta
modeloProposta | (object) | Dados do modelo de proposta utilizado
oportunidade | (object) | Dados da oportunidade da proposta
autor | (object|entidade) | Dados do autor da proposta
dataCriacao | (date) | Data de criação da proposta
destinatario | (string) | Destinatário da proposta
codigoFormatado | (string) | Código da proposta formatado
statusLabel | (string) | Label do status da proposta

Exemplo
```js
    [
      {
        "id": 87135,
        "status": 2,
        "versao": 2,
        "numero": 1,
        "codigo": "02001/2019",
        "publicUrl": "https://app.nectarcrm.com.br/crm/PublicAttachment?data=8wNaH28BG2Pj6n0xs1K05jjDKQIv4pyCX",
        "dataProposta": "2019-02-19T17:16:19.420Z",
        "modeloProposta": {
            "id": 30423,
            "nome": "Nome do modelo de proposta"
        },
        "oportunidade": {
            "id": 1826618,
            "nome": "Oportunidade Cliente",
            "cliente": {
                "id": 1395938,
                "codigo": "183497",
                "nome": "José da Silva",
                "emailPrincipal": "josedasilva@gmail.com",
                "email": "josedasilva@gmail.com"
            },
            "funilVenda": {},
            "temperatura": "",
            "valorTotalDescontos": 0,
            "origem": {}
        },
        "autor": {
            "id": 13361,
            "login": "fulano@nectacrm.com.br",
            "nome": "Fulano",
            "foto": "13360-foto-13361.png"
        },
        "dataCriacao": "2019-02-19T17:16:19.420Z",
        "destinatario": "Maria da Silva",
        "codigoFormatado": "02001/2019",
        "statusLabel": "Aprovada"
    },
    ]
```