REFERÊNCIA: https://www.youtube.com/watch?v=K8L6KVGG-7o

Ver também: https://www.w3schools.com/python/gloss_python_regex_metacharacters.asp

Para um nível avançado, veja: https://docs.python.org/3/howto/regex.html#non-capturing-and-named-groups

# EXPRESSÕES REGULARES (REGULAR EXPRESSIONS - REGEX))

**METACARATERES** (., ^, $, *, +, ?, { }, [ ], ( ), \ e |)

Caso se queira obter o valor literal de um metacaractere, é necessário utilizar "\\" antes desses caracteres.

Exemplo:
texto: "Bom dia..."

padrão sem o scape: ".+"

resultado: ["Bom dia..."] 

padrão com o scape "\\":  "\\.+"

resultado: ["..."]


**CARACTERES ESPECIAIS UTILIZADOS EM REGEX**

Temos ainda, caracteres especiais, que posseum valores próprios em REGEX, conforme detalhado a seguir:

. - Qualquer caractere, exceto nova linha

\d - Dígitos (0-9)

\D - NÃO dígitos (0-9)

\w - Caracteres (a-z, A-Z, 0-9, _)

\W - NÃO caracteres (todos os demais não especificados no item anterior)

\s - Espaços em branco (espaço, tabulação, nova linha)

\S - NÃO é espaço em branco (espaço, tabulação, nova linha)

\A - Retorna uma coincidência se os caracteres espedificados estão no início de uma sentença

\b - Palavra na borda (retorna coincidência onde o texto contém um espaço em branco)

\B - Palavra NÃO na borda (retorna coincidência onde o texto NÃO CONTÉM um espaço em branco)

^ - Início de uma sentença (colocar antes dos caracteres)

$ - Final de uma sentença (colocar após os caracteres)

\Z - Retorna uma coincidência se os caracteres espedificados estão no final de uma sentença (colocar após os caracteres)

[] - Coincide caracteres que estão entre colchetes

[^ ] - Coincide caracteres que não estão entre colchetes

| - ou

( ) - grupo - Grupos são padrões a serem retornados. Você pode buscar um padrão e retornar apenas o que está no grupo (entre parêntesis)



**QUANTIFICADORES**

São caracteres utilizados para delimitar quantidades de ocorrências, conforme detalhado a seguir:

? - 0 ou uma ocorrência

\* - 0 ou mais ocorrências

\+ - 1 ou mais ocorrências

{3} - Quantidade exata (neste caso, 3)

{1,4} - Intervalo entre números (mínimo, máximo)


**TRABALHANDO COM SETS**

Sets são conjuntos entre colchetes com significados especiais. Veja alguns exemplos:

[arn] - Retorna uma coincidência quando ao menos um dos caracteres especificados está presente (a, r ou n)

[a-n] - Retorna uma coincidência para qualquer caractere em caixa baixa, alfabeticamente entre a e n

[^arn] - Retorna uma coincidência para qualquer caractere EXCETO a, r, and n

[0123] - Retorna uma coincidência onde qualuqer dos dígitos expecidifcados (0, 1, 2, or 3) esteja presente

[^0123] - Retorna uma coincidência onde qualuqer dos dígitos expecidifcados (0, 1, 2, or 3)NÃO esteja presente

[0-9] - Retorna uma coincidência para qualquer dos dígitos entre 0 e 9

[a-zA-Z] - Retorna uma coincidência para qualquer caractere alfabeticamente entre a e z, caixa baixa ou caixa alta

[+] - Dentro de um set +, *, .,|, (), $,{} têm significado literal. Por exemplo, [+] significa: retornar uma coincidência para qualuqer caractere "+" no texto


**TRABALHANDO COM GRUPOS**

Grupos são utilizados para capturar apenas a parte desejada de uma sentença. Apenas a parte que está entre parêntesis "()", será retornada.
Exemplo: 

texto = "123abc123 abc texto"

padrão sem grupo: "\d+\D+\d+"

resultado: ["123abc123"]

padrão com grupo: "\d+(\D+)\d+"

resultado: ["abc"]

Observação: quando se utiliza expressões com grupos, mas não se deseja capturar o conteúdo, é necessário indicar o Python, utlizando o símbolo "?:".
Exemplo: Na expressão regular r"abc(isto|aquilo)(segunda_expresao)", caso o desejo seja apenas capturar o segundo grupo, use:
r"abc(?:isto|aquilo)(segunda_expresao)" 
ou simplesmente troque (abc) por (?:abc) se não deseja capturar o conteúdo do grupo.
Exemplo:

texto = "123abc 456abc texto"

padrão com grupo: "(123|456)+\D+\s+"

resultado: ['123', '456']

padrão desconsiderando o grupo: "(?:123|456)+\D+\s+"

resultado: ['123abc', '456abc']


**ALGUNS EXEMPLOS DE CARACTERES ESPECIAIS, COMUNS A VÁRIAS LINGUAGENS DE PROGRAMAÇÃO TAMBÉM USADOS EM REGEX:**


\n - Nova linha

\t - Tabulação

\s - Não é apenas espaço, mas também outros meta caracteres (\s = [\t\n\r\f\v])

' ' - espaço
