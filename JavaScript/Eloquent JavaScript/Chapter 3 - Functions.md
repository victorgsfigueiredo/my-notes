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

```javascript
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

### Optional arguments

Vejamos a função abaixo:
```javascript
const square = x => x * x;

console.log(square(5, 'hello world', 10);
// -> 25
```

O código acima funciona perfeitamente. Veja: a função ```square()``` tem apenas um parâmetro definido, ```x```, mas na sua chamada, são dados três argumentos. Por que, então, funciona?

O JavaScript é um grande camarada. Ele simplesmente irá ignorar os argumentos extras dados, utilizando apenas o primeiro. De forma semelhante, se um parâmetro estiver definido mas não for dado um valor a ele, o JavaScript irá, de forma automática, atribuir ```undefined``` a esse parâmetro:

```javascript
console.log(square());
// -> NaN
```

No exemplo acima, obtemos ```NaN```, porque ```undefined * undefined``` é ```NaN``` (not a number).

O que falamos é muito útil, uma vez que o JavaScript pode simplesmente ignorar argumentos extras e atribuir ```undefined``` a argumentos faltantes. Mas pode existir um ponto negativo: quando você comete um deslize e declara um argumento a mais, ou até mesmo se deixa de declarar um argumento, vai ser muito difícil você localizar esse erro, uma vez que a própria linguagem faz essa atribuição para gente. Acima, no ```square()``` sem argumento, obtivemos ```NaN``` que não é, necessariamente, um erro.

Também existe uma funcionalidade muito útil: **se você utiliza ```=``` após um parâmetro durante a declaração da função seguido de uma expressão, essa expressão será atribuída ao parâmetro caso ele não seja declarado**.

Por exemplo:

```javascript
function power(base, exponent = 2) {
  let result = 1;
  for(let i = 0; i < exponent; i++) {
    result *= base;
    }
  return result;
  }
```

Se agora utilizarmos o 2 quando não recebermos o parâmetro, obteremos:

```javascript
console.log(power(2, 3));
// -> 8

console.log(power(2));
// -> 4
```
No primeiro exemplo, como atribuímos ```3``` ao parâmetro ```exponent```, a potência foi executada corretamente. Entretanto, no código abaixo, não declaramos um expoente. Mas, como deixamos uma instrução na função dizendo que, _caso não haja a declaração de um parâmetro, atribua 2_, ele faz a potência e se comporta como a função ```square()```, fazendo ```2 ^ 2```.


### Closure

Vejamos o código abaixo:

```javascript
function wrapValue(n) {
  let local = n;
  return () => local;
  }

let wrap1 = wrapValue(1);
let wrap2 = wrapValue(2);

console.log(wrap1());
// -> 1

console.log(wrap2());
// -> 2
```

Perceba que há uma função que retorna uma função, a qual fica armazenada em uma variável. Mas agora vem a pergunta: como a função ```wrap1()``` consegue acessar a variável ```local```, sendo que ela é uma função diferente e ```local``` está declarada em um escopo diferente?

A resposta é um pouco complicada, mas vamos lá: quando você chama uma função, ela cria um escopo próprio. No entanto, quando ela é criada dentro de outro escopo, no momento em que ela é chamada, ela passa a ter acesso também ao escopo onde foi declarada. Isto é, **a função não acessa o escopo onde é chamada, e sim onde foi criada**. Essa capacidade, portanto, de acessar variáveis locais de um escopo diferente chama-se _closure_.

No caso acima, temos uma função que retorna uma função, e quando a função retornada é chamada, ela cria um escopo **dentro do escopo local** da função que a retorna. Talvez seja complicado entender na primeira vez, mas se ficares com dúvida, releia até entender.

### Recursion

Imagine uma função que chame a si própria. Isso é possível e perfeitamente razoável de ser feito. Quando uma função chama a si mesmo, a chamamos **função recursiva**.

Vejamos abaixo uma alternativa recursiva para a função ```power()```:

```javascript
function power(base, exponent) {
  if(exponent == 0) {
    return 1;
  } else {
    return base * power(base, exponent - 1);
  }
}

power(2, 4);
// -> 16
```

A forma recursiva da função ```power``` se aproxima muito mais da forma como matemáticos veêm potências. Logo, podemos dizer que as alternativas recursivas aos loopings são muito mais elegantes e lógicas para os seres humanos. Dito isso, por que não utilizamos a recursão para tudo?

Porque a recursão pode ser até 3 vezes mais demorada do que um simples loop. Isso gera uma certa discussão: o programa deve ser mais amigável aos humanos ou mais amigáveis às máquinas (eficiente)? Essa pergunta deve ser respondida pelo programador que está codando, ao qual caberá equilibrar esses dois pontos.

Obviamente, a recursão não é apenas uma alternativa ruim aos loops. Existem problemas que realmente são melhor resolvidos através da recursão. Veja o desafio abaixo:

_By starting from the number 1 and repeatedly either adding 5 or multiplying by 3, an infinite set of numbers can be produced. How would you write a function that, given a number, tries to find a sequence of such additions and multiplications that produces that number?_

E a resposta a esse desafio:

```javascript
function findSolution(target) {
  function find(current, history) {
    if (current == target) {
      return history;
    } else if (current > target) {
      return null;
    } else {
      return find(current + 5, `(${history} + 5)`) ||
             find(current * 3, `(${history} * 3)`);
    }
  }
  return find(1, "1");
}

console.log(findSolution(24));
// → (((1 * 3) + 5) * 3)
```

Entender como o código acima funciona pode ser complexo em uma primeira olhada, mas conforme o estudamos, começamos a entender ele. Para facilitar nossa compreensão, vamos editar o seguinte trecho do código acima, adicionando um ```console.log```:

```javascript
// [...]
function findSolution(target) {
  function find(current, history) {
    console.log(`${current} é o current. ${history} é o history.`);
    if (current == target) {
      return history;
// [...]
```

O que o console nos exibiria? Veja:

- 1 é o current. 1 é o history.
- 6 é o current. (1 + 5) é o history.
- 11 é o current. ((1 + 5) + 5) é o history.
- 16 é o current. (((1 + 5) + 5) + 5) é o history.
- 33 é o current. (((1 + 5) + 5) * 3) é o history.
- 18 é o current. ((1 + 5) * 3) é o history.
- 3 é o current. (1 * 3) é o history.
- 8 é o current. ((1 * 3) + 5) é o history.
- 13 é o current. (((1 * 3) + 5) + 5) é o history.

"(((1 * 3) + 5) + 5)"

Ou seja, o código teve que executar vários "galhos" (branches) diferentes para conseguir encontrar um resultado. Primeiro ele começou com adições de 5 e, quando chega em um número grande demais, ele substitui a última adição por uma multiplicação por 3, e assim faz até conseguir encontrar uma solução.

### Growing functions

Um dia, um fazendeiro resolve contratar os seus habilidosos serviços de programação porque ele deseja criar um programa que mostre o inventário de animais da fazenda dele em uma página, e disse a você que o número deve conter sempre 3 casas. Isto é, ele gostaria que você construísse um programa que fizesse o seguinte _output_:

```
009 Vacas
012 Galinhas
```

Após discutir o contrato e seus valores, vocês chegam a um acordo e, então, você passa a produzir o programa. Como resultado final, você obtém:

```javascript
function inventarioFazenda(vacas, galinhas) {
  let vacasString = String(vacas);
  while(vacasString.length < 3) {
    vacasString = '0' + vacasString;
  }
  console.log(`${vacasString} Vacas`);
  
  let galinhasString = String(galinhas);
  while(galinhasString.length < 3) {
    galinhasString = '0' + galinhasString;
  }
  console.log(`${galinhasString} Galinhas`);
}

inventarioFazenda(9, 12);
```

Funciona perfeitamente e o fazendeiro fica feliz da vida com seu programa complexo e longo. Entretanto, menos de uma semana depois, o fazendeiro resolveu comprar 16 porcos e pede a você para que inclua os porcos no programa.

Você, então, tem duas opções:

1) Você percebe que a função que mostra o inventário tem um código praticamente igual para cada animal e, então, você copia e cola essa parte repetida, mudando os nomes para 'porcos' e adicionando o parâmetro 'porcos' à declaração da função; ou
2) Você percebe que essa se trata de uma **growing function**, porque a cada vez que você precisa adicionar um novo animal, você precisará repetir o código, então você resolve refazer o programa para que não seja mais necessário alterar o código sempre que desejar adicionar um novo animal.

Você, como o ótimo programador que é, escolhe a opção 2. Não apenas porquê dará menos trabalho, mas porque você também imagina outras situações: e se o fazendeiro resolver comprar 1000 pintinhos, como eles serão mostrados na lista com até 3 dígitos? Você precisa de um programa pouco repetitivo e mais flexível.

A habilidade de perceber padrões e refazer o código para armazenar esse padrão de código numa função é uma habilidade que todo desenvolvedor de software deve possuir para ser ótimo. Você chega a essa conclusão e bola a seguinte solução:

```javascript
function animalFazenda(numero, nome, tamanhoDoNumero) {
  let numeroString = String(numero);
  while(numeroString.length < tamanhoDoNumero) {
    numeroString = '0' + numeroString;
  }
  document.write(`${numeroString} ${nome} <br>`)
}

animalFazenda(9, 'Vacas', 3);
animalFazenda(12, 'Galinhas', 3);
animalFazenda(16, 'Porcos', 3);
```

Com esse código, você agora pode adicionar quantos animais quiser, e ainda pode definir número de casas que será mostrado no final! Esse, certamente, é um código muito melhor do que o primeiro.

A habilidade de reconhecer padrões e adequar o código para que fique mais legível e conciso deve ser sempre desenvolvida com afinco pelo desenvolvedor.
