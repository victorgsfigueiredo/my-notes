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


