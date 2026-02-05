# Análise de Vendas e Entregas da Empresa MaxOil Solutions
Utilizando um banco de dados fictício em Excel, referente a uma empresa imaginária de vendas de aditivos e lubrificantes, iniciamos uma análise com o objetivo de compreender o panorama de vendas, a distribuição por filiais, categorias, produtos e entregas no período de 2019 a 2022. O objetivo inicial é realizar uma análise exploratória, buscando identificar onde está a maior concentração de vendas, quais produtos atuam como drivers, se houve crescimento ao longo dos anos e onde se encontra o maior impacto dessa evolução. Além disso, será analisada a performance das entregas, com o objetivo de identificar pontos de melhoria e direcionar ações para corrigir possíveis atrasos.

Fazendo o download dos arquivos na pasta Dataset que está no repositório desse projeto, é possível extrair, transformar e carregar os dados utilizados nesta análise e obter os mesmos resultados apresentados.
<br><br>

## Análise exploratória de dados
<img align="right" width="600"  src="https://github.com/Pedrofx-98/MaxOilSolutions/blob/main/Figures/Modelo_fonte_dados_PQ.png">
Iniciamos o projeto importando e compreendendo cada objeto, tabela, campo, tipo de dado e relacionamento do modelo de dados obtido no Excel.

Após a identificação das chaves primárias (PK) e a definição dos campos das tabelas fato e dimensão necessários para as análises, desenvolvemos a etapa de transformação, contemplando a padronização dos tipos de dados (`Data`,`Texto`,`Inteiro`e`Decimal`), a aplicação de filtros nas colunas e a mesclagem entre as tabelas (joins).

O objetivo dessa etapa foi reduzir e otimizar os dados contidos na base, preparando-os para uma abordagem mais organizada e estratégica. As análises e os primeiros insights passaram a ser identificados a partir da construção dos dashboards, quando foi possível visualizar os dados de forma consolidada durante a análise exploratória de dados, como por exemplo:
 <br><br>
- Vendas por Região <br>
- Vendas por Filiais <br>
- Categorias com mais vendas <br>
- Vendas por Business Line.
<br><br>
<a href="https://github.com/BruceFonseca/AdventureWorks2022/blob/main/SQL/AdventureWorks%20-%20Clientes.sql" target="_blank">Clique aqui</a> e acesse o script SQL no Github.


<br><br>

## Análise de Novos Clientes
<img align="left" width="500"  src="https://github.com/BruceFonseca/AdventureWorks2022/blob/main/imagens/AdventureWorks%20-%20Novos%20Clientes.png?raw=true">
Para identificar os novos clientes, primeiro foi necessário agrupar os clientes por ano e mês em uma CTE - Common Table Expression, porém é possível o mesmo resultado utilizando outras técnicas. Na CTE criada com o nome ClientesPrimeiraDataCompra, identificamos qual foi a primeira compra de cada, agrupando novos clientes por ano e mês.
Com os dados agrupados, utilizamos a função de janela LAG para encontrar novos clientes no mesmo mês do ano anterior, permitindo os seguintes cálculos: <br><br>
- Novos Clientes  <br>
- Novos Clientes Ano Anterior<br>
- Variação de novos clientes entre períodos <br>
<br>
<a href="https://github.com/Pedrofx-98/MaxOilSolutions/blob/main/Figures/Dashboard_MaxOil_Vendas.png">Clique aqui</a> e acesse o Dashboard de vendas no Github.
<br><br>
Analisando a variação de novos clientes entre períodos, é possível identificar em 2013, um crescimento mensal muito acima da variação de 2012, sendo necessário aprofundar a análise e identificar de onde está vindo este grande crescimento de novos clientes.

<br><br>
## Variação de novos clientes entre períodos
<img align="right" width="500" height="320" src="https://github.com/BruceFonseca/AdventureWorks2022/blob/main/imagens/AdventureWorks%20-%20Novos%20Clientes%20Delta.png?raw=true">
Analisando a variação de novos clientes, quando comparados com o mesmo período/mês do ano anterior, decidimos agrupar esta variação por região/país para identificar se houve crescimento. 
Filtramos apenas o ano de 2013, pois foi o período com maiores taxas de crescimentos de novos clientes, o que nos permitiu concluir que: <br><br>
- Canadá teve o maior crescimento percentual entre todos os países - aproximadamente 623% <br>
- Estados Unidos teve o maior crescimento cumulativo de clientes - aproximadamente 5050 <br>
- Apenas os Estados Unidos tiveram um crescimento maior que todos países da Europa juntos, sendo a América do Norte o principal mercado de atuação da empresa.
- Todos países europeus dobraram ou superaram sua base de novos clientes. <br>
- Austrália, apesar de não ter um crescimento comparável com Europa e América do Norte, aumentou sua base de novos clientes em quase 50%, sendo um ótimo resultado em 2013. <br>

<br>
<a href="https://github.com/BruceFonseca/AdventureWorks2022/blob/main/SQL/AdventureWorks%20-%20Novos%20Clientes%20Delta%202013.sql" target="_blank">Clique aqui</a> e acesse o script SQL no Github.

<br><br>

## Conclusão técnica SQL
Com o SQL, podemos analisar, extrair, manipular e exibir os dados de uma base de dados de uma forma simples e rápida, apenas conectando direto na fonte dos dados. Porém, não é uma ferramenta dinâmica em com abordagem visual, pois cada vez que pricisa ver os dados de uma forma diferente, precisa reescrever o comando SQL para extrair os dados da forma que gostaria, porem os dados sempre serão exibidos em formato de tabela, deixando sua análise menos dinamica do que um dashboard, por exemplo.

A minha conclusão é que o SQL é sempre uma linguagem muito importante e deve ser utilizada para analisar um banco de dados antes de escolher outra ferramenta para análise dos dados, como o Power BI por exemplo. Ou seja, valide as informações no SQL e só depois considere outras ferramentas de acordo com a necessidade da empresa ou projeto que estiver atuando.
Não existe uma ferramenta melhor que a outra, existe ferramentas adequadas as necessidades apresentadas em cada projeto de dados.

<br><br>

## Dashboard Power BI
<img align="right" width="500"  src="https://github.com/BruceFonseca/AdventureWorks2022/blob/main/imagens/Captura%20de%20tela%202023-12-03%20121514.png?raw=true">
Seguindo a idéia que SQL não é a melhor ferramenta para uma análise dinâmica e visual de informações, desenvolvi um dashboard focado na análise dos clientes novos e recorrentes da mesma base de dados AdventureWorks.
Como o Power BI permite análises dinâmicas e visuais de forma simples, escrevendo menos código DAX e permitindo o usuário total interação com a ferramenta, fiz uma análise exploratória na quantidade e receira entre novos e recoreente.<br>
Com esta análise, chegamos as seguintes conclusões:<br>
 - A maioria dos clientes a partir de 2013 é novo. <br>
 - Além da quantidade de clientes novos, a receita trazida por clientes novos também é a maior fatia do total.<br>
 - Os clientes novos não são a maioria para todos países e períodos. Por isso o Power BI é uma ferramenta de extrema importância, pois permite o usuário final fazer seus filtros e ter análises de forma dinâmica.
<br><br>
<a href="https://app.powerbi.com/view?r=eyJrIjoiNWJjODBmOTAtYmNhMy00YjdmLTk5ZDMtMDc4NGI4NDY3YzJmIiwidCI6IjQxNGU0N2Q2LTVhNGUtNDkzZS05OWJkLTUzMTYwZjJhYWY2ZiJ9" target="_blank">Clique aqui</a> e acesse o a solução desenvolvida para a empresa AdventureWorks.
<br>
<a href="https://github.com/BruceFonseca/AdventureWorks2022/tree/main/POWERBI" target="_blank">Clique aqui</a> e acesse o arquivo .pbix no Github.
<br><br>

## Ferramentas e linguagens utilizadas
<div style="display: inline_block">
    <img align="center" alt="SQL" height="40" width="40" src="https://github.com/BruceFonseca/ferramentas/blob/main/logo.png?raw=true">
    <img align="center" alt="Power BI" height="40" width="40" src="https://github.com/BruceFonseca/ferramentas/blob/main/1200px-New_Power_BI_Logo.svg.png?raw=true">
</div>
