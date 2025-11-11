Técnica para direcionar uma porta rodado na rede interna da máquina para uma porta aberta na nossa máquina
Shell meterpreter:
```
portfwd add -l $port.LOCAL -p $port.INTERNA -r $ip.HOST
portfwd add -l 110 -p 110 -r 10.10.20.4
```