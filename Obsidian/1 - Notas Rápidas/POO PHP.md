
Progamação orientada a objeto é um padrão de programação em que um software não é composto por um grande bloco de códigos específicos, e sim de vários blocos de códigos distantes e independentes, que juntos montam um sistema.

Esse padão possui diversos objetivos: reutilização de código, escalabilidade, manutenibilidade e desenvolvimento mais rápido.

### A POO possui alguns conceitos fundamentais para seu desenvolvimento:

**Abstração:** São tipos abstratos de dados;

**Objetos:** Um objeto é uma entidade do mundo real, concreta ou abstrata, que seja aplicável ao sistema

**Casses:** Uma classe é a representação de vários objetos que possuem as mesmas características e comportamentos;	

**Atributos / Propriedades:** São as características de um determinado objeto.



As classes definem as características e comportamentos dos seus objetos. Cada característica é representada por um atributo e cada comportamento é definido por um método.
Então **uma classe não é um objeto** e sim uma abstração de sua estrutura, no qual podemos definir quantos objetos desejamos ter.

```
<?php
 Class Conta {
   public $saldo = 500;
   public $titular;

   function sacar($valor){

   }

   function depositar($valor){

   }

   function verSaldo(){

   }
 }

  $conta1 = new Conta();
  $conta1 ->depositar(500);
  $conta1->sacar(20);

  $conta2 = new Conta();
  $conta2->depositar(250);
  $conta2->verSaldo();
?>
```

A classe Conta tem como atributos o saldo da conta e o titular. E como métodos possui **depositar(), sacar() e verSaldo()**. Para acessarmos o método **depositar()** do nosso objeto **$conta1** precisamos utilizar uma **seta(->)**. Seu nome é Operador de Acesso a Objetos e é através dessa seta que indicamos que estamos acessando um atributo ou método de tal objeto.


