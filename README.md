# Segmentação de clientes
Este projeto tem por objetivo desenvolver um modelo de Machine Learning não supervisionado para agrupar clientes que frequentam um shopping em grupos com características parecidas, facilitando a crianção de campanhas de marketing para grupos de consumidores específicos.

O dataframe usado foi retirado do Kaggle:
https://www.kaggle.com/shwetabh123/mall-customers

O dataframe é constituído pelos atributos: 

* CustomerID: identificação do cliente.
* Genre: Gênero.
* Age: Idade.
* Annual Income (k$): Rendimento anual.
* Spending Score (1 a 100): Pontuação de gastos.

Segue a ordem de tratamento e criação dos modelos usando diferentes algoritmos de clusterisação:

# 1º - Importando as bibliotecas iniciais e os dados csv
A primeira etapa é a importação das bibliotecas Pandas e Numpy e o carregamento dos dados do arquivo CSV em um dataframe inicial nomeado simplesmente de "df".

Obs.: O arquivo mall-customers.csv foi previamente carregado no google drive para facilitar o acesso.

# 2º - Visualização gráfica dos dados
Usando a biblioteca Plotly podemos visualizar os dados em forma de gráficos interativos. Nesta etapa foi usado histograma para visualizar a variação de idades no dataframe, assim como a distribuição de gênero.

# 3º Exploração e tratamento dos dados
No tratamento dos dados foi analisado atributos desnecessários, como o CustomerID que apenas enumera os clientes em ordem crescente, não representando relevância para o modelo. Em seguida foram renomeados os nomes dos atributos ( colunas ) para nomes de mais facil entendimento e identificação de valores nulos ( NAN ), que nesse dataframe felizmente não existia.

A estatística descritiva foi usada para identificar parâmetros como média, mediana, valores minímos, máximos e quartis.

Por último foram usados gráficos boxplot para localizar outliers, ou dados discrepântes.  

# 4º Pré-processamento
O pré-processamento é uma etapa fundamental que pode melhorar a performance dos algoritmos de análise, através da redução de dimensionalidade e eliminação de ruidos que interfiram no funcionamento dos algoritmos.

Nesta etapa foi excluído o atributo CustomerID  e transformado os dados categóricos do atributo genero ( Female, Male ) em dados numéricos ( 0, 1 ).

Nesta etapa também foi realizado o escalonamento dos dados, fazendo com que dados de escalas diferentes fossem normalizados em uma escala compatível entre os atributos.


