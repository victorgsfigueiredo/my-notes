## Números e variáveis

### O que é um literal? Como escrevê-los?

**Literal** nada mais é do que um trecho de código com um valor fixo e específico. Exemplos de literais são ```5```, ```+25```, ```-17```, e por aí vai. 

Temos um literal um pouco diferente, chamado de _número de ponto flutuante_, como ```0.5```. Ele é representado de uma forma diferente na máquina, uma vez que ele não é um inteiro e, inclusive, possui seu próprio tipo em Python, o _float_:

```python3
>>> type(0.5)
<class 'float'>
```

O literal de ponto flutuante é diferente porque não consiste numa sequência ininterrupta de bites para a sua representação. A grosso modo, o número acima seria representado como ```0.101``` em binário (base 2).

### O que são variáveis e atribuições? Como são escritos?

**Variáveis** são nomes que recebem um valor específico, o qual é armazenado na memória e é resgatado sempre que o programa invoca o nome desta variável.

Atribuições nada mais são do que a _declaração de uma variável_, isto é, o processo de escrever a atribuição de um valor a um nome. Abaixo, veremos isso com mais nitidez:

```python3
>>> a = 1
>>> b = -5
>>> c = 6
```

Acima, vemos o processo de atribuição de algumas variáveis. A variável de nome ```a``` recebe a atribuição do valor ```1```. Isso significa que, se digitarmos ```a``` no _shell_ do Python 3, receberemos o retorno ```1```.

### Explique o impacto da ordem da declaração de variáveis.

É impossível invocar uma variável antes de seu valor ser atribuído. O código abaixo, certamente, produzirá um erro:

```python3
>>> print(nome)
>>> nome = 'Victor'
```

Por isso, é de absoluta importância observar a ordem de atribuição de variáveis, bem como o seu uso no programa.

### O que acontecerá com uma variável cujo valor seja uma expressão formada de outras variáveis, caso uma das variáveis usada na expressão mude o seu valor?

O que a pergunta acima está questionando é, no código abaixo, teremos o seguinte:

```python3
>>> x = 3
>>> y = 4
>>> z = x + y
>>> print(z)
7
>>> x = 10
>>> print(z)
# -> ????
```

A resposta é simples:
```python3
>>> print(z)
7
```

Mas fica a pergunta: por que o retorno é 7, sendo que alteramos o valor de ```x```? Simples: a atribuição do valor da variável ```z``` foi feita com o valor que estava presente em ```x``` _naquele momento_, de forma que a simples reatribuição de ```x``` não mudará o valor de ```z```. Se quiséssemos essa alteração, precisaríamos fazer o seguinte:

```python3
>>> x = 3
>>> y = 4
>>> z = x + y
>>> print(z)
7
>>> x = 10
>>> z = x + y #reatribuição de z
>>> print(z)
14
```

### Explique a precedência dos operadores.

Seguem a mesma procedência matemática: **PEMDAS** -> Parênteses, exponenciação, multiplicação e divisão, adição e subtração.

Obviamente, essa procedência pode ser alterada com o uso de parênteses, conforme a vontade do programador.

### Por que a expressão, que deveria representar uma das respostas de uma equação de segundo grau, ```(-b + delta ** 0.5 / 2*a)``` está incorreta?

Porque a procedência está incorreta. A procedência correta seria:
```python3
(-b + delta ** 0.5) / (2 * a)
```
Com os parênteses, esclarecemos que a divisão deve ser feita por último, o que não estava acontecendo antes, uma vez que, quando a precedência não é definida por parênteses e os operadores possuem a mesma precedência, o código é lido da esquerda para a direita, o que não é nosso desejo.
