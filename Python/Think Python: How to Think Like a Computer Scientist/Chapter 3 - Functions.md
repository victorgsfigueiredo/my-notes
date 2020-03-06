## 3.1 Functions calls

Uma função é um conjunto de declarações com o objetivo de performar uma ação computacional. 

Nós já vimos um exemplo de função em Python: ```type(32)```, a qual retorna ```<type 'int'>```. Neste exemplo, o nome da função é ```type``` e ```32```, que ó valor entre parênteses, é o seu argumento. Frequentemente dizemos que **uma função recebe um argumento e retorna um valor**. Neste caso, ```<type 'int'>``` é o valor retornado, o qual informa o tipo do valor inserido como argumento.

## 3.2 Type conversion functions

O Python dispõe de algumas funções nativas que são destinadas a converter valores. Vejamos alguns exemplos:

![Função int()](https://i.ibb.co/GRG7WVq/image.png)

A função ```int(argument)``` irá converter o ```argument``` para um valor inteiro, caso seja possível. Se não for possível, a mesma irá retornar um erro informando de que não é possível realizar a operação.

O que aconteceria se inseríssemos um valor decimal na função ```int()```?

![Função int() com valor decimal](https://i.ibb.co/QFYdv0t/image.png)

O valor é convertido para um inteiro, **mas não é arredondado**! Ao invés disso, a função simplesmente retira a parte decimal e retorna a parte inteira.

A função ```float()``` desempenha um papel parecido, mas com números decimais:

![Função float()](https://i.ibb.co/MR2dXXg/image.png)

Quando inserimos um valor inteiro na função ```float()```, ela simplesmente retorna o valor com um ponto flutuante:

![Função float() com inteiro](https://i.ibb.co/qy6jHMb/image.png)

Já a função ```str()``` irá retornar sempre uma string:

![Função str()](https://i.ibb.co/sWdqr9K/image.png)

## 3.3 Math functions

Em Python, temos um módulo de funções chamado **math**. Ele contém, como o próprio nome já diz, funções matemáticas que podem facilitar a execução de códigos que demandem operações matemáticas específicas. Antes de utilizar qualquer uma delas, no entanto, precisamos importar esse módulo através da seguinte declaração:

![Importando math](https://i.ibb.co/VByDZ9V/image.png)

Para utilizar as funções desse módulo, primeiro precisamos inserir o nome do módulo e depois da função, separados por um ```.```. Esse formato é chamado de **dot notation**.

Vejamos alguns dos exemplos mais comuns que podemos utilizar:

- ```math.log10(x)``` -> irá retornar o log10 de x.
- ```math.log(x, [base])``` -> irá retornar o log[base] de x.
- ```math.sin(x) (or cos or tan)``` -> irá retornar o seno, ou cosseno, ou tangente de x.
- ```math.sqrt(x)``` -> irá retornar a raiz quadrada de x.
- ```math.pi``` -> irá retornar o valor de pi com uma precisão de 15 dígitos.

**A documentação completa das Math functions pode ser encontrada [clicando aqui](https://docs.python.org/3/library/math.html?highlight=math%20module#module-math)**.

## 3.4 Composition
