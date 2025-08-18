Sistemas operacionais hoje em dia trabalham com o sistema de **variáveis de ambiente**.Variáveis de ambiente são valores que são armazenados na memória do computador com objetivo de **configurar** algo. Essa configuração pode ser feita para definição de algo do próprio sistema operacional ou para configuração de um programa. As variáveis funcionam no padrão chave valor
**Para verificar o conteúdo das variáveis de ambiente no linux utilizamos o comando **env**:**

![[env.png]]

Para verificar uma variável especifica o comando **echo $var**
![[env2.png]]
Podemos criar um variáveis de ambiente utilizando o comando **export**:
```$ export TREINAWEB="/tmp/temporario"```

## **Variáveis de sessão, usuário e sistema**

Uma **variável de sessão** é declarada como comando **export** e ela é valida somente enquanto o terminal estiver ativo assim que ele é fechado a variável deixa de existir
	```export TREINAWEB="/tmp/temporarios_tw"```

Uma **variável de usuário** vai ser valida somente para o usuário que ela foi criada e não vai existir para outro usuário. Vamos declarar a variável dentro de um arquivo que é executado toda vez que o shell é executado, ele fica dentro do diretório do usuário e se chama **.bashrc**
	```$ nano /home/lucas/.bashrc```

Para declara uma **variável de sistema** vamos declara ela dentro do diretório **/etc** no arquivo **bash.bashrc**
	```$ sudo nano /etc/bash.bashrc```