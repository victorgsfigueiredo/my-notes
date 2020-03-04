## 2.1 Values and Types

Python possui alguns tipos de valores. Para verificar o tipo de um determinado valor, podemos utilizar o _interactive mode_ no console Python através da função ```type(value)```, a qual irá retornar o tipo da informação inserida no lugar de ```value```. Abaixo, listo os principais tipos de valores do Python.

- **INT**: abreviação de integer. É o tipo de dado de um número inteiro.

![Tipo INT](https://i.ibb.co/9g5TkCw/image.png)
- **FLOAT**: é o tipo de dado de um número decimal. Tem esse nome por ser um número "flutuante".

![Tipo FLOAT](https://i.ibb.co/tMSQCjz/image.png)
- **STR**: é a abreviação de string. É um conjunto de letras e caracteres. Geralmente é incluída em aspas simples ou duplas.

![Tipo STR](https://i.ibb.co/R9mT2H9/image.png)

É importante destacar que números devem sempre ser representados sem representações adicionais, de forma a não obtermos um _semantic error_. Um bom exemplo disso é a representação do número 1 milhão. O que aconteceríamos se colocássemos ```1,000,000``` no console Python?

![Retorno de 1,000,000 no console Python](https://i.ibb.co/m4JXRs8/image.png)

Obtemos o retorno ```1, 0, 0```! Isso significa que o Python interpretou o número como uma sequência de integrais. A representação correta de 1 milhão, em código, é ```1000000```.

## 2.2 Variables and 2.3 Variable names and keywords

Uma das atividades mais presentes no cotidiano de um cientista da computação é a manipulação de variáveis. Elas podem ser definidas como a representação de um valor qualquer.

Em Python, declaramos uma variável através de um nome, seguido do operador ```=``` e, então, de seu valor. **Uma variável em Python deve sempre iniciar com uma letra!**

![Representação de variáveis e seus tipos no console Python](https://i.ibb.co/ZV1ZJDr/image.png)

Vejamos abaixo algumas variáveis inválidas declaradas no console Python:

![Variáveis inválidas no console Python](https://i.ibb.co/rQDqPkq/image.png)

```76toblerones``` é uma variável inválida porque começa com um número. Já ```minha@``` não é válida porque ```@``` é um caractere ilegal na declaração de variáveis. Agora a pergunta: por que a variável ```class``` deu erro, sendo que foi declarada corretamente?

Isso aconteceu porque ```class``` pertence a uma lista de keywords reservadas pelo Python e que não podem ser utilizadas como variáveis. [Neste link](https://www.w3schools.in/python-tutorial/keywords/), pode-se encontrar uma lista de todas as keywords reservadas pelo Python.

## 2.4 Operators and operands

Na lista abaixo, observa-se os principais operadores do Python:
- ```+``` -> Operador de adição
- ```-``` -> Operador de subtração
- ```*``` -> Operador de multiplicação
- ```/``` -> Operador de divisão
- ```//``` -> Operador de _floor division_ (explicação logo abaixo)
- ```**``` -> Operador de potenciação

Devemos diferenciar os operadores de divisão e de _floor division_. Vejamos abaixo:

![Diferença entre divisão e floor division - 1](https://i.ibb.co/74ssMyQ/image.png)

A diferença é simples: a _floor division_ fará a divisão normalmente, mas retornará o resultado sem a sua porção decimal. Isso significa que, já que o resultado da divisão é ```0.98333```, o ```.9833``` será ignorado e o retorno será apenas ```0```. Neste outro exemplo, isso fica um pouco mais claro:

![Diferença entre divisão e floor division - 2](https://i.ibb.co/k190QmY/image.png)

