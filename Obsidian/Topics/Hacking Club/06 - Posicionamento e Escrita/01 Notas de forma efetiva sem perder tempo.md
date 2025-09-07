
**Ao iniciar um pentest já devemos ter organizado onde vamos fazer nossas primeiras anotações para posterior mente escrever o relatório sem perder tempo retornando ao ambiente para repetir as etapas já feitas.**
#### 1 Anotar as portas abertas e tirar prints para o relatório
Para não ter que retornar ao endereço IP da máquina podemos adicionar ele a uma variável  de ambiente:
```
export IP=172.16.1.5
```
Adicionar o comando utilizado acima das prints.

#### 2 Encontrando informações interessantes
Ao enumerar as portas vamos encontrar serviços, devemos enumerar os serviços e quando encontrar algum vetor adicionar a print ao relatório.

#### 3 Tentativas de exploração
Ao tentar explorar algum vetor de ataque adicionar ao relatório oque fizemos mesmo que não tenha funcionado, para ter um controle do que já foi testado.

#### 4 Exploração
Encontrando falhas vamos tirar evidencias de como encontramos a vulnerabilidade e como exploramos a vulnerabilidade passo a passo.

#### 5 Pós Exploração
Depois de comprometer o servidor vamos fazer enumeração do ambiente e busca possiveis vetores para escalação de privilegio e adicionar o que encontramos de interessante no relatório