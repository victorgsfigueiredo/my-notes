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

