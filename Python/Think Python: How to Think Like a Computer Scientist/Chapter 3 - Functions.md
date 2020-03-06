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

Até agora, vimos vários componentes do Python de forma isolada, sem combiná-los de verdade. Aqui, o que queremos dizer é que você pode misturar funções, operadores aritméticos e variáveis da forma que você quiser, desde que o valor à esquerda seja uma variável.

- ```x = math.sin(degrees / 360.0 * 2 * math.pi)```
- ```x = math.exp(math.log(x+1))```

## 3.5 Adding new functions

Até agora, utilizamos apenas funções nativas do Python. Mas também é possível adicionar novas funções ao nosso programa. Vejamos um exemplo:

![Declarando a primeira função no Python](https://i.ibb.co/vkmwhHp/image.png)

A primeira linha da declaração é chamada de **header**. Nela, possuímos a keyword ```def```, que indica que naquela linha começa a declaração de uma função. Logo em seguida, temos ```mostrar_letra```, que é o nome da função. E então, os parênteses vazio ```()```, que indicam que aquela função não recebe nenhum argumento. Por fim, o **header** termina com dois pontos.

Após o **header**, vem o **body**, com todas as declarações, variáveis e argumentos daquela função. Por convenção, todo o **body** deve ser identado com quatro espaços. Após terminarmos a declaração do **body**, devemos deixar uma linha identada em branco, a qual indicará que a declaração daquela função terminou.

No exemplo acima, chamamos ```mostrar_letra()``` para vermos o resultado da função.

## 3.6 Definitions and uses

Esta pequena seção diz que, para usar uma função, você deve declará-la primeiro. Ou seja, não se pode chamar ```mostrar_letra()``` sem antes definí-la.

Entretanto, veremos como funciona o **flow of execution** em seguida.

## 3.7 Flow of execution

O Python sempre lerá um programa de cima para baixo. Entretanto, uma função funciona como um detonador nessa lógica: quando uma função é chamada, o Python volta o programa até onde a função foi declarada e executa todas as suas declarações.

Isso pode soar simples, até você lembrar que a função chamada pode chamar outra função. E essa última ainda pode chamar outra!

**A lição que fica é: quando se tem um programa, nem sempre o melhor é ler de cima para baixo. O melhor mesmo é seguir o flow of execution.**
