# Contato Resource

Esta API permite o controle total dos contatos (Leads, Suspects, Prospects, Clientes, etc.). Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/contatos/

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)
* Seção: &constante=x (integer 0 = cliente, 1 = prospect, 2 = suspect, 3 = lead, 4 = contatos relacionados, 5 = descartados)
* Data de criação: 
    * Inicio: &dataInicio=dd/MM/yyyy
    * Fim: &dataFim=dd/MM/yyyy
* Data atualização: 
    * Inicio: &dataInicioAtualizacao=dd/MM/yyyy
    * Fim: &dataFimAtualizacao=dd/MM/yyyy
* Responsáveis: &responsaveisId=X,Y - onde X e Y = ids do objeto [/usuario](./usuario)
* Origem: &origemId=x (integer) = ids do objeto [/origem](./origem)
* Segmento: &segmentoId=x (integer) = ids do objeto [/segmento](./segmento)

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
enderecos | (array)["object"] | Endereços do contato
facebook | (string) | Facebook do contato
id | (long) | Identificador do contato no sistema
indicadoPor | (string) | Campo de indicação
isEmpresa | (string) | Campo que diz se é ou não empresa (PJ ou PF)
linkedin | (string) | Linkedin
lista | (string) | Lista relacionada do contato
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
compromissos | (integer) | Quantidade de compromissos pendentes
oportunidades | (integer) | Quantidade de oportunidades pendentes
tarefas | (integer) | Quantidade de tarefas pendentes


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
	    "dataCriacao":"2016-03-11T10:00:00-03:00",
        "enderecos": [
          {
            "bairro": "Jardim São Paulo",
            "cep": "08465000",
            "complemento": "N 100",
            "estado": "São Paulo",
            "logradouro": "Rua 111",
            "municipio": "São Paulo",
            "numero": "0",
            "pais": "Brasil",
            "principal": true,
            "tipo": 2 //RESIDENCIAL = 0 / CORRESPONDENCIA = 1 / COMERCIAL_MATRIZ = 2 / COMERCIAL_FILIAL = 3 / COMERCIAL_RURAL = 4 / COMERCIAL_RURAL = 5
          }
        ],
        "emails": [
          "novo@trial.com.br"
        ],
        "facebook": "facebook1",
        "indicadoPor": "Fulano",
        "isJuridico": true,
        "linkedin": "linkedin1",
        "lista": "Lista 1",
        "nome": "Empresa 1",
        "observacao": "Observação qualquer",
        "origem": "Telefone",
        "razaoSocial": "Empresa 1 LTDA",
        "receitaAnual": 10000000,
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