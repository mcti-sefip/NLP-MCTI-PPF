Nesta meta do projeto, visamos criar, a partir de um modelo LDA a realização de recomendações ao usuário, usando a biblioteca surprise.

A biblioteca surprise fornece 11 modelos de classificadores que tentam prever a classificação dos dados de treinamento com base em várias técnicas diferentes de filtragem colaborativa. Os modelos fornecidos com uma breve explicação são mencionados abaixo.

random_pred.NormalPredictor: Algoritmo que prevê uma classificação aleatória com base na distribuição do conjunto de treinamento, que é considerado normal. 

baseline_only.BaselineOnly: Algoritmo que prevê a estimativa de baseline para determinado usuário e item.

knns.KNNBasic: Algoritmo básico de collaborative-filtering

knns.KNNWithMeans: Um algoritmo básico de collaborative-filtering, levando em conta as avaliações médias de cada usuário.

knns.KNNWithZScore: Um algoritmo básico de collaborative-filtering, levando em consideração a normalização do z-score de cada usuário.

knns.KNNBaseline: Um algoritmo básico de collaborative-filtering que leva em consideração uma classificação de baseline

matrix_factorization.SVD: O famoso algoritmo SVD, popularizado por Simon Funk durante o Prêmio Netflix. 

matrix_factorization.SVDpp: O algoritmo SVD++, uma extensão do SVD que leva em consideração classificações implícitas.

matrix_factorization.NMF: Um algoritmo de collaborative-filtering baseado na fatoração de matriz não negativa. 

slope_one.SlopeOne: Um algoritmo de collaborative-filtering simples, mas preciso.

co_clustering.CoClustering: Um algoritmo de collaborative-filtering baseado em co-clustering. É possível passar um dataframe personalizado como argumento para esta classe. O dataframe em questão precisa ter 3 colunas com o seguinte nome: ['userID', 'itemID', 'rating'].


É importante ressaltar inicialmente que neste modelo deparamo-nos com alguns obstáculos que havíamos ultrapassado, mas alguns deles, pela natureza do projeto, não puderam ser totalmente resolvidos. Bancos de dados contendo perfis de possíveis usuários do protótipo planejado não estão disponíveis. Por esse motivo, foi necessário realizar simulações de forma a representar os interesses desses usuários, para que o sistema de recomendação pudesse ser modelado. Foi realizada uma simulação de clusters de interesses latentes, com base em tópicos presentes nos textos que descrevem os produtos financeiros. Devido ao fato de que o conjunto de dados foi construído por nós mesmos, ainda não houve interação entre um usuário e o conjunto de dados, portanto, não temos classificações realistas, tornando os resultados menos críveis.

Posteriormente, utilizamos um banco de dados de scrappings de perfis do LinkedIn. O problema é que os perfis que o linkedin mostra são tendenciosos, então os perfis que aparecem foram geograficamente fechados ou relacionados à organização e e-mail dos usuários.

Todos os modelos foram usados e avaliados. Quando confrontados, diferentes métodos apresentaram diferentes estimativas de erro.

A biblioteca surprise fornece 4 métodos diferentes para avaliar a precisão da previsão de classificações. São eles: rmse, mse, mae e fcp.
