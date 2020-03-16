### Convertendo inteiros na base 10 para a base 2

Muito simples: para isso, basta dividir o inteiro sucessivamente por 2 e registrar a sua sobra.

Convertendo o número 6, teremos:

- 6 / 2 = 3 (0)
- 3 / 2 = 1 (1)
- 1 / 2 = 0 (1)

Lendo os restos de baixo para cima, teremos que a representação de 10, em binário, é 110.

### Entendendo o complemento de dois

Complemento de dois é uma técnica utilizada por processadores que reduz o uso de memória para a representação de um número ou caractere, uma vez que, dada uma limitação de bits, precisamos representar não apenas números naturais, mas todos os números inteiros (isto é, também os negativos).

Vejamos: **como representaríamos o número -110 em binário utilizando a técnica complemento de dois utilizando _8 bits_?**

- 1º passo: retirar o sinal = 110
- 2º passo: subtrair 1 = 109
- 3º passo: converter o número obtido (109) para binário normalmente e completar 8 bits com zeros à esquerda, caso necessário = 00110110
- 4º passo: Inverter os bits = 11001001

Portanto, a representação de -110, usando complemento de dois, é ```11001001```.

### Convertendo um número fracionário para binário

Para isso, precisamos converter para uma notação científica em binário, isto é, ao invés da base da potência da notação ser 10, ela será 2.

Tomemos como exemplo o número ```22.375``` para converter para binário.

- 1º passo: convertemos a porção inteira para binário = ```10110```.
- 2º passo: convertemos a porção decimal para binário (ao invés de dividir por 2, multiplica por 2) = ```.011```
- 3º passo: somamos a parte inteira binária com a parte decimal = ```10110.011```
- 4º passo: fazemos agora a normalização, que significa colocar o número do terceiro passo em uma notação científica de base 2: ```1.0110011 * 2^4```.
- 5º passo: assumindo que queiramos representar esse número numa base de 32 bits, teríamos: i) 1 bite para o sinal; ii) 8 bits para o expoente; e iii) 23 bits para a mantissa: ```0 10000011 01100110000000000000000``` (ignorar os espaços, foram colocados apenas para fins de visualização).

Acima, temos uma sequência de 32 bits, onde o primeiro ```0``` significa o sinal do número, neste caso, ```+```. A segunda parte representa o denominador: precisamos adicionar 127 ao denominador original (4) e, então, convertê-lo para binário que  é ```10000011```. Caso o denominador encontrado tivesse menos de 8 bits, seria necessário completá-los com 0s à esquerda. A terceira parte é a mantissa, que se inicia com o número após o ponto flutuante do número binário normalizado, e tem seus 23 bits completados com zeros à direita.

### 0.1 + 0.2

O que acontece quando tentamos fazer essa soma no console? Veremos que o resultado não é ```0.3```, isso porque essa soma, em binário, ocasiona a ocorrência de uma dízima periódica. Isso serve para demonstrar como que, por mais que vejamos graficamente números decimais, nem sempre podemos confiar na aproximação do computador para algumas representações matemáticas que existem números flutuantes.

