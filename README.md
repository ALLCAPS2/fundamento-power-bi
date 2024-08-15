# Fundamento Power BI.
Reciclagem sobre ETL, Modelagem de Dados e Visualização de Dados.
# Fonte de dados.
Conjunto de dados de vendas disponibilizados pela Prime Cursos.
- Tabelas dimensão: dim_canal, dim_categoria, dim_cidade, dim_clientes, dim_marca, dim_produto e dim_subcategoria.
- Tabelas fato: vendas 2010-2013, vendas 2014-2017, vendas 2018-2021.
# Processo ETL (Extração, Transformação e Carga).

## Extração:
-Tabelas dimensão importadas individualmente, checada a tipagem das colunas.

## Transformação:
- Verifiquei que a coluna 'Data Nascimento'  da tabela "dim_clientes" está com inconsistência de dados e foi tipada como "texto", portanto, substitui os apóstrofos por " " e alterei a tipagem para data localizada no padrão "Inglês - Estados Unidos".

## Carga
Após verificar todas as tabelas, fechei o PowerQuery e apliquei todas as alterações considerando o fato que não há mais tratamento para os dados pois o conjunto de dados é bem consistente.
# Modelagem de dados.
Modelado as seguintes relações: 
- dim_clientes 1:N fato_vendas
- dim_cidade 1:N dim_clientes
- dim_canal 1:N fato_vendas
- dim_categoria 1:N dim_subcategoria
- dim_subcategoria 1:N dim_produto
- dim_marca 1:N dim_produto
- dim_produto 1:N fato_vendas

Criado a tabela dim_calendario para visualização de valores por tempo determinado.
`dim_calendario = calendarauto()`
- Tipo alterado para "Data" e formato "Short Date"
- Adicionado colunas: Ano `Ano = YEAR([Data]) `, Mes `Mes = Month([Data]) `, Nome do Mes `Nome do Mes = FORMAT([Data, "mmm"]) `, Dia `Dia = Day([Data]) ` e Nome do Dia `Nome do dia = FORMAT([Data, "dddd"]) `
- dim_calendario 1:N fato_vendas

# Análise e Visualização de dados.
Utilizei novas "medidas" para manipular os dados e criar análises, para melhor organização, inseri uma nova tabela para armazenar as medidas deste projeto.
## Medidas Criadas: 

