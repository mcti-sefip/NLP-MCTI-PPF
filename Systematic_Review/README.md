
# Systematic Literature Review Methodology

## What is Systematic Literature Review

The systematic literature review's (SLR) goal is to gather similar materials (papers, books, etc.) in order to answer a given scientific question or to realize an overview of a scientific base in the literature regarding an issue.

## What are the steps to produce a SLR

The steps of a SLR are meant to structure a work plan which is done in a systematic way. They help guiding the researcher and people who are interested in reading the research in order to make possible the replicability of the bibliogaphical gathering of the review or it's processes.

### Phase 1 (Review Plan)

1. Specify the research question (e.g. Which are the most advanced hardwares for Deep-Learning?)
2. Develop the review protocol (e.g. inclusion/exclusion criteria, search strategy, quality evaluation criteria, etc.)
3. Validate the review protocol (e.g. evaluate if it's possible that examples enter into this protocol)

### Phase 2 (Produce the review)

4. Gather the database (database containing examples from the search strategy with keywords in a search mechanism)
5. Select the primary studies (In this methodology - with the inclsuion/exclusion criteria having been defined - it must be done using the title and summary of each example.)
6. Evaluate the quality of the studies (with the primary studies having been selected, the quality evaluation criteria must be applied to the examples included in the SLR.)
7. Synthetize the data bank with high-quality studies (Create a data bank with the high quality examples which were selected for the SLR.)

### Phase 3 (Review report)

1. Format the main report (Obs.: Este passo é a escrita de um documento em formato de relatório explicitando a metodologia da SLR empregada definida na Fase 1, os resultados da Fase 2 e a conclusão/discussão sobre as bases de dados levantadas para a SLR.)
2. Evaluate the report (Revisão do relatório por parte da equipe e/ou do projeto)
3. Share the database and/or the report (Obs.: Este passo tem como objetivo disponibilizar a SLR para que outros pesquisadores consiga utilizar dos recursos concretizados para efetuar alguma pesquisa ou aprimorar a SLR. Este pode ser feito utilizando a plataforma [zenodo](https://zenodo.org/))

## Tools to help the researcher doing a SLR

Para o controle e ajuda do levantamento e classificação dos exemplos para a SLR, foi criada uma aplicação que possibilita realizar os passos 4 e 5 utilizando o [notebook de aplicação](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb). Esta aplicação procura reduzir o tempo para levantar bases de dados e a classificação dos estudos primários.

A busca é feita utilizando a ferramenta de busca do [Semantic Scholar](https://www.semanticscholar.org/), que possui um grafo de relações entre os resultados da busca criado por uma IA. Esta busca é realizada utilizando a biblioteca de python [S2Query](https://github.com/mcti-sefip/NLP-MCTI-PPF/tree/main/Systematic_Review/Systematic_Review_Methodology/Buscador).

A classificação para estudos primários é realizada por um modelo de inteligência artificial (IA) que ao rotular 4 exemplos (2 incluídos, 2 excluídos) para a revisão sistemática, o modelo predita, utilizando o titulo e o resumo do exemplo, uma confiança (*confidence*) para cada exemplo, no qual é ranqueado/ordenado com base no *rank* a base de dados passada. Exemplos com confianças próximas de 1 (*confidence* $\approx$ 1) indica que o modelo tende a incluir estes exemplos na SLR. O modelo utilizado é resultado da pesquisa "Few-shot approach for systematic literature review classifications" descrito na pasta [Systematic_Review_Methodology/Pesquisa](https://github.com/mcti-sefip/NLP-MCTI-PPF/tree/main/Systematic_Review/Systematic_Review_Methodology/Pesquisa).

### Automatization of steps 4 and 5 of Phase 2

#### Step 4

- a) Raise one or multiple databases using keywords and [Semantic Scholar](https://www.semanticscholar.org/)'s search tool. The mentioned search is done via the [`SearcherWeb()`](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=kXCMmkts700P) or [`SearcherAPI()`](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=mTQwDdhG6kxe) functions, and the main differences between them are described in the [notebook](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=19agpVfcMqBu).

#### Step 5

- b) Fazer a rotulagem destes artigos utilizando o **titulo** e **resumo**, com base nos critérios de **inclusão**  e **exclusão** da revisão sistemática imposta. Se for utilizar o **passo 3**, fazer no **mínimo 16 rotulagens** (8 incluídos e 8 excluídos). Este pode ser feito utilizando a função **`Interface(data)`**.

- c) (Opcional) [Treinar o modelo de linguagem natural](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=z5AsHo-wMsRP) para automatizar a rotulagem e/ou ranquear os exemplos da base passada na função **`Interface(data)`**. O modelo é treinado com a quantidade de exemplos por classe (incluído, excluído) passado para o parâmetro `size_per_class`.

- d) (Opcional) Rotular novos exemplos (ou corrigir a classificação do modelo) utilizando o ranqueamento predito pelo modelo. Este procura ajudar o pesquisador na busca de estudos primários sob a base passada em **`Interface(data)`**. Este passo ajuda o pesquisador a rotular os exemplos para a revisão sistemática utilizando a confiança do modelo em excluir o máximo de exemplos irrelevantes e retornar os mais relevantes para a inclusão na SLR na busca de estudos primários.

- e) (Opcional) Voltar aos **itens c)** e **d)** até que esteja satisfeito com as rotulagens ou tenha rotulado toda a base de dados.

O passo 4 e 5 são realizados utilizando apenas a função **`Interface(data)`**. Alguns dos critérios para utilizar esta função estão descritos na [seção ***Training the model on labeling***](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=si5nOu94eT4w).

Apos feita as rotulagens, estes dados podem ser salvos no Drive da conta logada no [colab-notebook](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb), no qual na [seção ***Save data in Google Sheets***](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=lyQj-AxYNIbh) é passado o caminho do arquivo no **Arquivos** do notebook como `data_path`.

As funções `SearcherAPI()`, `SearcherWeb()` e `Interface()` obtém na interface abaixo da célula usada com a função, um botão que salva os arquivos em formato *.csv*.


# Referências

Van Dinter, R., Tekinerdogan, B., & Catal, C. (2021). Automation of systematic literature reviews: A systematic literature review. Information and Software Technology, 136, 106589. doi:10.1016/j.infsof.2021.106589
