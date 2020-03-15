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

Neste pequeno pedaço do capítulo, é explicado que uma função também pode ser tratada como uma variável. Isso significa que podemos utilizá-la como valor e, até mesmo, como um parâmetro de uma outra função. Isso permite atividades bastante avançadas que, de outra forma, não seriam possíveis.

Este tópico será explorado, essencialmente, no Capítulo 5.

### Declaration notation

Existe um jeito mais fácil de se escrever uma função. Chama-se **declaração de função**:

```javascript
function square(x) {
  return x * x;
  }
```
No caso acima, a palavra ```function``` é usada primeiro e ```square``` é o nome da função, o qual também poderá se comportar como uma variável, conforme dissemos no tópico _Functions as values_. É uma forma menos verbosa, mais fácil e não requer ponto e vírgula após a sua conclusão.

Também oferece outra vantagem:

```javascript
console.log('O futuro diz: ' + future());
// -> 'O futuro diz Olá!'

function future() {
  return 'Olá!';
  }
```
O código acima funciona porque quando uma função é declarada dessa forma, mesmo que seja declarada depois de seu uso, ela será movida para o topo do escopo. Isso é bastante útil porque você não precisa se preocupar com o lugar em que a função será declarada, de forma que você poderá colocá-la no lugar que a faça ter mais significado e deixar o código o mais legível possível.

### Arrow functions

Existe uma terceira forma de declarar funções, além das variáveis e da notação. Ela se chama _arrow function_ e é declarada da seguinte maneira:

```javascrit
const power = (base, exponent) => {
  let result = 1;
  for(let i = 0; i < exponent; i++) {
    result *= base;
    }
  return result;
  };
```
A função acima recebe o nome ```power```, onde ```base``` e ```exponent``` são seus parâmetros. Possuímos a flecha ```=>``` e, em seguida, o corpo da função. 

Podemos ler essa expressão como "_para esses parâmetros, retorne este body_".

Se tivermos funções com apenas um parâmetro, podemos omitir os parênteses. Se ela não tem parâmetro nenhum, colocamos parênteses vazios.

```javascript
const square = x => { return x * x; };

const pling = () => { console.log('pling!'); };
```

Se tivermos apenas um parâmetro e apenas um retorno, podemos ser ainda menos verbosos e omitir o termo ```return```. As duas funções abaixo funcionam e fazem exatamente a mesma coisa:

```javascript
const square1 = x => { return x * x; };

const square2 = x => x * x;
```
Como dito anteriormente, devemos ler esse tipo de função como "_para esses parâmetros, retorne este body_". Portanto, na função ```square2``` acima, lemos "_para o parâmetro x, retorne x * x_".

### The call stack

Vejamos o seguinte programa, que faz algumas chamadas de funções:

```javascript
function greet(who) {
  console.log('Hello, ' + who);
  }

greet('Victor');

console.log('Bye!');
```

Quando a função ```greet()``` é chamada, o compilador pula de onde está para o início da função declarada (linha 2 do código acima). Lá, ele executará o ```console.log```, e, após terminar, voltará para a função e, vendo que não há nenhuma outra função, encerra sua execução. Depois disso, o compilador volta para onde a função foi chamada e continua a executar o programa a partir daquele ponto, sendo que, logo em seguida, ele irá chamar a função ```console.log('Bye!');```.

Esquematizando, teríamos algo como:
```
não está na função
o programa chama a função greet()
  o compilador entra na função
    o compilador executa console.log
  o compilador volta para a função e a encerra
o compilador volta para onde estava e continua de onde parou
não está na função
  o compilador executa console.log('bye!')
não está na função
```

Para fazer tudo isso, o computador precisa armazenar o caminho que ele está percorrendo e para onde precisará retornar, para que assim ele possa fazer a sua execução. O lugar onde ele faz esse armazenamento chama-se **call stack**.

Esse armazenamento ocupa memória do nosso computador. É por isso que, quando fazemos programas que precisam montar um _call stack_ exageradamente grande, o computador retorna um erro como "Call stack exceeded size" ou "Too much recursion". É o que acontece quando pedimos para o computador responder uma das dúvidas mais frequentes da biologia humana:

```javascript
// Quem veio primeiro, o ovo ou a galinha?
function ovo() {
  return galinha();
  }

function galinha() {
  return ovo();
  }

console.log(ovo());
// -> ??
```

No caso acima, se o computador não tivesse um mecanismo de freio devido às suas limitações de memória, ele montaria um _call stack_ infinito. Como isso não é possível, ele retorna o erro que dissemos.

### 

