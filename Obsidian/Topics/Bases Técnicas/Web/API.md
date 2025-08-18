Application Programming Interface
É uma interface que permite a comunicação entre diferentes sistemas.
Geralmente API é utilizada para servir alguma informação para o cliente.

Notas aula (Arquitetura de aplicações API GW, Micro-serviços e outros)


API Gateway / Reserse Proxy - Em uma aplicação existem diversos micro-serviços que precisam ser acessados e quem controla o acesso e as requisições é o API Gateway. 
Dentro do API Gateway existe um cadastro de rotas que define para qual micro-serviço a quesição deve ser redirecionada.
Nessa arquitetura os serviços devem ser independentes e se caso um pare de funcionar os outros vão continuar funcionado, cada um deles deve possuir um banco de dados.
Quando dentro dessa arquitetura um micro-serviço faz uma requisição HTTP para outro micro-serviço sinaliza que é uma requisição síncrona.

O correto a se utilizar é fazer requisições assíncronas, vai existir um um software que permite a comunicação e a troca de informações entre aplicações, sistemas e serviço, chamado massege broker dentro entre esses micro-serviços, ele é responsavel por armazernar as requisições dos micro serviços  e enviar para o micro-serviços de destino.
Ele possui:
	Producer: é aplicação que envia uma mensagem para uma queue(topico) do Message Broker
	Consumer:  é aplicação que consumirá as mensagens que estão presentes na fila.
Se um micro-serviço parar o message Broker vai armazenar as requisições feitas a ele de periodo e enviar assim que ele voltar ao ar.

Proxy: É o usuário acessado a internet onde todas as requisições do usuário passão por ele. Está entre o usuário e a internet
Proxy reverse: entre 


Cookies: A set HTTP_ONLY define que somente requisições HTTP podem ler o cookei, o java Script, front-End não podem ler.
SAMESITE: Se um site terceiro pode usar os cookie do seu site para alterar informações do usuario do site.




### Tipo de API

REST API: 
Representational State Transfer 

API GraphQL:

SOAP: