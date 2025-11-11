# **Expression Language Injection (Spring)**

O Spring é um template do **java** e agora vamos entender como explorar o modelo de template. **Language (EL) injection** é uma linguagem usada para se comunicar com o sistema de template spring. Veremos como a injeção em expressões EL permite que atacantes manipulem comandos arbitrários no servidor, utilizando a capacidade dinâmica da linguagem de expressões.

**O Expression Language é muito similar ao jinja2 onde podemos acessar as classes e seus métodos**
	**jinja2** - {{"lucas".__class__}}
	**Expression Language** - {{"lucas".class}}

Dentro do java também podemos chamar bibliotecas que estejam importadas dentro do programa. Também podemos importar uma subclasse porem é um jeito muito lento pois temos que enumerar cada médoto por vez pois ele não retorna o out put de todos métodos disponíveis.

Para explorar uma aplicação Java é necessário sempre enviar nossas requisições utilizando URL Encode.
	**{{"".class.getMethod()[6]}}**

Porém no Java podemos importar diretamente uma classe para isso vamos usar o {{"".class.forName('classe')}}. A classe que vamos chamar é a runtime:
	**{{"lucas".class.forName('java.lang.Runtime')}}**

Vamos chamar a classe|método **Runtime** porque dentro dela existe a **getRuntime()** que possui o método **exec()** que permite executar comandos dentro do servidor
	**{{“lucas”.class.forName('java.lang.Runtime').getRuntime()}}**
	**{{“lucas”.class.forName('java.lang.Runtime').getRuntime().exec('id')}}**

O comando anterior **não vai retornar o out put** pois é uma requisição assincronia, ela vai deixa o comando executado e vai retornar o PID do processo e um valor de comando concluído oque já torna possível conseguir uma reverse shell.

## **Método usando Notação**

O Express Language possui uma notação que permite pegar o tipo de um dado:
	**T(String)** = class java.lang.String

Assim ele nos permite chamar a Runtime mais facilmente
	T(java.lang.Runtime).getRuntime().exec('id')


[[Exemplo_SSTI_Spring]]
