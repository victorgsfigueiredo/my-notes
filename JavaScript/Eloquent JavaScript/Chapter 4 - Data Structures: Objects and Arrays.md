Os tipos de dados como números, strings e booleanos são os átomos da programação. Entretanto, em nossa jornada pelo JavaScript, tudo o que vimos até agora foram dados simples e que, de forma bastante honesta, não fazem parte do mundo real e, portanto, permitem construir programas limitados. Um _objeto_, no entanto, é um conjunto agrupado de dados que pode incluir outros objetos, nos permitindo construir estruturas lógicas mais complexas.

### Data sets

Imagine que queremos criar uma lista para armazenar os números 2, 3, 5, 7 e 11. Como faríamos isso em JavaScript? Bem, poderíamos ser um tanto criativos e tentar fazer isso com uma string, da mesma forma que vimos no capítulo anterior. Mas isso é extremamente inadequado, pois além de ser complicado acessar números de dois dígitos, também seria necessário convertê-los de volta para número, o que geraria uma bagunça enorme para uma tarefa que deveria ser simples.

Felizmente, as pessoas que criaram o JavaScript sabem da importância disso e criaram uma funcionalidade nativa que nos permite fazer uma lista de dados. Essa lista de dados se chama _array_ e é declarada da seguinte forma:

```javascript
let listOfNumbers = [2, 3, 5, 7, 11];

console.log(listOfNumbers[2]);
// → 5
console.log(listOfNumbers[0]);
// → 2
console.log(listOfNumbers[2 - 1]);
// → 3
```

Para se invocar um determinado item de um _array_, você simplesmente invoca o nome da variável em que está armazenada o _array_ seguido de ```[i]```, onde ```i``` é o index. O index seria a posição onde o item está dentro do _array_. Note que o primeiro item possui index 0, não 1. Isso sempre foi uma tradição na tecnologia e há uma série de razões para que isso seja assim. Em vez de pensar no index como a posição do número, pense nele como _o número de itens que tenho que pular para chegar no item desejado_. O index 0 seria o primeiro item porquê não precisa pular nenhum, enquanto o index 1 seria o segundo item, pois você pula o primeiro.

### Properties

Até agora, vimos algumas funções suspeitas, como ```Math.max``` e ```myString.length```. Essas funções que vimos, na verdade, estão acessando uma propriedade de um valor. No primeiro caso, estamos acessando a propriedade ```max``` de ```Math``` e o mesmo se aplica à propriedade ```length```.

Praticamente todos os valores em JavaScript possuem propriedades. As únicas exceções são ```null``` e ```undefined```:

```javascript
null.length;
// Error: Cannot read property 'length' of null
```

As duas formas principais de se acessar uma propriedade são com o ponto (```myString.length```) e com as chaves (```myString[length]```). Apesar das duas formas serem parecidas e nós empregarmos o mesmo nome nas duas maneiras, eles não necessariamente acessarão a mesma propriedade. Vejamos:

```javascript
let a = [1, 2, 3];
// → undefined

a.length
// → 3

a['length']
// → 3

length = 'tamanho';
// → "tamanho"

a[length]
// → undefined
```

Perceba que, com a notação de ponto, ```a.length``` acessou uma propriedade de nome ```length``` dentro do _array_ ```a```. No segundo caso, utilizamos ```a['length']``` o qual nos retornou o mesmo resultado. Mas por que precisamos utilizar as aspas para obtermos o mesmo resultado? Simples: quando utilizamos a chave, não estamos passando um nome, mas uma expressão a qual será _interpretada_ antes de ser efetivamente computada e retornar um valor. Veja:

```javascript
a[3 % 2];
// -> 2
```
No exemplo acima, o console primeiro interpretou ```3 % 2```, que é igual a 1, e depois fez ```a[1]```, o que o fez acessar o segundo item da _array_ ```a```, que é 2.

O mesmo funciona para variáveis:

```javascript
let nomeQualquer = 'length';

a[nomeQualquer];
// -> 3
```

Em resumo: se você quer acessar a propriedade de nome ```i```, você diz ```a.i```, se você quer acessar a propriedade cujo nome é o resultado da interpretação de ```i```, você diz ```a[i]```.

Os nomes das propriedades sempre serão strings. Entretanto, na notação de ponto, você só pode passar um nome que obedeça às regras de declarações de variáveis. Então, se você quer acessar uma propriedade de nome "Víctor Gustavo", você precisa fazer ```object["Victor Gustavo"]``` pois "Víctor Gustavo" não é um nome de variável válido.

No caso de _arrays_, os seus elementos são armazenados como propriedades e cada propriedade recebe um número como nome. Como número não são variáveis válidas, você precisa acessar a propriedade de um _array_ através de ```array[number]```. ```length```, por outro lado, é um nome válido e acessamos através de ```object.length``` porque é mais fácil de fazê-lo do que ```object['length']```.

### Methods

Existem propriedades que armazenam valores de funções nativas. Essas propriedades são chamadas de **métodos**.

```javascript
let nome = 'Victor Gustavo';

console.log(typeof nome.toUpperCase);
// -> function

console.log(nome.toUpperCase());
// -> VICTOR GUSTAVO
```

Toda _string_ tem um método chamado ```toUpperCase```, que torna todas as letras da string maísculas. De forma semelhantemente oposta, temos o método ```toLowerCase```.

Portanto, podemos dizer que "```toUpperCase``` e ```toLowerCase``` são métodos de ```nome```".

Existem dois métodos para a manipulação de _arrays_, vejamos:

```javascript
let sequence = [1, 2, 3];
sequence.push(4);
sequence.push(5);

console.log(sequence);
// -> (5) [1, 2, 3, 4, 5]

sequence.pop();

console.log(sequence);
// -> (4) [1, 2, 3, 4]
```

Os métodos ```push``` e ```pop``` são opostos entre si. ```push``` adiciona um item a um array, enquanto ```pop``` retira o último item da lista.

### Objects

Objetos são, por definição arbitrária, a declaração de um conjunto de propriedades. A forma mais comum de se criar um objeto é utilizando ```{}```:

```javascript
let matematica = {
  halve: x => x / 2,
  twice: x => x * 2
};

console.log(matematica.halve(2));
// -> 1

console.log(matematica.twice(2));
// -> 4
```

Você deve nomear a propriedade, seguindo o nome com dois pontos e então o valor da propriedade, que pode ser absolutamente qualquer coisa. No exemplo acima, atribuí funções matemáticas às propriedades que eu declarei.

Também é possível atribuir uma nova propriedade a um objeto com o operador ```=```:

```javascript
matematica.plusTwo = x => x + 2;

matematica.plusTwo(6);
// -> 8
```

No caso acima, se a propriedade ```plusTwo``` existir, ela será reatribuida, enquanto caso não exista, será criada.

Podemos também deletar essa propriedade, apesar de isso não ser muito frequente:

```javascript
delete matematica.plusTwo;

console.log(matematica.plusTwo);
// -> undefined
```

Podemos ainda usar o operador unário ```in``` para verificar se um objeto possui uma propriedade com um nome especificado:

```javascript
console.log("plusTwo" in matematica);
// -> false

console.log("halve" in matematica);
//-> true
```

E ainda, podemos utilizar a função ```Object.keys()``` para descobrir os nomes de todas as propriedades presentes em um objeto:

```javascript
console.log(Object.keys(matematica));
// -> (2) ["halve", "twice"]
```

Temos também a função ```Object.assign()```, que mescla dois objetos diferentes:

```javascript
Object.assign(matematica, {oneThird: x => x / 3});

console.log(Object.keys(matematica));
// -> (3) ["halve", "twice", "oneThird"]
```

Seria um _array_ um objeto? A resposta é sim!

```javascript
typeof []
// -> "object"
```

Isso significa algumas coisas interessantes. A mais legal de todas é que podemos fazer um _array_ de objetos. Isso nos permite armazenar e manipular a informação de diferentes formas criativas e interessantes! Veja o exemplo abaixo extraído do [Eloquent Javascript](https://eloquentjavascript.net/04_data.html):

```javascript
let journal = [
  {events: ["work", "touched tree", "pizza",
            "running", "television"],
   squirrel: false},
  {events: ["work", "ice cream", "cauliflower",
            "lasagna", "touched tree", "brushed teeth"],
   squirrel: false},
  {events: ["weekend", "cycling", "break", "peanuts",
            "beer"],
   squirrel: true},
  /* and so on... */
];
```

### Mutability

Estamos quase chegando na programação de verdade. Antes de chegar lá, temos um último conceito teórico para aprender: a mutabilidade ou imutabilidade dos valores.

Até agora, vimos valores que não mudam, como números, strings e booleanos. 1 sempre será igual a 1, e 'cat' sempre será igual a 'cat'. Isto é, não temos como alterar a string 'cat' para imprimir 'rat' e ao mesmo tempo manter a igualdade entre 'cat' e 'rat'. Objetos, no entanto, se comportam diferentemente. Vejamos o exemplo abaixo.

```javascript
let object1 = {value: 10};
let object2 = object1;
let object3 = {value: 10};

object1 == object2;
// -> true

object1 == object3;
// -> false
```

Quando comparamos o ```object1``` e ```object2```, obtemos ```true``` porque o definimos que o ```object2``` é igual ao ```object1```. Isto é, toda vez que alteramos uma propriedade do ```object1```, o ```object2``` também será alterado. Entretanto, por que o ```object1 e 3``` são diferentes, sendo que sua declaração é exatamente igual?

Bem, objetos sempre serão diferentes entre si. Apesar de terem as mesmas propriedades, eles vivem vidas separadas. Veja:

```javascript
object1.value = 15;

console.log(object1.value);
// -> 15

console.log(object3.value);
// -> 10
```

Portanto, apesar das propriedades antes serem iguais, eles não estão atrelados. Isso pode ser visto facilmente acima. É por isso que eles não são iguais.

Variáveis também possuem um comportamento semelhante. A diferença é que você pode definir se elas serão mutáveis ou não. Se você quiser que uma variável seja mutável, você a declara usando a declaração ```let```, caso contrário, você utiliza ```const```.

```javascript
const objectTest = {value: 10};

objectTest.value = 15;
// It works!

objectTest = {value: 15};
// Error! Assignment to constant variable.
```

Como podemos ver, não é possível reatribuir uma variável ```const```, mas podemos mudar uma propriedade dentro dela.

### The lycanthrope’s log

Apesar de não estar presente neste resumo, o capítulo deste livro inicia-se com a história de um homem que se transforma em esquílo todas as noites e, numa tentativa de descobrir o que causa a sua transformação, está tentando encontrar uma associação entre o que ele faz durante o dia e suas transformações.

Para isso, ele constrói o seguinte programa, de forma a sempre poder adicionar os registros diários:

```javascript
let journal = [];

function addEntry(events, squirrell) {
  journal.push({events, squirrell});
}
```

Note acima que foi colocada a variável diretamente no lugar onde seria a propriedade, ao invés de algo como ```events: events```. Isso porque o JavaScript assume que, caso uma propriedade declarada não tenha uma atribuição, a atribuição será igual à variável de mesmo nome. Veja a demonstração:

```javascript
let oi = 10;
let objeto1 = {oi};

console.log(objeto1.oi);
// -> 10
```

Voltando à história do homem que (supostamente) se transforma em esquilo. Todos os dias, às 10 p.m., ou então na manhã seguinte (caso ele _supostamente_ se transforme), ele registra o que fez naquele dia e se se transformou. Vejamos os registros dos últimos 3 dias:

```javascript
addEntry(["work", "touched tree", "pizza", "running",
          "television"], false);
addEntry(["work", "ice cream", "cauliflower", "lasagna",
          "touched tree", "brushed teeth"], false);
addEntry(["weekend", "cycling", "break", "peanuts",
          "beer"], true);
```

Após muitos dias de registros, ele finalmente quer verificar a correlação entre o que ele faz e as transformações.

_Correlação_ é o grau de medida que uma variável estatística afeta outra variável estatística. Toda vez que verificamos uma correlação, obteremos como retorno um número entre -1 e 1, sendo que 1 significa que as variáveis são perfeitamente correlacionadas, 0 significa que não correlacionadas de forma alguma e -1 significa que elas são perfeitamente correlacionadas, mas de forma oposta (quando uma variável é ```true```, a outra é ```false```).

Para se obter esse número, precisamoas utilizar o **coeficiente phi**.

Para entendermos como o _phi_ funciona, vamos pegar a pizza. Qual a correlação entre comer pizza e se transformar em um esquilo? Primeiro, precisamos organizar os dados de forma que possamos saber o número de vezes em que pizza e transformação aconteceram.

![Correlação pizza e transformação](https://eloquentjavascript.net/img/pizza-squirrel.svg)

O coeficiente phi segue a seguinte fórmula:

![Coeficiente phi](https://i.ibb.co/XtS9Q0P/image.png)

Legenda:

- n11 = variável 1 true; variável 2 true.
- n00 = variável 1 false; variável 2 false.
- n1• = variável 1 true;
- n•1 = variável 2 true;

