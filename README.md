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



