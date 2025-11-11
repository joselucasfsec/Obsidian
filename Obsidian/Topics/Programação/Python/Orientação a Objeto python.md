Tags: #python #progamação
## Classes
Classes são moldes para criar novos objetos, as classes geram novos objetos (instâncias) que podem ser seus próprios atributos e métodos. 
**Atributo = dados dentro da classe**
**Método = Funções dentro da classe**
Os objetos gerados pela classe podem usar seus dados internos para realizar várias ações.
**Por convenção, usamos PascalCase(Todas as palavas começam com letra maiúscula) para nomes de classes.**

#### Exemplo da estrutura para criação de uma classe no python:
```
class pessoa:
	def __init__(self, nome1, sobrenome1):
	self.nome = nome1 # dentro da classe vai have uma variavel nome com o valor de nome1
	self.sobrenome = sobrenome1
```
O primeiro parâmetro dentro de todos os métodos dentro de uma classe devem receber o nome de **Self** servem de referencia ao objeto que está sendo criado. Ao passar parâmetros para um método ele já reserva o primeiro como self e oque passarmos var ser na verdade o segundo parâmetro

###### O exemplo acima é uma maneira mais usual para criação de uma classe no python pois também é possível criar uma classe da seguinte forma:
```
class Pessoa:
	...
	
p1 = Pessoa()
p1.nome = 'Lucas'
p1.sobrenome = 'jose'
print(p1.nome)
print(p1.sobrenome)
```

**init** É chamado para inicializar os atributos da classe
**def** quando está dentro de um classe não é mais uma função, apenas utiliza a mesma estrutura
