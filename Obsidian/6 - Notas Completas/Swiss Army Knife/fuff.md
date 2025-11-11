Tags: #fuzzing #tools

### **Listagem de Diretórios

Directory Discovery
Onde está escrito FUZZ é onde ele vai adicionar a wordlist.

**ffuf -c -w wordlist.txt -u** **[http://bussinescop.com.br](http://bussinescop.com.br/FUZZ)****/FUZZ**

Para descobrir arquivos podemos usar a opção -e

**ffuf -c -w wordlist.txt -u** **[http://bussinescop.com.br/FUZZ](http://bussinescop.com.br/FUZZ)** -e .aspx,.html,.php,.txt

### Parâmetrôs importantes

**-H** : Header “Name:Value”

**-t** : Número de requisiçẽos

**-o** : Salvar output em arquivo

**VHOSTS**

Start by figuring out the response lenght of false positive

curl -s -H “Host: naoexiste.alvo.com.br” http/alvo.com.br | wc -c

612

Filter out responses of lenght 612

ffuf -c -w wordlist.txt -u http://ffuf.io.fi -H “Host: FFUF.ffuf.io.fi" -fs 612

É muito comum ele retornar muitos falsos positivos, podemos identificar e filtrá-los.
```
_**-fw**_ : to filter by the amount of words
_**-fl**_ : to filter by the number of line
_**-fs**_ : to filter by the size of the response
_**-fc**_ : to filter by the status code
_**-fr**_ : to filter by the regex pattern
```
#### GET parameter fuzzing
Conseguimos enumerar os paramentos GET utilizando o ffuf. Primeiro precisamos saber o tamanho da resposta 200 para iniciar o fuzzing:
```
**ffuf -w wordlists.txt -u http://target/script.php?FUZZ=test_value -fs 4242**
```
#### **POST data fuzzing**
Usando a flag -X para mudar o método de requisição, no exemplo a flag -d para especificar os dados a enviar.
```
ffuf -w /path/to/postdata.txt -X POST -d "username=admin\&password=FUZZ"
-u https://target/login.php -fc 401
```
#### Miscellaneous
A ferramenta nos permite fazer fuzz em qualquer parte da URL ou do header HTTP.

**Brute-force**
Conseguimos fazer brute force em páginas de login usando a flag -mode com dois modos de ataque **clusterbomb** and **pitchfork**. A ferramenta vai aceitar duas listas.

**clusterbomb:** cada item da lista é testado com todos da outra.
**pickfork:** o item 1 da listaA é testado com o item 1 da listaB.

A flag -request pode ser usada com um arquivo com a requisição HTTP modificada

especificando onde a ferramenta deve colocar as wordlists:

**ffuf -request req.txt -request-proto http -mode clusterbomb -w**

**usernames.txt:HFUZZ -w passwords.txt:WFUZZ**

HFFUZ é onde ele vai colocar a lista de users e WFUZZ a lista de senhas que estão

especificadas no req.txt