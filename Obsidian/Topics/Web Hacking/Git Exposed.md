O Git é um **sistema de controle de versão distribuído**, é uma ferramenta essencial para equipes de desenvolvimento e até para desenvolvedores individuais, garantindo a organização, o histórico e colaboração em projetos. O Git serve para:
- **Rastrear mudanças:** Ele registra cada alteração feita nos seus arquivos, quem fez a alteração, quando foi feita e por quê.
- **Colaboração:** Permite que várias pessoas trabalhem no mesmo projeto simultaneamente, sem sobrescrever o trabalho umas das outras.
- **Histórico:** Você pode ver o histórico completo das alterações, voltar para versões anteriores do projeto, ou comparar diferentes versões.
- **Branches (ramificações):** Facilita a criação de "linhas de desenvolvimento" separadas, onde você pode experimentar novas funcionalidades ou corrigir bugs sem afetar a versão principal do projeto. Depois, você pode mesclar essas ramificações de volta à principal.

**Git Exposed** ocorre quando o diretório oculto `.git` de um repositório Git é acidentalmente exposto e acessível publicamente em um servidor web. Esse diretório contém todo o histórico do repositório, incluindo: Versão completas do código-fonte, metadados do Git, configurações do repositório.

#### Principais Comandos Git
 `git init` - Inicializa um novo repositório Git vazio no diretório atual.
 `git clone <url_do_repositorio>` - Clona um repositório Git existente.

**Gerenciamento de Status e Arquivos**
 `git status` - Mostra o estado atual do seu repositório, informa quais arquivos foram modificados, quais estão prontos para serem commitados.
 `git add <nome_do_arquivo>` - Adiciona um arquivo específico à  **staging area**(também conhecida como "índice").
 `git rm --cached <nome_do_arquivo>` - Remove um arquivo da **staging area**, mais mantém no diretório de trabalho.

**Salvando Alterações(Commits)**
`git commit -m "Mensagem do commit Version 1.0"` Registra as alterações que estão na **staging area** no histórico do repositório. A mensagem do commit deve ser descritiva, explicando oque foi feito nas alterações.
`git commit -am "mensagem do commit"` Combina **git add .** e **git commit -m** para arquivos que já estão sendo rastreados pelo Git.

**Visualizando o Histórico**
`git log` Monstra o histórico de commits do repositório. Você verá quem fez o commit, quando e a mensagem.
`git log --oneline` Mostra o histórico de commits de forma mais concisa, com uma linha por commit.
`git log --graph --oneline --decorate` Mostra o histórico de commits com um gráfico ASCII que ilustra a estrutura das branches.
`git show <hash>` Visualizar a alteração.
`git checkout <hash>` Voltar para esse commit.

**Gerenciando Branches(Ramificações)**
Branches são essenciais para trabalhar em recursos isolados ou em equipe sem interferir no código principal.
`git branch` Lista todas as branches locais no seu repositório e mostra qual branch você está atualmente.
`git branch <nome_da_nova_branch>` Cria uma nova branch com o nome especificado.
`git checkout <nome_da_branch>` Muda para a branch especificada.
`git checkout -b <nome_da_nova_branch>` Cria e imediatamente muda para uma nova branch.
`git merge <nome_da_branch_para_mesclar` Mescla as alterações de uma branch em sua branch atual.
`git branch -d <nome_da_branch>` Deleta uma branch local (após ela ter sido mesclada). Use `-D` para forçar a exclusão de uma branch não mesclada.