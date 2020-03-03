## 1.1 The Pyhton programing language

Python é uma linguagem de programação de alto nível, assim como C, C++ e Java, que são outras linguagens de programação bastante famosas. 

Ser uma linguagem de alto nível significa que, antes de ser lida pelo computador, os comandos serão primeiro processados por um **interpretador**, o qual converterá o código para uma linguagem de baixo nível, que a única que o computador consegue interpretar. Isso pode significar uma pequena desvantagem em termos de eficiência do programa.

Entretanto, linguagens de alto nível possuem vantagens enormes se comparadas às suas desvantagens. Entre elas, podemos destacar:

- Facilidade de aprender e programar;
- Redução da quantidade de erros, uma vez que o código é mais claro;
- Maior clareza do código;
- Código mais curto;
- Multiplataforma, o que significa que o mesmo código pode rodar em computadores e sistemas operacionais diferentes, diferentemente das linguagens de alto nível.

### Interpretador e compilador

Em linguagens de alto nível, o _source code_ sempre será processado primeiramente por um **interpretador** ou **compilador**.

- **Interpretador**: o interpretador traduz o programa linha a linha e, conforme o mesmo é traduzido, é executado imediatamente. Ou seja, linguagens de alto nível **interpretadas** executam o programa um pouco de cada vez.
![Representação do interpretador](https://i.ibb.co/z2KBjCh/image.png)
- **Compilador**: o compilador traduz todo o programa antes de sua execução. Dessa forma, o compilador transforma o _source code_ em _object code_, o qual será executado de uma só vez.
![Representação de um compilador](https://i.ibb.co/ChPtkh3/image.png)

**Pyhon é uma linguagem interpretada** porque utiliza um interpretador na tradução de seu código.

### Usando o interpretador

Existem duas maneiras de se utilizar o interpretador em Python: _interactive mode_ e _script mode_.

- **Interactive mode**: neste, você escreve pouquíssimas linhas de código e o interpretador o executa imediatamente. É o método utilizado para a realização de testes e executação de programas que demandem poucas linhas. Na imagem abaixo, podemos ver como seria a representação deste modo dentro do programa.
- **Script mode**: é o mais utilizado. Normalmente, quando você escreve um programa que utiliza muitas linhas de código, o ideal é criar um arquivo terminal em ```.py``` para codificar o seu programa. O programa só será executado caso o arquivo codificado seja executado.
Por exemplo, se criássemos um arquivo chamado ```meuPrograma.py```, ele seria executado no Linux através do terminal com o a sintaxe: ```python meuPrograma.py```.

## 1.2 What is a program?

Um programa nada mais é do que um aglomerado de instruções com um objetivo específico. Existem cinco conceitos fundamentais comuns a todas as linguagens de programação:

- **input**: capturar alguma informação do usuário, como o que é digitado, onde é clicado, etc.
- **output**: mostrar alguma informação na tela do usuário.
- **math**: executar contas matemáticas, como equações, polinômios, etc.
- **conditional**: executar instruções somente se alguma condição pré-estabelecida for satisfeita.
- **repetition**: executar instruções de forma repetida enquanto uma condição pré-estabelecida é satisfeita.

Basicamente, todo e qualquer programa que você já viu na sua vida é um aglomerado das instruções acima. Programas são construídos em blocos, e esses blocos são subdivididos até um nível tão simples que podem ser codificados de uma das formas acima.

## 1.3 What is debugging?

_Debugging_ é a ciência de encontrar e corrigir erros. Isso porque programar, em geral, é uma atividade que tende a causar erros.

Existem três tipos de erros que um programador deve lidar no dia-a-dia:

- **Syntax error**: erro de sintaxe significa que você escreveu um código da forma incorreta e, por isso, o interpretador não é capaz de executar o seu código.
- **Runtime error**: é um erro gerado durante a execução do código, ou seja, não tem nada a ver com a sua sintaxe, mas sim um problema mais profundo. Em programas simples, esse tipo de erro é extremamente raro.
- **Semantic error**: basicamente, é quando você codifica um programa que faz uma coisa diferente daquilo que você estava planejando. Ou seja, o código em si não possui nenhum erro, o erro foi na lógica de programação em si.

Fazer o _debugging_ é uma atividade essencial na vida de qualquer programador, tanto é que alguns programadores consideram programar e debugar a mesma coisa.

## 1.4 Formal and natural languages

- **Natural language**: é a linguagem falada naturalmente, utilizada por todos no dia-a-dia, como português, inglês e espanhol. 
- **Formal language**: é a linguagem utilizada na padronização de alguma coisa, como a escrita de expressões matemáticas e fórmulas químicas.

Enquanto a linguagem natural permite ambiguidades e metáforas, a linguagem formal é extremamente literal. Em um exemplo tosco, quando dizemos em português **"Aquela menina é uma gata"**, entendemos que ela é bonita, apesar das palavras serem diferentes. Em uma linguagem formal, se dissermos que uma menina é uma gata, a sentença seria interpretada de forma literal, classificando a menina como um animal gato fêmea.
