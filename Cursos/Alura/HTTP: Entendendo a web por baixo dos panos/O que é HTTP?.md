## HTTP

É a abreviação de **Hypertext Transfer Protocol**. Se você consegue ler essas anotações, é porque é capaz de ler em português. Podemos dizer que nós estamos nos comunicandoa através do **protocolo** português. Obviamente, os navegadores e servidores não falam português. Para se comunicarem, eles utilizam uma língua diferente, o HTTP.

Podemos também dizer que o HTTP funciona como a interface de comunicação para o canal **Cliente-Servidor**. Dito isso, o HTTP também define quais são as regras que essa comunicação deve seguir.

Obviamente, o HTTP não é o único protocolo de comunicação da internet, apesar de ser, de longe, o mais popular. Por exemplo, o torrent utiliza o protocolo **P2P**, onde o foco não é a comunicação Cliente-Servidor, como no HTTP. No P2P, cada usuário da rede assume uma pequena fração do processamento do servidor, aumentando a velocidade e, por muitas vezes, eliminando a necessidade de um servidor físico, como no HTTP.

No curso da Alura, é exemplificado como a estrutura da Alura está montada:

![A estrutura da Alura](https://s3.amazonaws.com/caelum-online-public/http/arquitetura_alura.png)

O cliente (navegador) se comunica, através do HTTP, com o Apache Tomcat, um servidor baseado em Java que é responsável por receber e interpretar as requisições do cliente. Também se comunica com o MySQL através do SQL, para guardar e resgatar dados de seus clientes e cursos.
