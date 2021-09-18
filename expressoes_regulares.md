REFERÊNCIA: https://www.youtube.com/watch?v=K8L6KVGG-7o

Ver também: https://www.w3schools.com/python/gloss_python_regex_metacharacters.asp

Para um nível avançado, veja: https://docs.python.org/3/howto/regex.html#non-capturing-and-named-groups

# EXPRESSÕES REGULARES (REGULAR EXPRESSIONS - REGEX))

Metacaracteres precisam ser desconsiderados (escaped). Para isso precisam ser precedidos de \ caso queira o valor literal dos caracteres:
```. ^ $ * + ? { } [ ] \ | ( )```

```.```       - Qualquer caractere, exceto nova linha

```\d```      - Dígitos (0-9)

```\D```      - Não dígitos (0-9)

```\w```      - Caracteres (a-z, A-Z, 0-9, _)

```\W```      - Não caracteres

```\s```      - Espaços em branco (espaço, tabulação, nova linha)

```\S```      - Não é espaço em branco (espaço, tabulação, nova linha)

```\A``` 	    - Retorna uma coincidência se os caracteres espedificados estão no início de uma sentença

```\b```      - Palavra Word Boundary (Returns a match where the string contains a white space character)

```\B```      - Not a Word Boundary (Returns a match where the string DOES NOT contain a white space character)

```^```       - Início de uma sentença

```$```       - Final de uma sentença

```\Z``` 	    - Retorna uma coincidência se os caracteres espedificados estão no final de uma sentença

```\s``` 	    - Retorna uma coincidência quando a sentença contém espaço(s) em branco

```\S``` 	    - Retorna uma coincidência quando a sentença NÃO CONTÉM espaço(s) em branco

```[]```      - Coincide caracteres que estão entre colchetes

```[^ ]```    - Coincide caracteres que não estão entre colchetes

```|```       - ou

```( )```     - grupo

## Quantificadores:
```*```       - 0 ou mais

```+```       - 1 ou mais

```?```       - 0 ou mais

```{3}```     - Quantidade exata

```{3,4}```   - Intervalo entre números (mínimo, máximo)

## Sets (W3Schools)

### Um conjunto (set) entre colchetes possui significados especiais:
Set 	      Descrição

```[arn]``` 	    Retorna uma coincidência quando ao menos um dos caracteres especificados está presente (a, r, or n) 	

```[a-n]``` 	    Retorna uma coincidência para qualquer caractere em caixa baixa, alfabeticamente entre a e n 	

```[^arn]``` 	    Retorna uma coincidência para qualquer caractere EXCETO ```a, r, and n```

```[0123]``` 	    Retorna uma coincidência onde qualuqer dos dígitos expecidifcados (0, 1, 2, or 3) esteja presente

```[0-9]``` 	    Retorna uma coincidência para qualquer dos dígitos entre 0 e 9 	

```[0-5][0-9]``` 	Retorna uma coincidência para qualquer número de dois dígitos de 00 a 59 	

```[a-zA-Z]``` 	  Retorna uma coincidência para qualquer caractere alfabeticamente entre a e z, caixa baixa ou caisa alta

```[+]``` 	      Em sets, ```+, *, ., |, (), $,{}``` têm significado especial, então ```[+]``` significa: retornar uma coincidência para qualuqer ```+``` caractere no texto

### Alguns caracteres especiais comuns a várias linguagens

```\n```  - Nova linha

```\t```  - Tabulação

### ```\s``` não é apenas espaço, mas também outros meta caracteres. 

```\s``` = ```[\t\n\r\f\v]```

```' '``` (espaço)

```\t``` TAB

```\n``` nova linha (quebra de linha)

```\r``` retono de cursor (volta o cursor para o inicio da linha)

```\f``` avanço de página

```\v``` vertical TAB - (usado em configurações de impressora)

### Trabalhando com grupos
Quando se utiliza expressões com grupos apenas para capturar o retorno booleano (True or False), pode ser útil indicar que não irá utilizar o conteúdo,
o que evita advertências do Python (warnings).

Exemplo: Na expressão regular ```r"abc(isto|aquilo)"```, use ```r"abc(?:isto|aquilo)"``` ou simplesmente troque ```(abc)``` por ```(?:abc)``` se espera apenas o resultado booleano.

## Exemplo de regex
```[1-5]```	- Intervalo entre 1 e 5

```[a-zA-Z]``` - Coincide de a a z caixa baixa e caixa alta

