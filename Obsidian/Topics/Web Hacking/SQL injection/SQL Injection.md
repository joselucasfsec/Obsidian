Tags: #injection

SQL injection é uma vulnerabilidade de segurança que ocorre quando um atacante injeta comandos SQL maliciosos em campos de entrada de dados (como formulários, campos de login, URLs, ou cookies), com o objetivo de manipular ou acessar indevidamente um banco de dados.

## 1 - Enumerar o número de colunas

Depois de descobrir a qual tipo de SQL injection o alvo é vulnerável vamos enumerar o número de colunas existentes:
	' union select 1,2,3,4,5,6# 
Iniciamos com 1 e vamos aumentado o número de colunas até o servidor retornar um comportamento diferente.




















Refêrencias: