# Intensivo-SQL

Notebook de estudo prático de SQL no Databricks, cobrindo desde consultas básicas até tópicos avançados como JOINs, Subqueries, CTEs, Views e Criação de Tabelas.

## Datasets

Os dados estão na pasta `datasets/` em formato CSV e são carregados como temp views no início do notebook.

### tabela_clientes.csv

| Coluna | Tipo |
| --- | --- |
| id_cliente | int |
| primeiro_nome | string |
| segundo_nome | string |
| ultimo_nome | string |
| cidade | string |
| idade | int |
| data_cadastro | date |

### tabela_produtos.csv

| Coluna | Tipo |
| --- | --- |
| id_produto | int |
| nome_produto | string |
| categoria | string |
| preco_unitario | double |

### tabela_vendas.csv

| Coluna | Tipo |
| --- | --- |
| id_venda | int |
| id_cliente | int |
| id_produto | int |
| quantidade | int |
| data_venda | date |

## Tópicos Cobertos

### SELECT FROM (células 2–6)

Consulta básica de dados com `SELECT *`, seleção de colunas específicas, `LIMIT` para restringir o número de linhas retornadas e `DISTINCT` para eliminar duplicatas.

### WHERE (células 7–10)

Filtragem de linhas com operadores de comparação (`=`, `>`, `>=`, `<=`, `<>`) e condições com valores específicos. Base para todos os filtros aplicados nas consultas.

### ORDER BY (células 11–13)

Ordenação dos resultados por uma ou mais colunas, em ordem crescente (`ASC`, padrão) ou decrescente (`DESC`).

### COUNT (células 14–20)

Contagem de linhas com `COUNT(*)`, aplicação de filtros combinados com `WHERE`, uso de `BETWEEN` para faixas de valores e contagem condicional.

### Funções Agregadas (células 21–26)

Cálculo de métricas estatísticas com `MAX()` (maior valor), `MIN()` (menor valor), `AVG()` (média), `MEAN()` e `MODE()` sobre colunas numéricas.

### LIKE (células 27–28)

Correspondência de padrões de texto com o operador `LIKE` e o curinga `%`. Permite buscar nomes que começam, terminam ou contêm determinadas letras (ex.: `LIKE 'A%'` para nomes que começam com A).

### IS NULL / IS NOT NULL (células 29–31)

Verificação de valores nulos com `IS NULL` (encontra registros sem valor) e `IS NOT NULL` (encontra registros preenchidos). Útil para identificar dados faltantes ou incompletos.

### GROUP BY (células 32–33)

Agrupamento de linhas por uma ou mais colunas, combinado com funções agregadas (`AVG`, `SUM`, `COUNT`, `MAX`, `MIN`) para calcular métricas por categoria. Ex.: média de preço por categoria de produto.

### HAVING (células 34–35)

Filtro aplicado sobre resultados já agrupados por `GROUP BY`. Diferente do `WHERE` (que filtra linhas individuais), o `HAVING` filtra grupos com base em valores agregados. Ex.: apenas categorias com média de preço acima de 1000.

### JOINs (células 36–43)

Combinação de dados de tabelas relacionadas através de chaves em comum:

* **JOIN / INNER JOIN**: retorna apenas as linhas que têm correspondência em ambas as tabelas
* **LEFT JOIN**: retorna todos os registros da tabela à esquerda, mesmo sem correspondência na direita (preenche com NULL)
* **RIGHT JOIN**: retorna todos os registros da tabela à direita, mesmo sem correspondência na esquerda (preenche com NULL)

### Subqueries (células 44–45)

Consultas aninhadas dentro de outra consulta. Permitem usar o resultado de um `SELECT` como condição em outra query. Ex.: selecionar clientes com idade acima da média geral (`WHERE idade > (SELECT AVG(idade) FROM tabela_clientes)`).

### CTEs (células 46–47)

Common Table Expressions com a cláusula `WITH`. Criam tabelas temporárias nomeadas dentro da query, tornando consultas complexas mais legíveis e organizadas. Diferente das subqueries, as CTEs podem ser referenciadas múltiplas vezes na mesma consulta.

### Views (células 48–50)

Criação de visões virtuais com `CREATE OR REPLACE TEMP VIEW`. Uma view armazena uma consulta SQL como uma tabela virtual que pode ser consultada repetidamente sem reescrever o código. Útil para encapsular lógica complexa e padronizar consultas frequentes.

### Criação de Tabelas (células 51–53)

Criação de tabelas a partir de resultados de consultas com `CREATE TABLE AS SELECT` (CTAS). Permite armazenar permanentemente o resultado de uma análise, como um resumo de vendas por categoria com receita total calculada.
