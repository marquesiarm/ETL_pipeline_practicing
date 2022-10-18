# ETL_pipeline_practicing
Overview and implementation with Python of a ETL pipeline.
Uma vez definido o problema de negócio, o início  da esteira de produção da área de Ciência de Dados é o processo chamado de ETL (extract-transform-load). Como o termo sugere, compreende a etapa de obtenção de dados, podendo ser de diferentes fontes e formatos; transformação e/ou organização inteligível e a sua disposição adequada para uso (armazenamento).
Encontrei no Medium uma excelete publicação do autor Nair (<https://towardsdatascience.com/building-etl-pipelines-for-beginners-17c3492d29d2>) que apresenta de forma bastante interessante uma prática desse processo utilizando a linguagem Python. Veja o vídeo que compartilho com esse exercício.
Isso foi feito coletando dados sobre artigos publicados na New Yourk Times (NYT) sobre COVID-19 (“extract”) , preparação destes para uso (“transform”) e armazenamento em um banco de dados (“load”).
A primeira etapa do ETL é realizada com o uso de uma API  da NYT  (<https://developer.nytimes.com/>). A etapa seguinte de transformação do dados neste caso, basicamente é um processo de data cleanning  and filtering, como a remoção de duplicatas e daqueles que não possuem headline. Também foram desconsiderados do dataset artigos “op-ends”.

A terceira etapa foi o armazenamento do dataset em um banco de dados relacional. O autor fez isso usando um PostgreSQL. Como pode ser visto no vídeo, fiz usando um MySQL database o que exigiu pequenas alterações no código.

A partir desse ponto, percebi eu deveria colocar a minha contribução a essa prática. Como a API fornece somente 10 artigos por solicitação, são necessárias multiplas solicitações delimitadas por período de tempo (“begin_date” e “end_date”) para compor o banco de dados. Isso pode produz duplicatas no processo de load, caso o banco de dados já possua alguma insertção anterior. Para evitar isso, mudei um pouco a ordem do processo e incluí um filtro adicional.

Antes do processo de load, fiz a conexão com o banco de dados anteriormente criado no MySQL e solicite quais as tabelas deste via SHOW TABLES. Caso ainda não exista tabela, todo o dataframe limpo e filtrado requirido da API é inserido no banco de dados. Caso a tabela já exista, é feita uma comparação entre as túplas desta com as do dataframe obtido da API. Isso possibilita identificar duplicatas e removê-las, e então seguir para o load. Veja o vídeo e repare os comentários que fiz em cada bloco de código.
Uma vez com o banco de dados composto, pode-se praticar a análise de dados fazendo as mais diversas queries possíveis. Vejam as queries que deixei o código e os exemplos de dois casos de word cloud que apresentei.
A conclusão disso é que consegui repoduzir por completo uma prática de processo ETL usando dados reais com  aporte do que tenho aprendido dos cursos básicos e gratuítos sobre Ciência de Dados e leituras no Medium.
Dicas, sugestões e correções serão bem vindas!
