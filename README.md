![Desafio 1 - Python para Dados](imagens/Desafio_2_banner.png)  

# Desafio 2 - Frequências e Medidas

Segundo desafio prático desenvolvido pela **Squad Ada Lovelace** durante o **Bootcamp Data Analytics**, promovido pela **WoMakersCode**.

O objetivo deste desafio foi aprofundar os conceitos de frequência e medidas estatísticas (média, mediana, moda) por meio da análise exploratória do catálogo da Netflix.

## Sobre o desafio

O desafio propôs uma Análise Exploratória de Dados (EDA) a partir de uma base pública do Kaggle sobre o catálogo de filmes e séries da Netflix, contendo 5837 linhas e 12 colunas (título, diretor, elenco, país, data de adição, classificação, duração, gêneros, entre outras).

A partir dessa base, o grupo precisou responder perguntas de investigação sobre frequência, proporção, medidas de tendência central e visualização de dados, usando pandas, matplotlib e seaborn — incluindo a identificação e o tratamento de valores ausentes, presentes em algumas colunas da base original.

É possível acessar o arquivo em Jupyter Notebook clicando [aqui](Ada_Lovelace_Frequências_e_Medidas_Bootcamp_Data_Analytics_2026.ipynb).

## O que foi feito

O notebook segue essa estrutura:

1. **Importação e exploração inicial** dos dados (`shape`, `info`, identificação de valores nulos).
2. **Análises de frequência**: proporção entre filmes e séries, gênero mais frequente no catálogo.
3. **Análises estatísticas**: média, mediana e moda da duração dos filmes, além dos títulos mais curto e mais longo.
4. **Visualização de dados**: gráfico de barras por gênero e histograma de duração dos filmes.
5. **Atividade extra**: os 5 países com mais produções no catálogo.

## Perguntas respondidas

| # | Pergunta | Resumo do código | Resposta |
|---|----------|-------------------|----------|
| 1 | Exploração inicial: linhas e colunas, tipos, valores ausentes | `df.info()`, `df.isna().sum()` + cálculo de percentual, visualizado com `plot(kind='barh')` | 5837 linhas e 12 colunas, com variáveis dos tipos `int` e `string`, valores nulos em diretor, elenco, país, data de adição e classificação |
| 2 | Análise de frequência: proporção de filmes vs. séries no catálogo; gênero mais frequente | `value_counts(normalize=True)*100`, visualizado com gráfico de pizza;  `explode()` na coluna de gêneros + `groupby('tipo')['lista_generos'].value_counts()` | 67,5% filmes e 32,5% séries. O genêro mais frequente é International Movies, com 1797 contagens|
| 3 | Análises estatísticas: média, mediana e moda do tempo de duração dos filmes; filme mais curto e mais longo | Filtro por `tipo == 'Movie'` + `groupby('tipo')['duracao'].agg(mean, median, mode)`; Filtro pelo valor mínimo/máximo de `duracao` | Média = 98, Mediana = 97, Moda = 90; Mais curto: **Silent** (3 min); mais longo: **Black Mirror: Bandersnatch** (312 min) |
| 4 | Visualização de Dados: quantidade de títulos por gênero e distribuição da duração dos filmes | `value_counts().plot(kind='barh')`, depois reagrupamento dos gêneros com `.map()` e `sns.countplot()`; `df_filmes['duracao'].plot(kind='hist')`| Gráfico de barras com os gêneros originais e também reagrupados em categorias mais amplas; Histograma gerado mostrando a concentração das durações |
| 5 | (Extra) Quais os 5 países com mais produções no catálogo? | `str.split(', ')` + `explode()` + `value_counts().head()` | Estados Unidos, Índia, Reino Unido, Canadá e França |

## Visualizações

### Proporção de filmes vs. séries no catálogo

![Proporção de filmes vs. séries no catálogo da Netflix](/imagens/grafico_proporcao_filmes_series.png)

O catálogo é composto majoritariamente por filmes (67,5%), enquanto séries representam 32,5% do total. Essa diferença reflete o perfil do catálogo da Netflix em novembro de 2019 (data da base), período em que o investimento em produções seriadas originais ainda estava em expansão.

### Quantidade de títulos por gênero (reagrupado)

![Quantidade de títulos por gênero](/imagens/grafico_generos_reagrupado.png)

Para chegar a esse gráfico, o grupo reagrupou os mais de 400 rótulos de gênero originais da base (muitos deles sobrepostos, como "Dramas" e "TV Dramas") em categorias mais amplas e comparáveis, usando um dicionário de mapeamento. Depois do reagrupamento, **Internacional** segue como a categoria mais frequente, seguida por **Ação** e **Comédia** — confirmando, em outra granularidade, o mesmo padrão identificado na pergunta 4 (onde "International Movies" já aparecia como gênero isolado mais comum). Categorias como Musical, Fantasia e Sci-Fi e Outros aparecem com poucos títulos, indicando nichos pouco explorados no catálogo da época.

### Distribuição da duração dos filmes

![Distribuição da duração dos filmes](/imagens/grafico_duracao_filmes.png)

O histograma mostra uma concentração clara de filmes entre 70 e 130 minutos, com o maior volume de títulos na faixa de 100 a 125 minutos — o que é coerente com a média (98 min), mediana (97 min) e moda (90 min) calculadas na pergunta 5. A distribuição tem uma cauda longa à direita, puxada por poucos filmes de duração muito maior (como o já citado *Black Mirror: Bandersnatch*, com 312 min), o que explica por que a média fica levemente acima da moda.

## Tecnologias utilizadas

- Python
- Pandas
- Matplotlib
- Seaborn
- Jupyter Notebook

## Como executar

1. Clone este repositório.
2. Abra o notebook `Ada_Lovelace_Frequências_e_Medidas_Bootcamp_Data_Analytics_2026.ipynb` no Jupyter ou no Google Colab.
3. Execute as células em ordem — a base de dados é carregada diretamente de uma URL, sem necessidade de download manual.

---

<p align="center">
  Feito com 💜 por nosso Squad!
</p>
