Tags: #PHP
#### Strings e Multilites
O php é uma linguagem que foi escrita em inglês e não possui acentos ou seja quando letras com acentos forem passadas não vão ser contabilizadas pelo php, para que elas possam ser contabilizadas devemos utilizar o multibyte.
Vamos informar as mesmas funções porem com um **mb_**  antes do nome da função: **mb_convert_case**.

#### Conversão de caixa
É o processo de transformar uma string ou valor para diferentes formatos de caixa, como maiúsculas, minusculas, ou primeira letra maiúscula.
```
mb_strtoupper($mbString)
mb_strtolower($mbString)
```
Também existe a mb_convert_case() é usada para converter a capitalização de uma string, com suporte a multibyte é essencial para idiomas com acentuação.
```
mb_convert_case(string $mbstring, MB_CASE_UPPER),
mb_convert_case(string $mbstring, MB_CASE_LOWER),
mb_convert_case(string $mbstring, MB_CASE_TITLE),
```

#### Substituição
As funções de substituição no PHP são funções usadas para trocar partes de uma string por outra.
```
$str = "Olá mundo!"
str_replace("mundo", "josé, $str) //saida> Olá José!
```

## Funções para arrays
#### Manipulação
Funções de array no PHP são extremamente poderosas e essenciais para qualquer desenvolvedor. Elas permitem que você adicione, remova, ordene, filtre e transforme dados de diversas maneiras.
**Principais funções de Manipulação de Array em PHP**
 - `count($array);` Retorna o número de elementos em um array.
 - `is_array($array);` Verifica se uma variável é um array.

**Adição e Remoção de Elementos**
 - `array_push($array, valor1, $valor2);` Adiciona um mais elementos ao final de um array.
 - `array_pop($array);` Remove e retorna o último elemento de um array. 
 - `array_unshift($array, $valor1, $valor2);` Adiciona um ou mais elementos ao início de um array.
 - `array_shift($array);` Remove e retorna o primeiro elemento de um array.
 - `array_filter($array);` Remove valores vazios.
 - `unset($array);` Remove um elemento específico de um array pela sua chave.

**Ordenação**
 - `sort($array);`  Ordena um array em ordem crescente.
 - `rsort($array);` Ordena um array em ordem decrescente.
 - `asort($array);` Ordena um array associativo pelos valores em ordem crescente, mantendo a associação chave-valor.
 - `arsort($array);` Ordena um array associativo pelos valores em ordem decrescente, mantendo a associação chave-valor.
 - `ksort($array);` Ordena um array associativo pelas chaves em rodem crescente.
 - `krsort($array);` Ordena um array associativo pelas chaves em ordem decrescente.
 - `usort($array, $callback);` Ordena um array usando uma função de comparação definida pelo usuário.

#### Manipulação de objetos

