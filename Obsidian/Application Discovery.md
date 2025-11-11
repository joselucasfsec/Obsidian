## O objetivo nessa etapa é obter informações sobre as aplicações que estão rodando nos subdomínios, utilizamos print's de sites e informações como URL's e parâmetros das aplicações. 

### URL Discovery
Enumerar diretórios e arquivos dentro da aplicação. É interessante descobrir com qual tipo de Framework estamos trabalhando pois podemos direcionar nossas wordlists para esse tipo de aplicação.
- github.com/lc/gau
- github.com/hakluke/hakrawler
- github.com/xmendez/wfuzz
- github.com/ffuf/ffuf
- github.com/maurosoria/dirsearch

https://web.archive.org/
Podemo usar um wildcard * para buscar por subdomínios dentro do web archive.
```
http://web.archive.org/cdx/search/cdx?url=http://testphp.vulnweb.com/*&output=txt&fl=original
```
O site vai retornar resultados correspondentes depois do asterisco.
#### **Crawling**
É quando fazemos fuzzing de arquivos no servidor e vamos buscar dentro desse arquivo por entrypoints e parâmetros para criar possíveis URLs existentes.
https://github.com/projectdiscovery/katana
É uma ferramenta que faz crawling em aplicações java. Uma possibilidade é combinar os resultados das três ferramentas e criar uma wordlist nova com os três resultados:
```
cat list1.txt list2.txt list3.txt | sort -u | uniq > new_wordlist.txt
```

### Parameter Discovery
- github.com/devanshbatham/ParamSpider
- github.com/tomnomnom/gf
- github.com/s0md3v/Parth
- github.com/tomnomnom/hacks/tree/master/kxss

### Content discovery
- github.com/projectdiscovery/httpx
- github.com/michenriksen/aquatone
- github.com/m4ll0k/SecretFinder

### Automation
- github.com/yogeshojha/rengine
- github.com/edoardottt/scilla
- github.com/kpcyrd/sn0int