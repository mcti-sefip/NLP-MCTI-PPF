
# Metodologia de Revisão Sistemática da Literatura

## O que é Revisão Sistemática da Literatura

A revisão sistemática da literatura (SLR) tem como objetivo reunir materiais semelhantes (artigos, livros, etc.) para responder alguma pergunta científica ou realizar um levantamento de uma base de literatura científica sobre algum assunto.

## Quais fases são realizadas para fazer uma SLR

As fases de uma SLR têm como objetivo estruturar um plano de trabalho que seja realizado de forma sistemática e consiga orientar o pesquisador e pessoas que queiram ler a pesquisa no intuito de possibilitar a replicabilidade do levantamento bibliográfico da revisão ou os processos deste.

### Fase 1 (Plano de Revisão)

1. Especificar a pergunta da pesquisa (Ex.: Quais são os hardwares mais avançadas para Deep-learning ?)
2. Desenvolver o protocolo de Revisão (Ex.:  Critérios de inclusão/exclusão, estratégia de busca, Critérios de avaliação de qualidade, etc.)
3. Validar o protocolo de Revisão (Ex. Avaliar se é possível exemplos entrarem nestes protocolo)

### Fase 2 (Conduzir Revisão)

4. Levantar a Base de dados (Base de dados contendo exemplos resultantes da estratégia de busca com palavras chaves em algum mecanismo de busca)
5. Selecionar os estudos primários (Obs.: Nesta metodologia, os critérios de inclusão/exclusão definidos, devem ser feitos utilizando o titulo e o resumo de cada exemplo.)
6. Avaliar a qualidade dos estudos (Depois de realizar a seleção dos estudos primários, aplica-se os critérios de avaliação de qualidade para os exemplos incluídos para a SLR.)
7. Sintetizar banco de dados com estudos de qualidade (Criar banco de dados com os exemplos de qualidade que entraram para a SLR.)

### Fase 3 (Relatório da Revisão)

1. Formatar o relatório principal (Obs.: Este passo é a escrita de um documento em formato de relatório explicitando a metodologia da SLR empregada definida na Fase 1, os resultados da Fase 2 e a conclusão/discussão sobre as bases de dados levantadas para a SLR.)
2. Avaliar o relatório (Revisão do relatório por parte da equipe e/ou do projeto)
3. Divulgar Base de dados e/ou relatório (Obs.: Este passo tem como objetivo disponibilizar a SLR para que outros pesquisadores consiga utilizar dos recursos concretizados para efetuar alguma pesquisa ou aprimorar a SLR. Este pode ser feito utilizando a plataforma [zenodo](https://zenodo.org/))

## Ferramentas para ajudar o pesquisador na SLR

Para o controle e ajuda do levantamento e classificação dos exemplos para a SLR, foi criada uma aplicação que possibilita realizar os passos 4 e 5 utilizando o [notebook de aplicação](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb). Esta aplicação procura reduzir o tempo para levantar bases de dados e a classificação dos estudos primários.

A busca é feita utilizando a ferramenta de busca do [Semantic Scholar](https://www.semanticscholar.org/), que possui um grafo de relações entre os resultados da busca criado por uma IA. Esta busca é realizada utilizando a biblioteca de python [S2Query](https://github.com/mcti-sefip/NLP-MCTI-PPF/tree/main/Systematic_Review/Systematic_Review_Methodology/Buscador).

A classificação para estudos primários é realizada por um modelo de inteligência artificial (IA) que ao rotular 4 exemplos (2 incluídos, 2 excluídos) para a revisão sistemática, o modelo predita, utilizando o titulo e o resumo do exemplo, uma confiança (*confidence*) para cada exemplo, no qual é ranqueado/ordenado com base no *rank* a base de dados passada. Exemplos com confianças próximas de 1 (*confidence* $\approx$ 1) indica que o modelo tende a incluir estes exemplos na SLR. O modelo utilizado é resultado da pesquisa "Few-shot approach for systematic literature review classifications" descrito na pasta [Systematic_Review_Methodology/Pesquisa](https://github.com/mcti-sefip/NLP-MCTI-PPF/tree/main/Systematic_Review/Systematic_Review_Methodology/Pesquisa).

### Automatização dos passos 4 e 5 da Fase 2

#### Passo 4

- a) Fazer levantamento de uma ou várias bases de dados utilizando palavras chaves e a ferramenta de busca do [Semantic Scholar](https://www.semanticscholar.org/). Esta busca é através das funções [`SearcherWeb()`](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=kXCMmkts700P) ou [`SearcherAPI()`](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=mTQwDdhG6kxe), as principais diferenças estão descritas no [notebook](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=19agpVfcMqBu).

#### Passo 5

- b) Fazer a rotulagem destes artigos utilizando o **titulo** e **resumo**, com base nos critérios de **inclusão**  e **exclusão** da revisão sistemática imposta. Se for utilizar o **passo 3**, fazer no **mínimo 16 rotulagens** (8 incluídos e 8 excluídos). Este pode ser feito utilizando a função **`Interface(data)`**.

- c) (Opcional) [Treinar o modelo de linguagem natural](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=z5AsHo-wMsRP) para automatizar a rotulagem e/ou ranquear os exemplos da base passada na função **`Interface(data)`**. O modelo é treinado com a quantidade de exemplos por classe (incluído, excluído) passado para o parâmetro `size_per_class`.

- d) (Opcional) Rotular novos exemplos (ou corrigir a classificação do modelo) utilizando o ranqueamento predito pelo modelo. Este procura ajudar o pesquisador na busca de estudos primários sob a base passada em **`Interface(data)`**. Este passo ajuda o pesquisador a rotular os exemplos para a revisão sistemática utilizando a confiança do modelo em excluir o máximo de exemplos irrelevantes e retornar os mais relevantes para a inclusão na SLR na busca de estudos primários.

- e) (Opcional) Voltar aos **itens c)** e **d)** até que esteja satisfeito com as rotulagens ou tenha rotulado toda a base de dados.

O passo 4 e 5 são realizados utilizando apenas a função **`Interface(data)`**. Alguns dos critérios para utilizar esta função estão descritos na [seção ***Training the model on labeling***](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=si5nOu94eT4w).

Apos feita as rotulagens, estes dados podem ser salvos no Drive da conta logada no [colab-notebook](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb), no qual na [seção ***Save data in Google Sheets***](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=lyQj-AxYNIbh) é passado o caminho do arquivo no **Arquivos** do notebook como `data_path`.

As funções `SearcherAPI()`, `SearcherWeb()` e `Interface()` obtém na interface abaixo da célula usada com a função, um botão que salva os arquivos em formato *.csv*.


# Referências

Van Dinter, R., Tekinerdogan, B., & Catal, C. (2021). Automation of systematic literature reviews: A systematic literature review. Information and Software Technology, 136, 106589. doi:10.1016/j.infsof.2021.106589
