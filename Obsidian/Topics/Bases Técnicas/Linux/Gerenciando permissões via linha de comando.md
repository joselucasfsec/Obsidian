Funcionamento das permissões para usuários em sistemas linux:
![[Ca.png]]
Essas permissões são definidas utilizando o comando **chmod** que determina quais permissões um usuário tem sobre um arquivo ou diretório.
![[permisaolinux.png]]
## **Chmod**
O comando **chmod**(Change mode) é usado para lidar com permissões de arquivos do sistema linux. Cada arquivo possui um sistema de sinalizadores que indicam quais são as permissões que cada usuário tem para ler ou editar cada arquivo. 
![file:///tmp/.TO6V82/2.png](file:///tmp/.TO6V82/2.png)

A estrutura do comando para definir as permissões é:
	    <span style="color:red">Dono</span> <span style="color:green">Grupo</span> <span style="color:yellow">Usuários</span>
   $ sudo chmod <span style="color:red">7</span><span style="color:green">6</span><span style="color:yellow">5</span> script.sh

Existem também o comando **chown** que define quem é o proprietário do arquivo.
