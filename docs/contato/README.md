# Contato Resource

Esta API permite o controle total dos contatos (Leads, Suspects, Prospects, Clientes, etc.). Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/contatos/

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
ativo | (boolean) | Se está ou não ativo no sistema
autor | (object) | Autor do contato
autorAtualizacao | (object) | Quem fez a última atualização
camposPersonalizados | (properties){"campo 1": "valor 1", "campo 2": "valor 2"} | Campos criados para uso no NectarCRM
categoria | (string) | Categoria do contato (se não tiver, será criado)
cnpj | (string) | CNPJ do contato
cpf | (string) | CPF do contato
constante | (integer) | Tipo do contato (0 = Clientes, 1 = Prospects, 2 = Suspects, 3 = Leads, 4 = Contatos relacionados, 5 = Descartados)
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
responsavel | (object) | Quem será responsável por esse contato
segmento | (string) | Origem do contato (se não tiver, será criado)
sigiloso | (boolean) | Se for sigiloso, apenas você e administradores verão.
site | (string) | Website do contato
skype | (string) | Skype do contato
telefones | (array)["string"] | Telefones do contato
twitter | (string) | Twitter do contato


Exemplo
```js
    {
        "ativo": true,
        "autor": {
          "id": 12,
          "login": "contato1@teste.com.br",
          "nome": "Usuario 1"
        },
        "camposPersonalizados": {
            "campo1": "Teste",
            "campo2": "Teste 2"
        },
        "categoria": "Cliente ativo",
        "cnpj": "99.999.999/9999-99",
        "constante": 2,
        "contatos": [
          {
              "nome": "Contato-relacionado",
              "cargo": "Diretor",
              "emails": [
                  "novo@trial.com.br"
                ]
          }
        ],
        "emails": [
          "novo@trial.com.br"
        ],
        "facebook": "facebook1",
        "indicadoPor": "Fulano",
        "linkedin": "linkedin1",
        "nome": "Contato 1",
        "observacao": "Observação qualquer",
        "origem": "Telefone",
        "razaoSocial": "Contato 1 LTDA",
        "receitaAnual": "R$ 10.000.000,00",
        "responsavel": {
          "id": 12,
          "login": "contato1@teste.com.br", //se nao tiver id, procura por esse
          "nome": "Usuario 1" //se nao tiver id, procura por esse
        },
        "segmento": "Advocacia ",
        "sigiloso": false,
        "site": "www.site.com.br",
        "skype": "skype1",
        "telefones": [
          "99999999999",
          "11999999999"
        ],
        "twitter": "twitter1"
    }
```