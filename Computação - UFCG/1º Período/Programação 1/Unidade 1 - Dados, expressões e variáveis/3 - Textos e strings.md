### Concatenação

```python3
>>> a = 'Oi, '
>>> b = 'tudo bem, '
>>> c = 'Víctor?'

>>> print(a + b + c)
'Oi, tudo bem, Víctor?'
```

Antigamente, a programação era uma atividade que lidava, basicamente, com números. Com o avanço da tecnologia, no entanto, começou a ser necessário também lidar com caracteres não numéricos, como letras e outros caracteres especiais.

Apesar disso, como podemos ver no exemplo acima, quando utilizamos um operador aritmético de soma, ele funciona com strings. Por que?

Muito simples: chama-se concatenação. O Python sobrepõe todas as strings com o objetivo de formar uma nova string, que é retornada no fim do programa.

Algo semelhante pode ser feito com o operador de multiplicação:
```python3
>>> 'oi' * 10
'oioioioioioioioioioi'
```

Quando multiplicamos um número, por exemplo, ```2 * 3```, é a mesma coisa que ```2 + 2 + 2```. A instrução acima segue o mesmo raciocínio: ```'oi' + 'oi' + ... + 'oi'```.
