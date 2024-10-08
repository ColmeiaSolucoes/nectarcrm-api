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
- /action-logs -- Criação;
- /forms -- Criação, atualização;


Agrupadores disponíveis:

* Data de criação = 0;
* Data limite = 1;
* Data de conclusão = 2;
* Data de atualização = 3;
* Data de prorrogação = 4;
* Data de início = 5;

Incluir seções:

Para incluir na requisição os campos desejados, você pode indicar quais seções serão incluídas. Por padrão, enviamos somente os campos padrões de cada seção. Exemplo adicionado duas seções: `...big-data/opportunity?includeSections=personalized&includeSections=tags&initialDate...`

Seções disponíveis para inclusão por tabela:
- /opportunity -- personalized, contact (campos personalizados de contato), tags, product, reason (motivo de ganho/perda);
- /opportunity-with-products -- personalized, contact (campos personalizados de contato), tags, product, reason (motivo de ganho/perda);
- /contact -- personalized, tags
- /task -- personalized
- /appointment -- personalized
- /qualification -- personalized, contact (campos personalizados de contato), tags, product, reason (motivo de ganho/perda);
- /qualification-with-products -- personalized, contact (campos personalizados de contato), tags, product, reason (motivo de ganho/perda);

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
