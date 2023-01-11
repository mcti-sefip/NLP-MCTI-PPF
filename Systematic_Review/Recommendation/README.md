Neste trabalho, foi realizado um empenho para realização da Revisão de Literatura a partir de duas vertentes:

### a.  	Revisão de Literatura Narrativa
Primeiramente foi realizada a Revisão de Literatura Narrativa baseada em citação. Para essa construção o artigo original de Richie (1979) propõe o primeiro sistema de recomendação e posteriormente Pazzani (1999) elaborou um framework dos principais algoritmos de recomendação utilizados.
Ao utilizar esses dois papers seminais com o suporte, foi construído inicialmente um conjunto de artigos e trabalhos científicos que são correlatos a esses trabalhos. A estrutura teórica construída na revisão sistemática de literatura, foi baseada no trabalho de Pazzani (1999). Esse trabalho guiou as principais buscas realizadas nessa parte da revisão de literatura narrativa.

### b.  	Revisão de Literatura Sistemática
Além da revisão de literatura narrativa, baseada em citação, foi também utilizada a Revisão de Literatura Sistemática. Para esta etapa, foi utilizado o Semantic Scholar[1] como base para pesquisa dos artigos obtidos através de metodologia de recomendações, obtida através do algoritmo produzido na Meta 5 do projeto, cuja teoria está demonstrada no artigo científico: ## “Few-shot approach for systematic literature review classification” (Melo et al., 2022).##
A Revisão de Literatura Sistemática foi necessária para minimizar a chance de artigos recentes importantes não serem estudados neste trabalho, por isso, foram buscados de forma sistemática, artigos e trabalhos científicos publicados a partir de 2018, com base nas palavras-chaves do assunto pesquisado.
Esta revisão sistemática utilizou os componentes do protocolo definido por Kitchenham e Charters (2007, p 6), utilizados em revisões sistemáticas na engenharia de software. 
O intuito desta Revisão foi de aumentar a inclusão na revisão de artigos recentes publicados sobre recomendações.  As estratégias de pesquisa utilizadas foram as apresentadas logo abaixo:
 
●        Base de Periódicos: Semantic Scholar

●        Ferramenta de busca: metodologia semiautomatizada “Few-shot approach for systematic literature review classification” (Melo et al., 2022).

●        Search: +”recommendation” +”nlp”

●        Date Range: 2018 a 2022

●        Fields of Study: “Computer Science”

●        Publication Type: “Journal Article” “Conference”

●        Classificação: Relevância e Número de Citações.

# RESULTADOS DA REVISÃO DE LITERATURA

Dividimos e identificamos cinco abordagens diferentes usadas para fazer recomendações, conforme Pazzani (1999). Esta divisão inclui demographic filtering, collaborative-filtering, content-based, knowledge-based, e hybrid. 



## Demographic Filtering
 
Sistemas de Recomendação demográficas categorizam as recomendações aos usuários com base em seus atributos demográficos, como estereótipos, e suas opiniões sobre os itens. Grundy (Rich 1979) foi o primeiro e seminal Sistema de Recomendação. Na aplicação em um Grundy, (Rich 1979) desempenha o papel de um bibliotecário que coleta informações pessoais usando um sistema e um banco de dados estruturado para fazer uma recomendação de livros para os usuários. Na mesma ideia, em (Pazzani 1999), ao invés de ter um banco de dados estruturado para aprender com os usuários, eles aprendem informações demográficas sobre os usuários usando classificação de texto.
Collaborative-filtering 
Recomenda fontes de informação com base em informações demográficas altamente avaliadas por usuários com interesses semelhantes . A abordagem colaborativa faz recomendações achando correlações entre os usuários de sistemas de recomendação e usando o coeficiente de correlação  como um peso para prever a avaliação que  o usuário atual dará para um item (Pazzani, 1999).
 
## Content-based filtering

analisa o conteúdo de fontes de informação para criar perfil dos interesses do usuário. Em métodos de content-based que fazem recomendações analisando a descrição de itens que foram avaliados por usuários e a descrição de itens para ser recomendados (Pazzani, 1999). Todas as abordagens de content-based  representam documentos pelas palavras “importantes” nos documentos.

## Knowledge-based filtering
	
Diferentemente de outras tarefas de resolução de problemas, uma formalização compreensiva para sistemas de recomendação de knowledge-based ainda não estava disponível. Recentemente, Cena et al. (2021) forneceu uma base lógica na tentativa de unificar diferentes abordagens. A possibilidade de comparar sistemas baseados em “a maneira como eles usam o conhecimento para gerar recomendações” normalmente não atrai atenção suficiente na literatura, mas a possibilidade de escolher entre diferentes estratégias de geração de recomendações com base em sua semântica subjacente pode fornecer insights muito interessantes sobre a tarefa em si.

## Hybrid filtering

Para criar um sistema híbrido content-based ou collaborative, o sistema mantém perfis de usuários baseados em análise de conteúdo e compara diretamente esses perfis para determinar usuários semelhantes para recomendação colaborativa. Os usuários recebem itens quando pontuam muito contra seu próprio perfil, e quando são altamente avaliados por um usuário com um perfil semelhante.

