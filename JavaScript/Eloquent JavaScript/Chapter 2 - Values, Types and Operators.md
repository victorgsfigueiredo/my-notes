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

### Comparação

Os valores booleanos são produtos de comparações lógicas. Quando passamos uma expressão lógica, ela será interpretada e, sendo verdadeira, retornará o valor true, do contrário, false. Vejamos alguns exemplos:

```2 < 3 ``` returns ```true```

```3 < 2``` returns ```false```

Também é possível realizar comparações lógicas com strings, não apenas números. Por exemplo:

```"Aardvark" < "Zoroaster``` returns ```true```

A comparação entre strings não é feita alfabeticamente. Na verdade, cada caractere é comparado através do sistema Unicode, de forma que caracteres em minúsculos valem mais do que caracteres em maiúsculo. Outros caracteres especiais, como !, ?, -, entre outros, também entram nessa ordem de alguma maneira.

Fora os operadores lógicos de maior e menor, também temos os seguintes:

```==``` - é igual a
```!=``` - é diferente de
```>=``` - maior ou igual a
```<=``` - menor ou igual a

O único valor que não é igual a si próprio é o valor NaN.

```
console.log(NaN == NaN)
// → false
```

### Operadores lógicos: E, OU e ternário

Assim como na lógica matemática, em JavaScript possuímos os operadores lógicos E e OU.

O operador lógico E é representado em JavaScript por ```&&```. Para que uma expressão lógica envolvendo o E retorne ```true```, é necessário que ambas as condições passadas sejam true. Vejamos dois exemplos:

```
1 == 1 && 10 / 2 == 5
// → true
```

```
1 == 1 && 50 / 5 == 1
// → false
```

Já o operador lógico OU é representado por ```||``` e retorna true caso um dos valores passados seja true. Dois exemplos:

```
1 == 1 || 50 / 5 == 1
// → true
```

```
1 != 1 || 50 / 5 == 1
// → false
```

É importante destacar que o JavaScript lê a expressão da seguinte maneira: se a expressão à esquerda for true, a expressão à direita é ignorada e o JavaScript retorna true. Se a expressão à esquerda for false, somente nessa ocasião o JavaScript irá avaliar a expressão à direita.

O último operador lógico que vamos apresentar é o **operador ternário**. Ele é assim chamado porque, obviamente, leva três valores.

```
console.log(true ? 1 : 2);
// → 1

console.log(false ? 1 : 2);
// → 2
```

Ele é bastante simples: se o primeiro valor for true, ele retornará o valor do meio. Se for false, ele retornará o último valor. Nesse exemplo, é apresentado um valor booleano, mas este pode ser substituído por qualquer expressão lógica que retorne um valor booleano.

### Conversão automática de tipos de dados

O JavaScript sempre tenta converter um dos tipos de dados quando a comparação ou a interação entre eles não é possível. No começo, isso visava facilitar a vida dos desenvolvedores, de forma a minimizar o número de erros possíveis. Apesar disso, existe uma certa desvantagem nisso, uma vez que, às vezes, não queremos que o JavaScript faça essa correção, ou até mesmo quando não queremos que nosso erro seja encoberto. Vejamos alguns exemplos abaixo.

```
console.log(8 * null)
// → 0

console.log("5" - 1)
// → 4

console.log("5" + 1)
// → 51

console.log("five" * 2)
// → NaN

console.log(false == 0)
// → true
```

No primeiro exemplo, o JS converteu ```null``` para 0. No segundo exemplo, ele converteu "5" (string) para 5 (número). No terceiro exemplo, como o sinal de adição pode ser utilizado para a concatenação, é exatamente isso que o JS faz, convertendo o 1 (número) para "1" (string), gerando a expressão "51". No quarto exemplo, como não é possível realizar uma operação matemática com uma string, o JavaScript retorna ```NaN```. Por último, o JS converte 0 para false, retornando true.

Quando comparamos duas expressões usando ```==```, o resultado é fácil de ser previsto: ele retornará ```true``` caso os dois lados sejam iguais, e caso não, retornará ```false```. No entanto, em alguns casos específicos, quando são comparados dois tipos de dados diferentes, o JavaScript utiliza uma série de regras bastante confusas para realizar a comparação final.

```
console.log(null == undefined);
// → true

console.log(null == 0);
// → false
```

O comportamento acima pode ser útil em algumas ocasiões, principalmente quando queremos comparar se alguns valores que estamos buscando são diferentes de null e undefined.

Expressões como ```0 == false``` e ```"" == false``` retornam ```true```, por causa da conversão automática do JavaScript. O 0 é transformado em false e "" também, de forma que ```false == false``` retorna ```true```.

**Quando não queremos que o JS realize essa conversão**, podemos utilizar os operadores ```===``` e ```!==```, que significam _precisamente igual a_ e _precisamente diferente de_, de forma que o tipo de dado também será comparado. Dessa forma, ```0 === false``` retornará ```false```.

### Curto-circuito nos operadores lógicos

Como visto anteriormente, quando usamos a expressão ```||``` para operações lógicas, ela irá avaliar a primeira expressão e, caso ela retorne true, o JS irá retornar true. Se retornar false, o JS irá avaliar a segunda expressão, e só retornará true se a segunda expressão for true, do contrário, retornará false.

Mas e quando fazemos operações lógicas com expressões não lógicas? Veja o exemplo abaixo:

```console.log("Victor" || "Gustavo");```

Estamos comparando duas strings. Nesse caso, como o JS faria para retornar true ou false? Na verdade, o **JS não retorna true ou false, e sim a própria expressão**. No caso acima, será impressa no console a string "Victor", porque foi a primeira a ser avaliada e, como não é possível retornar true ou false, o JS imediatamente a retorna.

Caso a primeira expressão seja convertida para ```false```, então o JS irá retornar a segunda expressão:

```
console.log(null || "Gustavo");
// → Gustavo
```

Isso pode ser extremamente útil em situações onde queremos retornar um valor diferente caso a primeira string seja vazia, uma vez que "" pode ser convertido para ```false```.

Também podemos fazer o mesmo para o operador ```&&```, que retornará sempre o contrário:

```
console.log("Victor" && "Gustavo");
// → "Gustavo"

console.log(null && "Gustavo");
// → null
```

Três valores são convertidos para ```false``` pelo JS, são eles: 0, NaN e "" (string vazia). A partir disso, podemos construir nossos programas utilizando desses "curtos-circuitos".
