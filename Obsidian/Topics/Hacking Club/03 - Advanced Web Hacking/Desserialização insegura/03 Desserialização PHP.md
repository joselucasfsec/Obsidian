A desserialização insegura ocorre quando uma aplicação PHP recebe dados não confiáveis, geralmente de entrada do usuário, e os desserializa sem a devida validação. Se o atacante manipular esses dados, ele pode conseguir executar código malicioso no servidor, levando a um ataque de execução remota de código (RCE)

Exemplo:


