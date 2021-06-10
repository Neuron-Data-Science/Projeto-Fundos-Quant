# Projeto Fundos Quant (Neuron&Insertus)
Repositório para informações e códigos realizados pelo projeto de criação de um fundo quantitativo.

# Tese de Investimento 1: Back Test Média Móvel 9D vs. 40D
Utilizar backtest para verificar a relação entre a Média Móvel de 9 dias (MM9) e a Média Móvel de 40 dias (MM40). A tese é que, no cruzamento ascendente dessas médias, o preço tende a continuar subindo. E no cruzamento descendente dessas duas médias, o preço tende a continuar caindo. O programa deve, analisando o cruzamento das médias, tomar uma decisão: estar comprado na ação ou estar vendido na ação. Essa comparação pode ser feita dividindo a MM9 pela MM40. Caso o resultado seja maior que um, indica que estão ascendentes e devemos comprar. Caso contrário, os ativos estariam em tendência de queda, e deveríamos estar vendidos na ação. Nosso sucesso é medido pelo Índice Sharpe obtido no período e comparação dele com o Índice Sharpe de uma estratégia de Buy and Hold para o mesmo período. Esses testes devem ser feitos em períodos de 252 pregões. Os períodos devem ser selecionados após o ano 2000, quando já vivíamos em um período de câmbio flutuante.

## Ativos para teste: 
 - PETR3
 - VALE3

## Inputs (deverão ser fornecidos para a máquina os seguintes dados):

Preço fechamento ajustado D

Preço fechamento ajustado D+1

Média móvel 9 dias

Média móvel 40 dias

## Solução:

Estamos no período D.

Se ( MM9 > MM40 ) ; Retorno = Log Natural do ( Preço em D+1 / Preço em D )

Se ( MM9 < MM40 ) ; Retorno = Log Natural do ( Preço em D+1 / Preço em D ) vezes menos 1.

Caso, utilizando essa estratégia durante 252 dias, a máquina obtenha Índices Sharpes consistentemente acima do Índice Sharpe de 252 dias em uma estratégia de Buy and Hold, aprovaremos nossa tese.

## Comentários extras:

1- Quando estamos comprados, nosso patrimônio varia positivamente com o retorno da ação no período. Quando vendemos, varia negativamente. E quando estamos neutros, a variação no ativo em D+1 não afetará nosso patrimônio.

2- Retornos diários devem ser calculados pela fórmula LN(Pa/Ph) , sendo LN= Log Natural; Pe= Preço de fechamento em D+1; e Ph= Preço de fechamento hoje;

3- O retorno total do portifólio é calculado pela soma dos Logs Naturais;

4- É válido utilizar de outros mecanismos estatísticos necessários para normalização e manipulação dos dados;

5- Retorno durante a estratégia de Buy and Hold deve ser mensurado pela fórmula: Preço Final/Preço Inicial - 1.

6- A taxa livre de risco a ser utilizada deve ser a Selic acumulada no período de 252 dias.

7- Índice Sharpe é calculado pela seguinte fórmula: (Retorno do Ativo – Retorno da Selic) / Volatilidade do investimento.

8- Sugerimos testar o modelo para vários períodos de 252 dias aleatórios entre os períodos de 2000 a 2020.

## Apêndice 1: Nível de Acerto
O nível de acerto é uma medida que mensura qual a porcentagem de sucessos que a estratégia obteve no período sobre o total de sinais executados. Nesse sentido, sucesso (ou acerto) seria classificado como um retorno positivo, desde a abertura da posição, até seu fechamento, dado a estratégia. No nosso modelo, um sucesso seria concebido se, a partir de uma posição comprada (ou seja, a MM9 cruzando para cima a MM40), o encerramento dessa posição (então, MM9 cruzando para baixo a MM40) fosse acima do ponto de entrada. Em outras palavras, um acerto seria concebido se o retorno da operação fosse maior que 0. De maneira análoga, agora em relação à uma posição vendida, caso a MM9 cruzasse descendentemente a MM40 e, quando retornasse, cruzando a MM40 de forma ascendente, um sucesso seria dado se o ponto do cruzamento no encerramento fosse inferior ao do ponto de entrada, então, da mesma maneira, o retorno seria maior que zero.

                                               𝑁í𝑣𝑒𝑙 𝑑𝑒 𝐴𝑐𝑒𝑟𝑡𝑜 = 𝑁º 𝑑𝑒 𝐴𝑐𝑒𝑟𝑡𝑜𝑠/𝑇𝑜𝑡𝑎𝑙 𝑑𝑒 𝐸𝑥𝑒𝑐𝑢çõ𝑒𝑠

![image](https://user-images.githubusercontent.com/53500368/121584076-6e5b6f80-ca07-11eb-809c-41f6c7f067ef.png)

### Legenda:
Linha Amarela: MM9

Linha Azul: MM40

Seta Roxa para cima: Início de uma posição comprada e/ou encerramento de uma posição vendida

Seta Roxa para baixo: Início de uma posição vendida e/ou encerramento de uma posição comprada

Traço Verde: Sinal executado assertivo

Traço Vermelho: Sinal executado errôneo

Linhas Brancas diagonais: período de análise 𝑁í𝑣𝑒𝑙 𝑑𝑒 𝐴𝑐𝑒𝑟𝑡𝑜=𝑁º 𝑑𝑒 𝐴𝑐𝑒𝑟𝑡𝑜𝑠𝑇𝑜𝑡𝑎𝑙 𝑑𝑒 𝐸𝑥𝑒𝑐𝑢çõ𝑒𝑠= 36=50%
