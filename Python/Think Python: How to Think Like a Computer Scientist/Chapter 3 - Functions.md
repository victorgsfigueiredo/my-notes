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

## 3.8 Parameters and arguments

Até agora, nós declaramos apenas funções que não utilizam argumentos. Mas para declarar uma função com um argumento, é bastante simples:

![Função print_twice](https://i.ibb.co/MZb6QW4/image.png)

Aqui, passamos um argumento ```x``` para a função. Quando a função for chamada, ```x``` será substuído pelo valor que o _caller_ a atribui, como se fosse uma variável. Ou seja: **não importa o nome do argumento, e sim o valor atribuído pelo *caller***. O nome do argumento é necessário para ser utilizado na declaração da função, mas seu uso termina ali.

Na função acima, o argumento será printado duas vezes. É importante destacar que o argumento pode ser qualquer coisa, como uma variável, uma operação aritmética e até mesmo um valor booleano.

![Função com variável](https://i.ibb.co/SBDP806/image.png)

## 3.9 Variables and parameters are local

Quando declaramos variáveis e parâmetros dentro de uma função, esses valores existem apenas **dentro da função**.

```python3
def cat_twice(part1, part2):
    cat = part1 + part2
    print_twice(cat)
    
```

Na função acima, a variável ```cat``` existe apenas dentro dessa função. Se após essa função tentarmos ```print(cat)```, obteremos ```NameError: name 'cat' is not defined```

## 3.10 Stack diagrams

Com o objetivo de manter o entendimento do código, uma vez que algumas variáveis são locais e outras não, podemos criar um _stack diagram_. Ele indicará exatamente quais variáveis e funções estão inseridas no ```---main---``` (nome especial dado ao nível mais superior do _stack_) e quais estão inseridas localmente, dentro de uma função.

O Console Python também disponibiliza um **traceback** quando ocorre algum erro relacionado ao _stack_, isto é, quando se tenta invocar uma variável local em uma função diferente, por exemplo. Veja o código abaixo:

```python3
def print_twice(bruce):
    print(bruce)
    print(bruce)
    print(cat)
    
def cat_twice(part1, part2):
    cat = part1 + part2
    print_twice(cat)
    
cat_twice('Menin', 'ix');
```

Em ```print_twice(x)```, na terceira linha do **body**, temos ```print(cat)```, cuja finalidade é mostrar o ```cat``` definido na segunda função do stack, ```cat_twice(part1, parte2)```. Como ```cat``` é uma variável local, temos um erro de stack que é retornado, juntamente a um **traceback**.

![Erro com traceback](https://i.ibb.co/Z8Bgy8J/image.png)

Veja que ele imprime um erro com todas as funções chamadas, traçando o caminho até finalmente alcançar um erro, e ainda retorna a linha onde está o erro (neste caso, _line 4_).

Olhando um _stack diagram_ estritamente, obtemos:

![Stack diagram](https://i.ibb.co/Kq2yFrf/image.png)

Essa imagem foi retirada do livro Think Python. Nele, ao invés dos atributos ```'Menin'``` e ```'ix'``` que usamos para a função ```cat_twice(part1, part2)``` foram substuídos por ```'Bing tiddle '``` e ```'tiddle bang.'```.

Note como o _stack diagram_ representa todas as camadas encapsuladas.

## 3.11 Fruitful functions and void functions

Até agora, todas as funções que vimos **não retornam nenhum valor**. O autor chama essas funções de _void functions_, pois, por não retornarem nenhum valor, o resultado delas não pode ser armazenado em uma variável.

Se tentarmos armazenar o valor da função ```print_twice``` numa variável, obteríamos o seguinte:

![Tentando armazenar função sem retorno numa variável](https://i.ibb.co/4MxcMx1/image.png)

Ao pedirmos para o console Python mostrar o armazenamento de ```eu```, obtemos o valor ```None```. Este é um valor especial, e tem seu tipo próprio:

![None Type](https://i.ibb.co/McfG9h8/image.png)

Quando uma função tem retorno, o autor as chama de _fruitful functions_, pois é possível utilizar seus retornos para performar outras ações dentro do nosso programa.

## 3.12 Why functions?

Até esse momento, talvez não esteja claro a importância de usar funções em um código. Mas funções são peças primordiais de qualquer programa, em qualquer linguagem, pelas seguintes razões:

- Diminuição do programa ao diminuir a quantidade de código repetido: isto é, se você precisa usar o mesmo código duas vezes, você pode colocá-lo numa função e então apenas chamá-la duas vezes.
- Facilidade no _debugging_, uma vez que se um erro acontecer, você pode analisar função por função até encontrar o problema, o que é muito mais fácil do que procurar um pequeno erro em meio a um código solto e repetitivo.
- Facilidade na alteração do programa, uma vez que, conforme o exemplo um, se você quiser alterar a funcionalidade da função naqueles dois lugares, basta alterar o **body** da função.
- Funções bem-feitas são úteis em vários programas diferentes. Você pode reaproveitar uma função em um novo programa.

## 3.13 Importing with ```from```

Existem duas maneiras de se importar um módulo. A primeira já vimos, através do ```import math```. Com isso, importamos o módulo math para o nosso código.

A outra maneira é usando o ```from```:

```python3
>>> from math import pi

>>> print(pi)
3.141592653589793

```

Usando o ```from```, importamos um único objeto do módulo math. Portanto, ```pi``` passa a se comportar como uma variável com o valor do objeto ```math.pi```. Ainda mais: podemos usar ```*``` para importar **todo o módulo** usando o ```from```:

```python3
>>> from math import *

>>> cos(pi)
-1.0
```

A vantagem é que, com isso, você consegue **eliminar o _dot notation_**. A desvantagem é que pode haver conflito de nomes com variáveis, nomes de funções e outros objetos de outros módulos que possivelmente podem ser importados. Cabe ao programador decidir qual a melhor maneira de manter seu código organizado, conciso e sem erros.

## 3.14 Debugging

Certifique-se de que você está utilizando um editor de texto que cuide da identação para você, uma vez que no Python ela é tão importante! Debugar os 4 espaços de identação exigidos pelo Python é extremamente difícil, uma vez que eles são tão comuns. Portanto, o editor de texto é fundamental para que esse tipo de erro não aconteça.

Fora isso, **nunca se esqueça de salvar seu programa**! Muitos programadores, quando enfrentam um erro, tentam corrigí-lo mas esquecem de salvar o programa antes de executá-lo, o que os faz perder várias horas debugando um código que possivelmente já havia sido resolvido! Se você não tem certeza de que o seu código está sendo salvo, coloque algo como ```print('olá')``` na primeira linha do seu programa. Se você não ver o ```olá``` ao executá-lo, significa que ele não está sendo salvo!

