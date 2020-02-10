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
