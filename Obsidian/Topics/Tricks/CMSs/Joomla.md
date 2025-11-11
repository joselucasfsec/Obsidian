Joomla é um sistema de gerenciamento de conteúdo (CMS) gratuito e de código aberto que permite criar, gerenciar e publicar sites e aplicações online de forma flexível e extensível.

# Enumeração e Reconhecimento

#### Identificar joomla e a versão do Joomla
Para determina se um site roda joomla, e identificar a versão, existem três métodos simples que podem ser usados para determinar a versão do joomla:
#### Gerador meta
Checar o código fonte da página em busca de **meta generator** tag na sessão HEAD no código HTML. Esse é um jeito simples de determinar se joomla é utilizado:
```
<meta name="generator" content="Joomla! - Open Source Content Management" />
```
#### joomla.xml
Para identificar a versão nos podemos checar o arquivo **joomla.xml** dentro do diretório **/administrator/manifests/files/joomla.xml**
```
http://joomla.org/administrator/manifests/files/joomla.xml
```

#### /language/en-GB/en-GB.xml
Outra opção para encontrar a versão é acessar o arquivo de linguagem
``` 
https://joomla.org/language/en-GB/en-GB.xml
<version> 3.6.5 </version>
```

#### Version in README.txt
Se as meta tags estiverem desativadas, check o arquivo /README.txt from the web root of the install. Joomla tem a versão no topo do arquivo ReadMe file.

## Extensões e enumerando versões
Similar aos plugins do Wordpress o Joomla permite a funcionalidade de "extensões" que são do tipo:
- Módulos
- Componentes
- Templates
- Plugins
- Languages
Infelizmente, a menos que você tenha os detalhes da conta de administrador, não há uma maneira fácil de encontrar todas as extensões de uma instalação específica do Joomla. Vale ressaltar que o Joomla possui uma lista ativa chamada **Lista de Extensões Vulneráveis**
```
https://vel.joomla.org/live-vel
```
