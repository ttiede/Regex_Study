# Regex_Study

Podemos definir facilmente a classe de qualquer caractere com o [A-Z].


O símbolo + é um outro atalho para definir a quantidade e agora já conhecemos todos:

? - zero ou uma vez.
* - zero ou mais vezes.
+ - uma ou mais vezes.
{n} - exatamente n vezes.
{n,} - no mínimo n vezes.
{n,m} - no mínimo n+1 vezes, no máximo m vezes.

[ \t\r\n\f] onde:
O primeiro caractere é um espaço branco.
\t é um tab.
\r é carriage return.
\n é newline.
\f é form feed.
\w - classe de wordchar [A-Za-z0-9_]
\s - classe de whitspaces [ \t\r\n\f]


[A-Z] significa de A até Z, sempre maiúscula.
[a-z] significa de a até z, sempre minúscula,
[A-Za-z] significa A-Z ou a-z.
[abc] significa a, b ou c.


 quantifiers como ?, +, * e {n}.
\s significa whitespace e é um atalho para [ \t\r\n\f].
\w significa word char e é uma atalho para [A-Za-z0-9_].

Definir classe de qualquer caractere com o colchetes
Exemplo: a classe [a1-] define 3 caracteres: a,1e -
Exemplo: a classe [A-Z] define letras maiúscula de A até Z.
Existem classes predefinidas como \w ou \s

[a-z\d]

First Chapter
Find:  CNPJ
  15.123.321/8883-22
  Regex pattern:  
  \d{2}\.\d{3}\.\d{3}\/\d{4}\-\d{2}


Find:  IPS
  126.1.112.34
  128.126.12.244
  192.168.0.34
  Regex pattern:  
 \d{1,3}.\d{1,3}.\d{1,3}.\d{1,3}  

Find: CEP
    João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro
Regex pattern:
  \d{5}-\d{3}

Find: Phone with DDD
  (21) 3216-2345
Regex pattern:
   \(\d{2}\)\s*\d{4}\-\d{4}

Find:  <code> </code>
Regex pattern:
  \<\/?code>

Find: 09h32min16s.
Regex pattern:
  \d{2}h\d{2}min\d{2}s
  .{2}h.{2}min.{2}s

Find:KMG-8089
Regex pattern:[A-Z]{3}\-\d{4}

Find: 9.8 - Robson, 7.1 - Teresa, 4.5 - Armênio, 6.5 - Zulu, 7.7 - Stefania, 7.8, 5.0 -   
      Romeu, 7.2 - Pompilho, 3.1 - Reinaldo, 7.3 - Bernadete, 4.7 - Cinério
Regex pattern: 7\.[2-9] - \w+
               Regra para possível espaço a + na regra acima
               [7]\.[5-9]\s+-\s+\w+   
Find:BALEIRO GARROTE SERROTE GOLEIRO ROTEIRO
  match apenas com as palavras GARROTE, SERROTE e ROTEIRO.
Regex pattern: [A-Z]*ROT[A-Z]+

Find:?classes+poderosas*
Regex pattern:[a-z?*+]+
Find: 5asd - asdasd - ASDASD - asd3 - a4asd
o primeiro sendo inválido
Regex pattern: [a-zA-Z]{1}[A-Z, 0-9,a-z]*
Find:
Regex pattern: 11 de Abril de 1995
    [0123]?\d\s+de\s+[A-Z][a-zç]{1,8}\s+de\s+[12]\d{3}
    var DIA  = "[0123]?\\d";
    var _DE_ = "\\s+de\\s+";
    var MES  = "[A-Za-z][a-zç]{1,8}";
    var ANO  = "[12]\\d{3}";

Find:
Regex pattern:
Find:
Regex pattern:
Find:
Regex pattern:
