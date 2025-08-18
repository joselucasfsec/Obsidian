  
Servidor: disponibiliza algum serviço para o cliente
Cliente: Utiliza algum serviço disponibilizado pelo servidor

Responsabilidades das camadas:
	Aplicação --> Software
	Transporte --> Sistema operacional
	Redes        --> Sistema operacional
	Link de dados --> Hardware
	Física --> Hardware

PDU(Protocol Data Unit)
	Estrutura de dados gerada em uma camada, ela vai ser enviada para a camada abaixo dela.

Camada de aplicação
Na camada de aplicação estão presentes os protocolos de aplicação que são linguagens de comunicação usadas pelo software da máquina para sem comunicar com a rede. Esses protocolos podem ser HTTP, FTP, SNMP, POP3 entre outros.
 A PDU da camada de Aplicação é a Mensagem.

Camada de Transporte
	   Recebe a mensagem da camada de aplicação e encapsula a mensagem em uma estrutura de dados própria. Essa estrutura é determinada conforme o protocolo utilizado na camada de transporte o TCP(Transmission Control Protocol) e UDP(User Datagram Protocol).
Diferenças
	TCP é orientado a conexão ou seja precisa de estabelecer uma conexão para a troca de dados e é confiável. Ele é um protocolo mais complexo. Seu PDU é chamado Segmento TCP.
	UDP é sem conexão ou seja não estabelece uma conexão para começar a enviar dados e se torna não confiável. Ele é um protocolo mais simples. Seu PDU é chamado Datagrama UDP.
A camada de transporte é responsável por adicionar no cabeçalho a porta de origem e a porta de destino.

Camada de rede
	É considerada o coração do modelo TCP/IP pois permite ligar redes diferentes
	mantendo o uso da mesma pilha de protocolos.
	O equipamento de rede roteador trabalha nessa camada ele permite a comunicação entre redes diferentes.
	Seu principal protocolo é o IP(Internet Protocol), protocolo de comunicação entre redes ou simplesmente protocolo de rede. Ele possui duas versões IPV4 e IPV6 e seu PDU é Datagrama IPv4 e Datagrama IPv6 sem conexão e sem confiança pois precisamos que esses data grama sejam rápidos afinal ele passa de roteador em roteador até chegar no destino.
	O Datagrama IP vai encapsular o segmento TCP ou Datagrama UDP ou seja vai colocar ele dentro da sua área de dados.
	Também existe o protocolo IPsec que adiciona criptografia e autenticação ao protocolo IP.
	Na camada de rede existem também protocolo internos para informar mensagem de controle, confirmação, estado entre uma máquina e outra, como o ICMP(Internet Control Message Protocol), IGMP(Internet Group Message Protocol) as mensagens desse protocolo são encapsuladas diretamente no Datagram IP sem segmento TCP ou datagrama UDP
	O sistema de endereçamento utilizado na camada de rede é o Endereçamento lógico é um endereçamento de software que identifica cada maquina presente na rede.
	Também temos o endereçamento físico gerado pela camada de enlace que é sistema de hardware que também identifica cada máquina na rede.
	Diferenças:
		Endereço lógico: endereçamento de software, opera na camada de rede, atravessa roteadores.
		Endereço físico: endereçamento de hardware, Opera na camada de link de dados, não atravessa roteadores, Só vale dentro de uma mesma rede.
	Na pilha TCP/IP os endereços lógicos  são endereços ip

Camada Link de Dados | Enlace
	Controlada pelo hardware e seu funcionamento vai depender da arquitetura de rede utilizada.
	  O primeiro papel dessa camada é fazer o controle de acesso ao meio.
	   Existem duas abordagens principais para o Controle de Acesso ao Meio: Controle de Acesso  ao Meio Distribuído (CSMA/CD) e Controle de Acesso ao Meio Centralizado.
	   Redes Ethernet vão usar o método de contenção e o algoritmo:
	1. **CSMA/CD (Carrier Sense Multiple Access with Collision Detection):**
	- **Carrier Sense (CS):** As estações verificam se o meio de transmissão está livre antes de transmitir dados.
	- **Multiple Access (MA):** Várias estações têm acesso ao meio compartilhado.
	- **Collision Detection (CD):** Se duas estações transmitirem simultaneamente e ocorrer uma colisão, elas podem detectar a colisão e interromper a transmissão. Em seguida, um algoritmo de recuperação é usado para retransmitir os dados.
	Essa abordagem é comumente associada a redes Ethernet tradicionais, mas não é tão utilizada em redes modernas devido à predominância de comutadores (switches) que operam em modo full-duplex, onde as colisões são menos prováveis.
    Redes WI-FI vão usar o método de contenção e o algoritmo:
	Controle de Acesso ao Meio na camada de enlace é crucial para garantir a eficiência e a ordem nas transmissões de dados em redes locais, evitando colisões e garantindo que várias estações possam compartilhar o mesmo meio de comunicação de maneira ordenada.

   Outro papel importante dessa camada é gerar um PDU compatível com o hardware de rede, essa PDU vai ser chamada Quadro(tamanho variável) ou Célula(tamanho fixo).
   Essa camada vai receber o datagrama IP da camada acima e vai colar dentro do seu quadro que se chama MTU(Maximum Transmition Unit).
   A camada de enlace usa o tipo de endereçamento físico(MAC) só valido dentro da mesma rede.

Camada física
	Definida pelo hardware da maquina e o funcionamento depende da arquitetura de rede sendo usada. A camada física codifica e modula o quadro (ou célula) para que ele possa ser enviado ao meio.

O processo de desencapsulamento
	

Endereçamento IPV4
	O coração do modelo TCP/IP é o endereçamento lógico(endereçamento IP) ele que permite que computadores em localizações diferentes se comuniquem. Quando um pacote é enviado pelo endereçamento lógico ao chegar na rede de destino ele é descapsulado o endereço lógico é convertido em endereço físico e entregue ao dispositivo de destino.
	A principal vantagem do endereçamento IP é que não precisamos saber o endereço físico do dispositivo de destino. Os protocolos reesposáveis por converter esses endereços são ARP(Address Resolution Protocol), RARP(Reverse Address Resolution Protocol) e NDP no IPv6.

Endereço Físico vs Endereçamento lógico

Endereço Físico 
	Todos os dispositivos conectados a internet recebem um endereço físico que em arquiteturas ethernet e Wifi é chamado de endereço MAC, ele está disponível só na rede local.

Endereçamento lógico
	Usado para acessar computadores que não estão na mesma rede.


Protocolo ARP e RARP
	ARP(Address Resolution Protocol) sabemos o endereço lógico, queremos saber o endereço físico.
	RARP(Reverse Address Resolution Protocol) sabemos o endereço físico queremos saber o endereço lógico. 
	Quando uma máquina quer se comunicar com outra maquina na rede ela lança um ARP pacote broadcast perguntando quem possui o endereço físico de destino, a máquina de destino vai preencher esse pacote com seu endereço físico e vai devolver para a maquina 
	de origem para que possam se comunicar.
	O RARP não é mais usado suas funcionalidades foram substituídas pelo protocolo DHCP.
	O protocolo DHCP(Dynamic Host Configuration Protocol) é encontrado no roteador da rede é responsável por atribuir automaticamente configurações de rede, como endereços IP, máscaras de sub-rede, gateways padrão e servidores DNS, aos dispositivos que se conectam à rede.


Tipos de Endereço IPv4
	## Unicast: Identifica uma única máquina(roteadores, dispositivos, hosts, nó, estação). Quando dizemos "endereço IP", normalmente estamos nos referindo a um endereço Unicast.	
	## Broadcast: Identifica todas as máquinas da rede. Datagramas enviados a este endereço são transmitidos a todas as máquinas da rede.      
    ## Multicast: Endereços de um grupo de máquinas. Todas as máquinas do grupo recebem datagramas enviados àquele endereço. Ex protocolos de roteamento. Gerenciado através do protocolo IGMP(Internet Group Management Protocol).
	## Anycast: Permite mais de uma máquina utilizar o mesmo endereço IP. Usado para o cliente acessar a máquina que estiver mais perto. Não suportado nativamente pelo IPv4 é implementado via protocolo BGP. Ex CDN(Content Delivery Network). Servidores espalhados pelo mundo e você acessa aquele mais próximo a você, todos respondendo no mesmo endereço IP.
	                                                                        s
Endereço IPv4 é um endereço de 32bits de comprimento com grupos de 8bits convertidos para decimal(255.255.255.255)variando entre 0 a 255.
Esses 32 bits são divididos em duas partes uma para identificar a rede e outra para identificar a máquina. Endereços IP que não tenham o campo 'Identificação da rede igual' não funcionara nesta rede. Para conectar redes diferentes é necessário  um roteador para conectar redes diferentes.

A quantidade de bits que identificam rede pode ser alterado e existem dois Métodos de confi-
guração.
1) Sistema de classes(classful)
	Não é mais utilizado desde 1993. Esse método divide os endereços IPv4 disponíveis em 
	cinco classes ou faixas. O número de bits usado para identificar a rede depende da classe (faixa) do endereço IP.  A desvantagem desse método é que só há três configurações possíveis para o campo 'identificação da rede': 8,16,24 bits.
 2) Sistema em classe(classless)
	 Método atualmente utilizado. Configuramos manualmente quantos bits do endereço IP são usados para identificar a rede e quantos bits são usados para identificar a máquina(host).
	 Essa configuração pode ser feita de duas formas:
	Máscara de rede(máscara de sub-rede) ou CIDR(Classless Inter-Domain Routing).	 
	Máscara de Rede
	Mais usada na configuração de máquinas em uma rede. É uma informação adicional, configurada em separado, o endereço IP não é alterado. É um número de 32 bits onde colocamos em "1" os bits de identificação da rede(números a esquerda) e em "0" os bits de identificação da máquina(números a direita.
	CIDR
	Mais usado em tabelas de roteamento e divisão de blocos de endereçamento IP. É uma informação adicional, configurada em separado, o endereço IP não é alterado. Indicamos, em decimal, a quantidade de bits utilizada para identificar a rede, precedida de de uma barra(/).

Números de redes e máquinas
	Aumentando o número de bits de identificação de rede:
		Aumentamos o número de redes disponíveis
		Diminuímos o número de máquinas por rede
	Diminuindo o número de bits de identificação de rede:
		Diminuímos o número de redes disponíveis
		Aumentamos o número de máquinas por rede

O primeiro endereço IP de uma rede é reservado para identificar a rede Ex: 192.168.0.0
O ultimo endereço IP da rede é reservado para o endereço de broadcast Ex: 192.168.0.255
Para descobrir o número de endereços IP disponíveis só elevar o 2 ao número de bits e subtrair 2.

Máscara de rede e CIDR
	Máscara de rede: 255.0.0.0 (CIDR/8 - Class A)
		Ex: 10.0.0.0/8
	Máscara de rede: 255.255.0.0 (CIDR/16 - Class B)
		Ex: 172.16.0.0/16
	Máscara de rede: 255.255.255.0 (CIDR/24 - Class C)
		Ex 192.168.0.0/24

Para descobrir o número de endereços IP disponíveis primeiro precisamos converter para binário:
	172.16.23.0/22 = 11111111.11111111.11111100.00000000
	Convertemos esse número de binário para decimal para descobrir sua mascara de rede:
	255.255.252.0
	Para descobrir o número de endereços IP disponível precisamos converter a mascara de rede para binário:
	255.255.252.0 = 10101100.00010000.001000 00.00000000
	Os últimos 12 bits vão ser o número de identificação da máquina:
	10101100.00010000.001000 11.11111111 = 172.16.35.255

Exemplo: Rede 200.147.11.3/22 fazendo as conversões descobrimos que esse endereço é de uma máquina dentro da rede 200.147.8.0. Pois se convertermos o endereço para binário ele retorna:
200.147.11.3/22 = 11001000.10010011.00001011.00000011
Os bits que identificam a máquina não estão em zero então sabemos que esse endereço IP não identifica a rede e sim uma máquina na rede. Pois identificamos o endereço da rede colocando todos os  bits da máquina em zero.
11001000.10010011.00001 00.00000000 = 200.147.8.0/22 é o endereço da rede.
200.147.11.3 é um endereço unicast.
Podemos usar anotação CIDR para identificar endereços unicast usando /32:
200.147.11.3/32

Exemplo: A rede 169.17.35.0 com a máscara de rede: 255.255.233.0 se convertermos para binário:
11111111.11111111.11101001.00000000
Vemos que temos "1" a direita oque o torna invalida

Exemplo: O endereço 169.17.35.0 com a mascara 255.255.224.0 significa oque?
Primeiro convertemos a mascara de rede para binário:
	11111111.11111111.11100000.000000
Temos uma mascara de rede valida /19. Se convertemos o endereço IP para binário temos:
	10101001.00010001.00100011.00000000
Podemos ver que esse endereço IP não é o endereço que identifica a rede(primeiro endereço).
Esse endereço é de uma máquina dentro da rede(endereço unicast).
Para descobrir a qual rede esse endereço IP pertence precisamos colocar os bits que identificam a máquina em zero então "19" bits em 1 e 13 bits em 0 e converter para decimal:
	169.17.32.0
Esse é o endereço da rede 169.17.32.0/19-169.17.63.255

Podemos utilizar calculadoras CIDR para descobrir a faixa da rede.

Blocos de endereços IPv4
  Uma empresa pode receber um bloco de endereços IP e dividir em faixas de IP menores. Essa segmentação de endereços IP é chamada de VLSM(Variable-Length Subnet Masking).
  Adicionando um bit a máscara de rede criamos uma sub-rede.

Agregação de rotas
   Vamos pegar diversas redes menores e criar um único endereço IP para acessar todas essas redes menores. O objetivo dessa agregação é otimizar a tabela de roteamento.

Máscara coringa(Wildcard mask)
  Permite criar um filtro para endereços IP. Criamos uma mascara que só vai aceitar endereços IP que atendem o filtro. Vamos definir os bits que queremos que variem e oque não podem variar.
Exemplo: Criar filtro para dar "match" com endereços 192.168.10.x:
Endereço padrão: 
	192.168.10.0 = 11000000.10101000.00001010.00000000
Máscara:
	0.0.0.255 = 00000000.00000000.00000000.11111111
Só endereços dentro de 192.168.10.0 - 192.168.10.255 vão dar match

Classes
	Sistema de classes utilizado na década de 80 e não é utilizado hoje em dia. Era utilizado um sistema de classe a, b, c, d, e onde os primeiros bits determinavam a classe 
	Classe A - 0        | 0.0.0.0     | /8
	Classe B - 10      | 128.0.0.0 | /16
	 Classe C - 110   | 192.0.0.0 | /24
	 Classe D - 1110 | 224.0.0.0 | Multicast
	 Classe E - 1111  | 240.0.0.0 | reservada

Endereços IPv4 Especiais
	0.0.0.0/8 == Indica a rede local
	127.0.0.0/8 == Endereçamento de realimentação(loopback)
	10.0.0.0/8 =>
	172.16.0.0/12 == Endereçamento privado
	192.168.0.0 =>
	169.254.0.0/16 == Zeroconf/APIPA
	198.18.0.0/15 == Equipamentos para teste de rede
	192.0.0.0/24 =>
	224.0.0.0 == Reservado
	240.0.0.0 =>

Endereços IPv4 Público e Privado
	Endereços IP privados estão disponíveis somente na rede interna, e endereços IP Públicos são usados na rede mundial de computadores. A organização responsável por distribuir esses endereços é a IANA(Internet Assigned Numbers Authority) ela cria os blocos de IP e distribui para cada região(continente) a responsável pela América do Sul é a LACNIC. Dentro do Brasil, é a NIC.br quem controla a distribuição de endereços IP públicos.
	Para utilizar a internet recebemos um IP público do nosso provedor de internet e utilizamos um método de tradução de endereços NAT(Network Address Translation)

NAT(Network Address Translation)
	Tradução de endereços IP privados em IPs públicos. Quando um endereço privado deseja enviar um datagrama para fora da rede interna o roteador vai alterar o campo do endereço de origem no datagrama IP pelo endereço IP público configurado no roteador.
	O roteador possui duas portas a LAN para a rede interna e a WAN para o endereço Público.
	Geralmente o roteador possui um endereço público para toda a rede interna ou seja todo datagrama que chegar vai ter o mesmo endereço IP então como o roteador vai saber para qual máquina entregar o datagrama, existem duas soluções:
	NAT dinâmico o nosso roteador vai ter mais de um endereço Público configurados na porta WAN, cada endereço público recebe um endereço IP privado para enviar os datagramas recebidos, o problema é que só podemos ter o número de conexões com internet baseado na quantidade de endereços públicos da porta WAN ou seja se existir só 4 endereços Públicos na porta WAN só podemos ter 4 conexões com a internet. Os endereços IP privados podem está em conexões com endereços IP públicos diferentes uma solução é usar endereços NAT estáticos: força a conversão de um endereço IP privado sempre no mesmo endereço IP público dentro do sistema NAT dinâmico.
NAT overload(PAT)
	Tradução de endereço de porta esse endereço permite utilizar apenas 1 endereço IP Público, resolve o problema do roteador receber os datagramas da internet com o mesmo endereço de destino.
	O roteador agora também vai manipular os campos porta de origem e porta de destino do datagrama IP, esses campo ficam dentro do segmento TCP ou datagrama UDP na Camada de transporte. O roteador recebe no datagrama IP o segmento ou datagrama e ele sabe onde encontrar os campos porta de origem e porta de destino dentro da sua área de dados.
	FUNCIONAMENTO:
	O roteador recebe o datagrama IP e altera o endereço IP privado para público e gera uma porta que vai identificar a máquina de origem.
		LAN                                  WAN
		192.168.0.5:10000  ===  200.123.123.123:50000

DHCPv4(Dynamic Host Control Protocol para IPv4)
	Toda máquina conectada a rede TPC/IP precisa receber um endereço IP e alguns parâmetros:
	Endereço IP, Servidor DNS, Máscara de rede e Gateway padrão. Cada um deles pode ser configurado manualmente porem em redes com diversas máquina se torna inviável a configuração manual.
	A solução para para isso é o servidor DHCP ele distribui a configuração para as máquinas na rede automaticamente. DHCP é um protocolo da camada de aplicação.
	Ele pode ser configurado Manualmente, Dinamicamente a máquina solicita um endereço IP  esse pode variar cada vez que a máquina se conecta a rede esse endereço possui um período em que ele garantido a aquela máquina quando ele espira ela pode ou não receber o mesmo IP e na configuração Automática o DHCP tenta entregar sempre o mesmo endereço IP e por fim a Estática o gerente da rede configura para alguma máquina sempre receber o mesmo endereço IP.
	Ele funciona no protocolo UDP da camada de transporte Porta 67 (Servidor) 68 (cliente).
	FUNCIONAMENTO:
	 A máquina envia um DHCPDISCOVERY(Broadcast) para 255.255.255.255 pois não sabe qual rede ele está conectado, o servidor DCHP responde com DHCPOFFER e os parâmetros de configuração, a máquina escolhe o servidor DHCP que ela vai se conectar e envia pra rede um DHCPPREQUEST o servidor escolhido responde com DHCPACK confirmando que aceitou e passou as parâmetros e a máquina já está configurada.
	Existem outras duas mensagens DHCPRELEASE onde o administrador da rede solicita o endereço IP que uma máquina está utilizando assim a máquina fica sem endereço IP podendo receber outro endereço. E a outra mensagem DHCPINFORM pedindo informações.
	Quando uma máquina Windows tem algum problema na comunicação com o servidor DHCP a máquina é configurada automaticamente com endereços do Zeroconf/APIPA 169.254.0.0/16


Endereçamento IPv6
	Esse sistema de endereçamento foi criado para resolver o problema de exaustão de endereços IPv4, além disso, o sistema de endereçamento IPv6 traz várias melhorias.
	Ele é um endereço de 128 bits com 2 elevado a 128 endereços disponíveis.
	É representado em hexadecimal com oito blocos de 16 bits(quatro algarismos hexadecimais) separados por dois pontos (:), cada algarismo em hexadecimal equivale a 4 bits.
		2031:000:140F:0000:0000:0AC0:975B:010C
	O mesmo mecanismo de identificação usado no IPv4 é utilizado no IPv6 dividido uma parte para rede e a outra para máquina.
	Na maioria dos endereços IPv6 unicast, o campo de identificação da máquina é formada a partir do endereço físico (MAC) da interface de rede.
	O IPv6 possui um sistema de configuração do endereço automática chamado SLAAC(StateLess Address AutoConfiguration), com a autoconfiguração ativada, um servidor DHCP não é necessário. A configuração ocorre com a parte do endereço da máquina sendo o próprio endereço físico a parte do endereço de rede é obtida através do protocolo NDP(Neighbor Discovery Protocol) Protocolo responsável pela autoconfiguração.
	No sistema IPv6 não há os protocolos ARP e RARP (substituídos pelo NDP).
	Não há endereço de broadcast no sistema IPv6, todas as máquinas precisam ter ao menos dois endereços IPv6 configurador: um unicast e um Multicast.
	Endereço multicast padrão para todas as máquinas ff02::1 e ff02::2 para todos os roteadores

Simplificação de endereços IPv6
	Regra 01 - Podemos remover os zeros a esquerda deixando apenas um em caso de quatro zeros. 2031:0000:14of:0000:0000:0ac0:975b:010c --> 2031:0:14of:0:0:ac0:975b:010c
	Regra 02 - Podemos substituir a sequencia de dois zeros por dois pontos(::) apena uma vez.
		2031:0:14of:0:0:ac0:975b:010c --> 2031:0:14of::ac0:975b:010c
	Também podemos fazer o inverso e voltar ao tamanho normal de 8 blocos de 4 algarismos.

Tipos de endereço IPv6
	Unicast - identifica uma única máquina
	Anycast - Um mesmo endereço IP identifica mais de uma máquina oferecendo o mesmo serviço. Utilizado em redes grandes com máquinas que oferecem o mesmo serviço porém estão distantes uma da outra, quando o cliente acessar o serviço ele vai se conectar a máquina que estiver fisicamente mais próxima a ele. Um exemplo é o serviço CDN(Content Delivery Network). O IPv6 suporta endereços Anycast nativamente, ele têm a mesma estrutura dos endereços unicast.
	No endereçamento IPv6 o primeiro endereço da rede é um endereço anycast que indica o roteador padrão da rede (default gateway).
	Multicast - É técnica de criar grupos de máquinas dentro de uma rede e esse grupo recebe um endereço de multicast, uma mensagem enviada para esse endereço vai ser replicada para todas as máquinas pertencentes desse grupo.
	O IPv6 não tem endereço de broadcast! A funcionalidade de broadcast é implementada através de um grupo multicast onde todas as máquinas da rede estão o endereço é ff02::1 endereços IPv6 de multicast sempre começam com 'ff'. O protocolo responsável por gerenciar os endereços Multicast é o MLD(Multicast Listener Discovery).

Escopos do IPv6
	Indica a área da rede em que o endereço IP é valido. No Ipv4 existem apenas três escopos loopback(Máquina), Privado(Rede interna) e Público(internet) no IPv6 existem 16 escopos com 7 sendo utilizáveis:
	Valor    Escopo 
	   0        (reservado)	
	   1         interface-local(Loopback)
       2         link-local(Privado)
	   3         realm-local(baseado na arquitetura da rede)
	   4         admin-local
	   5         site-local
	   8         orgonization-local
	   e         global(Público)
	   f          (reservado)
	Os escopos 3, 4 e 5 são definidos pelo admin onde ele define o escopo da rede. Alguns endereços IPv6 são armazenados a um escopo específico; em outros, o escopo pode ser configurado. Dentro dos endereços IPv6 existe um 'x' que indica o escopo.

Estrutura dos endereços IPv6 unicast e anycast
	No endereçamento IPv6 existem endereço global(público) e privado(local).
	Estrutura:
		Identificação da rede
			Prefixo(Min. 48 bits) Sub-rede(máx. 16 bits)
		Identificação da máquina
			IID(64 bits)
	Na maioria das vezes a 'identificação da máquina' é gerado automaticamente, a partir do endereço físico (MAC) da interface de rede. Este mecanismo não é usado quando endereços IPv6 unicast/anycast têm os três primeiros bits em "0" ou "1" o endereço inicia com 0 ou 1.
		0xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx
	Ou seja o endereço da máquina não foi gerado pelo endereço físico da máquina. Endereços IPv6 iniciados entre 2 e F utilizam o IID configurado pela máquina.
	Com o campo "identificação da máquina" fixo em 64 bits, o CIDR só pode ser, no máximo /64.
	Delegação de endereços IPv6 unicast globais  no caso do Brasil: IANA > LACNIC > NIC.br empresas que solicitam blocos(Prefixo) de IPv6 recebem blocos a partir de /32 para provedores e /48 para empresas e /64 para usuários finais.
	Exemplo
		 | PREFIXO | Sub-rede |        IID         |
	  Empresa recebeu um bloco /48 da NIC.br. Teremos um campo "sub-rede" de 16 bits. O admin da rede poderá configurar até 2 elevado a 16 sub-redes. Teremos sempre 2 elevado a 64 endereços IPv6 disponíveis por sub-rede.
	  Em teoria qualquer endereço que não seja reservado ou local pode ser usado como global. Porém a IANA só disponibilizou endereços iniciados em 2 até 3

Endereços IPv6 unicast/anycast locais(privados)
	No IPv6 existem duas estruturas de endereçamento privado:
	Endereços de link-local(local-link)
		Estrutura simples de configuração rápida destinada a redes menores, não permite segmentação(configuração de sub-redes): todas as máquinas pertencerão à mesma rede.
		Prefixo: f380::/64, i.e.:
			fe80:0000:0000:0000:IID
		Sempre seguida dessa estrutura com 48bits zeros.
	Endereços ULA(Unique Local Address Endereço local único)
		A principal diferença do link-local é que o ULA permite a configuração de sub-redes. É usado em casos onde é necessária a segmentação da rede privada em sub-redes.
		Prefixo: fd00::/8
		| fd | Bits aleatórios(40 bits) | Sub-rede(16 bits) | IID(64 bits) |
		O campo bits aleatórios precisa conter o mesmo valor para todas as máquinas da rede. Ver RFC 4193 para o algoritmo recomendado para a geração deste número.
		Permite configuração de sub-redes; com 16 bits.

Construção do campo IID(Interface identifier)
	Esse campo de identificação é gerado automaticamente a partir do endereço físico da interface da rede da máquina. Esse campo utiliza um formato chamado "EUI-64" modificado e tem 64 bits(8 bytes), mas o endereço MAC tem 48 bits, logo uma conversão é necessária.
	Conversão:
		Endereço MAC 48 bits(6 bytes) Exemplo:
		 00-80-AD-0A-CD-DC
		Vamos remover os hifens e dividir em dois grupos de 3 bytes e adicionar "FF FE" entre esses grupos:
		00 80 AD FF FE 0A CD DC
		O endereço MAC tem um endereço Universal/Local(U/L) que identifica se o endereço é local(rede interna) ou universal(rede global)
			0 = Local
			1 = Universal
		Bit 41 do MAC e bit 57 do IID é o sétimo bit contando da direita para esquerda.
			0"0" 80 AD FF FE 0A CD DC
			000b --> 0010b --> 2h
			0"2" 80 AD FF FE 0A CD DC
		Precisamos modificar esse bit para que o endereço passe a ser Universal.
		Próximo passo é colocar no padrão de endereçamento IPv6, podemos abrevia-lo.
			0280:ADFF:FE0A:CDDC --> 280:ADFF:FE0A:CDDC

Índices
	Pode acontecer de, em máquinas com mais de uma interface de rede, mais de uma interface receber o mesmo endereço IPv6. Resolvemos esse problema utilizando um índice.
	Em máquinas Windows vai ser feito através do sinal de "%"e o número da interface.
		fe80::1234%1(primeira interface)
		fe80::1234%2(segunda interface)
	Em máquinas unix vamos colocar "%eth" e o número da interface.
		fe80::1234%eth0(primeira interface)
		fe80::1234%eth1segunda interface)
Colchetes
	Quando usados em URLs, endereços IPv6 devem ser grafados entre colchetes. Isto resolve o problema de ambiguidade quando um número de porta é informado. Exemplos:
		http://[2001:db8:85a3::8a2e:370:7334]/index.php
		http://[2001:db8:85a3::8a2e:370:7334]:8080

CIDR
	É um número que indica quantos bits do endereço IP são usados para identificar a rede.
	Exemplo 1:
	Temos o endereço IPv6 abaixo e sabemos que o CIDR da rede é /48. Qual é o endereço da rede? Qual é a faixa de endereçamento desta rede?
		    2001:db8:85a3::8a2e:370:7334
	Precisamos remover as simplificações feitas antes para descobrir o CIDR. Precisamos de 8 campos cada um com 4 bytes.
			2001:0db8:85a3:0000:0000:8a2e:0370:7334
	Sabemos que o CIDR é 48 então os primeiros 48 bytes desse endereço vão indicar o endereço da rede, cada algarismo hexadecimal representa 4 bits então podemos dividir 48 por 4 que é igual a 12. Então o endereço da rede vai até o 12 algarismo hexadecimal.
		2001:0db8:85a3 é o prefixo.
		0000:0000:8a2e:0370:7334 identificação da máquina
	Endereço inicial == 2001:0db8:85a3:0000:0000:0000:0000:0000
	Endereço IP final == 2001:0db8:85a3:ffff:ffff:ffff:ffff:ffff
	Podemos fazer a simplificação desse endereço:
		2001:0db8:85a3::/48

Exemplo 2:
	Temos o endereço IPv6 abaixo e sabemos que o CIDR da rede é /53. Qual é o endereço da rede? Qual é a faixa de endereçamento desta rede?
	1 - Remover simplificações
		2001:db8:85a3::8a2e:370:7334 --> 2001:0db8:85a3:0000:0000:8a2e:0370:7334
	2 - Pegar o CIDR 53 e dividir por 4, o resultado vai ser 13,25. Como não é inteiro esse 0,25% representa 1 bit 0,50% 2 bit e 0,75 3 bit.
	3- Sabemos que podemos usar 13 algarismos para representar o endereço IP. o decimo quarto algarismo vamos  pega apenas o primeiro bit a esquerda:
		"0"000b
	4 - Endereço inicial e final:
		Endereço inicial == 2001:0db8:85a3:0000:0000:0000:0000:0000
		Endereço IP final == 2001:0db8:85a3:"07"fff:ffff:ffff:ffff:ffff
									0111b=7h
	Endereço da rede
		2001:0db8:85a3::/53

Exemplo 3:
	Temos o endereço IPv6 abaixo e sabemos que o CIDR da rede é /55. Qual é o endereço da rede? Qual é a faixa de endereçamento desta rede?
	1 - Remover a Simplificação
		2001:0db8:85a3:0000:0000:8a2e:0370:7334
	2 - Pegar o CIDR 55 e dividir por 4, o resultado vai ser 13,25. Como não é inteiro esse 0,25% representa 1 bit 0,50% 2 bit e 0,75 3 bit. Os 13 primeiros algarismos fazer parte da rede.
	3 - Sabemos que podemos usar 13 algarismos para representar o endereço IP. Vamos pegar o décimo quarto desse endereço e converter para binário.
		3 = 0011b 
	Os três primeiros bits vão ser parte da rede e o quarto bit do endereço a máquina
	4 -Vamos converter os bits a direta para zero e esse binário para hexadecimal novamente assim teremos o primeiro endereço da rede:
		0010b = 2h
		Endereço inicial: 2001:0db8:85a3:1200:0000:0000:0000:0000
		Endereço final: 2001:0db8:85a3:13ff:ffff:ffff:ffff:ffff
		Endereço da rede: 2001:0db8:85a3:12::/55

VSLM (Segmentação)
Segmentação de Endereços IPv6 Parte 1
	Segmentação é a divisão da faixa de endereçamento disponível em sub-redes. Em redes IPv6
	a segmentação em sub-redes não diminui a quantidade de endereços de redes disponíveis.
	Em endereços IPv6 podemos aproveitar as bits do campo identificação da rede para segmentar as sub-redes. Os tipos de endereços locais no IPv6 são: 
		Endereços link-local - Não permite segmentação
		ULA (Unique Local Address) - permite segmentação

















