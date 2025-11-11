
Técnica de explorar a rede interna do alvo e pular para outro computador.
Usando Msfconsole com módulos:
``run autoroute -s 10.10.20.0/24``

Ele vai criar uma rota para a rede interna traves da primeira interface de rede. Para verificar se a rota foi criada, usar o seguinte comando:

``run autoroute -p``

Para não utilizar mais módulos do meterpreter podemos usar um proxy para utilizar ferramentas da nossa própria máquina.

1. Colocar nossa sessão em background
2. utilizar o modulo auxiliar do meterpreter como servidor proxy
``auxiliary/server/sockes4a``
3. Configurar o **/etc/proxychains.conf** para funcionar na mesma porta do módulo auxiliar
4. Utilizar a ferramenta proxychains para interagir com a rede
``proxychains nmap -v $ip``