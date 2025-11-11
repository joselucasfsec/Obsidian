Muito se fala que não devemos misturar códigos PHP com HTML, é um mito! Trabalhar com ambos faz total sentido e é incrível a produtividade obtida assim.

**Boas práticas de codificação**
- Arquivos JS e CSS devem ser separados sempre, essa é uma ÓTIMA regra de boas práticas.
- Regras e lógicas de negócio devem ser separadas de visões e interfaces visuais.
- Arquivos e trechos que precisam ser reutilizados também precisam ser separados.

**O que você não deve fazer**
O PHP é permissivo ao extremo, com isso você pode construir qualquer coisa boa na mesma medida que ruim. Vejamos algumas práticas a serem evitadas:
- Repetição, qualquer projeto web terá inevitavelmente repetição de estruturas a serem apresentadas. Mas repetir a estrutura não significa repetir o código. **Substituição repetição por reuso em código que serão utilizados mais de uma vez na aplicação**
- Declaração com saída, declara um funcionalidade ou configuração em um arquivo com saída impede de reutilizar de reutilizar essa funcionalidade em outras camadas de aplicações. **Declare todas as configurações e funcionalidades em arquivos separados, sem saída e que possam ser requeridos.**
- Materialização, na correria de um projeto é  comum ligar o piloto automático e aplicar um programação funcional ignorando a regra para aplicar funcionalidades.

****
#### Outros arquivos PHP
**classes.php** - Um arquivo de classe PHP cada classe deve ter seu próprio arquivo.
**trait.php** - Os traits em PHP servem para definir comportamentos e recursos comuns em classes.
**interface.php** - A interface é um contrato de implementação de classe.
**function.php** pode ser incluído em qualquer outro que precise usar essas funções.
**config.php** - Configurações gerais como ini_sets e constantes que podem ser incluídas globalmente.
**includes.php** Trechos de códigos que serão reutilizados no projeto como headers, sidebars e footers.