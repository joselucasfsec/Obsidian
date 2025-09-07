Confusão de dependência ocorre quando um atacante cria pacotes maliciosos com o mesmo nome que uma dependência interna do projeto, mais o atacante vai hospedar uma versão mais atualizada dessa dependência em repositórios públicos com seu conteúdo malicioso.
É uma vulnerabilidade que está na maneira como os repositórios funcionam.

Consiste em uma falha de configuração na forma como os repositório se organizam na formação das dependências. A falha está em instalar bibliotecas internas que estão em repositórios públicos.

Quando o projeto é criado utilizando dependências de bibliotecas internas o atacante malicioso pode criar um projeto publico com uma versão superior a existente no projeto interno, quando esse projeto for iniciado novamente ele vai buscar por uma versão mais atualizada no repositorio local e depois no repositoro publico onde a versão atualizada maliciosa está instalada

Ocorre quando um atacante cria pacotes maliciosos com o mesmo nome que uma dependência interna de um projeto, mas hospedados em repositórios públicos. Quando o repositório público (como npm, PyPI, NuGet) tem precedência sobre o repositório privado onde as dependências legítimas são armazenadas, o sistema de build pode inadvertidamente baixar e instalar a versão maliciosa.

![[Captura de tela de 2025-09-04 12-52-27.png]]