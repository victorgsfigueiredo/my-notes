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

