# Experimentos de Sumarização Automática de Texto e Avaliação de Resumos

## Objetivo
Este repositório apresenta scripts em Python para baixar e manipular uma seleção de corpus relevantes da literatura de Sumarização Automática de Texto (ATS), bem como aplicar uma variedade de métodos abstratos e extractivos de sumarização. Os resumos resultantes podem então ser avaliados usando uma seleção de métricas da literatura. Os scripts aqui desenvolvidos foram desenvolvidos com o processamento de inteiros corpus em mente, fazendo uso de paralelização. No entanto, também é possível realizar sumarização e avaliação de documentos únicos.

## Conjunto de dados MCTI + download do corpus CNN

Além dos conjuntos de dados populares da literatura de Processamento de Linguagem Natural (PLN) disponíveis para download através do próprio script, foram implementadas funções de manipulação para os conjuntos de dados do Projeto de Pesquisa de Ciência de Dados Aplicada ao Portfólio de Produtos Financeiros (PPF-MCTI), bem como o conjunto de dados CNN Corpus. Esses conjuntos de dados devem ser baixados externamente e extraídos para a raiz do repositório (em uma pasta chamada ./data) e estão disponíveis aqui: [DOWNLOAD](https://zenodo.org/record/7262127)

### Conjuntos de Dados Disponíveis:
- ArXiv + PubMed
- BIGPATENT
- CNN + Daily Mail
- XSum
- CNN Corpus
- MCTI (News)
- MCTI (Oportunities)
- MCTI (Policies)

### Métodos de Sumarização Extractiva Disponíveis:
- Reduction Summarizer
- LexRank Summarizer
- LSA Summarizer
- Luhn Summarizer
- Random Summarizer
- SumBasic Summarizer
- TextRank Summarizer

### Métodos de Sumarização Abstrativa Disponíveis:
- BART
- T5
- PEGASUS

### Métodos de Avaliação de Resumo Disponíveis:
- ROUGE
    - ROUGE-1,2,3,4
    - ROUGE-L
    - ROUGE-W
    - ROUGE-SU-4
- Precision, Recall, F
- Jaccard and Hellinger Divergences
- Kullback-Leibler Divergences
- Cosine Similarity

# Classes e Métodos
Os processos de importação de dados, sumarização e avaliação são definidos nas classes `Data`, `Method` e `Evaluator` , respectivamente. A função principal  `main`  sugere a sumarização e avaliação de 50 entradas de todos os conjuntos de dados disponíveis. O número de resumos a serem gerados N pode ser modificado em `Data.read_data(corpus, N)`.

Para cargas de trabalho de CPU, sugerimos um número baixo de resumos $(N<100)$, dada as longas tempos de computação, especialmente para modelos abstratos *transformer*. Os resultados apresentados em nossos relatórios, gerados com $N=3000$, foram obtidos com a ajuda do Google Colab e computação GPU.

## Resultados
As saídas para cada corpus *corpus* em `.\results` são:

Todos os resumos gerados, em um arquivo finalizado por `_examples.csv`
- Todos os resultados dos avaliadores escolhidos, em um arquivo finalizado por `_results.csv`
- Deve ser mencionado que os conjuntos de dados da literatura são baixados usando a biblioteca `datasets`, da huggingface, e podem ocupar uma grande quantidade de espaço em disco.

# References 

Baeza-Yates, R. and Ribeiro-Neto, B. (2008). Modern Information Retrieval, 2nd edn,
Addison-Wesley Publishing Company, USA.

Erkan, G. and Radev, D. R. (2004). Lexrank: Graph-based lexical centrality as salience in text
summarization, Journal Artificial Intelligence Research 22(1): 457–479.

Haghighi, A. and Vanderwende, L. (2009). Exploring content models for multi-document
summarization, Proceedings of human language technologies: The 2009 annual conference of
the North American Chapter of the Association for Computational Linguistics, pp. 362–370.

Lewis, M., Liu, Y., Goyal, N., Ghazvininejad, M., Mohamed, A., Levy, O., Stoyanov, V. and
Zettlemoyer, L. (2019). Bart: Denoising sequence-to-sequence pre-training for natural language
generation, translation, and comprehension, arXiv preprint arXiv:1910.13461 .

Lin, C.-Y. (2004). Rouge: A package for automatic evaluation of summaries, Text summarization
branches out, pp. 74–81.

Louis, A. and Nenkova, A. (2013). Automatically assessing machine summary content without a
gold standard, Computational Linguistics 39(2): 267–300.

Luhn, H. P. (1958). The automatic creation of literature abstracts, IBM Journal of Research and
Development 2(2): 159–165.

Mihalcea, R. and Tarau, P. (2004). Textrank: Bringing order into text, Proceedings of the 2004
conference on empirical methods in natural language processing, pp. 404–411.

Raffel, C., Shazeer, N., Roberts, A., Lee, K., Narang, S., Matena, M., Zhou, Y., Li, W. and Liu,
P. J. (2019). Exploring the limits of transfer learning with a unified text-to-text transformer,
arXiv preprint arXiv:1910.10683.

Saggion, H., Radev, D. R., Teufel, S., Lam, W. and Strassel, S. M. (2002). Developing infrastructure
for the evaluation of single and multi-document summarization systems in a cross-lingual
environment., LREC, pp. 747–754.

Salton, G. (1989). Automatic text processing, Reading: Addison-Wesley.

Steinberger, J., Jezek, K. et al. (2004). Using latent semantic analysis in text summarization and
summary evaluation, Proceedings of ISIM 4(93-100): 8.

Zhang, J., Zhao, Y., Saleh, M. and Liu, P. (2020). Pegasus: Pre-training with extracted
gap-sentences for abstractive summarization, International Conference on Machine Learning,
PMLR, pp. 11328–11339
