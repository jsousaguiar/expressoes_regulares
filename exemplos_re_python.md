# EXEMPLOS DE UTILIZAÇÃO DE EXPRESSÕES REGULARES NO PYTHON
Antes de utilzar a função "re", é necessário realizar a importação, da seguinte forma:
```
import re
```

Capturar apenas os números de uma string:
```
texto =  '894654ajkjj teste123'
ocorrencias = re.findall(r'\s\D+(\d+)', texto)
print(ocorrencias)
>>> ['123']
```

Capturar uma coordenada precedida do termo "Latidude" ou "Longitude":

```
texto =  "Latitude: -28.098883 Longitude: -048.675000 e outras informações relevantes"
ocorrencias = re.findall(r'(?:Latitude|Longitude):\s(-?\d{2,3}\.\d{6})', texto)
#ocorrencias = re.sub(r"\.",",",str(ocorrencias))
print(ocorrencias)
>>> ['-28.098883', '-048.675000']
```

Capturar sequências numéricas que atendam determinados padrões:

```
texto = '''
abcdefghijklmnopqurtuvwxyz
ABCDEFGHIJKLMNOPQRSTUVWXYZ
1234567890
Ha HaHa
MetaCharacters (Need to be escaped):
. ^ $ * + ? { } [ ] \ | ( )
coreyms.com
321-555-4321
123.555.1234
123*555*1234
800-555-1234
900-555-1234
Mr. Schafer
Mr Smith
Ms Davis
Mrs. Robinson
mr. T
'''
padrao = r'\d{3}[\-\.\*]\d{3}\D\d{4}'
ocorrencias = re.findall(padrao, texto)
print(ocorrencias)
>>> ['321-555-4321', '123.555.1234', '123*555*1234', '800-555-1234', '900-555-1234']
````

Capturar os nomes precedidos pelos pronomes "Mr", "Ms" ou "Mrs":
 ```
 padrao = r'm(?:r|s)+[\.]?\s[a-z]+'
ocorrencias = re.findall(padrao, texto,re.IGNORECASE)
print(ocorrencias)
>>> ['Mr. Schafer', 'Mr Smith', 'Ms Davis', 'Mrs. Robinson', 'mr. T']
```

No regex, os padrões \1 \2 \3 etc. referem-se a grupos capturados. Veja exemplos:

Procura por palavras repetidas em sequência. O \\1 refere-se ao grupo capturado (o que tem "(\w+)")
```
texto = "este texto tem tem palavras 123 repetidas repetidas"
re.findall(r"\s(\w+)\s\1", texto)
>>> ['tem', 'repetidas']
```
Na função re.sub, pode-se utilizar os padrões \1 \2 \3 etc. para se referir a grupos capturados na regex principal. Exemplo abaixo:
```
texto = "vou usar os números 12343 e 54323 em outro lugar.."
novo_texto = re.sub(r"^\D+(\d+)\D+(\d+)\D+$", r"Extraí os números \1 e \2 do texto, podendo invertê-los: \2 e \1", texto)
print(novo_texto)
>>> 'Extraí os números 12343 e 54323 do texto, podendo invertê-los: 54323 e 12343'
```

A captura e referências de grupos também pode ser útil para se substituir apenas parte de um texto, mantendo-se o restante, você precisa de um match da string inteira, mas dividindo as partes sequenciais em grupos. 
Assim, você pode substituir toda a string por um novo texto ou utilizar os grupos que criou para montar a nova string.
```
texto = "Meu nome é substituir."
nome = "João"
novo_texto = re.sub(r"(.*\s)([A-Za-z]+)(\.?)$", f"\\1{nome}\\3", texto)
print(novo_texto)
>>> 'Meu nome é João.'
```

Você pode ainda indicar o(s) grupo(s) que não irá utilizar, para que sejam desconsiderados na contagem, facilitando a referência.
```
novo_texto = re.sub(r"(.*\s)(?:[A-Za-z]+)(\.?)$", f"\\1{nome}\\2", texto)
print(novo_texto)
>>> 'Meu nome é João.'
```
# EXEMPLOS DE UTILIZAÇÃO DE EXPRESSÕES REGULARES NO PANDAS

Primeiramente, é necessário importar o Pands, da seguinte forma:
```
import pandas as pd
```
Depois, precisamos criar ou importar um DataFrame existente. No exemplo abaixo, iremos criar um DataFrame simples:
```
linhas = ['Fulano de tal','titular','sim',2],['Beltrano da Silva','titular','sim',1],['Beltrano Resende','cotitular','sim',1],['Investigado Anonimo','titular','não',2]
colunas = ['conta_nome_titular','tipo_relacionamento','investigado','tipo_pessoa']

df_teste = pd.DataFrame(linhas,columns=colunas)
```
Neste exemplo, iremos localizar os dados em que a coluna "conta_nome_titular" possui a expressão "trano":
```
linhas = df_teste['conta_nome_titular'].astype(str).str.contains(r'\D+trano\D+',regex=True)
colunas = ['conta_nome_titular','tipo_relacionamento']
print(df_teste.loc[linhas,colunas])
> > > 
  conta_nome_titular tipo_relacionamento
1  Beltrano da Silva             titular
2   Beltrano Resende           cotitular
```
