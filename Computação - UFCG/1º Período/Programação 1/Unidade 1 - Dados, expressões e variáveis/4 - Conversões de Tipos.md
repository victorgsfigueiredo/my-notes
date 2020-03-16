### Conversões implícitas

Quando estamos fazendo uma operação matemática que envolva um inteiro e um ponto flutuante, a CPU não consegue fazer essa operação porque operações só podem ser feitas com valores do mesmo tipo. É por isso que, quando se quer fazer a soma ```3 + 2.5```, a CPU tem duas alternativas:

- Converter o segundo número para um dado do tipo ```int```, ficando portanto ```3 + 2```, resultando em ```5```.
- Converter o primeiro número para um dado do tipo ```float```, ficando ```3.0 + 2.5```, resultado em ```5.5.

Obviamente o segundo jeito é o mais correto e, por isso, é o mais utilizado pelo Python.

Entretanto, existem situações em que queremos forçar um tipo de dado.

### Conversões explícitas

Quando queremos forçar uma conversão, podemos simplesmente usar as funções ```int()```, ```float()``` e ```str()```. O parâmetro passado a elas será forçado a ser convertido no tipo apontado.

```python3
>>> int(2.9)
2

>>> str(2.9)
'2.9'
```

### Divisão _float_ ou _int_?

Antes do Python 3, normalmente todas as divisões **sempre** retornavam inteiros. Isso, é claro, gerava uma série de confusões. É por isso que, a partir do Python 3, a divisão sempre retornará um dado do tipo _float_: ```6 / 2 = 3.0```. Se você desejar, poderá utilizar o operador ```//``` para divisões inteiras.

```python3
>>> 6 / 2
3.0

>>> 6 // 2
3
```
