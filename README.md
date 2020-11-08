# PREVISÃO AUTOMÁTICA, COM REDES NEURAIS, DA PROBABILIDADE POR BAIRROS DE SEREM SOLICITADOS TRANSPORTES POR APLICATIVOS

Monografia apresentada ao Departamento de Engenharia Elétrica da PUC/Rio como parte dos requisitos para a obtenção do título de Especialização em Business Intelligence

Data: 31/08/2020

## Autor: Fernando Mauro **Buleo** Barbosa

### O texto abaixo apresenta um resumo do trabalho. Clique no link a seguir para acessar a [Monografia Completa](https://github.com/buleo/TCCTeste/blob/main/BI-Master-Monografia-final%20-FMBB.pdf).

## RESUMO:
No presente trabalho foi desenvolvido modelo preditivo visando identificar as áreas de cidades com maior probabilidade de demandarem transporte por aplicativo, a cada dia e hora. O modelo preditivo foi desenvolvido em uma rede neural e treinado para prever a probabilidade de transportes serem demandados em 3 (três) cidades brasileiras. Para o treinamento foi utilizada a base completa de 1 (um) mês de 2020 de transportes realizados por aplicativo. 

Os melhores resultados obtidos indicaram que, em 84% dos casos, o modelo consegue prever a probabilidade de bairros demandarem transporte com uma distância de até 3 posições em relação a ordem (“ranking”) real de bairros, quando consideramos os 5 que mais demandam transportes. Expandindo a análise para os 10 bairros que mais solicitam transportes, foi verificado que, em 77% dos casos, o modelo consegue prever a probabilidade de bairros demandarem transportes com uma distância de até 3 posições em relação ao “ranking” real.


## ABSTRACT:
In this work, a predictive model was developed to identify the areas of cities most likely to require transportation, every day and hour. The predictive model was developed in a neural network and trained to predict the likelihood of a demand for transport in 3 (three) Brazilian cities. For the training of the model, the complete base of transports performed in 1 (one) month of the year 2020 of a transport application was used.

The best results obtained indicated that, in 84% of the cases, the model is able to predict the probability of neighborhoods requiring transport with a distance of up to 3 positions in relation to the real "ranking", when we consider the 5 neighborhoods that most originate races. Expanding the analysis to the 10 neighborhoods that demand the most transport, It was found that, in 77% of the cases, the model is able to predict the probability of neighborhoods requiring transport with a distance of up to 3 positions in relation to the real "ranking".

## OBJETIVOS DO TRABALHO
Para realização desse trabalho foi obtida, junto a empresa [Gaudium](https://gaudium.global/), a qual desenvolveu e comercializa o aplicativo de transportes [Machine](https://machine.global/), a base completa de transportes realizados em janeiro de 2020. Essa base dispõe para cada transporte, de informações como a data da “corrida” (transporte), horário, cidade de partida, cidade de destino, bairro de partida e bairro de destino. De posse dessa base os objetivos do trabalho foram: 
  -	Gerar base de informações, a partir da base disponível de transportes realizados, com a probabilidade de cada bairro, em cada cidade de partida, demandar transportes a cada dia e hora do mês de modo a servir como base de treino e base de testes do modelo preditivo a desenvolver
  -	Eleger, dentre as 1.118 cidades de partida presentes na base, quais seriam usadas nesse estudo
  -	Desenvolver Rede Neural para prever, por método de regressão, a probabilidade de cada bairro das cidades eleitas no estudo, demandar transportes a cada dia, de hora em hora
