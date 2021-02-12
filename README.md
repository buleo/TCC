# PREVISÃO AUTOMÁTICA, COM REDES NEURAIS, DA PROBABILIDADE POR BAIRROS DE SEREM SOLICITADOS TRANSPORTES POR APLICATIVOS

Monografia apresentada ao Departamento de Engenharia Elétrica da PUC/Rio como parte dos requisitos para a obtenção do título de Especialização em Business Intelligence

Data: 31/08/2020

## Autor: Fernando Mauro **Buleo** Barbosa

### O texto abaixo apresenta um resumo do trabalho. Clique no link a seguir para acessar a [Monografia Completa](https://github.com/buleo/TCC/blob/main/BI-Master-Monografia-final%20-FMBB%20vr%20Leonardo-RevBuleoB.pdf).

## RESUMO
No presente trabalho foi desenvolvido modelo preditivo visando identificar as áreas de cidades com maior probabilidade de demandarem transporte por aplicativo, a cada dia e hora. O modelo preditivo foi desenvolvido em uma rede neural e treinado para prever a probabilidade de transportes serem demandados em 3 (três) cidades brasileiras. Para o treinamento foi utilizada a base completa de 1 (um) mês de 2020 de transportes realizados por aplicativo. 

Os melhores resultados obtidos indicaram que, em 84% dos casos, o modelo consegue prever a probabilidade de bairros demandarem transporte com uma distância de até 3 posições em relação a ordem (“ranking”) real de bairros, quando consideramos os 5 que mais demandam transportes. Expandindo a análise para os 10 bairros que mais solicitam transportes, foi verificado que, em 77% dos casos, o modelo consegue prever a probabilidade de bairros demandarem transportes com uma distância de até 3 posições em relação ao “ranking” real.


## ABSTRACT
In this work, a predictive model was developed to identify the areas of cities most likely to require transportation, every day and hour. The predictive model was developed in a neural network and trained to predict the likelihood of a demand for transport in 3 (three) Brazilian cities. For the training of the model, the complete base of transports performed in 1 (one) month of the year 2020 of a transport application was used.

The best results obtained indicated that, in 84% of the cases, the model is able to predict the probability of neighborhoods requiring transport with a distance of up to 3 positions in relation to the real "ranking", when we consider the 5 neighborhoods that most originate races. Expanding the analysis to the 10 neighborhoods that demand the most transport, It was found that, in 77% of the cases, the model is able to predict the probability of neighborhoods requiring transport with a distance of up to 3 positions in relation to the real "ranking".

## OBJETIVOS DO TRABALHO
Para realização desse trabalho foi obtida, junto a uma empresa que desenvolveu e comercializa um aplicativo de transportes, a base de transportes realizados em janeiro de 2020. Essa base dispõe para cada transporte, de informações como a data da “corrida” (transporte), horário, cidade de partida, cidade de destino, bairro de partida e bairro de destino. Nenhuma informação pessoal dos clientes foi disponibilizada. De posse dessa base os objetivos do trabalho foram: 
  -	Gerar base de informações, a partir da base disponível de transportes realizados, com a probabilidade de cada bairro, em cada cidade de partida, demandar transportes a cada dia e hora do mês de modo a servir como base de treino e base de testes do modelo preditivo a desenvolver
  -	Eleger, dentre as 1.118 cidades de partida presentes na base, quais seriam usadas nesse estudo
  -	Desenvolver Rede Neural para prever, por método de regressão, a probabilidade de cada bairro das cidades eleitas no estudo, demandar transportes a cada dia, de hora em hora
  
## OPORTUNIDADE E BENEFÍCIOS 

O uso da tecnologia e de métodos “inteligentes” tem sido fundamental para viabilizar o negócio de transporte por aplicativos, permitindo, inclusive, que motoristas sem experiência prévia em transportes atuem na área. Aplicativos de navegação permitem que um motorista busque um passageiro e o leve até o destino sem nunca ter ido antes aos endereços de partida e de destino. Mesmo motoristas experientes no ramo de transporte e conhecedores dos mapas e ruas da cidade onde atuam, podem se beneficiar dessa inteligência usando a rota mais rápida apontada pelo aplicativo naquele momento, em vez de se basearem unicamente em sua experiência prévia, insuficiente para prever situações excepcionais como congestionamentos do tráfego, sinistros nas vias etc. 

Nesse sentido, motoristas buscam circular nas áreas que, segundo a experiência adquirida, tem mais probabilidade de demandar transportes, a fim de maximizar sua receita e evitar ficarem circulando pela cidade a esmo consumindo combustível. 

O modelo proposto nesse Trabalho de Conclusão de Curso se destina a estimar, para um conjunto de cidades eleitas, a probabilidade de serem demandados transportes em cada bairro dessas cidades, a cada período de 1 (uma) hora do dia. 

Esse modelo viabiliza que qualquer motorista tenha conhecimento das áreas da cidade com maior probabilidade de originar transportes naquele dia e horário, independente de experiência prévia. Dessa forma, ele poderá se dirigir para uma das áreas apontadas por essa solução, que se situe mais próxima de sua localização atual. 
Alguns dos benefícios dessa solução são:
  - Maximizar a receita dos transportadores
  -	Minimizar o custo dos transportadores, que podem despriorizar a circulação em áreas com menor probabilidade de demandar transportes, reduzindo o gasto de combustível sem receita associada
  -	Maximizar o total de clientes satisfeitos, reduzindo o tempo de espera por um transportador em função da maior disponibilidade de transportadores nas áreas que mais geram transportes

## ETAPAS DO TRABALHO
O execução desse trabalho envolveu as seguintes etapas:
  - O estudo de ferramentas de ETL
  -	O estudo de técnicas de Data Mining
  -	O estudo de modelos de Machine Learning e redes neurais para previsão por regressão
  -	O desenvolvimento de ETL para extração e transformação da base de dados do cliente em uma base de informações das probabilidades dos bairros originarem transportes
  -	Desenvolvimento de Rede Neural para previsão por regressão da probabilidade de bairros originarem transportes
  -	Execução de simulações para parametrização da Rede Neural
  -	Avaliação dos Resultados


## SOLUÇÃO - O MODELO DE INFERÊNCIA

A base histórica com as informações de um mês de transportes foi carregada e convertida, utilizando o [Pentaho](https://g.co/kgs/3B2LN7) como ferramenta de ETL, em arquivos em formato CSV (Comma Separated Values) contendo a probabilidade de cada bairro demandar corridas a cada dia e hora do mês de Janeiro/2020. Foi gerado um [arquivo para a cidade de Fortaleza](https://github.com/buleo/TCCTeste/blob/main/Corridas_Fortaleza-FINAL-Acentuado-Probabilidades-ComSemanaTeste.csv) e um [arquivo para as demais cidades](https://github.com/buleo/TCCTeste/blob/main/Corridas_Cidades_Eleitas-FINAL-Acentuado-Probabilidades-ComSemanaTeste.csv) eleitas para estudo nesse trabalho. Esses arquivos serviram como base de treino e base de testes do modelo preditivo.

A fim de garantir que, tanto a base de treino como a base de testes dispusesse de registros de todas as horas e todos os dias da semana, foram considerados para teste os transportes ocorridos no período de 12 a 18 de janeiro de 2020 e para treino os demais dias.

O modelo de inferência foi desenvolvido em um programa utilizando a linguagem [Python](https://www.python.org/). 

Para criação da rede neural foi utilizada a biblioteca [Keras](https://keras.io/) do Python.
Foi utilizada uma rede neural de 3 camadas.
Como função de ativação dos neurônios da rede foi utilizada a função “Relu”.

Foi utilizado o [Google Colaboratory](https://colab.research.google.com/notebooks/intro.ipynb) para executar as simulações do modelo. 

Vários otimizadores foram utilizados nas simulações sendo que os melhores resultados foram obtidos com os listados abaixo:
  - SGD - Otimizador de Gradiente descendente com Momentum   
  - NAdam - Otimizador que implementa o algoritmo Adam conjugado com o momentum Nesterov

Clique [aqui](https://github.com/buleo/TCCTeste/blob/main/TCC_Gaudium_SemanaTeste_Limpo.ipynb) para acessar o código completo do programa em [Jupiter Notebook](https://jupyter.org/). 


## SIMULAÇÕES

Foram realizadas, ao todo, 127 simulações desse modelo. Os parâmetros cuja configuração foi variada nessas simulações são os seguintes:

- Número de Camadas da Rede Neural

   Do total de 127 simulações, 116 foram realizadas com redes neurais de 3 camadas. Após atingir o melhor modelo com 3 camadas, algumas simulações foram realizadas com 4 ou 5 camadas (11 simulações no total). Os resultados não apresentaram ganhos significativos, portanto as melhores soluções mantiveram somente 3 camadas.
   
-	Quantidade de Neurônios das Camadas Escondidas

   As simulações, em geral, seguiram a heurística mencionada na seção 3.3.4 da [monografia](https://github.com/buleo/TCC/blob/main/BI-Master-Monografia-final%20-FMBB%20vr%20Leonardo-RevBuleoB.pdf) quanto a quantidade de neurônios das camadas escondidas.
   
-	Otimizador

   Foram realizadas simulações utilizando os otimizadores _[SGD](https://keras.io/api/optimizers/sgd/), [RMSPROP](https://keras.io/api/optimizers/rmsprop/), [Adam](https://keras.io/api/optimizers/adam/), [Nadam](https://keras.io/api/optimizers/nadam/), [Adamax](https://keras.io/api/optimizers/adamax/), [Adagrad](https://keras.io/api/optimizers/adagrad/) e [Adadelta](https://keras.io/api/optimizers/adadelta/)_. Os melhores resultados, contudo, foram obtidos com os otimizadores _**Nadam e SGD**_.
   
-	Indicador de Perda

   Foram realizadas simulações utilizando os indicadores MAE, MSE e MAPE, associados ao algoritmo otimizador. Observou-se, contudo, que a maior parte dos valores a serem previstos eram muito pequenos. Considerando as bases de informações das cidades eleitas, 88% dos registros (bairros por horário) apresentavam probabilidade inferior a 5% (0,05). 
  
   Assim, os erros medidos pelos indicadores MAE e MSE eram muito pequenos, levando a resultados menos satisfatórios quando esses foram utilizados no modelo preditivo.
Já o indicador MAPE, por representar a distância percentual entre o valor previsto e o real, mede gera valores mais significativos proporcionando melhores resultados para esse conjunto de simulações. 

-	Épocas de Treinamento

   Foram realizadas simulações com até 20.000 épocas de treinamento. No entanto, o ajuste desse parâmetro evidenciou que bastavam em torno de 250 épocas para obter os melhores resultados. 
   
   A realização de simulações com até 20.000 épocas proporcionou a observação do fenômeno de Overfitting (Super Treinamento), conforme podemos observar no gráfico abaixo. Tal gráfico representa a variação do indicador MAE em função do total de Épocas utilizadas na simulação. Nas simulações ilustradas nesse gráfico foi utilizada rede neural de 3 camadas com 160, 80 e 1 neurônio respectivamente. O otimizador utilizado foi o Adam. A cidade em questão foi Petrolina.
   
   ![Overfit](https://github.com/buleo/TCCTeste/blob/main/Overfit-Gr%C3%A1fico.png "Overfit em rede neural de 3 camadas com 160, 80 e 1 neurônios e Otimizador Adam")

-	Faixa Horária
   
   Na base de informações disponibilizada de transportes realizados, para as cidades eleitas nesse trabalho, 73% dos transportes ocorriam no período de 8 as 19 horas.  Por conta disso, foram executadas não só simulações visando desenvolver modelos para prever a probabilidade de transportes a qualquer hora do dia, mas também simulações visando prever somente os transportes no período de 8 às 19 horas, faixa próxima ao “Horário Comercial”.

   O objetivo foi otimizar os resultados dos modelos nesse período horário (próximo ao “Horário Comercial”), sem prejuízo da relevância dos resultados dado que esse período corresponde a 73% dos transportes. 

   A figura abaixo apresenta a distribuição do total de transportes realizados por hora para cada uma das cidades eleitas.

   ![FaixaHoraria](https://github.com/buleo/TCCTeste/blob/main/FaixaHoraria-Gr%C3%A1fico.png "Distribuição do total de transportes realizados por hora para cada uma das cidades eleitas")


## RESULTADOS

Foram realizadas simulações para as cidades de Fortaleza, Patos de Minas e Petrolina. Os melhores resultados foram obtidos para Fortaleza e estão sumarizados nessa seção. A relação completa de resultados de Fortaleza, bem como, os resultados das demais cidades pode ser obtida diretamente na [monografia](https://github.com/buleo/TCC/blob/main/BI-Master-Monografia-final%20-FMBB%20vr%20Leonardo-RevBuleoB.pdf)

### Melhores Resultados - Fortaleza

A tabela abaixo apresenta os parâmetros da simulação na qual foram obtidos os melhores resultados utilizando o Otimizador Nadam, na cidade de Fortaleza, considerando transportes iniciados em qualquer hora do dia. Apresenta, também, os resultados dos indicadores de performance obtidos nessa simulação. 

| Nome do Parâmetro | Valor |
| --- | --- |
| Faixa Horária | 0 a 23 horas |
| Algoritmo Otimizador | Nadam |
| Parâmetros do Algoritmo Otimizador	| Default 	|
| Rede Neural	| 3 camadas densamente conectadas com 314, 157 e 1 neurônio respectivamente |
| Total de Épocas | 10 |
| Indicador de Perda | MAPE |
| Resultados	| RMSE:		1,6736 |
| | MSE:		2,8009 |
| | MAE:		0,797523916 |
| | MAPE:		31,68181038 |

O gráfico abaixo apresenta, para cada elemento da base de teste, a distância entre a probabilidade real e a estimada pelo modelo nessa simulação. 

![ResultadoTodosOsHorarios](https://github.com/buleo/TCCTeste/blob/main/NadamFortalezaTodosOsHorarios-Grafico.png)

A tabela abaixo apresenta os parâmetros da simulação na qual foram obtidos os melhores resultados utilizando o Otimizador Nadam, na cidade de Fortaleza, considerando transportes iniciados entre 8 e 19 horas (Horário "Comercial"). Apresenta, também, os resultados dos indicadores de performance obtidos nessa simulação. 

| Nome do Parâmetro | Valor |
| --- | --- |
| Faixa Horária | 8 a 19 horas |
| Algoritmo Otimizador | Nadam |
| Parâmetros do Algoritmo Otimizador	| Default 	|
| Rede Neural	| 3 camadas densamente conectadas com 314, 157 e 1 neurônio respectivamente |
| Total de Épocas | 350 |
| Indicador de Perda | MAPE |
| Resultados	| RMSE:		0,9447 |
| | MSE:		0,8924 |
| | MAE:		0,5397 |
| | MAPE:		34,20235825 |

O gráfico abaixo apresenta, para cada elemento da base de teste, a distância entre a probabilidade real e a estimada pelo modelo nessa simulação. 

![ResultadoTodosOsHorarios](https://github.com/buleo/TCCTeste/blob/main/NadamFortalezaHorarioComercial-Grafico.png)


### Indicador de Distância entre o “Ranking” Real e Estimado de Bairros com Maior Probabilidade de Demandar Transporte

Os melhores modelos simulados apresentaram MAPE de 31,68%. Ou seja, as probabilidades estimadas distam, em média, da ordem de 31,68% das probabilidades reais. Independentemente dessa distância, a questão que cabe ser respondida para indicar a utilidade dos modelos é: as probabilidades previstas são capazes de indicar os bairros com maior probabilidade de originar transportes, em linha com o “ranking real” de bairros com maior probabilidade de originar transportes?

Para responder essa pergunta os bairros foram classificados em ordem decrescente de probabilidade real e prevista, na base de teste, para cada dia e hora cheia. Foi estabelecido o “ranking” para cada dia e hora cheia, de modo que o bairro com maior probabilidade recebeu o número 1 (primeiro), o bairro com segunda maior probabilidade recebeu o número 2 (segundo) e assim por diante. A Tabela abaixo, apresenta, como exemplo, o “ranking” para Fortaleza no dia 15 para transportes iniciados na faixa de 7 horas da manhã para as probabilidades **reais** da base de testes.

|nome da cidade de partida |	dia|	dia da semana|	hora|	bairro de partida|	Probabilidade REAL (%)| Ranking|
|:---:|:---:|:---:|:---:|:---:|---:|---:|
|Fortaleza|	15	|4	|7	|Aldeota	|13,442623 |			1 |
|Fortaleza|	15	|4	|7	|Conjunto Prefeito Jose Walter|	8,5245902|	2 |
|Fortaleza|	15	|4	|7	|Meireles	|7,5409836|			3 |
|Fortaleza|	15	|4	|7	|Bairro de Fatima|	6,557377|		4 |
|Fortaleza|	15	|4	|7	|Centro	|5,2459016|				5 |	
|Fortaleza|	15	|4	|7	|Mondubim|	4,2622951|			6 |
|Fortaleza|	15	|4	|7	|Dionisio Torres	|3,2786885|		7 |
|Fortaleza|	15	|4	|7	|Joaquim Tavora	|3,2786885|			8 |
|Fortaleza|	15	|4	|7	|Papicu	|2,6229508|				9 |
|Fortaleza|	15	|4	|7	|Coco	|2,295082|				10 |

 

Já a Tabela seguinte apresenta, como exemplo, o “ranking” para Fortaleza no dia 15 para transportes iniciados na faixa de 7 horas da manhã para as probabilidades **estimadas** pelo modelo para a base de testes.

|nome da cidade de partida |	dia|	dia da semana|	hora|	bairro de partida|	Probabilidade ESTIMADA (%)| Ranking|
|:---:|:---:|:---:|:---:|:---:|---:|---:|
|Fortaleza|	15|	4|	7|	Aldeota	|10,51550198|	1|
|Fortaleza|	15|	4|	7|	Conjunto Prefeito Jose Walter|	8,172930717|	2|
|Fortaleza|	15|	4|	7|	Meireles|	7,201272488	|3|
|Fortaleza|	15|	4|	7|	Centro	|4,353507996	|4|
|Fortaleza|	15|	4|	7|	Bairro de Fatima|	4,114582539|	5|
|Fortaleza|	15|	4|	7|	Joaquim Tavora|	2,678854227	|6|
|Fortaleza|	15|	4|	7|	Mondubim|	2,312119007	|7|
|Fortaleza|	15|	4|	7|	Coco	|2,051606655	|8|
|Fortaleza|	15|	4|	7|	Papicu	|1,704099059	|9|
|Fortaleza|	15|	4|	7|	Dionisio Torres	|1,627932549|	10|


Em seguida, foi realizada a correspondência dos “rankings” associados a probabilidade real e a probabilidade estimada para cada bairro, dia e horário, criando-se o indicador de “Distância” correspondendo a fórmula abaixo:

				Distância= | Ranking(_real_) - Ranking(_estimado_) |

O cálculo do indicador de **“Distância”** está ilustrado na Tabela a seguir, a qual apresenta o resultado desse indicador para Fortaleza no dia 15 para transportes iniciados na faixa de 7 horas da manhã.

|nome da cidade de partida |	dia|	dia da semana|	hora|	bairro de partida|	 Ranking **REAL**|	 Ranking **ESTIMADO**| 	  **DISTÂNCIA**|
|:---:|:---:|:---:|:---:|:---:|---:|---:|---:|
|Fortaleza	|15	|4	|7	|Aldeota	|1|	1|	0|
|Fortaleza	|15	|4	|7	|Conjunto Prefeito Jose Walter|	2|	2|	0|
|Fortaleza	|15	|4	|7	|Meireles	|3	|3|	0|
|Fortaleza	|15	|4	|7	|Bairro de Fatima|	|4	|5|	1|
|Fortaleza	|15	|4	|7	|Centro	|5	|4|	1|
|Fortaleza	|15	|4	|7	|Mondubim	|6	|7|	1|
|Fortaleza	|15	|4	|7	|Dionisio Torres|	7	|10|	3|
|Fortaleza	|15	|4	|7	|Joaquim Tavora|	8|	6|	2|
|Fortaleza	|15	|4	|7	|Papicu	|9	|9|	0|
|Fortaleza	|15	|4	|7	|Coco|	10	|8|	2|

Analisando a tabela acima observamos que:
   - para o bairro Dionisio Torres, a Distância calculada foi 3 pois esse bairro tem a 7ª maior probabilidade de originar transportes na base real (ranking 7) enquanto que, na probabilidade estimada, foi a 10ª maior (ranking 10). 
   - para os bairros Aldeota, Conjunto Prefeito José Walter, Meireles e Papicu, a Distância foi 0 pois esses bairros tiveram o mesmo ranking para probabilidades reais e probabilidades estimadas de originarem transportes (o modelo foi capaz de prever exatamente a posição do bairro no "ranking").

### Análise do Indicador de Distância entre o “Ranking” Real e Estimado de Bairros com Maior Probabilidade de Demandar Transporte - Cidade de Fortaleza

#### Fortaleza / Otimizador Nadam / Todas as Horas do Dia

Para a simulação com o otimizador Nadam, todas as horas do dia, a distribuição por faixas de distância referente aos 10 Bairros com maior probabilidade real de originar transportes em relação aos ranking estimado é o apresentado na Tabela abaixo.

|Faixa de Distâncias	|% Faixa	|% Acumulado|
|:---|---:|---:|
|0|	21%|	21%|
|1 a 3|	45%|	66%|
|4 a 5|	8%|	74%|
|mais de 5|	26%|	100%|
 
Ou seja:
   - para 21% dos bairros o modelo previu a posição exata do ranking (Distância 0)
   - para 66% dos bairros o modelo previu a posição no ranking com distância de até 3 posições em relação ao ranking real
   - para 74% dos bairros o modelo previu a posição no ranking com distância de até 5 posições em relação ao ranking real 

Se considerarmos somente os 5 bairros com maior probabilidade real de originar transportes, a distribuição por faixas de distância é a apresentada na Tabela abaixo. 

|Faixa de Distâncias	|% Faixa	|% Acumulado|
|:---|---:|---:|
|0|	31%	|31%|
|1 a 3|	49%	|80%|
|4 a 5|	5%	|85%|
|mais de 5|	|15%|	100%|
 
Ou seja:
   - para 31% dos bairros o modelo previu a posição exata do ranking (Distância 0)
   - para 80% dos bairros o modelo previu a posição no ranking com distância de até 3 posições em relação ao ranking real
   - para 85% dos bairros o modelo previu a posição no ranking com distância de até 5 posições em relação ao ranking real 

Analisando um ranking maior, ou seja, os 20 bairros com maior probabilidade real de originar transportes, observamos também bons resultados quanto a distância em relação ao ranking estimado, como demonstrado na Tabela abaixo. 

|Faixa de Distâncias	|% Faixa	|% Acumulado|
|:---|---:|---:|
|0|	13%	|13%|
|1 a 3|	34%	|47%|
|4 a 5|	9%	|56%|
|mais de 5|	44%|	100%|
 
Ou seja:
   - para 56% dos bairros o modelo previu a posição no ranking com distância de até 5 posições em relação ao ranking real 


#### Fortaleza / Otimizador Nadam / Período de 8hs às 19hs

Já para a simulação com o otimizador Nadam, somente no período de 8hs às 19hs, a distribuição por faixas de distância referente aos 10 Bairros com maior probabilidade real de originar transportes em relação aos ranking estimado é o apresentado na Tabela abaixo.

|Faixa de Distâncias	|% Faixa	|% Acumulado|
|:---|---:|---:|
|0	|26%|	26%|
|1 a 3	|44%|	70%|
|4 a 5	|7%|	77%|
|mais de 5|	23%|	100%|
 
Ou seja:
   - para 26% dos bairros o modelo previu a posição exata do ranking (Distância 0)
   - para 70% dos bairros o modelo previu a posição no ranking com distância de até 3 posições em relação ao ranking real
   - para 77% dos bairros o modelo previu a posição no ranking com distância de até 5 posições em relação ao ranking real 


Se considerarmos somente os 5 bairros com maior probabilidade real de originar transportes, a distribuição por faixas de distância é a apresentada abaixo. 

|Faixa de Distâncias	|% Faixa	|% Acumulado|
|:---|---:|---:|
|0	|39%	|39%|
|1 a 3	|45%	|84%|
|4 a 5	|2%	|86%|
|mais de 5|	14%|	100%|
 
Ou seja:
   - para 39% dos bairros o modelo previu a posição exata do ranking (Distância 0)
   - para 84% dos bairros o modelo previu a posição no ranking com distância de até 3 posições em relação ao ranking real
   - para 86% dos bairros o modelo previu a posição no ranking com distância de até 5 posições em relação ao ranking real 

Analisando um ranking maior, ou seja, os 20 bairros com maior probabilidade real de originar transportes, observamos também bons resultados quanto a distância em relação ao ranking estimado, como demonstrado na Tabela a seguir. 

|Faixa de Distâncias	|% Faixa	|% Acumulado|
|:---|---:|---:|
|0|	15%|	15%|
|1 a 3|	33%|	47%|
|4 a 5|	10%|	58%|
|mais de 5|	42%|	100%|
 
Ou seja:
   - para 58% dos bairros o modelo previu a posição no ranking com distância de até 5 posições em relação ao ranking real 


## CONCLUSÕES E TRABALHOS FUTUROS

O objetivo deste trabalho foi criar modelo preditivo capaz de indicar os bairros com maior probabilidade de demandarem transportes, a cada hora, de modo a orientar o posicionamento dos transportadores por aplicativo.

Na [seção de análise do indicador de Distância do ranking](https://github.com/buleo/TCCTeste/blob/main/README.md#an%C3%A1lise-do-indicador-de-dist%C3%A2ncia-entre-o-ranking-real-e-estimado-de-bairros-com-maior-probabilidade-de-demandar-transporte---cidade-de-fortaleza) foi demonstrada a proximidade do “ranking” real de principais bairros demandadores de transporte e o “ranking” estimado pelo modelo. Entendo, portanto, que os objetivos do trabalho foram cumpridos.

Em trabalhos futuros as seguintes oportunidades de melhoria poderiam ser exploradas visando aprimoramento dos modelos e de seus resultados:

**1.	Período da Base de Dados de Transportes**

  A base de transportes dispõe de informações do mês de janeiro/2020 apenas. Os modelos preditivos foram treinados a partir de simulações com essas bases.  Assim, entendo que os modelos em questão são capazes de efetuar previsões referentes a janeiro/2020. Não é possível afirmar que esse modelo é adequado para efetuar previsões de outros meses, ou mesmo que será adequado para efetuar previsões em relação a meses de janeiro de outros anos, como por exemplo, janeiro/2021.
Seria interessante dispor de base de pelo menos 2 anos de transportes realizados de modo a viabilizar que o modelo possa inferir:
  - O comportamento de outros meses do ano. Cada mês pode ter sazonalidades específicas. Sem dispor de informações de outros meses para treinamento do modelo, não podemos afirmar que o mesmo estaria capaz de efetuar previsões de todos os meses do ano
  - O padrão de comportamento de um mês ao longo dos anos. Importante que o modelo disponha de informações de mais de um mês de janeiro. Somente assim poderíamos avaliar se o modelo estaria habilitado a prever os meses de janeiro independente do ano em questão. O mesmo vale para os demais meses do ano
  - Sazonalidades específicas tais como o comportamento do modelo em feriados, festividades e eventos locais, dia das mães, dia dos pais, dia dos namorados etc.
  
**2.	Agrupamento de Bairros por Regiões**

  A quantidade de bairros nas cidades eleitas, bem como, nas cidades em geral da base de transportes é muito grande, superando em pouco a quantidade de variáveis preditoras do modelo. 
  Fortaleza possui 251 bairros contra 314 variáveis preditoras utilizadas no modelo. 
  Patos de Minas possui 118 bairros na base contra 176 variáveis preditoras utilizadas no modelo. 
  Petrolina possui 108 bairros na base contra 160 variáveis preditoras utilizadas no modelo. 

  A baixa granularidade dos bairros torna o modelo menos assertivo. Ao mesmo tempo, tal nível de detalhe pode ser desnecessário para os objetivos do negócio.
  Em trabalhos futuros seria recomendável o estudo das zonas e áreas das cidades de modo a agrupar os bairros por zonas (Norte, Sul, Leste, Oeste, Centro) ou áreas (área Portuária, Universitária, Industrial, Comercial, Residencial etc). A base de treino passaria a dispor dessa informação e o modelo seria treinado para prever a probabilidade por Região da cidade e não bairro a bairro

**3.	Correlação com outros fatores externos (Condições Climáticas)**

  Fatores externos, tais como, as condições climáticas, talvez afetem a probabilidade de bairros ou regiões originarem transportes. É esperado, por exemplo, que em dias de chuva, ou de baixa temperatura, haja menos demandas de transportes envolvendo regiões praianas.
Seria interessante, portanto, em trabalhos futuros, incluir informações das condições climáticas como variáveis preditoras na base de treino e teste, bem como outras informações pertinentes.

**4.	COVID-19**

  A base de dados utilizada para treino dos modelos é de janeiro/2020, antes do início do isolamento social em geral no Brasil. Após meses do início do isolamento, várias medidas de flexibilização já foram adotadas, no entanto paradigmas relacionados a ineficiência e ineficácia do home-office e ensino a distância foram quebrados. Costumes foram alterados com as pessoas fazendo mais uso de serviços de “delivery”, compras pela internet e outros. Áreas das cidades antes ocupadas principalmente por escritórios comerciais permanecem com pouca circulação de pessoas mesmo com a flexibilização do isolamento. Por tudo isso é possível que o perfil de probabilidades de regiões das cidades originarem transportes seja diferente agora do que era antes do início do isolamento. 
  Trabalhos futuros devem levar em consideração também, dados recentes, visando o aprendizado pelos modelos das probabilidades após o evento do isolamento, do COVID-19 e dos novos costumes da população. 

