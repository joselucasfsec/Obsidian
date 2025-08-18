Tags: #tools #reconhecimento

Nmap é uma ferramenta poderosa e versátil diponível para a varredura de redes usada por administradores de rede para descobrir hosts e serviços em uma rede contruindo um mapa da rede.

Aqui estão algumas das principais funcionalidades:
	1. Descoberta de Host
	2. Varredura de Portas
	3. Detecção de Versão
	4. Detecção de Sitema Operacional
	5. Scripts Nmap
	6. Mapeamento de Rede

## Flags

A flag 	`--min-rate <número>`  define a taxa mínima de pacotes por segundo. O Nmap vai tentar não enviar menos doque esse número de pacotes por segundo, forçando uma taxa mínima constante
	 `$ nmap --min-rate 500 -p- 192.168.0.1`

A flag `--max-rate <número>` define a taxa máxima de pacotes por segundo. O Nmap vai tentar não ultrapassar esse número de pacotes por segundo. útil para tornar a varredura mais discreta, reduzindo a chance de detecção por sistemas de IDS/IPS.
	`$ nmap --max-rate 50 -p- 192.168.0.1`