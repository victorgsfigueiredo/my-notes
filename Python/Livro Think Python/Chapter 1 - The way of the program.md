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
![Representação do interactive mode](link da imagem)
- **Script mode**: é o mais utilizado. Normalmente, quando você escreve um programa que utiliza muitas linhas de código, o ideal é criar um arquivo terminal em ```.py``` para codificar o seu programa. O programa só será executado caso o arquivo codificado seja executado.
Por exemplo, se criássemos um arquivo chamado ```meuPrograma.py```, ele seria executado no Linux através do terminal com o a sintaxe: ```python meuPrograma.py```.

## 1.2 What is a program?


