Encontrada uma vulnerabilidade precisamos descrever ela com:
- Descrição executiva
- Descrição técnica
- Impacto
- Passo a Passo para reprodução
- Recomendações

#### Descrição executiva
Deve ser de fácil compreensão sem informações muito técnicas, uma pessoa sem conhecimento na area de tecnologia deve entender.
Vamos tentar seguir a 5w2h:
- O quê?
- Por quê?
- Quem?
- Quanto?
- Como?
- Quando?
- Onde?
Vamos responder essas perguntas e depois no relatório vamos construir a descrição executiva sem ser técnico

#### Descrição técnica
Como foi explorada e como resolver? 
Vamos estar escrevendo essa parte para o departamento de tecnologia de empresa, vamos descrever de maneira mais técnica e especifica como exploramos o ambiente, ferramenta utilizadas.
E descrever o passo a passo para exploração e oque fizemos para demonstrar o **impacto**. E finalizar essa descrição com a **recomendação**
#### Impacto
Quais impactos dentro do ambiente podem ser gerados caso um atacante malicioso explore essa falha? Exemplos: manipular dados de outro cliente, acessar dados de cartões de credito, comprometer completamente todo o ambiente do cliente.
Vamos descrever qual impacto a exploração das vulnerabilidade encontradas podem gerar no ambiente do cliente principalmente financeiros.

#### Passo a Passo
Vamos demonstrar de forma clara como realizamos a exploração da vulnerabilidade com as ferramentas utilizadas, todos os comandos executados na ordem enque foram executados e prints de todos os passos para a a reprodução da exploração

#### Recomendações
Dar uma solução para que o cliente implemente e corrija onde a vulnerabilidade ocorre, atualize algum recurso ou ferramenta, implemente algum mecanismo de autenticação mais seguro.
Podemos trazer referencias com OWASP, CWE. Sugerir que aplique monitoramento e auditoria para detectar atividades suspeitas e responder rapidamente a incidentes.