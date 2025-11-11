SSRF é uma falha de segurança que permite com que o atacante faça requisições para a rede interna através de uma aplicação web. Se trata da falsificação de solicitações do lado do servidor .
Em um ataque SSRF, o invasor normalmente manipula a entrada usada para especificar a URL de destino para uma solicitação HTTP do lado do servidor. Isso pode ocorrer quando um aplicativo não valida ou higieniza uma URL inserida por um usuário antes de extrair dados de um recurso remoto.
![[Captura de tela de 2025-08-27 09-38-54.png]]

## Exploração
Vamos interceptar uma requisição utilizando burpsuite , essa requisição é para fazer check do stock
![[Captura de tela de 2025-08-27 09-41-30.png]]
Ao interceptar a requisição, o parâmetro em stockApi encodado por urlencode e ao desencodar no módulo decoder do seu burpsuite será mostrado o link cujo qual esta sendo feito uma solicitação.
![[Captura de tela de 2025-08-27 09-47-45.png]]
Então alterarmos ele para um endereço local como por exemplo: http://192.168.0.1:8080/admin e realizarmos um brute force no 1, para ir de 1 à 255, escaneando toda a rede /24, afim de encontrarmos um site interno com painel de administrador.
![[Captura de tela de 2025-08-27 09-50-13.png]]




























