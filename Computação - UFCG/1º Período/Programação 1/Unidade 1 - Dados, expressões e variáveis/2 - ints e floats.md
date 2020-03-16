### Convertendo inteiros na base 10 para a base 2

Muito simples: para isso, basta dividir o inteiro sucessivamente por 2 e registrar a sua sobra.

Convertendo o número 6, teremos:

- 6 / 2 = 3 (0)
- 3 / 2 = 1 (1)
- 1 / 2 = 0 (1)

Lendo os restos de baixo para cima, teremos que a representação de 10, em binário, é 110.

### Entendendo o complemento de dois

Complemento de dois é uma técnica utilizada por processadores que reduz o uso de memória para a representação de um número ou caractere, uma vez que, dada uma limitação de bits, precisamos representar não apenas números naturais, mas todos os números inteiros (isto é, também os negativos).

Vejamos: **como representaríamos o número -110 em binário utilizando a técnica complemento de dois utilizando 8 bits?**

- 1º passo: retirar o sinal = 110
- 2º passo: subtrair 1 = 109
- 3º passo: converter o número obtido (109) para binário normalmente e completar 8 bits com zeros à esquerda, caso necessário = 00110110
- 4º passo: Inverter os bits = 11001001

Portanto, a representação de -110, usando complemento de dois, é ```11001001```.
