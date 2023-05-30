# Calculando a Data Mínima de Prospecção de Vendas usando DAX
Este repositório oferece uma solução para calcular a data mínima de prospecção de vendas usando a linguagem DAX (Expressões de Análise de Dados).


## Introdução
Olá, comunidade do GitHub!

Hoje, gostaria de compartilhar com vocês um problema de negócios onde uma medida em DAX pode ser extremamente útil. Neste projeto, discutiremos como calcular a data mínima para prospecção de vendas usando a linguagem DAX.

## Problema de Negócio

Imagine que você trabalha para uma empresa especializada em prospecção de clientes e venda de produtos ou serviços. O sucesso das suas vendas depende de uma estratégia de prospecção eficiente, onde a data do primeiro contato ou abordagem com um potencial cliente é um fator crucial.

Para otimizar esse processo, você precisa identificar a data mais antiga em que cada cliente foi abordado pela primeira vez. Essa informação permite avaliar o desempenho da sua equipe de prospecção, determinar o tempo médio necessário para converter um potencial cliente em um cliente efetivo e tomar decisões estratégicas com base nesses dados.


## Solução: Usando Medida em DAX
É aqui que a medida em DAX se torna útil. Usando a fórmula mencionada abaixo, você pode calcular a data mínima de prospecção para cada cliente:

Descrição da Medida
Nome da Medida: Min_Data
A medida Min_Data calcula a data mínima de prospecção (FIRST_DATE) para cada combinação única de empresa (COMPANY_ID) e ano (YEAR) na tabela SALE_PROSPECTING.


### Fómula DAX

```dax
Min_Date = 
MINX(
    FILTER(
        'SALE_PROSPECTING',
        'SALE_PROSPECTING'[COMPANY_ID] = EARLIER('SALE_PROSPECTING'[COMPANY_ID]) &&
        'SALE_PROSPECTING'[YEAR] = EARLIER('PRIMEIRO RELACIONAMENTO'[YEAR])
    ),
    'SALE_PROSPECTING'[FIRST_DATE]
) 
```
# Descrição da Medida

## Nome da Medida: Min_Date

A medida Min_Data calcula a data mínima de prospecção (FIRST_DATE) para cada combinação única de empresa (COMPANY_ID) e ano (YEAR) na tabela SALE_PROSPECTING.

Na fórmula acima, substitua 'SALE_PROSPECTING' pelo nome real da sua tabela que contém os dados de prospecção de vendas. Certifique-se de que os nomes das colunas 'COMPANY_ID', 'YEAR' e 'FIRST_DATE' correspondam aos nomes das colunas correspondentes na sua tabela.

## Solução e Resultados

A solução utiliza a medida DAX Min_Data para determinar a data mínima de prospecção para cada combinação única de empresa e ano nos dados de prospecção de vendas.

### Conjunto de Dados como este: 

| COMPANY_ID | YEAR | FIRST_DATE | MIN_DATE   |
|------------|------|------------|------------|
|     1      | 2021 |  2021-01-01| 2021-01-01 |
|     1      | 2021 |  2021-02-15| 2021-01-01 |
|     1      | 2022 |  2022-03-10| 2022-03-10 |
|     2      | 2021 |  2021-06-20| 2021-06-20 |
|     2      | 2022 |  2022-08-05| 2022-08-05 |

# Ao implementar essa medida no Power BI, você pode:

- Avaliar a data mais antiga em que cada empresa foi abordada pela primeira vez para prospecção.
- Obter insights sobre o momento e a eficácia dos seus esforços de prospecção de vendas.
- Analisar tendências e padrões nas datas mínimas de prospecção por empresa e ano.
- Tomar decisões baseadas em dados e planejar seus esforços de vendas com base nessas informações.
- Os resultados podem ser visualizados usando diversas visualizações do Power BI, como tabelas, gráficos ou linhas do tempo, para mostrar as datas mínimas de prospecção para cada combinação de empresa e ano.

Sinta-se à vontade para incorporar a medida Min_Data fornecida e adaptá-la aos seus dados específicos de prospecção de vendas e necessidades de visualização, a fim de aprimorar sua análise de vendas e processo de tomada de decisão.

#### Aproveite a exploração e utilização dessa medida para otimizar suas atividades de prospecção de vendas!
