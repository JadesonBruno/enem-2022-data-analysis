# Análise de Dados do ENEM 2022

[![License](https://img.shields.io/npm/l/react)](https://github.com/JadesonBruno/enem-2022-data-analysis/blob/main/LICENSE)

Este repositório tem como objetivo armazenar o projeto desenvolvido no  módulo "Vizualização de Dados com Power BI" do Curso de Especialização  "Vem Ser Tech - Data Analystic", desenvolvido pela [ADA](https://ada.tech/) em parceria com o [Ifood](https://www.ifood.com.br/). O curso foi guiado pela instrução do professor [Bruno Trindade](https://www.linkedin.com/in/brunotrbr/).

O projeto foi um requisito essencial para a aprovação no módulo e encerra a cadeia de disciplinas que fizeram parte da formação em Data Analystic da ADA, consolidando o aprendizado prático dos participantes e preparando-os para o mercado de trabalho.

Este repositório tem por objetivo trazer insights pertinentes ao Exame Nacional do Ensino Médio (ENEM) de 2022, trazendo insights sobre os incritos, análise de absenteísmo dos estudantes, desempenho dos participantes e exploração de dados socioeconômicos e geográficos.

A análise foi projetada para ser visualizada no formato de "Dashboard´s" no [Microsoft Power BI](https://www.microsoft.com/pt-br/power-platform/products/power-bi), permitindo a demonstração dos resultados através de painéis interativos e facilitando o entendimento do público.

## Contextualização

Como Secretário do Ministério da Educação estou profundamente envolvido na melhoria contínua da qualidade da educação no Brasil. Uma parte crucial do meu trabalho é entender o desempenho dos estudantes no Exame Nacional do Ensino Médio (ENEM) de 2022.

Para facilitar meu trabalho e apresentar soluções para moldar políticas educacionais gostaria de obter informações sobre esses temas:

- Desempenho dos Estudantes: Analisar as notas dos estudantes em diferentes disciplinas para identificar áreas onde os estudantes estão se saindo bem e onde eles podem precisar de mais apoio.

- Tendências Geográficas: Examinar o desempenho dos estudantes com base em sua localização geográfica. Isso pode ajudar a identificar regiões que podem precisar de mais recursos educacionais.

- Dados Socioeconômicos: Explorar a relação entre o desempenho dos estudantes e seus antecedentes socioeconômicos. Isso pode fornecer insights sobre como fatores externos podem estar afetando o desempenho dos estudantes.

## Dataset

Os dados utilizados neste projeto são os [Micodados do ENEM 2022](https://www.gov.br/inep/pt-br/acesso-a-informacao/dados-abertos/microdados/enem). Os microdados do Enem são o menor nível de desagregação de dados recolhidos por meio do exame. Eles atendem a demanda por informações específicas ao disponibilizar as provas, os gabaritos, as informações sobre os itens, as notas e o questionário respondido pelos inscritos no Enem.

## Projeto

### Fluxograma do Projeto

<p align="center">
  <img src="./assets/fluxograma_enem_2022.png">
</p>

### ETL

Para otimizar o desempenho no Power BI, inicialmente, realizamos a leitura do arquivo CSV utilizando a biblioteca Pandas. Isso nos permitiu reduzir o número de colunas, focando apenas naquelas que são relevantes para a nossa análise.

**Antes:**
<p align="center">
  <img src="./assets/dataset_completo.png">
</p>

**Depois:**
<p align="center">
  <img src="./assets/dataset_filtrado.png">
</p>

Após essa etapa, foi possível exportar um conjunto de dados que inclui as colunas relevantes para nossa análise, bem como o total de inscritos no ENEM.

Posteriormente, para facilitar o processamento no Power BI, limitamos o conjunto de dados a uma amostra de 100.000 instâncias. 

Com essas etapas finalizadas foi possível obter um dataset completo e outro filtrado que foram usados como parâmetros para a troca do Dataset no Power BI.

Gostaria de destacar que essas etapas foram cruciais para garantir uma análise eficiente e ágil.

### Recategorização de Variáveis

Outro aspecto importante do nosso trabalho foi a recategorização de algumas variáveis do conjunto de dados. Enfrentamos um desafio com variáveis que continham múltiplas categorias, resultando em visualizações excessivamente complexas que dificultavam a interpretação gráfica pelos stakeholders.

Para resolver essa questão, optamos pela desnormalização dos dados, aplicando uma modelagem dimensional que reduziu efetivamente o número de categorias. Isso simplificou nossas visualizações, tornando-as mais acessíveis e compreensíveis para os stakeholders.

**Antes:**
<p align="center">
  <img src="./assets/varias_categorias.png">
</p>

**Depois:**
<p align="center">
  <img src="./assets/poucas_categorias.png">
</p>

### Modelagem

Optou-se pela modelagem dimensional do conjunto de dados, especificamente utilizando o modelo Snowflake. Essa abordagem nos permitiu estruturar os dados de forma otimizada para análises complexas e ágeis. Com o Snowflake, conseguimos implementar um possível ambiente de data warehousing altamente escalável e flexível.

<p align="center">
  <img src="./assets/modelagem_enem_2022.png">
</p>

### Dashboard: Inscritos

<p align="center">
  <img src="./assets/inscritos.png">
</p>

Nesta visualização, conseguimos extrair alguns insights significativos, como:

1. A proporção de mulheres que realizam o ENEM é superior à dos homens. Isso pode ser atribuído ao fato de que, de acordo com o Censo de 2022, há um maior número de mulheres no Brasil, o que se reflete nos participantes do ENEM. Além disso, é importante destacar a crescente participação das mulheres no mercado de trabalho, muitas das quais buscam construir carreiras sustentadas por uma formação acadêmica sólida.

2. O percentual de inscritos do Nordeste é maior que o Sudeste. Esse dado traz a região Nordeste para um ponto de destaque em políticas educacionais futuras.

3. A maior parcela da população de inscritos participam de famílias com renda per capita de até um salário mínimo. Esse dado reflete a vulnerabilidade econômica que enfrentamos no país nos diversos setores da sociedade.

4. O maior número de inscritos pertence a etinia parda, nos demonstrando o caráter miscigenado da sociedade brasileira.


### Dashboard: Absenteísmo

<p align="center">
  <img src="./assets/absenteísmo.png">
</p>

Nesta visualização, conseguimos extrair alguns insights significativos, como:

1. Os dados de absenteísmo parecem seguir uma proporção semelhante aos dados de inscrito. Por exemplo, o número de mulheres que faltaram ao exame é proporcional ao número de mulheres inscritas. 

2. O segundo dia de prova, que abrange Ciências da Natureza e Matemática, apresenta um percentual maior de faltas. Isso pode ser atribuído ao chamado “efeito do segundo dia de prova”, onde um desempenho insatisfatório no primeiro dia pode levar à desistência do estudante. Além disso, o fato de que as disciplinas do segundo dia são voltadas para as ciências exatas, áreas em que os estudantes geralmente enfrentam mais dificuldades, também pode contribuir para esse fenômeno.

### Dashboard: Resultados

<p align="center">
  <img src="./assets/resultados.png">
</p>

Nesta aba, algumas análises são:

1. Em resultados, podemos observar que a média geral, calculada como a soma de todas as notas dividida pelo número total de avaliações, é inferior à média da redação. A partir dessa constatação, podemos inferir que a habilidade técnica de produzir um texto dissertativo, aliada à criatividade na sua construção, é uma característica destacada entre os estudantes. Isso sugere que esses alunos possuem uma capacidade notável de analisar a realidade e comunicá-la de forma eficaz ao público.

2. A análise dos dados revela que, apesar de um grande número de respostas ausentes, a média geral em diversas disciplinas nas escolas públicas é inferior à das escolas privadas. Esta constatação evidencia as lacunas no sistema de ensino público do país, sinalizando a necessidade de intensificar as ações governamentais neste setor.


### Dashboard: Insight 1

<p align="center">
  <img src="./assets/insight_1.png">
</p>

1. Percebemos através do gráfico que quanto maior a renda familiar, maior o desempenho do estudante levando em consideração a nota média, levando em consideração também qualque região do Brasil, o comportamento é o mesmo. Pessoas sem nenhuma renda, pessoas que recebem até 1 salário e que recebem de 1 até 2 salários mínimos têm sempre um desempenho abaixo da média nacional.

2. A Região Norte possui o pior cenário levando em consideração qualquer faixa de renda.

### Dashboard: Insight 2

<p align="center">
  <img src="./assets/insight_2.png">
</p>

1. Independentemente da região, os alunos apresentaram o melhor desempenho em Redação e o pior desempenho em Ciências da Natureza, que inclui Biologia, Física e Química.

Diante deste cenário, torna-se necessário reformular a grade curricular dessas disciplinas, incorporando métodos mais eficazes para transmitir o conhecimento aos alunos.

### Dashboard: Insight 3

<p align="center">
  <img src="./assets/insight_3.png">
</p>

1. No 3º insight, é evidente o desempenho insatisfatório da população indígena. Ao analisarmos a Região Norte, segmentando o público por raça e cor, observamos que todos os grupos estão abaixo da média nacional.
Essa realidade é corroborada pelos dados e frequentemente retratada pela mídia nacional, que destaca as dificuldades enfrentadas pelos estudantes da região para se deslocarem até a escola.

As políticas educacionais devem ser direcionadas especificamente para a região e para a população indígena, transformando o que antes era um exemplo negativo em um modelo a ser seguido. 

### Dashboard: Insight 4

<p align="center">
  <img src="./assets/insight_4.png">
</p>

1. Embora a média geral das mulheres seja inferior à dos homens, essa diferença não se reflete na nota de redação. Este cenário reflete mudanças significativas na sociedade, onde o antigo paradigma da "Mulher Dona de Casa" está gradativamente perdendo força. Nos últimos anos, observamos a entrada crescente das mulheres no mercado de trabalho, impulsionadas por carreiras respaldadas por cursos de ensino superior. Um aspecto relevante a ser considerado é a comparação entre esses dados e o número de mulheres que se inscrevem no exame. Embora o número de inscritas já tenha superado o de homens, as médias das notas permanecem desiguais. Uma possível explicação para essa discrepância reside na natureza do exame: obter uma pontuação elevada no ENEM demanda um esforço considerável em termos de tempo de estudo. Muitas mulheres enfrentam obstáculos nesse sentido, desde tenra idade, ao serem direcionadas para assumir responsabilidades domésticas e, muitas vezes, para contribuir financeiramente para suas famílias desde cedo. É crucial ressaltar que, apesar dessa disparidade, estamos testemunhando uma redução gradual na diferença das notas entre homens e mulheres. Isso é particularmente evidente no caso da nota de redação, onde as mulheres já ultrapassaram seus colegas do sexo masculino. Essa tendência indica uma evolução positiva e demonstra que as mulheres estão conquistando seu espaço e reconhecimento no âmbito educacional, apesar dos desafios ainda presentes.

## Links Úteis:
- [Vizualização do Dashboard](https://app.powerbi.com/view?r=eyJrIjoiZTQwOGY2OGUtMjhhZi00NWVhLTkwY2ItOWQxNzg4YzE2MGNmIiwidCI6IjMzMWI2YTljLWJiNWYtNDk0Ni1hN2U3LWE5ZmQ5ZDUzNmVhNiJ9)
- [INEP ENEM](https://www.gov.br/inep/pt-br/areas-de-atuacao/avaliacao-e-exames-educacionais/enem)

- [Documentação do Power BI](https://learn.microsoft.com/pt-br/power-bi/)


## Tecnologias Utilizadas

- Microsoft Power BI
- Python (Pandas)
- Microsoft Excel

## Contribuições

Contribuições são bem-vindas. Sinta-se à vontade para sugerir melhorias e possíveis correções para o código por meio de uma issue ou pull requests.

## Author

Jadeson Bruno Albuquerque da Silva

[![Linkedin](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/jadeson-silva/)