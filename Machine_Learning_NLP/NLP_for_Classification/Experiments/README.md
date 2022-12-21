# Meta 10

## Metodologia:

Nesta etapa foi utilizado como entrada os dados pré-processados da Meta 9 e os modelos apresentados no artigo submetido na meta 6.
A metodologia consistiu na realização de uma análise cruzada da utilização de técnicas de representação vetorizada dos textos (Keras Embedding, Word2Vec, Longformer) com modelos de aprendizagem profunda (SNN, DNN, CNN, LSTM).

## Implementação:

O treinamento dos modelos foi feito utilizando o Google Colab Pro em ambiente de GPU (exceto para o longformer).
A implementação dos testes com Keras Embedding foi realizada sem grandes dificuldades. O notebook da meta 6 foi adaptado para a utilização dos novos dados e as redes foram treinadas 30+ vezes com 100 épocas de treinamento cada. 

Com o word2vec primeiro foi necessário realizar o pré-treino da rede com os dados. Desta vez, ao contrário da meta 6, todos os dados utilizados para o pré-treino da rede já estavam catalogados, o que justificaria uma proximidade maior dos resultados em relação ao modelo de Keras embedding. Após o pré-treino o modelo foi acoplado às redes neurais profundas que foram treinadas em conjunto 30+ vezes com 100 épocas de treinamento cada.

Com o longformer os problemas causados pelo tamanho do modelo ficaram mais visíveis. Primeiramente foi necessário ativamente desalocar pedaços de memória não utilizados logo após o uso para que fosse possível carregar as próximas etapas. Em seguida foi necessário utilizar ambiente de CPU para o treino das redes devido ao peso do modelo exceder os 16GB disponíveis de memória de vídeo da placa P100 disponível no Colab durante treino. Neste caso foi utilizado o ambiente de alta RAM, que entrega 25GB de memória para uso com o CPU, e isso significa um maior tempo necessário para o treino já que a GPU realiza operações matriciais mais rapidamente. Esses modelos foram treinados 5x com 100 épocas de treinamento cada.

## Resultados:

A tabela abaixo apresenta os resultados de acurácia, f1-score, recall e precisão obtidos no treino de cada rede. Além disso foi adicionado os tempos necessários para o treino de cada época, o tempo de execução da validação dos dados e o peso do modelo de aprendizagem profunda associado com cada implementação.

| Modelo                 | Acurácia | F1-score | Recall | Precisao | Tempo treino época (s) | Tempo validação (s) | Peso (MB) |
|------------------------|----------|----------|--------|----------|------------------------|---------------------|-----------|
| Keras Embedding + SNN  | 92.47    | 88.46    | 79.66  | 100      | 0.2                    | 0.7                 | 1.8       |
| Keras Embedding + DNN  | 89.78    | 84.41    | 77.81  | 92.57    | 1                      | 1.4                 | 7.6       |
| Keras Embedding + CNN  | 93.01    | 89.91    | 85.18  | 95.69    | 0.4                    | 1.1                 | 3.2       |
| Keras Embedding + LSTM | 93.01    | 88.94    | 83.32  | 95.54    | 1.4                    | 2                   | 1.8       |
| Word2Vec + SNN         | 89.25    | 83.82    | 74.15  | 97.10    | 1.4                    | 1.2                 | 9.6       |
| Word2Vec + DNN         | 90.32    | 86.52    | 85.18  | 88.70    | 2                      | 6.8                 | 7.8       |
| Word2Vec + CNN         | 92.47    | 88.42    | 80.85  | 98.72    | 1.9                    | 3.4                 | 4.7       |
| Word2Vec + LSTM        | 89.78    | 84.36    | 75.36  | 95.81    | 2.6                    | 14.3                | 1.2       |
| Longformer + SNN       | 61.29    | 0        | 0      | 0        | 128                    | 1.5                 | 36.8      |
| Longformer + DNN       | 91.93    | 87.62    | 80.37  | 97.62    | 81                     | 8.4                 | 12.7      |
| Longformer + CNN       | 94.09    | 90.69    | 83.41  | 100      | 57                     | 4.5                 | 9.6       |
| Longformer + LSTM      | 61.29    | 0        | 0      | 0        | 135                    | 8.6                 | 2.6       |

**Modelos pré-treinados:** 

Os modelos que utilizam Word2Vec e Longformer também precisam ser carregados e seus pesos são os seguintes:

Longformer: 10.88 GB 

Word2Vec: 56.1 MB


## Discussão

**Melhores modelos:** 

Keras Embedding + CNN: 	93.01	89.91	85.18	95.69 

Word2Vec + CNN	92.47	88.42	80.85	98.72 

Longformer + CNN	94.09	90.69	83.41	100 

Os resultados obtidos superaram os alcançados na meta 6 e na meta 9, com a melhor acurácia obtida de 94% no modelo longformer + CNN. Podemos também observar que os modelos que alcançaram os melhores resultados foram os que utilizaram a rede CNN para o aprendizado profundo.

Além disso foi possível perceber que o modelo do longformer + SNN e longformer + LSTM não foram capazes de aprender. Talvez os modelos necessitem de alguns ajustes, porém cada tentativa de treino levava entre 5 e 8 horas o que tornou inviável a tentativa de ajustar quando outros modelos já estavam apresentando resultados promissores.

Acima dos resultados obtidos também é necessário destacar dois limitantes encontrados para a replicação e treino das redes:

*Limitante de performance*: Carregar o modelo longformer em memória significa necessitar de 11Gb disponíveis apenas para o modelo, sem considerar o peso da rede de deep learning. Para o treinamento isso significa que precisamos de uma GPU de 20+ Gb para realizar o treino. Aqui isso foi resolvido utilizando o ambiente de alta RAM do google Colab Pro e treinando utilizando CPU o que justifica o maior tempo de treino por época.

Esses 10Gb do modelo excedem o limite do Github e não foram para o repositório, portanto para rodar o sistema precisamos fazer o download da rede pré-treinada no notebook e rodar o encoder-decoder com os dados para criar o modelo. Aconselha-se fazer isso em ambiente de GPU e salvar o arquivo no drive. Após isso trocar o ambiente para CPU para realizar o treinamento. Tentar gerar o modelo em CPU levará mais de 3 horas de processamento.

*Limitante de replicabilidade*: Devido a simplicidade do modelo do keras embedding, estamos utilizando one hot encodding, e ele possui um delicado problema para replicação em produção. Este detalhe está pendente de mais estudo para definir se é possível utilizar um desses modelos.


O melhor modelo que não apresenta nenhum limitante é o Word2Vec + CNN. Porém precisamos estudar as limitações para entender se é possível introduzir um novo modelo com melhor acurácia e indicadores. Estes ajustes serão trabalhados ao decorrer das metas 13 e 14 onde o objetivo central será encapsular a solução da maneira mais adequada para uso em produção.


