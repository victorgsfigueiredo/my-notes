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
- n1• = soma das situações em que variável 1 true;
- n•1 = soma das situações em que variável 2 true;

Colocando os valores na fórmula, obteremos que o numerador é 1×76−4×9 = 40, e o denominador √340000, o que resultará em **ϕ ≈ 0.069**. Esse número é muito pequeno e está muito próximo de zero, o que significa que a correlação entre comer pizza e se transformar em esquilo é praticamente inexistente.

### Computing Correlation

Podemos representar os dados da imagem acima, que possui dados sobre o evento pizza, em um _array_. Para isso, podemos utilizar uma lógica binária para fazer a relação entre dois eventos. Como vimos na legenda do tópico anterior, a variável 1 se refere a transformação e a variável 2 ao evento. Portanto, poderíamos representar da seguinte forma:

- 00: transformação ```false```, evento ```false```.
- 01: transformação ```false```, evento ```true```.
- 10: transformação ```true```, evento ```false```.
- 11: transformação ```true```, evento ```true```.

Como percebemos, as situações formam números binários, o que nos permite representar um _array_ com essa situações: ```[00, 01, 10, 11]``` (10 é 2 e 11 é 3).

O próximo passo é realizar uma função ```phi``` que nos permita traduzir a fórmula do coeficiente phi para JavaScript:

```javascript
function phi(array) {
  let result = (array[3] * array[0] - array[2] * array[1]) /
                Math.sqrt((array[2] + array[3]) *
                          (array[0] + array[1]) *
                          (array[1] + array[3]) *
                          (array[0] + array[2]));
  return result;
}
```

Sabendo que a _array_ para o evento "pizza" é ```[76, 9, 4, 1]```, se executarmos ```phi([76, 9, 4, 1])```, obteremos **ϕ ≈ 0.069**, que é o esperado.

Bem, nós montamos a tabela do evento "pizza" manualmente, baseados no exemplo anterior. Mas se quisermos analisar a correlação de vários eventos diferentes, será necessário criar uma função que faça isso para gente, certo? Aqui está a nossa.

```javascript
function takeTable(event, journal) {
  let table = [0, 0, 0, 0];
  for(let i = 0; i < journal.length; i++) {
    let index = 0;
    if(journal[i].events.includes(event)) index += 1;
    if(journal[i].squirrel) index += 2;
    table[index] += 1;
  }
  return table;
}
```

Nesse código, descobrimos uma nova propriedade! O ```includes``` verifica se existe o valor passado dentro da propriedade de um objeto. Portanto, se executarmos:

```javascript
takeTable("pizza", JOURNAL);
// -> [76, 9, 4, 1]
```

Obs: o código da variável ```JOURNAL``` está disponível [aqui](https://eloquentjavascript.net/code/journal.js).

## Array loops

É muito comum precisarmos fazer um loop através de todos os elementos de um _array_. Veja que, no código anterior, fizemos algo como:

```javascript
for(let i = 0; i < JOURNAL.length; i++) {
  let entry = JOURNAL[i];
  // Faça alguma coisa com entry
}
```

Boas notícias! Existe uma forma mais simples e menos verbosa de se fazer esses loops:

```javascript
for(let entry of JOURNAL) {
  console.log(`${entry.events.length} events.`);
}
```

Sempre que um ```for``` vier com a declaração de uma variável seguida de ```of```, significa que este é um _array_ loop, que irá transpassar por todos os elementos do array e que a variável declarada terá o valor ```array[i]```.

### The final analysis

Sabendo tudo o que sabemos agora, temos as ferramentas necessárias para verificar quais eventos tem uma correlação relevante.

Para isso, primeiro precisamos criar uma _array_ que possúa todos os eventos:

```javascript
functions allEventsFrom(journal) {
  let events = [];
  for(let entry of journal) {
    for(let event of entry.events) {
      if(!events.includes(event)) {
        events.push(event);
      }
    } 
  }
  return events;
}
```

Com a função acima, poderemos obter o _array_ com todos os eventos executando ```allEventsFrom(JOURNAL)```. Agora que possuímos um código para listar os eventos, bem como construir uma tabela para cada evento e, também, para calcular o coeficiente phi com base na tabela construída, podemos fazer uma solução final para calcular o phi de cada evento:

```javascript
let events = allEventsFrom(JOURNAL);
for(let event of events) {
  console.log(event + ':  ' + phi(takeTable(event, JOURNAL)));
}
```

Isso retornará o coeficiente phi de todos os eventos. Existem muitos eventos cujo phi é próximo de 0. Portanto, podemos colocar uma condição para que só sejam retornados coeficientes phi maiores que 0.1 ou menores que -0.1. Reorganizando o código, temos:

```javascript
let events = allEventsFrom(JOURNAL);
for(let event of events) {
  let result = phi(takeTable(event, JOURNAL)).toFixed(3);
  if(result > 0.1 || result < -0.1) {
    console.log(event + ':  ' + result);
  }
}
```

Também adicionei a propriedade ```.toFixed(3)``` ao resultado, para que só sejam exibidas as três primeiras casas decimais, de forma que os resultados não fiquem exorbitantemente grandes.

Obtivemos alguns retornos interessantes. Especial atenção para os seguintes:

```
brushed teeth:  -0.381
peanuts:  0.590
```

Comer amendoim parece ter uma forte relação com a transformação: quando o nosso acompanhado come amendoim, as chances de ele se transformar são muito maiores. Já escovar os dentes tem o efeito oposto: parece que escovar os dentes previne as transformações.

Visto isso, vamos tentar o seguinte: vamos pegar todos os dias em que ele comeu amendoim e não escovou os dentes e criar um evento chamado "amendoim e dente sujo" e adicioná-los a esses dias. Fazendo isso, seremos capazes de calcular o coeficiente phi para esse evento em específico, o que permitirá ver se eles possuem uma relação muito forte quando estão associados.

```javascript
for(let entry of JOURNAL) {
  if(entry.events.includes("peanuts") &&
     !entry.events.includes("brushed teeth")) {
       entry.events.push("amendoim e dente sujo");
     }
}

console.log(phi(takeTable("amendoim e dente sujo", JOURNAL)));
// -> 1
```

Uau! O cálculo do phi para o evento que criamos retornou 1. Isso significa que nosso cidadão se transformava sempre que comia amendoim e não escovava os dentes. Com a ajuda da programação, ele descobriu isso.

Depois dessa descoberta, nosso cidadão nunca mais comeu amendoim e passou a escovar os dentes todos os dias. Com isso, ele nunca mais se transformou em um esquilo.
