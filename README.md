# Análise de Vendas e Entregas da Empresa MaxOil Solutions
Utilizando um banco de dados fictício em Excel, referente a uma empresa fictícia de vendas de `aditivos` e `lubrificantes`, iniciamos uma análise com o objetivo de compreender o panorama de vendas, a distribuição por filiais, categorias, produtos e entregas no período de 2019 a 2022. O objetivo inicial é realizar uma análise exploratória, buscando identificar onde está a maior concentração de vendas, quais produtos atuam como drivers, se houve crescimento ao longo dos anos e onde se encontra o maior impacto dessa evolução. Além disso, será avaliada a performance das entregas, com o objetivo de identificar pontos de melhoria e direcionar ações para corrigir possíveis atrasos. Fazendo o download dos arquivos na pasta Dataset que está no repositório desse projeto, é possível extrair, transformar e carregar os dados utilizados nesta análise e obter os mesmos resultados apresentados.
<br><br>

## Análise exploratória de dados
<img align="right" width="600"  src="https://github.com/Pedrofx-98/MaxOilSolutions/blob/main/Figures/Modelo_fonte_dados_PQ.png">
Iniciamos o projeto importando e compreendendo cada objeto, tabela, campo, tipo de dado e relacionamento do modelo de dados obtido no Excel.
Após a identificação das chaves primárias (PK) e a definição dos campos das tabelas fato e dimensão necessários para as análises, desenvolvemos a etapa de transformação, contemplando a padronização dos tipos de dados padronização dos tipos de dados (<code>Data</code>, <code>Texto</code>, <code>Inteiro</code> e <code>Decimal</code>), a aplicação de filtros nas colunas e a mesclagem entre as tabelas (joins). O objetivo dessa etapa foi reduzir e otimizar os dados contidos na base, preparando-os para uma abordagem mais organizada e estratégica. As análises e os primeiros insights passaram a ser identificados a partir da construção dos dashboards, quando foi possível visualizar os dados de forma consolidada durante a análise exploratória de dados, como por exemplo:
 <br><br>
- Vendas por Região <br>
- Vendas por Filiais <br>
- Categorias com mais vendas <br>
- Vendas por Business Line.
<br><br>
<a href="https://app.powerbi.com/view?r=eyJrIjoiM2I2YTlmNGItZTgzZS00MDEyLWFlOWYtZDk2ZmY5OTQyNDkzIiwidCI6IjY1OWNlMmI4LTA3MTQtNDE5OC04YzM4LWRjOWI2MGFhYmI1NyJ9" target="_blank">Clique aqui</a> e acesse o Dashboard.
<br><br>

## Modelo e Fonte dos dados
<img align="left" width="450"  src="https://github.com/Pedrofx-98/MaxOilSolutions/blob/main/Figures/Modelo_fonte_dados.png">
Após conversa com a equipe de Tecnologia da Informação da empresa, fomos informados sobre a existência de um data warehouse contendo informações adicionais que poderiam fornecer insights valiosos sobre as entregas dos produtos. Diante disso, surgiu a necessidade de importar dados de outras fontes, como planilhas Excel, que continham informações sobre a ordem de compra, a expectativa de entrega e a data de finalização.

Após a importação, essa tabela foi mesclada à tabela fato, aplicando-se uma regra para classificar o status da entrega como **“On time”** ou **“Late”**, de acordo com a comparação entre o prazo previsto e o tempo real de entrega, resultando na criação de uma nova coluna.

Com o objetivo de aprimorar a visualização dos dados e viabilizar a criação de medidas de inteligência temporal, foi criada e adicionada uma nova tabela denominada `Dim_Calendario`, contendo informações detalhadas de vendas e entregas organizadas por ano, trimestre, mês e semana.
<br>
<br>
## Medidas

<img align="right" width="500" height="320"
     src="https://github.com/Pedrofx-98/MaxOilSolutions/blob/main/Figures/Medidas_Vendas.png">

A partir da identificação das necessidades do negócio, considerando as regras de negócio definidas pelo cliente e sua correta aplicação no modelo de dados, iniciamos o desenvolvimento das medidas analíticas.

Foram criadas medidas voltadas à análise de desempenho de vendas, incluindo: total de vendas, vendas do último ano, variações (delta) entre anos e meses, percentual de crescimento, valores acumulados, além do total de entregas dentro e fora do prazo, seus respectivos percentuais e a média de dias de entrega.

Para garantir organização, padronização e escalabilidade do modelo, as medidas foram estruturadas em duas tabelas distintas: uma dedicada às medidas de inteligência temporal e outra concentrando as medidas calculadas relacionadas às entregas, sempre seguindo um padrão consistente de nomenclatura.

Durante o desenvolvimento das medidas, foram utilizadas funções DAX amplamente aplicadas em cenários analíticos, tais como: `SUM`, `CALCULATE`, `DATEADD`, `VAR`, `DIVIDE`, `SAMEPERIODLASTYEAR`, `TOTALMTD`, `TOTALYTD`, `COUNT`, `USERELATIONSHIP`, `FILTER`, `VALUES`, `AVERAGEX`, `MAX`, `LASTDATE`, `REMOVEFILTERS`, `IF` e `SELECTEDVALUE`.

As medidas relacionadas às entregas possibilitaram uma avaliação mais precisa do desempenho logístico, permitindo identificar gargalos operacionais, níveis de atraso e oportunidades de melhoria no cumprimento dos prazos acordados.
<br><br>
<a href="https://github.com/Pedrofx-98/MaxOilSolutions/blob/main/Figures/Medidas_Entregas.png" target="_blank">Clique aqui</a> e acesse a figura de medidas das entregas no Github.
## Conclusão técnica

Neste projeto, os dados foram extraídos a partir de planilhas em Excel, uma ferramenta amplamente utilizada pelas empresas até hoje devido à sua flexibilidade, facilidade de uso e rápida adoção por diferentes áreas do negócio. O Excel permite a construção e manutenção de bases de dados de forma ágil, sendo muitas vezes o primeiro ponto de organização e armazenamento das informações operacionais.

No entanto, à medida que o volume de dados cresce e as análises se tornam mais complexas, torna-se necessário estruturar, tratar e modelar essas informações de forma mais robusta. Nesse contexto, o Power BI desempenha um papel fundamental ao possibilitar a transformação dos dados, a criação de modelos analíticos e a construção de dashboards interativos, permitindo uma análise mais dinâmica e orientada à tomada de decisão.

Apesar das vantagens do Excel e do Power BI no aspecto visual e analítico, é importante destacar que a adaptação desses dados para um banco de dados relacional, como o SQL, traz benefícios significativos. O uso de um banco de dados permite maior controle sobre a integridade dos dados, melhor desempenho em grandes volumes de informação, padronização de regras de negócio e escalabilidade para projetos futuros.

Dessa forma, não existe uma ferramenta superior à outra, mas sim ferramentas adequadas a diferentes necessidades. O Excel continua sendo extremamente relevante no dia a dia das empresas, o Power BI agrega valor ao transformar dados em insights visuais, e o SQL se mostra essencial para estruturar, validar e garantir a consistência dos dados. O uso combinado dessas tecnologias permite construir soluções analíticas mais sólidas, eficientes e alinhadas às necessidades do negócio.


<br><br>

## Dashboard Power BI
<img align="right" width="500"  src="https://github.com/Pedrofx-98/MaxOilSolutions/blob/main/Figures/Dashboard_MaxOil_Vendas.png">
Com o objetivo de realizar uma análise mais dinâmica, interativa e visual, foi desenvolvido um dashboard em Power BI integrando as análises de vendas e entregas a partir da base de dados fornecida pela empresa. A escolha da ferramenta se deu pela sua capacidade de explorar a informação com menor complexidade de código no DAX, além de permitir total interação do usuário final por meio de filtros e segmentações.

A partir de uma análise exploratória orientada pelas necessidades do cliente, foram identificados os seguintes principais insights:

-A principal Business Line da empresa está concentrada na venda de lubrificantes, que representam aproximadamente 88% do total de vendas ao longo do período analisado.

-Em termos regionais, as regiões Centro-Oeste e Sudeste concentram 66,5% das vendas, com destaque para a filial de Sorocaba, responsável por 64% do faturamento total da empresa.

-No recorte por categorias, a Categoria 6 (Aditivos) apresentou o maior volume de vendas, representando 27,1% do total.

-Avaliando o desempenho da empresa entre 2019 e 2022, foi identificado um crescimento médio anual (CAGR) de 3,62%, métrica escolhida por capturar oscilações relevantes ao longo do tempo. Destaca-se que 2020 apresentou a menor performance, fortemente impactada pelos efeitos da pandemia de COVID-19.

-Apesar de Sorocaba liderar em volume total de vendas, a filial de Blumenau apresentou o maior crescimento percentual, com 5,1%, superando a média da empresa. Em contrapartida, a filial de Itapuã registrou crescimento negativo de −2,78% no período.

-Na análise de crescimento mensal, o mês de março apresentou o melhor desempenho médio (+7,66%), enquanto abril registrou retração média de −2,91%, indicando possível sazonalidade ou impacto operacional específico.

-Entre as categorias, a Categoria 7 destacou-se com o maior crescimento (19,48%), enquanto a Categoria 11 apresentou o pior desempenho (−3,17%).

-Considerando as divisões geográficas, a Divisão Sul apresentou o maior crescimento médio anual (5,16%), impulsionada principalmente pelo desempenho da filial de Blumenau. Já a divisão Norte/Nordeste registrou crescimento negativo (−1,59%).

-No cenário de entregas, foi identificado um ponto crítico: aproximadamente 60% das entregas encontram-se em atraso. A filial de Sorocaba lidera o ranking de atrasos, seguida por Blumenau. Ao aprofundar a análise por categoria, observou-se que a Categoria 6 concentra o maior volume de atrasos em ambas as filiais, com destaque para o material Bl01-CA06-1051, que soma mais de 56 mil entregas atrasadas, além de apresentar as maiores médias de dias de atraso.

-Esses resultados indicam que o alto volume de vendas e crescimento acelerado, especialmente em Blumenau, pode estar gerando gargalos operacionais e limitações de capacidade logística, sugerindo a necessidade de revisão dos processos de distribuição, planejamento de demanda e infraestrutura logística para sustentar o crescimento futuro.

 Para aprofundar a análise, maiores detalhes sobre vendas e entregas podem ser explorados diretamente no dashboard por meio do uso de **tooltips**, que fornecem informações contextuais adicionais, e do recurso de **drill-through**, permitindo a navegação para análises mais detalhadas por filial, categoria, produto e período.
 
<br><br>
<a href="https://app.powerbi.com/view?r=eyJrIjoiM2I2YTlmNGItZTgzZS00MDEyLWFlOWYtZDk2ZmY5OTQyNDkzIiwidCI6IjY1OWNlMmI4LTA3MTQtNDE5OC04YzM4LWRjOWI2MGFhYmI1NyJ9" target="_blank">Clique aqui</a> e acesse o a solução desenvolvida para a empresa MaxOil Solutions.

## Ferramentas e linguagens utilizadas
<ul>
  <li>🟢 <strong>Excel</strong> — Fonte de dados</li>
  <li>🟡 <strong>Power BI</strong> — Transformação, modelagem e visualização</li>
  <li>🔵 <strong>DAX</strong> — Criação de métricas, KPIs e inteligência temporal</li>
</ul>

