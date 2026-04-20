# Tabela Dinâmica Resource

Esta API permite controlar **Tabelas Dinâmicas** — estruturas tabulares customizáveis que podem ser anexadas a um Contato, Oportunidade ou Qualificação. Uma tabela dinâmica é uma instância de um **Modelo de Tabela** (`TableTemplate`) que define as colunas (rótulo, tipo, posição, obrigatoriedade etc.). As linhas com os dados são gerenciadas separadamente.

Veja as instruções de como realizar a integração abaixo.

> **Importante:** este recurso depende do seu plano contratado. Caso não esteja disponível, os endpoints retornam **403**.

Instruções para realizar a integração:

URL
https://app.nectarcrm.com.br/crm/api/1/table/
* Alias: /tabela, /tables, /tabelas

### Endpoints disponíveis
    Listagem: GET /table/
    Inserção: POST /table/
    Visualização: GET /table/{id}
    Atualização: PUT /table/{id}
    Buscar/criar tabela relacionada a um objeto: GET /table/findRelatedTable
    Listar linhas da tabela: GET /table/{tableId}/rows/
    Listar linhas (filtros alternativos): GET /table/rows
    Inserir linha: POST /table/{tableId}/row/
    Atualizar linha: PUT /table/{tableId}/row/{rowId}
    Excluir linha: DELETE /table/{tableId}/row/{rowId}
    Exportar tabela (CSV): GET /table/export/{id}

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)
* &displayLength=x (integer) Quantidade de objetos por página (máximo 200)
* &ignorePagination=true (boolean) Retorna todos os registros sem paginação

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

## Schema Table

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
id | (long) | Identificador da tabela no sistema
tableTemplate | (object[[modelo-tabela](#modelo-de-tabela-tabletemplate)]) | Modelo que define as colunas da tabela (obrigatório na criação)
contact | (object[[contato](../contato)]) | Contato ao qual a tabela está vinculada (opcional)
opportunity | (object[[oportunidade](../oportunidade)]) | Oportunidade à qual a tabela está vinculada (opcional)
leadboard | (object[[qualificacao](../qualificacao)]) | Qualificação (leadboard) à qual a tabela está vinculada (opcional)

> **Regra de vínculo:** uma tabela deve estar vinculada a **exatamente um** dos três objetos pais (`contact`, `opportunity` ou `leadboard`). A referência é feita pelo `id` do objeto pai.

### Códigos de seção (`section`)

Diversos endpoints desta API (`findRelatedTable`, `/table/rows`, etc.) recebem um parâmetro `section` que identifica o **tipo do objeto pai** ao qual a tabela está vinculada. Use sempre um dos três códigos abaixo — combinado com o `objectId` correspondente:

Código (`section`) | Objeto pai | Propriedade no payload
:---: | ------------ | -------------
**404** | Contato | `contact`
**443** | Oportunidade | `opportunity`
**476** | Qualificação (Leadboard) | `leadboard`

> Exemplo: para operar sobre uma tabela de um contato cujo `id` é `25`, use `section=404&objectId=25`; ao criar a tabela via `POST /table/`, envie `"contact": { "id": 25 }` no body.

Exemplo
```js
    {
        "id": 57,
        "tableTemplate": {
            "id": 10,
            "nome": "Plano de ação",
            "alias": "plano_acao"
        },
        "opportunity": {
            "id": 456,
            "nome": "Venda Enterprise"
        }
    }
```

## Schema TableRow (linha da tabela)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
id | (long) | Identificador da linha no sistema
position | (integer) | Posição/ordenação da linha dentro da tabela
values | (array[[TableRowValue](#schema-tablerowvalue-valor-de-coluna)]) | Lista dos valores preenchidos em cada coluna

Exemplo
```js
    {
        "id": 8001,
        "position": 1,
        "values": [
            {
                "id": 12001,
                "column": { "position": 0 },
                "value": "Enviar proposta"
            },
            {
                "id": 12002,
                "column": { "position": 1 },
                "value": "2026-05-15"
            },
            {
                "id": 12003,
                "column": { "position": 2 },
                "value": "Em andamento"
            }
        ]
    }
```

## Schema TableRowValue (valor de coluna)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
id | (long) | Identificador do valor no sistema
column | (object) | Referência à coluna do modelo — deve conter `position` (a mesma `position` da coluna no `TableTemplate`)
value | (string) | Conteúdo preenchido. Sempre enviado como **string**, mesmo para números, datas ou booleanos

> **Observação:** cada valor é associado à coluna do modelo pela propriedade `position`. Envie apenas valores preenchidos — entradas vazias são ignoradas e não são armazenadas.

## Modelo de Tabela (TableTemplate)

As colunas da tabela dinâmica são definidas em um `TableTemplate` separado, acessível em `/api/1/table-template/` (aliases: `/modelo-tabela`, `/modelo-tabelas`, `/tables-template`). Cada coluna possui:

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
id | (long) | Identificador da coluna
label | (string) | Rótulo exibido no cabeçalho
alias | (string) | Identificador único em texto
type | (integer) | Tipo da coluna: 0 = Número, 1 = Texto, 2 = Data, 3 = Moeda, 4 = Booleano, 5 = Lista, 6 = Texto longo, 7 = Radio, 8 = URL, 11 = Checkbox, 12 = Fracionário
position | (integer) | Posição da coluna na tabela (usada para mapear os valores nas linhas)
mandatory | (boolean) | Define se o preenchimento é obrigatório
header | (boolean) | Define se a coluna aparece como cabeçalho
isUnique | (boolean) | Não permite duplicados nessa coluna
options | (string) | Opções separadas por `;` para tipo Lista/Radio/Checkbox
defaultValue | (string) | Valor padrão da coluna

## Fluxo para adicionar dados

A adição de dados em uma Tabela Dinâmica segue 3 etapas:

1. **Garantir o modelo** — ter um `TableTemplate` cadastrado com as colunas desejadas
2. **Criar a tabela** — `POST /table/` para instanciar o modelo e vincular a um Contato, Oportunidade ou Qualificação
3. **Inserir linhas** — `POST /table/{tableId}/row/` para cada registro a ser armazenado

### 1. Criar uma Tabela Dinâmica

Method: **POST**
https://app.nectarcrm.com.br/crm/api/1/table/

Vincule **apenas um** dos três pais (`contact`, `opportunity` ou `leadboard`):

Exemplo — tabela vinculada a uma Oportunidade:
```json
    {
        "tableTemplate": {
            "id": 10
        },
        "opportunity": {
            "id": 456
        }
    }
```

Exemplo — tabela vinculada a um Contato:
```json
    {
        "tableTemplate": {
            "id": 10
        },
        "contact": {
            "id": 141960
        }
    }
```

Exemplo — tabela vinculada a uma Qualificação:
```json
    {
        "tableTemplate": {
            "id": 10
        },
        "leadboard": {
            "id": 321
        }
    }
```

### 2. Inserir linhas (dados)

Method: **POST**
https://app.nectarcrm.com.br/crm/api/1/table/{tableId}/row/

Cada entrada de `values` deve referenciar a coluna por sua `position` (conforme definido no `TableTemplate`). Valores são sempre strings.

```json
    {
        "position": 1,
        "values": [
            {
                "column": { "position": 0 },
                "value": "Enviar proposta"
            },
            {
                "column": { "position": 1 },
                "value": "2026-05-15"
            },
            {
                "column": { "position": 2 },
                "value": "Em andamento"
            }
        ]
    }
```

Resposta de sucesso:
```json
    {
        "success": true,
        "row": {
            "id": 8001,
            "position": 1,
            "values": [ /* ... */ ]
        }
    }
```

> **Permissão extra:** para inserir ou editar linhas em uma tabela vinculada a uma Oportunidade, o usuário precisa ter permissão comercial ou administrativa. Sem isso a API responde **400**.

### 3. Atualizar uma linha existente

Method: **PUT**
https://app.nectarcrm.com.br/crm/api/1/table/{tableId}/row/{rowId}

Envie apenas os `values` que devem ser atualizados. Use o `id` do `TableRowValue` quando quiser atualizar um valor específico:
```json
    {
        "values": [
            {
                "id": 12003,
                "column": { "position": 2 },
                "value": "Concluído"
            }
        ]
    }
```

### 4. Excluir uma linha

Method: **DELETE**
https://app.nectarcrm.com.br/crm/api/1/table/{tableId}/row/{rowId}

## Exemplo — fluxo completo ao adicionar linha na tabela de um contato

Dados usados no exemplo:
* `tableTemplateId` = **10** (ID do modelo de tabela já cadastrado)
* `objectId` = **141960** (ID do contato em consulta)
* `section` = **404** (código da seção Contato)

### Passo 1 — Verificar se o contato já tem a tabela

Com `persistWhenDefaultRows=true`, a API cria a tabela automaticamente caso o modelo possua linhas padrão; caso contrário a resposta vem **vazia**.

```
GET /api/1/table/findRelatedTable?tableTemplateId=10&section=404&objectId=141960&persistWhenDefaultRows=true
```

```bash
curl "https://app.nectarcrm.com.br/crm/api/1/table/findRelatedTable?tableTemplateId=10&section=404&objectId=141960&persistWhenDefaultRows=true" \
  -H "Access-Token: SEU_TOKEN"
```

Possíveis respostas:

* **Tabela já existe** (ou foi criada automaticamente a partir das linhas padrão):
```json
    {
        "id": 57,
        "tableTemplate": { "id": 10, "nome": "Plano de ação" },
        "contact": { "id": 141960 }
    }
```
Guarde o `id` retornado — é o `tableId` usado nas próximas chamadas. Pule para o **Passo 3**.

* **Tabela não existe e o modelo não tem linhas padrão** (resposta `200` com corpo vazio):
```
(sem conteúdo)
```
Nesse caso, siga para o **Passo 2** para criar a tabela antes de inserir a linha.

### Passo 2 — Criar a tabela para o contato (somente se o Passo 1 veio vazio)

```
POST /api/1/table/
```

```bash
curl -X POST https://app.nectarcrm.com.br/crm/api/1/table/ \
  -H "Access-Token: SEU_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "tableTemplate": { "id": 10 },
    "contact": { "id": 141960 }
  }'
```

Resposta:
```json
    {
        "id": 57,
        "tableTemplate": { "id": 10, "nome": "Plano de ação" },
        "contact": { "id": 141960 }
    }
```

> Use a propriedade correta conforme a origem do registro:
> * **Contato** → `"contact": { "id": ... }` (section `404`)
> * **Oportunidade** → `"opportunity": { "id": ... }` (section `443`)
> * **Qualificação** → `"leadboard": { "id": ... }` (section `476`)

### Passo 3 — Inserir a linha na tabela

Com o `tableId` em mãos (do Passo 1 ou 2), envie os valores. Cada valor deve referenciar a coluna pela sua `position` no modelo e vir como string.

```
POST /api/1/table/57/row/
```

```bash
curl -X POST https://app.nectarcrm.com.br/crm/api/1/table/57/row/ \
  -H "Access-Token: SEU_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "position": 1,
    "values": [
      { "column": { "position": 0 }, "value": "Enviar proposta" },
      { "column": { "position": 1 }, "value": "2026-05-15" },
      { "column": { "position": 2 }, "value": "Em andamento" }
    ]
  }'
```

Resposta:
```json
    {
        "success": true,
        "row": {
            "id": 8001,
            "position": 1,
            "values": [
                { "id": 12001, "column": { "position": 0 }, "value": "Enviar proposta" },
                { "id": 12002, "column": { "position": 1 }, "value": "2026-05-15" },
                { "id": 12003, "column": { "position": 2 }, "value": "Em andamento" }
            ]
        }
    }
```

### Resumo do fluxo

```
  ┌───────────────────────────────────────────────────────┐
  │ 1. GET /table/findRelatedTable                        │
  │    ?tableTemplateId=10&section=404                    │
  │    &objectId=141960&persistWhenDefaultRows=true       │
  └───────────────────────────────────────────────────────┘
                         │
               resposta com id?
                ┌────────┴────────┐
              sim                 não
               │                   │
               │     ┌─────────────▼─────────────────────┐
               │     │ 2. POST /table/                   │
               │     │    { tableTemplate:{id:10},       │
               │     │      contact:{id:141960} }        │
               │     │    → resposta { id: 57, ... }     │
               │     └─────────────┬─────────────────────┘
               │                   │
               └────────┬──────────┘
                        ▼
           ┌────────────────────────────────┐
           │ 3. POST /table/{tableId}/row/  │
           │    { position, values:[...] }  │
           └────────────────────────────────┘
```

## Endpoints adicionais

### Buscar (ou criar) a tabela relacionada a um objeto

Method: **GET**
https://app.nectarcrm.com.br/crm/api/1/table/findRelatedTable

Busca a tabela associada a um modelo + objeto pai. Se não existir e o modelo possuir linhas padrão, a API cria a tabela automaticamente clonando essas linhas.

Parâmetros:
* &tableTemplateId=x (long) ID do modelo (obrigatório — pode ser substituído por `alias`)
* &alias=x (string) Alias do modelo (alternativa a `tableTemplateId`)
* &section=x (long) Seção do objeto pai (obrigatório). Valores aceitos:
    * `404` = Contato
    * `443` = Oportunidade
    * `476` = Qualificação
* &objectId=x (long) ID do objeto pai (obrigatório)
* &persistWhenDefaultRows=true (boolean) Se `true`, persiste a tabela e as linhas padrão do modelo quando a tabela ainda não existir

Exemplo:
```
GET /api/1/table/findRelatedTable?tableTemplateId=10&section=443&objectId=456&persistWhenDefaultRows=true
```

### Listar linhas de uma tabela

Method: **GET**
https://app.nectarcrm.com.br/crm/api/1/table/{tableId}/rows/

Parâmetros:
* &page=x (integer) Paginação
* &displayLength=x (integer) Itens por página (máximo 200)
* &ignorePagination=true (boolean) Retorna todas as linhas sem paginação

### Listar linhas com filtros alternativos

Method: **GET**
https://app.nectarcrm.com.br/crm/api/1/table/rows

Permite listar linhas filtrando pelo par `tableTemplateId + objectId` sem precisar do `tableId`.

Parâmetros:
* &tableId=x (long) ID da tabela (alternativa)
* &tableTemplateId=x (long) ID do modelo
* &section=x (long) Seção do objeto pai (404, 443 ou 476)
* &objectId=x (long) ID do objeto pai

### Exportar tabela em CSV

Method: **GET**
https://app.nectarcrm.com.br/crm/api/1/table/export/{id}

Parâmetros:
* &charset=UTF-8 (string) Charset do arquivo gerado (padrão: UTF-8)

## Códigos de resposta específicos

+ 200 — Sucesso
+ 400 — Parâmetros obrigatórios ausentes ou usuário sem as permissões necessárias
+ 403 — Recurso não disponível no plano contratado
+ 404 — Tabela ou linha não encontrada
+ 409 — Conflito de regra de negócio (retorna `{ erros: [...] }`)
+ 500 — Erro interno
