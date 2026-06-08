Mission_Control_ai - Explicação das estruturas utilizadas no código

Áreas Monitoradas

O sistema monitora cinco áreas fundamentais da missão espacial:

Temperatura Interna	 ---> Controle térmico da nave

Comunicação com a Base ---> 	Qualidade do sinal de comunicação

Sistema de Energia ---> 	Nível de bateria disponível

Suporte de Oxigênio ---> 	Nível de oxigênio da missão

Estabilidade Operacional ---> 	Funcionamento geral dos sistemas


Estrutura dos Dados

Os dados são armazenados em uma matriz chamada dados_missao.

Cada linha representa um ciclo de monitoramento.


23, 95, 91, 97, 93

28, 78, 74, 93, 82

33, 61, 55, 89, 67

37, 39, 35, 85, 52

41, 25, 17, 76, 32

35, 52, 30, 81, 48

Cada posição representa:

temperatura,  comunicacao, bateria, oxigenio,estabilidade



Regras de Classificação

Temperatura

Condição              	Status

Menor que 18°C	        ATENÇÃO

Entre 18°C e 30°C      	NORMAL

Entre 31°C e 35°C      	ATENÇÃO

Acima de 35°C	          CRÍTICO


Comunicação

Condição              	Status

Menor que 30%          	CRÍTICO

Entre 30% e 59%	        ATENÇÃO

60% ou mais	            NORMAL


Bateria

Condição	              Status

Menor que 20%	          CRÍTICO

Entre 20% e 49%        	ATENÇÃO

50% ou mais            	NORMAL


Oxigênio

Condição              	Status

Menor que 80%	          CRÍTICO

Entre 80% e 89%        	ATENÇÃO

90% ou mais	            NORMAL


Estabilidade Operacional

Condição	              Status

Menor que 40%	          CRÍTICO

Entre 40% e 69%        	ATENÇÃO

70% ou mais	            NORMAL



Sistema de Pontuação

Cada classificação gera uma pontuação de risco:


Status	      Pontuação

NORMAL	          0

ATENÇÃO          	1

CRÍTICO	          2

A soma dos pontos determina a situação do ciclo.


Pontuação Total      	Classificação

0 a 2                	MISSÃO ESTÁVEL

3 a 5                	MISSÃO EM ATENÇÃO

6 a 10	              MISSÃO CRÍTICA

