Gopherus é uma ferramenta para auxiliar na criação de payloads para exploração de SSRF. Ele cria payload apartir do protocolo gopher:
## Protocolo Gopher
É um protocolo antigo que funciona somente em texto, sem imagens ou conteúdo multimídia. Ele também
é um protocolo “puro” sem a necessidade de especificar padrões de comunicação como HEADER, basta se conectar e enviar o texto.
Para o protocolo Gopher funcionar é necessario que no servidor esteja rodando **Curl** ou **libcurl** do php, para executar nosso payload. Não funcionar se estiver utilizando file**_get_contents(**http://youtube.com**)**

#### Gopherus
Utilizamos  gopherus para explorarmos serviços internos como **mysql, redis, fastcgi (php-fpm), zabbix, memcached** utilizando o protocolo **gopher**. 
O gopherus vai criar um payload encodado de URL encode para enviarmos no campo de dados do protocolo gopher. 
![file:///tmp/.OZAVB3/1.png](file:///tmp/.OZAVB3/1.png)
Caso o parâmetro vulnerável seja sendo passado via **GET** é necessario fazer **duble-URL-encode**, para que quando chegar no curl da rede interna seja executado nosso payload encodado. 
Caso nosso payload não chegue encodado o curl não consegue interpretar os **null bytes** e não vai executar o payload. Quando o PHP recebe o conteúdo do parâmetro ele automaticamente faz **urldecode**