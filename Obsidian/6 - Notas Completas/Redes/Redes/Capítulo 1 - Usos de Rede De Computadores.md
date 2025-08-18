 **Modelo Cliente-Servidor**
Conhecido como modelo hierarquico onde cliente sempre será cliente e servidor sempre será servidor. Cliente solicita o Servidor Responde.

Principais motivações para implantação de redes domésticas:
	1-Acesso a informações remotas
	2-Comunicação entre pessoas
	3-Entretenimento interativo
	4-Comércio eletrônico
Em redes de computadores é uma prática ocultar detalhes técnicos do usuário.


**Modelo não hierárquico**
Conhecido como peer-to-peer e modelo descentralizado, onde não há hierarquia o usuario pode atuar hora como cliente hora como servidor.
Principais diferenças:
	Base de informações descentralizada
	Aumento na disponibilidade
	Incerteza do término da operação
	Redução da segurança

As redes de computadores são locais, elas podem ser corporativas ou domesticas nos modelos p2p E C.S

**Hardware de Rede**
Em termos gerais, há dois tipos de tecnologias de transmissão em uso disseminado nos dia de hoje:

**Links de difusão**
Esse tipo de rede possui apenas um canal de comunicação onde todas as máquinas enviam e todas as máquinas recebem mas somente a máquina destino não ignora o pacote. Todas as maquinas mandado mensagem curtas gerando confusão.(BROADCASTING)

**Links ponto a ponto**
Consistem em muitas conexões entre pares individuais de máquinas, para um pacote chegar ao destino talvez ele tenha que passar por varias máquinas.

**Classificação de redes por escala**
PAN - 1m
LAN - 1m-1km
WAN - 10km 1000KM
The internet - 10,000km

**LAN**
Redes privadas contidas em um único edifício ou campus com até quilômetros de extensão. Redes LAN têm um tamanho restrito esse limite permite a utilização de determinados tipos de projetos(topologia) barramento, anel, estrela, árvore, malha, híbrida. Podemos identificar uma se ela conter dispositivos pessoais.

**MAN**
Redes metropolitanas que abrange uma cidade. Podemos dizer que as redes MAN são AS das redes WAN.

**WAN**
Redes geograficamente distribuída de longas distancias que conectam redes LAN com frequência um país ou continente.

**REDES MAN + WAN --> Redes de INTERCONEXÃO**
As REDES DE INTERCONEXÃO surgiram com o objetivo de conectar uma rede LAN a outra. Elas utilizam roteadores para encontrar as melhores rotas até a outra rede LAN. a sub-rede de comunicação em geral pertence e é operada por uma empresa.

**Redes sem fio**
Podem ser divididas em três categorias principais:
	Interconexão do sistemas
	LANs sem fios
	WANs sem fios

**Inter-redes**
Existem muitas redes no mundo cada uma com tipos de dispositivos e softwares diferentes, para que essas redes se comuniquem entre si é necessário uma máquina chama gateway.

**Software de rede**
No projeto das primeiras redes de computadores, o hardware foi a principal preocupação e o software ficou em segundo plano. Todo projeto de rede é dividido em duas partes física e lógica.

**Hierarquias de protocolos**
As redes são organizadas como uma pilha de camadas, colocadas uma sobre as outras. O objetivo de cada camada é oferecer determinados serviços ás camadas superiores isolando essas camadas dos detalhes de implementação desses recursos.
A camada n de uma máquina se comunica com a camada n de outra máquina.
As regas de convenções usadas nesse diálogo são conhecidas como o protocolo da camada n.
	DADOS + COMPORTAMENTO = protocolo
Uma camada A de um host conversa de forma abstrata com a camada A de outro host.

Em um modelo de 5 camadas a camada 5 oferece serviços ao ser humano, a camada inferior oferece serviço a camada superior, a camada 4 oferece serviço a 5 e anexa uma informação no header da mensagem que a sua entidade par(mesma camada do outro host) vai utilizar, isso é feio em todas as camadas.

**Interfaces de Serviços**
A função de cada camada é oferecer serviços para uma camada acima dela. Os elementos ativos em cada camada são chamados de entidades. As entidades da mesma camada, mas contida em máquinas diferentes são chamas de entidades de par.
	PDU - protocolos entre entidades pares
A camada inferior é chamada de camada provedora de serviços e a camada superior de usuária do serviço.
Os serviços estão disponíveis em SAPs(Service Access Points).
Os SAPs da camada n são os locais onde a camada n+1 pode acessar os serviços.
A camada superior passa uma IDU(Interface Data Unit) ou R-PDU, N-PDUs para a entidade da camada n através do SAP chamado de parâmetro e usado para um processamento interno.
A IDU consiste em uma SDU(Service Data Unit) e algmas informações de controle,
	SAP = Service Access Point
	IDU = Interface Data Unit
	SDU = Service Data Unit
	PDU = Protocol Data Unit
	ICI  = Interface Control Information

**Serviços Orientados a Conexão e
Serviços não Orientados a Conexão
As camadas podem oferecer dois tipos diferentes de serviços ás camadas situadas acima delas:
	**Serviços orientados as conexões**
		Primeiro o usuário do serviço estabelece uma conexão conduz uma negociação de parâmetros a serem usados, e depois libera a conexão. A principal característica desse serviço é a confiabilidade.
	**Serviços não orietados a conexões**
		As mensagens são enviadas com um endereço de entrega, uma mensagem não está relacionada as demais e fluxa não é controlado. A principal característica é que não é confiável.

**Primiticas de serviço** 
primitivas de serviço **descrevem de forma abstrata os serviços e informações trocadas entre duas camadas adjacentes, através de um ponto de acesso** (SAP - Service Acess Point)

**O relacionamento entre serviço e protocolo**
**Serviço** é um conjunto de primitivas que uma camada oferece á camada situada acima dela. o serviço define as operações que a camada está preparada para executar em nome de seus usuários.

**Protocolo** é um conjunto de regras que controla o formato e o significado dos pacotes que são trocados pelas entidades pares contidas em uma camada. As entidades utilizam protocolos com a finalidade de implementar suas definições de serviço.