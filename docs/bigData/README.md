# BigData Resource

Esta API permite realizar a query de dados para integrar com serviços como PowerBI, QlikSense, etc.

Lembrando, somente usuários ADMIN com plano Enterprise conseguem acessar esse endpoint.

Instruções para realizar a integração:

URL
https://app.nectarcrm.com.br/crm/api/1/big-data/

Parâmetros de listagem:
* &aggregator=x (integer) Agrupador para seleção do período de datas (criação, atualização, limite, conclusão e prorrogadas). Conferir abaixo quais estão disponíveis para cada tabela;
* &initialDate=x (string) Data de início desejado para a query. Precisa estar no formato `YYYY-MM-DD`;
* &endDate=x (string) Data fim desejada para a query. Precisa estar no formato `YYYY-MM-DD`;
* &ignoreSections=x (string) Seções de campos para serem excluídos da requisição. Mais detalhes abaixo;

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Endpoints disponíveis com seus agrupadores:

- /opportunity -- Criação, limite, conclusão, atualização e prorrogação;
- /opportunity-with-products -- Criação, limite, conclusão, atualização e prorrogação;
- /contact -- Criação, atualização;
- /task -- Criação, limite, atualização;
- /appointment -- Criação, atualização;
- /indicator -- Criação;
- /qualification -- Criação, limite, conclusão, atualização e prorrogação;
- /qualification-with-products -- Criação, limite, conclusão, atualização e prorrogação;
- /load-report/{reportId} -- Criação, limite, conclusão, atualização e prorrogação (disponibilidade de acordo com a tabela utilizada no relatório);
- /goals -- Criação,atualização e início;
- /company-goals -- Criação,atualização e início;
- /company-goals-per-user -- Criação,atualização e início;
- /company-goals-per-product-category -- Criação,atualização e início;
- /opportunity-history -- Criação;


Agrupadores disponíveis:

* Data de criação = 0;
* Data limite = 1;
* Data de conclusão = 2;
* Data de atualização = 3;
* Data de prorrogação = 4;
* Data de início = 5;

Ignorar seções:

Para excluir da requisição os campos indesejados, você pode indicar quais seções serão ignoradas. Exemplo ignorando duas seções: `...big-data/opportunity?ignoreSections=personalized&ignoreSections=tags&initialDate...`

Seções disponíveis para remoção por tabela:
- /opportunity -- personalized, contacts (campos personalizados de contato), tags, product, reason (motivo de ganho/perda);
- /opportunity-with-products -- personalized, contacts (campos personalizados de contato), tags, product, reason (motivo de ganho/perda);
- /contact -- personalized, tags
- /task -- personalized
- /appointment -- personalized
- /qualification -- personalized, contacts (campos personalizados de contato), tags, product, reason (motivo de ganho/perda);
- /qualification-with-products -- personalized, contacts (campos personalizados de contato), tags, product, reason (motivo de ganho/perda);

-----

Exemplo de requisição: `https://app.nectarcrm.com.br/crm/api/1/big-data/opportunity?aggregator=0&initialDate=2020-01-01&endDate=2020-02-01`


Exemplo de retorno
```js
    [
      {
        "campo": "valor"
        .
        .
        .
      }
    ]
```
