## Functions

As funções são o 'pão e manteiga' da programação. São utilizadas para declarar um novo vocabulário, uma vez que nem tudo o que desejamos executar em uma linguagem de programação já venha embutido nativamente na linguagem. São, portanto, uma espécie de 'encapsulamento' do código que desejamos executar, com um nome definido por nós mesmos.

### Declarando uma função
Existem diversas formas de se declarar uma função em Javascript.  A mais simples, entretanto não comum, é declará-la através de uma variável, como demonstrado abaixo. Veremos, em seguida, que esse formato não é muito utilizado, uma vez que existem formas menos verbosas de se declarar uma função.

```javascript
const square = function(x) {
  return x * x;
 }
 ```
 No código acima, declaramos uma função denominada  ```square() ```, que recebe o parâmetro  ```x ```. Essa função irá retornar o quadrado do valor  ```x ```. Portanto, se executarmos no console Javascript a função acima para retornar o valor do quadrado de 12, teremos:
 ```javascript
 console.log(square(12));
 // -> 144
 ```
 É importante destacar que toda função sempre será declarada utilizando a palavra  ```function ```. Também deve-se destacar que uma função pode ter vários parâmetros, ou até mesmo parâmetro nenhum. Um parâmetro nada mais é do que uma "variável temporária", isto é, uma variável que só existirá durante a execução da função e cujo valor será definido durante a chamada da função. No exemplo acima, podemos ver isso claramente: o parâmetro  ```x ``` recebe o valor  ```12 ``` durante a chamada de  ```square() ```.
 
 Exemplificando uma função com vários parâmetros:
  ```javascript
  const power = function(base, exponent) {
    let result = 1;
    for(var i = 0; i < exponent; i++) {
      result *= base;
     }
     return result;
   }
  ```
 A função acima irá calcular uma potência cujos os valores dos parâmetros (```base``` e ```exponent```) receberão seus valores na chamada da função:
```javascript
console.log(power(2, 10));
// -> 1024
```
Já a função abaixo, fará apenas barulho:
```javascript
const makeNoise = function() {
  console.log("Pling!");
};

makeNoise();
// → Pling!
```
Funções como ```makeNoise()``` não possuem retorno, isto é, quando são executadas, após a execução das instruções em seu interior, irão retornar ```undefined```. Similarmente, funções que possuem apenas a palavra ```return```, sem especificar o que será retornado, também irão retornar ```undefined```.

### Variáveis e escopo

Imagine um código como uma cebola. Uma cebola tem uma camada grande, que recobre todas as outras, e então suas subcamadas. Assim como a cebola, o código também possui subcamadas. Chamamos essas subcamadas de **escopo**.

Escopo nada mais é do que um espaço isolado do programa onde as instruções e variáveis declaradas existirão apenas ali dentro. Mas quais atividades da programação geram escopo? As mais comuns são funções, loops e condicionais. Vejamos o código abaixo:

```javascript
let x = 1;

if(true) {
   let y = 2;
   }

console.log(x);
// -> 1

console.log(y);
// -> y is not defined
```
Note que, pela variável ```y``` ter sido declarada dentro de um ```if```, isso gerou um escopo e, portanto, a variável ```y``` existe _apenas_ dentro do escopo, não podendo ser acessada de fora.

E as variáveis declaradas fora do escopo, poderiam ser acessadas dentro dele? Vejamos:

```javascript
let x = 1;

if(true) {
  console.log(x)
  }
  
// -> 1
```
A resposta é: **sim**. Apesar de variáveis declaradas dentro de um escopo não serem vistas fora dele, todas as variáveis declaradas em escopos superiores podem ser acessadas. Neste caso, a variável ```x``` foi declarada no **escopo global**, o qual pode ser acessado de qualquer nível do programa.

Antes de 2015, na versão anterior do JavaScript, apenas funções produziam escopo. Naquela época, para se declarar variáveis, utilizávamos a sentença ```var```. Essa sentença pode ser utilizada até hoje, apesar de não ser muito comum. Ao fazermos uso dela, ela ignora o escopo em que está e passa a pertencer ao escopo global. Vejamos:

```javascript
if(true) {
  var escopo = 'se é var, então é global';
  }
  
console.log(escopo);
// -> se é var, então é global
```

Se usássemos ```let``` no lugar de ```var``` no código acima, teríamos um retorno diferente:

```javascript
console.log(escopo);
// -> escopo is not defined
```

Quando fazemos um loop ```for```, por exemplo, e usamos var, essa variável passará a existir no escopo global, apesar de ser inútil após a execução do loop:

```javascript
for(var i = 0; i < 3; i++) {
  console.log(i);
  }
  
console.log(i)
// -> 5
```

**Em resumo**: variáveis declaradas com ```let``` e ```const``` pertencem ao escopo onde foram declaradas, enquanto ```var``` sempre pertencerá ao escopo global.


### Nested scope

Como já explicado anteriormente, vimos que temos escopos aninhados e hierárquicos. Vejamos a função abaixo:

```javascript
  function bolo(quantidadeDeBolos) {
    function ingrediente(quantidade, unidade, nome) {
      let quantidadeTotal = quantidade * quantidadeDeBolos;
      document.write(`${quantidadeTotal} ${unidade} ${nome} <br>`);
    }
    ingrediente(3, 'xícaras de chá', 'farinha de trigo');
    ingrediente(2, 'xícaras de chá', 'açúcar');
    ingrediente(3, '', 'ovos');
    ingrediente(200, 'mL', 'leite');
    ingrediente(4, 'colheres de sopa', 'manteiga');
    ingrediente(1, 'colher de sopa', 'fermento químico em pó');

  }

  bolo(2);
  // -> 2, neste caso, é a quantidade de bolos que quero. Neste caso, será exibido a quantidade de ingredientes necessário para se fazer dois bolos.
  ```
  
Veja, na função acima, que a variável ```quantidadeDeBolos``` pode ser acessada dentro da função ```ingrediente```, que cria um subescopo. Isso só prova que os escopos sempre poderão acessar as informações dos escopos superiores, e todos os escopos sempre podem acessar o escopo global.

Isso significa que os escopos estão aninhados. Existem vários escopos, um dentro do outro, de forma que eles formam uma "cebola" de escopos. É isso que chamamos de _nested scope_.

Se você não conseguir entender esse conceito de forma completa, uma ótima aula no YouTube explicando pode ser encontrada [neste link](https://www.youtube.com/watch?v=dHYhMP8ESuk).

### Functions as values

