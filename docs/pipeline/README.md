# Pipeline Resource

Esta API permite o controle total dos funis de venda/outro tipo. Veja as instruções de como realizar a integração abaixo.

Instruções para realizar a integração:

URL
http://app.nectarcrm.com.br/crm/api/1/pipeline/

Parâmetros de listagem:
* &page=x (integer) Organiza a listagem de objetos por páginas (se colocar -1, lista o máximo de objetos: 200)
* &type=x (integer) Define o filtro de funil (0 = vendas, 1 = qualificação)

[Para mais informações, consulte a documentação completa clicando aqui](http://docs.nectarcrm.apiary.io)

Schema Info | [Schema JSON](schema.json)

Propriedade | Tipo | Descricao
------------ | ------------- | -------------
ativo | (boolean) | Marca se esse funil está ativo para utilização
id | (long) | Identificador no sistema
nome | (string) | Nome do funil
padrao | (boolean) | Determina se esse funil é o padrão do sistema
sequencias | (array) | Etapas do funil
tipo | (int) | Tipo do funil (0 = vendas, 1 = qualificação)
permitePularEtapa | (boolean) | Determina se pode pular etapas
iniciarQualquerEtapa | (boolean) | Determina se pode iniciar em qualquer etapa
permiteRetornoEtapa | (boolean) | Determina se pode retornar etapa
propostaObrigatoria | (boolean) | Determina se gerar proposta é obrigatória na etapa indicada com Gerar Proposta
produtoObrigatorio | (boolean) | Determina se as oportunidades precisam ter produtos para incluir/editar
permitirRecorrenciaVariavel | (boolean) | Determina se pode alterar a recorrência do produto
modeloVenda | (int) | Modelo de venda do funil (0 = B2B, 1 = B2C)
multiplasTabelasPreco | (boolean) | Determina se poderá usar múltiplas tabelas de preço
corresponsabilidade | (boolean) | Determina se poderá usar corresponsabilidade nas oportunidades
ignorarRestricaoEquipes | (boolean) | Caso corresponsabilidade esteja ativo, determina se irá ignorar restrição de equipes
consideracoesObrigatorioGanhar | (boolean) | Parâmetro para indicar se a consideração deve ser obrigatória ao ganhar
consideracoesObrigatorioPerder | (boolean) | Parâmetro para indicar se a consideração deve ser obrigatória ao perder
consideracoesObrigatorioProrrogar | (boolean) | Parâmetro para indicar se a consideração deve ser obrigatória ao prorrogar
consideracoesObrigatorioDescartar | (boolean) | Parâmetro para indicar se a consideração deve ser obrigatória ao descartar
moeda | (string) | Moeda configurada para a Pipeline

Exemplo
```js
    [
      {
        "ativo": true,
        "id": 1,
        "nome": "Funil de venda",
        "padrao": true,
        "sequencias": [
                    {
                        "id": 11,
                        "nome": "Gerar Interesse",
                        "sequencia": 1,
                        "prazo": 3,
                        "gerarProposta": false
                    },
                    {
                        "id": 22,
                        "nome": "Processo de Cadência",
                        "sequencia": 2,
                        "prazo": 2,
                        "gerarProposta": false
                    }
                    ],
        "tipo": 0,
        "permitePularEtapa": true,
        "iniciarQualquerEtapa": true,
        "permiteRetornoEtapa": true,
        "propostaObrigatoria": false,
        "produtoObrigatorio": false,
        "permitirRecorrenciaVariavel": true,
        "modeloVenda": 0,
        "multiplasTabelasPreco": false,
        "corresponsabilidade": true,
        "ignorarRestricaoEquipes": true,
        "consideracoesObrigatorioGanhar": true,
        "consideracoesObrigatorioPerder": false,
        "consideracoesObrigatorioProrrogar": true,
        "consideracoesObrigatorioDescartar": true,
        "moeda": "BRL"
      }
    ]
```
