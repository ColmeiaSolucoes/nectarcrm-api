# Contato Resource

Esta API permite o controle total dos contatos (Leads, Suspects, Prospects, Clientes, etc.). Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/contatos/


### Endpoints disponíveis
    Listagem: GET /contatos/
    Inserção: POST /contatos/
    Visualização: GET /contatos/{id}
    Atualização: PUT /contatos/{id}
    * Inserção/Atualização (upsert): POST /contacts/upsert
    Exclusão: DELETE /contatos/
    Procura por e-mail: GET /contatos/email/{email@dominio.*} (use * para busca por like)
    Procura por telefone: GET /contatos/telefone/{6299999999*} (use * para busca por like)
    Procura por CNPJ: GET /contatos/cnpj/{cnpj}
    Procura por CPF: GET /contatos/cpf/{cpf}
    Estatísticas por contato: GET /contatos/statistics/{contatoId}
    Próxima atividade: /contatos/{contatoId}/proximaAtividade
    
#### Parametros de Upsert (inserção / atualização):
* **mail** - irá buscar por e-mail (email tem prioridade acima do telefone);
* **phone** - irá buscar por telefone (caso nao venha o parametro de email, vamos usar de telefone);
* **ignoreRequiredFields**- mesmo parametro de ignorarCamposObrigatorios de atualizacao/insercao;
* **ignoreValidations** - mesmo parametro de ignorarValidacoes de atualizacao/insercao;
* **exactMatch** - aceito true/false, serve para indicar se iremos buscar o email/telefone exato ou nao (por padrao sempre true)
* **Com propriedade de email**: vamos buscar com iniciados com o texto. Ex: Caso seja true -- rafael@gm... || Caso seja false(ou nao seja passado): rafael@gm
* **Com propriedade de telefone**: vamos buscar contendo o texto caso seja true. Ex: True -- ...551299186... || False -- 551299186


#### Parâmetros de listagem:
+ &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)
+ &displayLength (optional, int) - Quantidade de objetos a serem listados (máximo 50)
+ &nome (optional, string) - Nome ou código do contato
+ &constante (optional, int) - 0 = cliente, 1 = prospect, 2 = suspect, 3 = lead, 5 = descartados
+ &dataInicio (optional, date) - Data de criação inicial (dd/MM/yyyy)
+ &dataFim (optional, date) - Data de criação final (dd/MM/yyyy)
+ &dataInicioAtualizacao (optional, date) - Data atualização inicial (dd/MM/yyyy)
+ &dataFimAtualizacao (optional, date) - Data atualização final (dd/MM/yyyy)
+ &listasIds (optional, array) - X,Y,Z... (array integer) onde X,Y e Z são ids do objeto  [/lista](../lista)
+ &origemId (optional, int) - id do objeto [/origem](../origem)
+ &segmentoId (optional, int) - id do objeto [/segmento](../segmento)
+ &responsaveisId (optional, array) - X,Y,Z... (array integer) onde X,Y e Z são ids do objeto [/usuario](../usuario)
+ &camposPersonalizados (optional, json) - filtro de campos personalizados
+ &useAlias (optional, string) - ao filtrar campos personalizados, utiliza o "alias" do campo personalizado ao invés do nome do campo.  
+ &exato (optional, boolean default false) - deixa a busca exata (encontra exatamente o valor digitado)

    Dica: quando estiver listando, você pode escolher os campos que deseja trazer enviando o parâmetro "attribute" na URL.
    
    Exemplo:
    /crm/api/1/contatos?attribute=id&attribute=nome
    Apenas id e nome virá na listagem.


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
codigo | (string) | Código do contato
cpf | (string) | CPF do contato
constante | (integer) | Tipo do contato (0 = Clientes, 1 = Prospects, 2 = Suspects, 3 = Leads, 5 = Descartados)
contatos | (array)(contato) | Contatos relacionados (pessoas)
contaPai | (object)["contato"] | Conta pai que esse contato se relaciona (diferente de empresaAtual) 
dataAtualizacao | (datetime) | Última data de atualização
dataCriacao | (datetime) | Data de criação desse contato
emails | (array)["string"] | E-mails do contato
empresa | (boolean) | Campo que diz se é ou não empresa (PJ ou PF)
empresaAtual | (object)["contato"] | Empresa atual em que o contato está vinculado
enderecos | (array)["object"] | Endereços do contato
facebook | (string) | Facebook do contato
id | (long) | Identificador do contato no sistema
indicadoPor | (string) | Campo de indicação
linkedin | (string) | Linkedin
lista | (string) | Lista relacionada do contato
listas | (array)["string"] | Listas relacionadas do contato
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
regiaoPais | (object)["Pais"] | País do contato
regiaoEstado | (object)["Estado"] | Estado do contato
regiaoMunicipio | (object)["Municipio"] | Cidade do contato


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
	"codigo": "ABC-001",
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
            "tipo": 2 //RESIDENCIAL = 0 / CORRESPONDENCIA = 1 / COMERCIAL_MATRIZ = 2 / COMERCIAL_FILIAL = 3 / COMERCIAL_RURAL = 4 / COMERCIAL_RURAL = 5,
	    "searchByCep": true //parametro para indicar a busca automatica por CEP ao inserir endereço (válido apenas para Brasil)
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
        "listas": [
            { 
                "id": 1,
                "nome": "Lista 1"
            }, 
            { 
                "nome": "Lista 2"
            }
        ],
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
        "twitter": "twitter1",
	"regiaoPais": {
          "id": 1,
          "nome": "Brasil"
        },
	"regiaoEstado": {
          "id": 2,
          "nome": "São Paulo",
	  "sigla": "SP"
        },
	"regiaoMunicipio": {
          "id": 3,
          "nome": "Sorocaba"
        }
    }
```
