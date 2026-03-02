# Fairness / Bias Report

## 1

- **Sexo:** Uma menor acurácia quanto a algum sexo pode levar à
injustiças contra esse grupo, que sairia mais prejudicado pelas
decisões tomadas baseada no modelo.
- **Raça:** Assim como sexo, qualquer viés presente resultará em
disparidade entre tratamentos e disposição de recursos para alguns
grupos com maior taxa de erro no modelo.
- **Idade:** Por mais que seja esperado resultados diferentes para cada
faixa etária, um viés presente dentro de uma faixa pode implicar em
um foco maior sendo dado a um grupo e ignorando os outros.
- **Região:** Naturalmente, há disparidade entre regiões, seja devido ao
recursos disponíveis ou condições externas que levam a mais casos de
doenças respiratórias. Por isso, mostra-se importante verificar o
desempenho do modelo, não importando a região.

## 2: Cálculo de Métricas

  Para análise de justiça, foi usado apenas a métrica de sMAPE,
uma vez que outras métricas disponíveis (como MAE e RMSE) trabalham com
valores absolutos, e trazem informações inconclusivas quando há diferença
na quantidade de dados por categoria.

  Além disso, para verificar impacto sobre grupos, categorizou-se cada dado
baseado na média histórica dos grupos sociais. Em outras palavras, como os
dados estão agregados e possui múltiplos valores (devido aos "lags"),
era necessário uma estratégia para categorizar qual grupo os dados melhor
representavam. Para tal, tira-se a média de todos os valores "lag" que representavam
um grupo específico, e no final verifica-se qual grupo é maioria.
Por exemplo, um hospital que, no agregado, possui mais mulher a homem é categorizado
como dentro do grupo sensível feminino ("Fem").

  Segue-se os resultados:

- Age:
![First evaluation based on Age](Images/age_v1.png "Evaluation by age")

- Sex:
![First evaluation based on Sex](Images/sex_v1.png "Evaluation by sex")

- Race:
![First evaluation based on Race](Images/race_v1.png "Evaluation by race")

- Region:
![First evaluation based on Region](Images/region_v1.png "Evaluation by region")

- Size:
![First evaluation based on Size](Images/size_v1.png "Evaluation by Size")

## 3: Avaliação Inicial

  Notou-se pequena disparidade entre os grupos dentro das
categorias de idade, sexo e raça. A maior diferença presente é
entre pessoas pretas e pessoas de outras raças (7%).

  No entanto, uma disparidade maior foi encontrada entre as regiões.
Por mais que a maioria esteja na casa dos 30%, temos regiões com
valores bons (SP, 26%) e valores péssimos (RR, 44.8%). Além das regiões,
há também uma grande disparidade entre tamanhos de hospitais, com uma diferença
de 18.8%.

  Para garantir maior justiça no modelo, definiu-se regiões como prioridade
de correção. Quanto aos outros grupos, o objetivo é não afetá-los durante
o processo de mitigação dos erros. Por mais que há uma grande diferença entre
os portes de hospitais, qualquer tentativa de correção de viés resulta em uma
piora drástica do modelo e aumenta a disparidade entre os grupos.

## 4: Correção

  A metodologia usada para esse processo é a reamostragem,
o qual consiste na equalização da quantidade de dados entre diferentes grupos.
Em especial, decidiu-se criar dados sintéticos para "over-sampling", uma vez que
a remoção de dados ("under-sampling") resultaria em poucos dados no total para
treinamento do modelo.

  Para reamostragem, foi utilizada a ferramenta SMOTENC, varição de SMOTE capaz
de trabalhar com dados categóricos. A fim de garantir replicabilidade, foi definido
uma semente aleatória fixada, com valor 18979.

- **Amostragem inicial:**

**Age:**

![Base sample for age](./Images/sample_age_1.png "Base sample based on age")

**Sex:**

![Base sample for sex](./Images/sample_sex_1.png "Base sample based on sex")

**Race**:

![Base sample for race](./Images/sample_race_1.png "Base sample based on race")

**Region**:

![Base sample for region](./Images/sample_region_1.png "Base sample based on region")

**Hospital Size**:

![Base sample for size](./Images/sample_size_1.png "Base sample based on size")

- **Amostragem pós processamento:**

**Age:**

![Resample for age](./Images/sample_age_2.png "Resample based on age")

**Sex:**

![Resample for sex](./Images/sample_sex_2.png "Resample based on sex")

**Race**:

![Resample for race](./Images/sample_race_2.png "Resample based on race")

**Region**:

![Resample for region](./Images/sample_region_2.png "Resample based on region")

**Hospital Size**:

![Resample for size](./Images/sample_size_2.png "Resample based on size")

## 5: Reavaliação

  Notou-se uma pequena diminuição da disparidade encontrada anterior,
reduzindo de 18.8% para 18.3%. Em especial, houve uma melhora na performance
geral do modelo em relação às regiões. O pior caso desceu de 44.8% para
43.9% e o melhor caso caiu de 26% para 25.6%.

  Quanto às outras categorias, cumpriu-se o objetivo de mantê-las similares, evitando
assim de criar uma nova diferença de desempenho entre os outros grupos.

**Resultados:**

- Age:
![Second evaluation based on Age](Images/age_v2.png "Evaluation by age")

- Sex:
![Second evaluation based on Sex](Images/sex_v2.png "Evaluation by sex")

- Race:
![Second evaluation based on Race](Images/race_v2.png "Evaluation by race")

- Region:
![Second evaluation based on Region](Images/region_v2.png "Evaluation by region")

- Size:
![Second evaluation based on Size](Images/size_v2.png "Evaluation by Size")

**Obs:** Foi feito vários testes de reamostragem, incluindo testes contendo
"over-sampling", "under-sampling" e reamostragem de outros grupos além da
categoria de região. Os resultados tendiam a piorar as outras categorias
sem haver melhora na categoria de região.
