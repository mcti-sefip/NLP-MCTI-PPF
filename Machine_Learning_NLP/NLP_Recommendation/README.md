# Meta 12

## Descrição do modelo

Nesta meta do projeto, visamos criar, a partir de um modelo LDA a realização de recomendações ao usuário, usando a biblioteca surprise.

A biblioteca surprise fornece 11 modelos de classificadores que tentam prever a classificação dos dados de treinamento com base em várias técnicas diferentes de filtragem colaborativa. Os modelos fornecidos com uma breve explicação são mencionados abaixo.

### random_pred.NormalPredictor: 
Algoritmo que prevê uma classificação aleatória com base na distribuição do conjunto de treinamento, que é considerado normal. 

### baseline_only.BaselineOnly: 
Algoritmo que prevê a estimativa de baseline para determinado usuário e item.

### knns.KNNBasic: 
Algoritmo básico de collaborative-filtering.

### knns.KNNWithMeans: 
Um algoritmo básico de collaborative-filtering, levando em conta as avaliações médias de cada usuário.

### knns.KNNWithZScore: 
Um algoritmo básico de collaborative-filtering, levando em consideração a normalização do z-score de cada usuário.

### knns.KNNBaseline: 
Um algoritmo básico de collaborative-filtering que leva em consideração uma classificação de baseline.

### matrix_factorization.SVD: 
O famoso algoritmo SVD, popularizado por Simon Funk durante o Prêmio Netflix. 

### matrix_factorization.SVDpp: 
O algoritmo SVD++, uma extensão do SVD que leva em consideração classificações implícitas.

### matrix_factorization.NMF: 
Um algoritmo de collaborative-filtering baseado na fatoração de matriz não negativa. 

### slope_one.SlopeOne: 
Um algoritmo de collaborative-filtering simples, mas preciso.

### co_clustering.CoClustering: 
Um algoritmo de collaborative-filtering baseado em co-clustering. É possível passar um dataframe personalizado como argumento para esta classe. O dataframe em questão precisa ter 3 colunas com o seguinte nome: ['userID', 'itemID', 'rating'].


É importante ressaltar inicialmente que neste modelo deparamo-nos com alguns obstáculos que havíamos ultrapassado, mas alguns deles, pela natureza do projeto, não puderam ser totalmente resolvidos. Bancos de dados contendo perfis de possíveis usuários do protótipo planejado não estão disponíveis. Por esse motivo, foi necessário realizar simulações de forma a representar os interesses desses usuários, para que o sistema de recomendação pudesse ser modelado. Foi realizada uma simulação de clusters de interesses latentes, com base em tópicos presentes nos textos que descrevem os produtos financeiros. Devido ao fato de que o conjunto de dados foi construído por nós mesmos, ainda não houve interação entre um usuário e o conjunto de dados, portanto, não temos classificações realistas, tornando os resultados menos críveis.

Posteriormente, utilizamos um banco de dados de scrappings de perfis do LinkedIn. O problema é que os perfis que o linkedin mostra são tendenciosos, então os perfis que aparecem foram geograficamente fechados ou relacionados à organização e e-mail dos usuários.

Todos os modelos foram usados e avaliados. Quando confrontados, diferentes métodos apresentaram diferentes estimativas de erro.

A biblioteca surprise fornece 4 métodos diferentes para avaliar a precisão da previsão de classificações. São eles: rmse, mse, mae e fcp.

# Benchmarks

## LDA-GENERATED DATASET
ranking

|                 |  RMSE     | MSE       | MAE       |   FCP     |
|-----------------|-----------|-----------|-----------|-----------|
| NormalPredictor |  1.820737 |	3.315084  | 1.475522  |	0.514134  |
| BaselineOnly    |  1.072843 | 1.150992  | 0.890233  | 0.556560  |
| KNNBasic        |  1.232248 |	1.518436  |	0.936799  | 0.648604  |
| KNNWithMeans    |  1.124166 |	1.263750  |	0.808329  |	0.597148  |
| KNNWithZScore   |  1.056550 |	1.116299  |	0.750004  |	0.669651  |
| KNNBaseline     |  1.134660 |	1.287454  |	0.825161  |	0.614270  |
| SVD             |  0.977468 |	0.955444  |	0.757485  |	0.723829  |
| SVDpp           |  0.843065 |	0.710758  |	0.670516  |	0.671737  |
| NMF             |  1.122684 |	1.260420  |	0.722101  |	0.688728  |
| SlopeOne        |  1.073552 |	1.152514  |	0.747142  |	0.651937  |
| CoClustering    |  1.293383 |	1.672838  |	1.007951  |	0.494174  |

## BENCHMARK DATASET
uniform

|                 |  RMSE     | MSE       | MAE       |   FCP     |
|-----------------|-----------|-----------|-----------|-----------|
| NormalPredictor |  1.508925 |	2.276854  | 1.226758  |	0.503723  |
| BaselineOnly    |  1.153331 | 1.330172  | 1.022732  | 0.506818  |
| KNNBasic        |  1.205058 |	1.452165  |	1.026591  | 0.501168  |
| KNNWithMeans    |  1.202024 |	1.444862  |	1.028149  |	0.503527  |
| KNNWithZScore   |  1.216041 |1.478756	  | 1.041070  |	0.501582  |
| KNNBaseline     |  1.225609 |	1.502117  | 1.048107  |	0.498198  |
| SVD             |  1.176273 |	1.383619  |	1.013285  |	0.502067  |
| SVDpp           |  1.192619 |	1.422340  |	1.018717  |	0.500909  |
| NMF             |  1.338216 |	1.790821  |	1.120604  |	0.492944  |
| SlopeOne        |  1.224219 |	1.498713  |	1.047170  |	0.494298  |
| CoClustering    |  1.223020 |	1.495778  |	1.033699  |	0.518509  |

