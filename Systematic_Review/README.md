
# Metodologia de Revisão Sistemática da Literatura

## O que é Revisão Sistemática da Literatura (SLR)

O objetivo da revisão sistemática da literatura é reunir materiais semelhantes (artigos, livros, etc.) para responder uma determinada questão científica ou para realizar uma visão geral da base científica na literatura sobre um problema.

## Quais são os passos para produzir uma SLR?

Os passos de uma SLR têm como objetivo estruturar um plano de trabalho que é feito de forma sistemática. Eles ajudam a orientar o pesquisador e as pessoas que estão interessadas em ler a pesquisa a fim de tornar possível a replicabilidade da coleta bibliográfica da revisão ou dos seus processos.

### Fase 1 (Plano de Revisão)

1. Especificar a pergunta de pesquisa (por exemplo, quais são os hardware mais avançados para Deep-Learning?)
2. Desenvolver o protocolo de revisão (por exemplo, critérios de inclusão/
3. exclusão, estratégia de busca, critérios de avaliação de qualidade, etc.)
Validar o protocolo de revisão (por exemplo, avaliar se é possível que exemplos entrem neste protocolo)

### Fase 2 (Produzir a revisão)

4. Coletar a base de dados (banco de dados contendo exemplos da estratégia de busca com palavras-chave em um mecanismo de busca)
5. Selecionar os estudos primários (Nesta metodologia - com os critérios de inclusão/exclusão definidos - deve ser feito usando o título e o resumo de cada exemplo.)
6. Avaliar a qualidade dos estudos (com os estudos primários selecionados, os critérios de avaliação de qualidade devem ser aplicados aos exemplos incluídos na RSL.)
7. Sintetizar a base de dados com estudos de alta qualidade (Criar uma base de dados com os exemplos de alta qualidade que foram selecionados para a RSL.)

### Fase 3 (Relatório de revisão)

1. Formatar o relatório principal (Obs.: Este passo é a escrita de um documento em formato de relatório explicitando a metodologia da SLR empregada definida na Fase 1, os resultados da Fase 2 e a conclusão/discussão sobre as bases de dados levantadas para a SLR.)
2. Avalie o relatório (Revisão do relatório por parte da equipe e/ou do projeto)
3. Compartilhe o banco de dados e/ou o relatório (Obs.: Este passo tem como objetivo disponibilizar a SLR para que outros pesquisadores consiga utilizar dos recursos concretizados para efetuar alguma pesquisa ou aprimorar a SLR. Este pode ser feito utilizando a plataforma [zenodo](https://zenodo.org/))

## Ferramentas para ajudar o pesquisador a fazer uma SLR

Para o controle e ajuda do levantamento e classificação dos exemplos para a SLR, foi criada uma aplicação que possibilita realizar os passos 4 e 5 utilizando o [notebook de aplicação](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb). Esta aplicação procura reduzir o tempo para levantar bases de dados e a classificação dos estudos primários.

A busca é feita utilizando a ferramenta de busca do [Semantic Scholar](https://www.semanticscholar.org/), que possui um grafo de relações entre os resultados da busca criado por uma IA. Esta busca é realizada utilizando a biblioteca de python [S2Query](https://github.com/mcti-sefip/NLP-MCTI-PPF/tree/main/Systematic_Review/Systematic_Review_Methodology/Buscador).

A classificação para estudos primários é realizada por um modelo de inteligência artificial (IA) que ao rotular 4 exemplos (2 incluídos, 2 excluídos) para a revisão sistemática, o modelo predita, utilizando o titulo e o resumo do exemplo, uma confiança (*confidence*) para cada exemplo, no qual é ranqueado/ordenado com base no *rank* a base de dados passada. Exemplos com confianças próximas de 1 (*confidence* $\approx$ 1) indica que o modelo tende a incluir estes exemplos na SLR. O modelo utilizado é resultado da pesquisa "Few-shot approach for systematic literature review classifications" descrito na pasta [Systematic_Review_Methodology/Pesquisa](https://github.com/mcti-sefip/NLP-MCTI-PPF/tree/main/Systematic_Review/Systematic_Review_Methodology/Pesquisa).

### Automatização das etapas 4 e 5 da Fase 2

#### Etapa 4

- a) a) Levantar um ou vários bancos de dados usando palavras-chave e a ferramenta de pesquisa do [Semantic Scholar](https://www.semanticscholar.org/). A pesquisa mencionada é feita através do [`SearcherWeb()`](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=kXCMmkts700P) ou [`SearcherAPI()`](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=mTQwDdhG6kxe) e as principais diferenças entre elas são descritos no [notebook](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=19agpVfcMqBu).

#### Etapa 5

- b) Fazer a rotulagem destes artigos utilizando o **titulo** e **resumo**, com base nos critérios de **inclusão**  e **exclusão** da revisão sistemática imposta. Se for utilizar o **passo 3**, fazer no **mínimo 16 rotulagens** (8 incluídos e 8 excluídos). Este pode ser feito utilizando a função **`Interface(data)`**.

- c) (Opcional) [Treinar o modelo de linguagem natural](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=z5AsHo-wMsRP) para automatizar a rotulagem e/ou ranquear os exemplos da base passada na função **`Interface(data)`**. O modelo é treinado com a quantidade de exemplos por classe (incluído, excluído) passado para o parâmetro `size_per_class`.

- d) (Opcional) Rotular novos exemplos (ou corrigir a classificação do modelo) utilizando o ranqueamento predito pelo modelo. Este procura ajudar o pesquisador na busca de estudos primários sob a base passada em **`Interface(data)`**. Este passo ajuda o pesquisador a rotular os exemplos para a revisão sistemática utilizando a confiança do modelo em excluir o máximo de exemplos irrelevantes e retornar os mais relevantes para a inclusão na SLR na busca de estudos primários.

- e) (Opcional) Voltar aos **itens c)** e **d)** até que esteja satisfeito com as rotulagens ou tenha rotulado toda a base de dados.

O passo 4 e 5 são realizados utilizando apenas a função **`Interface(data)`**. Alguns dos critérios para utilizar esta função estão descritos na [seção ***Training the model on labeling***](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=si5nOu94eT4w).

Apos feita as rotulagens, estes dados podem ser salvos no Drive da conta logada no [colab-notebook](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb), no qual na [seção ***Save data in Google Sheets***](https://colab.research.google.com/github/BecomeAllan/ML-SLRC/blob/main/Application/Classification_automation_SLR.ipynb#scrollTo=lyQj-AxYNIbh) é passado o caminho do arquivo no **Arquivos** do notebook como `data_path`.

As funções `SearcherAPI()`, `SearcherWeb()` e `Interface()` obtém na interface abaixo da célula usada com a função, um botão que salva os arquivos em formato *.csv*.


# Referências

Van Dinter, R., Tekinerdogan, B., & Catal, C. (2021). Automation of systematic literature reviews: A systematic literature review. Information and Software Technology, 136, 106589. doi:10.1016/j.infsof.2021.106589
