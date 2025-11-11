## Externally-Managed-Environment Error
O erro ocorre quando tentamos instalar uma biblioteca python em um ambiente que possui aplicações que dependem do python para o funcionamento. Esses ambientes são bloqueados para evitar alterações acidentais que possam prejudicar componentes críticos do sistema.
Quando você tenta usar o pip nesses ambientes, o Python desempenha o papel de colega de quarto responsável. Diz: “Ei, não toque nisso – é gerenciado externamente!” O resultado? Uma bela mensagem de erro impedindo você de instalar, modificar ou remover pacotes.

## Causas do erro
Essas distribuições usam seus próprios gerenciadores de pacotes — como apt ou dnf — para lidar com Python e suas bibliotecas. Instalar ou atualizar pacotes com pip nesses ambientes corre o risco de entrar em conflito com as dependências do sistema, potencialmente quebrando aplicativos importantes ou até mesmo o próprio sistema operacional.
Aqui está a verdade: ambientes Python gerenciados pelo sistema são delicados. Para evitar o caos, eles vêm com limites rígidos. O erro existe para impor esses limites.

# Passos para corrigir o erro

#### 1 Set up um ambiente
Ambientes virtuais são o padrão ouro para o desenvolvimento Python. Eles isolam as dependências do seu projeto, dando a você a liberdade de instalar o que quiser sem alterar a configuração do Python em todo o sistema.
Veja como configurar um:
**Passo 1:** Instalar o venv
``` 
apt install python3-venv
```
**Passo 2:** Set up um ambiente virtual.
Vamos navegar até a página do projeto e criar um projeto com o seguinte comando.
```
python3 -m venv nome
```
**Passo 3:** Iniciar o ambiente virtual.
``` 
source nome/bin/activate
```
**Passo 4:** Instalar a lib necessária.
Com o ambiente virtual ativo, podemos instalar nossas bibliotecas sem alterar a instalação padrão do python.
```
pip install requests
```
**Passo 5:** Desativar o ambiente
Depois de finalizado o projeto podemos desativar o ambiente criado.
```
deactive
```

#### 2 Usar o gerenciador de pacotes do sistema
Se você estiver trabalhando em um ambiente gerenciado por sistema, use as ferramentas projetadas para isso. Use o gerenciador de pacotes do seu sistema operacional para instalar bibliotecas Python.
Veja como:
**Identificar o pacote**
``` 
apt-cache search python3-requests # Debian-based
yum search python3-requests # Red Hat-based 
brew search requests # macOS
```
**Instalar o pacote**
```
sudo apt-get install python3-requests# Debian-based    
sudo yum install python3-requests# Red Hat-based    
brew install requests# macOS
```

#### 3 Forçar instalação com PIP
Desesperado para instalar um pacote, independentemente dos riscos? Você pode substituir as restrições. Mas deixe-me ser claro: isso pode prejudicar o ambiente Python do seu sistema. Proceda com cautela.
**Opção 1:** Aplicar o parâmetro `--break-system-packages`
```
pip install <lib> --break-system-packages
```
**Opção 2:** Usar o parâmetro --user para instalar o pacote da biblioteca no diretório do usuário.
```
pip install <package_name> --user
```
**Opção 3:** Combinar `--ignore-installed` com `--user` 
```
pip install <package_name> --ignore-installed --user
```
**Opção 4:** Usar sudo para instalar 
```
sudo pip install <package_name>
```