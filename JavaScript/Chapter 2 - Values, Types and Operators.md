## Type of data

### Números

O primeiro tipo de dado a ser estudado são os números. Os números podem ser representados de algumas maneiras em JavaScript. Um número inteiro é normalmente representado da forma como estamos acostumados:

```10```

Já os números que possuem casas decimais usam um . para separar os dígitos em JavaScript, diferente da vírgula que estamos acostumados a utilizar em nossas representações matemáticas:

```1.52```

Quando temos de lidar com números muito grandes ou muito pequenos, podemos fazer uso das extremamente úteis notações científicas, que são representadas como:

```1.55e5```, sendo a representação de 1.55 * 10⁵.

#### Operadores aritméticos

Quando estamos lidando com números em JavaScript, podemos realizar operações aritméticas com eles. Para isso, fazemos o uso dos operadores aritméticos, já bastante conhecidos:

```+``` - Soma

```-``` - Subtração

```*``` - Multiplicação

```/``` - Divisão

```%``` - Sobra

Dos operadores acima, o único que pode gerar certa dúvida é o último. Mas, na verdade, ele é bastante simples: dada a expressão, ```x % y```, o resultado será a sobra da divisão entre x e y. Um exemplo prático do que esta operação resultaria seria a equação ```11 % 5 = 1```.

#### Precedência dos operadores aritméticos

Assim como na matemática, operações aritméticas que envolvam mais de um operador são resolvidas através da procedência dos operadores, que são iguais às da matemática.

Dada a expressão ```5 + 2 * 5```, a multiplicação será resolvida primeiro. Tanto o operador de divisão quanto o operador de sobra possuem a mesma procedência que a multiplicação.

Existem casos em que queremos que a soma seja resolvida primeiro. Neste caso, assim como na matemática, podemos fazer o uso de parênteses: ```(5 + 2) * 5```.

Em casos de expressões aritméticas que envolvam operadores aritméticos de procedência igual, a expressão matemática é resolvida da esquerda para a direita:

```5 * 2 / 2 % 4 = 1```

#### Números especiais

Há três valores especiais que são tratados como números em JavaScript. São eles ```Infinity```, ```-Infinity``` e ```NaN```, respectivamente, o infinito positivo, o infinito negativo e NaN, que é a representação para "Not a Number".

É importante estabelecer que operações que envolvam **| ```Infinity``` |** não são dignas de confiança absoluta, embora possam ser úteis em algumas situações específicas. Isso porque o infinito é um valor abstrato, que não pode ser representado de forma precisa a não ser que haja um número de bits infinito.

O valor ```NaN``` é interpretado pelo JavaScript como número, apesar de sua própria sintaxe dizer o contrário. Entretanto, este é um valor útil, pois ele será o retorno de operações que não resultam em uma conclusão matemática lógica. Alguns exemplos são ```0 / 0``` e ```Infinity - Infinity```.

### Strings

O segundo tipo de informação que veremos é a string. String nada mais é que uma informação do tipo texto. Quando lidamos com texto em JavaScript, podemos lidar com ele de três maneiras diferentes:

``` `Isto é uma string.` ``` - Backticks

``` 'Isto é uma string.' ``` - Aspas simples

``` "Isto é uma string." ``` - Aspas duplas

Os três funcionam da mesma maneira. A única exigência é que a sintaxe utilizada ao iniciar a string seja a mesma ao terminar - ou seja, se começou aquela string com um backtick, você também deve terminá-la com um backtick.

Obviamente existem alguns problemas quando precisamos incluir caracteres utilizados pela sintaxe do JavaScript. Por exemplo, o que aconteceria se quiséssemos usar aspas em nosso texto?

```"Esta deveria ser uma string com "aspas"."```

Você deve imaginar que isso não será interpretado apropriadamente como uma string só. Por isso, quando precisamos utilizar caracteres especiais em nossa string, podemos fazer uso do backslash (```\```) precedido do caractere especial. Por exemplo: o texto acima, em código, ficaria:

```"Esta deveria ser uma string com \"aspas\"."```

Dessa forma, o programa irá interpretar as aspas como parte da string, e não como o fim ou início de uma nova.

O backslash também pode ser utilizado para outros caracteres especiais. Os dois mais comuns são:

```\n``` - o caractere criado quando clicamos ENTER, para iniciar uma nova linha.

```\t``` - o caractere criado quando clicamos TAB.

#### Strings com backticks

Também chamados de _template literals_.

Apesar de todos os operadores de strings funcionarem da mesma forma, os backticks nos permitem alguns poderes especiais na manipulação de texto. Quando se escreve uma string com os backticks, os caracteres especiais como \n e \t não precisam do backslash, pois apenas o clique no botão é suficiente para que o Javascript armazene esses caracteres.

Nós também podemos fazer o uso de ```${}```. Os valores que forem passados através desse código serão computados, interpretados e então convertidos para string.

``` 
`Metade de 100 é ${100 / 2}.` 
// -> Metade de 100 é 50.
```

### Operadores unários

Operadores que usam dois valores são chamados de binários. É o caso da soma e da multiplicação, por exemplo. Não é possível realizar uma multiplicação com apenas um valor, apenas com dois valores.

Existem outros operadores, no entanto, que só utilizam um valor. Como exemplo, podemos utilizar o ```typeof```, cujo retorno será uma string com o nome do tipo de informação passada para o operador.

```
console.log(typeof 2);
// -> number

console.log(typeof "dois");
// -> string
```

Alguns operadores, como o ```-```, podem ser tanto unários quanto binários: ```- (5 - 3)``` = ```-2```.

## Valores booleanos

Em toda linguagem de programação, possuímos a representação dos valores booleanos. Eles são necessários em situações em que o programa precisa de apenas duas opções, como "sim" e "não", ou "on" e "off". No Javascript, os valores booleanos são representados como ```true``` e ```false```.

## Comparação
