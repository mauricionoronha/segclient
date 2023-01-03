# Segmentação de clientes
Este projeto tem por objetivo desenvolver um modelo de Machine Learning não supervisionado para agrupar clientes que frequentam um shopping em grupos com características parecidas, facilitando a criação de campanhas de marketing para grupos de consumidores específicos.

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

# 3º - Exploração e tratamento dos dados
No tratamento dos dados foi analisado atributos desnecessários, como o CustomerID que apenas enumera os clientes em ordem crescente, não representando relevância para o modelo. Em seguida foram renomeados os nomes dos atributos ( colunas ) para nomes de mais facil entendimento e identificação de valores nulos ( NAN ), que nesse dataframe felizmente não existia.

A estatística descritiva foi usada para identificar parâmetros como média, mediana, valores minímos, máximos e quartis.

Por último foram usados gráficos boxplot para localizar outliers, ou dados discrepântes.  

# 4º - Pré-processamento
O pré-processamento é uma etapa fundamental que pode melhorar a performance dos algoritmos de análise, através da redução de dimensionalidade e eliminação de ruidos que interfiram no funcionamento dos algoritmos.

Nesta etapa foi excluído o atributo CustomerID  e transformado os dados categóricos do atributo genero ( Female, Male ) em dados numéricos ( 0, 1 ).

Nesta etapa também foi realizado o escalonamento dos dados, fazendo com que dados de escalas diferentes fossem normalizados em uma escala uniforme entre os atributos.

# Agora finalmente os algoritmos de clusterização serão utilizados:

# 5º - K-means
K-Means é um algoritmo de clusterização (ou agrupamento) disponível na biblioteca Scikit-Learn.

É um algoritmo de aprendizado não supervisionado (ou seja, que não precisa de inputs de confirmação externos) que avalia e clusteriza os dados de acordo com suas características, como por exemplo:

* lojas/centro logistico
* clientes/produtos ou serviços semelhantes
* clientes/características semelhantes
* séries/gênero da série ou faixa etaria
* usuarios de uma rede social/usuario influenciador
* paciente/sintoma ou característica semelhante

Um ponto importante no k-means é a configuração correta da quantidade de agrupamentos ( clusters ) que desejamos utilizar. 

A Curva de Cotovelo ou Método Elbow Curve é uma técnica usada para encontrar a quantidade ideal de clusters K. Este método testa a variância dos dados em relação ao número de clusters. O valor ideal de K é aquele que tem um menor Within Sum of Squares (WSS) e ao mesmo tempo o menor número de clusters. Chamamos de curva de cotovelo, porque a partir do ponto que seria o “cotovelo” não existe uma discrepância tão significativa em termos de variância. Dessa forma, a melhor quantidade de clusters K seria exatamente onde o cotovelo estaria.

Após determinar a quantidade de clusters ideal criamos o treinamento e agrupamento dos dados. 

O algoritmo K-means, neste modelo, foi usado:
* Com 2 atributos, possibilitando a visualização por meio de um gráfico de dispersão
* Com todos os atributos
* Com o uso do PCA, reduzindo a dimensão do dataframe para 2 atributos criados pelo algoritmo de PCA

# 6º - Agrupamento Hierárquico ( Agglomerative Hierarchical Clustering )
A análise de agrupamentos por métodos hierárquicos é um método “não supervisionado” de reconhecimento de “padrões naturais” de comportamento em amostras com base em dados multivariados.

O objetivo da técnica é reunir amostras (objetos) com base na sua “proximidade” (semelhança), reduzindo a “dimensionalidade” dos dados e permitindo a visualização de dados multidimensionais através de um gráfico bidimensional chamado dendrograma.

O algoritmo Hierárquico, neste modelo, foi usado:
* Com PCA para reduzir a quantidade de atributos, permitindo uma visualização através de um gráfico de dispersão
* Com todos os atributos

# 7º - DBSCAN - Density Based Spatial Clustering of Application with Noise
DBSCAN, ou traduzindo: Clusterização Espacial Baseada em Densidade de Aplicações com Ruído) é um método de clusterização não paramétrico baseado em densidade, proposto por ESTER et al (1996), que é significativamente efetivo para identificar clusters de formato arbitrário e de diferentes tamanhos, identificar e separar os ruídos dos dados e detectar clusters “naturais” e seus arranjos dentro do espaço de dados, sem qualquer informação preliminar sobre os grupos.

O método requer somente um parâmetro de entrada, mas dá suporte para determinar um apropriado valor para ele.

O algoritmo DBSCAN, neste modelo, foi usado:
* Com PCA para reduzir a quantidade de atributos, permitindo uma visualização através de um gráfico de dispersão.
É possível identificar uma quantidade considerável de ruídos ( -1 ) na criação do modelo com PCA.
* Com todos os dados

# 8º - Mean-Shift
A Mean-Shift é uma técnica de Clustering (agrupamento) na qual tem como objetivo inferir a média dos clusters de acordo com uma função de densidade, na qual em uma janela de interesse (range de dados que compreende o círculo) faz o cálculo da área em que há mais densidade, e nesse ponto será determinado o ponto central da Mean-Shift e o círculo de interesse se move até esse novo ponto central.

Esse processo é realizado de forma sucessiva e só termina quando a Mean-Shift é igual a inferência anterior.

O algoritmo Mean-Shift, neste modelo, foi usado:
* Com PCA para reduzir a quantidade de atributos, permitindo uma visualização através de um gráfico de dispersão
* Com todos os atributos

# 9º - K-PROTOTYPES
O K-Means é um dos algoritmos de cluster mais ( se não o mais usado, o que não é surpreendente. É rápido, tem uma implementação robusta no sklearn e é intuitivamente fácil de entender.

O K-Prototypes é um irmão menos conhecido, mas oferece uma vantagem de design de trabalho com tipos de dados mistos. Ele mede a distância entre os recursos numéricos usando a distância euclidiana ( como K-means ), mas também mede a distância entre os recursos categóricos usando o número de categorias correspondentes. Logo o K-prototype trabalha tanto com dados numéricos quanto com dados categóricos.

Neste modelo não foi usado o PCA e os dados categóricos não precisaram de tratamento.

# 10º - E finalmente foi criado um arquivo CSV com cada algoritmo. 
Alguns modelos apresentaram melhores resultados como o K_means escalonado, DBSCAN com todos os atributos e o K-Prototypes usando dados numéricos e categóricos.

Segue a lista dos arquivos criados:
* df3 - K-means com 2 atributos ( rendimento e pontuacao )
* df4 - K_means escalonado com todos os atributos
* df5 - K_means com PCA reduzindo atributos para 2
* df6 - Agrupamento Hierárquico com PCA reduzindo atributos para 2
* df7 - Agrupamento Hierárquico com todos os atributos
* df8 - DBSCAN com PCA reduzindo atributos para 2
* df9 - DBSCAN com todos os atributos
* df10 - Mean-Shift com PCA reduzindo atributos para 2
* df11 - Mean-Shift com todos os atributos
* df_final - K-Prototypes usando dados numéricos e categóricos
