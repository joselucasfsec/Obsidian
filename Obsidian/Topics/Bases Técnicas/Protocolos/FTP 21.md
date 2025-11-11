O Protocolo de Transferência de Arquivos (FTP) é um protocolo de rede padrão usado para a transferência de arquivos de computador entre um cliente e um servidor em uma rede de computadores.

Iniciar obtendo o banner para identificar a versão do ftp
nc -vn $ip 21

Conectar utlizando **nc** ou a ferramento do **ftp** validando user default:

ftp $ip

USER anonymous|ftp

PASS anonymous|ftp

Comandos do FTP

**get** - baixar arquivo

**put** - enviar arquivo

**help** - comandos

**PASV** - modo passivo

Servidores ftp podem ser configurados utilizando o modo passivo onde ele não responde sem estar com o

modo passivo ativo, para ativar: