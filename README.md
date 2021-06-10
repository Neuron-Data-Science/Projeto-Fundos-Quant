# Projeto-Fundos-Quant
Repositório para informações e códigos realizados pelo projeto de criação de um fundo quantitativo.

# Tese de Investimento 1: Back Test Média Móvel 9D vs. 40D
Utilizar backtest para verificar a relação entre a Média Móvel de 9 dias (MM9) e a Média Móvel de 40 dias (MM40). A tese é que, no cruzamento ascendente dessas médias, o preço tende a continuar subindo. E no cruzamento descendente dessas duas médias, o preço tende a continuar caindo. O programa deve, analisando o cruzamento das médias, tomar uma decisão: estar comprado na ação ou estar vendido na ação. Essa comparação pode ser feita dividindo a MM9 pela MM40. Caso o resultado seja maior que um, indica que estão ascendentes e devemos comprar. Caso contrário, os ativos estariam em tendência de queda, e deveríamos estar vendidos na ação. Nosso sucesso é medido pelo Índice Sharpe obtido no período e comparação dele com o Índice Sharpe de uma estratégia de Buy and Hold para o mesmo período. Esses testes devem ser feitos em períodos de 252 pregões. Os períodos devem ser selecionados após o ano 2000, quando já vivíamos em um período de câmbio flutuante.

Ativos para teste: PETR3; VALE3;

Inputs (deverão ser fornecidos para a máquina os seguintes dados):
Preço fechamento ajustado D
Preço fechamento ajustado D+1
Média móvel 9 dias
Média móvel 40 dias

Solução:
Estamos no período D.
Se ( MM9 > MM40 ) ; Retorno = Log Natural do ( Preço em D+1 / Preço em D )
Se ( MM9 < MM40 ) ; Retorno = Log Natural do ( Preço em D+1 / Preço em D ) vezes menos 1.

Caso, utilizando essa estratégia durante 252 dias, a máquina obtenha Índices Sharpes consistentemente acima do Índice Sharpe de 252 dias em uma estratégia de Buy and Hold, aprovaremos nossa tese.

Comentários extras:
1- Quando estamos comprados, nosso patrimônio varia positivamente com o retorno da ação no período. Quando vendemos, varia negativamente. E quando estamos neutros, a variação no ativo em D+1 não afetará nosso patrimônio.
2- Retornos diários devem ser calculados pela fórmula LN(Pa/Ph) , sendo LN= Log Natural; Pe= Preço de fechamento em D+1; e Ph= Preço de fechamento hoje;
3- O retorno total do portifólio é calculado pela soma dos Logs Naturais;
4- É válido utilizar de outros mecanismos estatísticos necessários para normalização e manipulação dos dados;
5- Retorno durante a estratégia de Buy and Hold deve ser mensurado pela fórmula: Preço Final/Preço Inicial - 1.
6- A taxa livre de risco a ser utilizada deve ser a Selic acumulada no período de 252 dias.
7- Índice Sharpe é calculado pela seguinte fórmula: (Retorno do Ativo – Retorno da Selic) / Volatilidade do investimento.
8- Sugerimos testar o modelo para vários períodos de 252 dias aleatórios entre os períodos de 2000 a 2020.
