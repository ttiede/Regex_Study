## Regex  Samples and Rules to review

Caso precise usar ferramentas online para teste:

http://regexr.com/
https://regex101.com/

Podemos definir facilmente a classe de qualquer caractere com o  [A-Z] .
O símbolo + é um outro atalho para definir a quantidade e agora já conhecemos todos:

> * `?`      // zero ou uma vez.
> *  `*`      // zero ou mais vezes.
> *  `+`      // uma ou mais vezes.
> *  `{n}`    // exatamente n vezes.
> *  `{n,}`   // no mínimo n vezes.   
> *  `{n,m}`  //no mínimo n+1 vezes, no máximo m vezes.*

----------

    __\n INSERT [ \t\r\n\f] onde:__

O primeiro caractere é um espaço branco.
Quantifiers como   `?, +, * e {n}`  .

> A classe `\d` é equivalente à classe `[0-9]` A classe `\s` é
> equivalente à classe `[ \t\n\x0B\f\r]` A classe `\w` é equivalente à
> classe `[a-zA-Z_0-9]` A classe `.` reconhece todos os tipos de
> caracteres, exceto o `\n`.

**Exemplo:**

>   `\s // significa whitespace e é um atalho para  [ \t\r\n\f]`
 >   `\w  //significa word char e é uma atalho para  [A-Za-z0-9_] .`
 >   `\t  // é um tab.`
 >   `\r  // é carriage return.`
 >   `\n  // é newline.`
 >   `\f  // é form feed.`
 >   `\w // classe de wordchar  [A-Za-z0-9_]`
 >   `\s  // classe de whitspaces  [ \t\r\n\f]`
 >    `[A-Z] // significa de A até Z, sempre maiúscula.`
 >    `[a-z] // significa de a até z, sempre minúscula.`
 >    `[A-Za-z] // significa A-Z ou a-z.`  
 >    `[abc] // significa a, b ou c.`  
 >    `\b // Âncora que seleciona um word boundary, isso é o início ou fim da palavra.`
>     `\b // Existe a inversão do \b, **non-word-boundary**:\B` (B maiúsculo) .
>     `^ //é uma âncora que selecione o início da string alvo.`
>     `$ //é uma âncora que selecione o fim do alvo.`
>   `? logo //após o quantifier, deixamos ele preguiçoso.`
>   `\n // referência ao () // Declaramos um grupo com ().`

Podemos ter grupos e subgrupos.
Um grupo é retornado na hora de executar, são úteis para selecionar uma parte do match.
Através do  `?:`, dizemos que não queremos ver esse grupo na resposta

Quantifiers são gananciosos por padrão.
Colocando `?` logo após o quantifier, deixamos ele preguiçoso.
Com `\n` podemos referenciar o texto de um grupo dentro da regex, onde n é o número do grupo .


Declaramos um grupo com parênteses `( ).`
Podemos ter grupos e subgrupos, por exemplo: `(\d\d(\d\d))`.
Um grupo faz parte do retorno da regex (na hora de executar) e são úteis para selecionar uma parte do match.

Através do `?:` dizemos que não queremos ver esse grupo na resposta da regex

Definir classe de qualquer caractere com o colchetes
* Exemplo: a classe   `[a1-]`   define 3 caracteres: a,1e -
* Exemplo: a classe   `[A-Z]`   define letras maiúscula de A até Z.

Existem classes predefinidas como  `\w` ou `\s`.

Alguns exemplos de Regex
-------
__Find: CNPJ => 15.123.321/8883-22__
Regex pattern:   `\d{2}\.\d{3}\.\d{3}\/\d{4}\-\d{2}`

__Find:  IPs 126.1.112.34 | 128.126.12.244 | 192.168.0.34__
Regex pattern:   `\d{1,3}.\d{1,3}.\d{1,3}.\d{1,3}`   

__Find:  CEP João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro__
Regex pattern: `\d{5}-\d{3}`

__Find: Phone with DDD (21) 3216-2345__
Regex pattern: `\(\d{2}\)\s*\d{4}\-\d{4}`
__Find:`<code> </code`__
Regex pattern:  `\<\/?code>`

__Find: 09h32min16s.__
Regex pattern:  `\d{2}h\d{2}min\d{2}s` Ou `.{2}h.{2}min.{2}s`

__Find:KMG-8089__
Regex pattern: `[A-Z]{3}\-\d{4}`

__Find: 9.8 - Robson, 7.1 - Teresa, 4.5 - Armênio, 6.5 - Zulu, 7.7 - Stefania, 7.8, 5.0 -   Romeu, 7.2 - Pompilho, 3.1 - Reinaldo, 7.3 - Bernadete, 4.7 - Cinério:__
Regex pattern: `7\.[2-9] - \w+`  **__Regra para possível espaço a + na regra acima__**   `[7]\.[5-9]\s+-\s+\w+`    

__Find:BALEIRO GARROTE SERROTE GOLEIRO ROTEIRO__
**Match apenas com as palavras GARROTE, SERROTE e ROTEIRO.**
Regex pattern:  `[A-Z]*ROT[A-Z]+`

__Find: ?classes+poderosas*__
Regex pattern:`[a-z?*+]+`

__Find: 5asd - asdasd - ASDASD - asd3 - a4asd__
**__o primeiro sendo inválido devido começar com número__**
Regex pattern:`[a-zA-Z]{1}[A-Z, 0-9,a-z]*`

__Find: 11 de Abril de 1995__
Regex pattern:

    [0123]?\d\s+de\s+[A-Z][a-zç]{1,8}\s+de\s+[12]\d{3}
    var DIA  = "[0123]?\\d";
    var _DE_ = "\\s+de\\s+";
    var MES  = "[A-Za-z][a-zç]{1,8}";
    var ANO  = "[12]\\d{3}";

__Find: CPF 111.111.111-11__
Inicio da linha e final
Regex pattern: `^\d{3}\.\d{3}\.\d{3}\-\d{2}$`

__Find:  Caused by: com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure__
**Pegar a linha inciado com **Caused by:**
Regex pattern:  `^Caused by:.*`

__Find: Data: 02/09/1964 ou Data:02/09/1964.__
Regex pattern: `^Data:[\s]?[0-9]{2}\/[0-9]{2}\/[1-9]{4}$`

__Find:  Página: meu-site.html  exercicio.html index.htmlx  https://cursos.alura.com.br/curso.html  __
Regex pattern: .`*\.html$`


__Find: 21 Maio 1993 ,21 Maio de 1993 e 21 de Maio de 1993__

Regex pattern: `([0123]?\d)\s+(de\s+)?([A-Z][a-zç]{1,8})\s+(de\s+)?([12]\d{3})` e `([0123]?\d)\s+(?:de\s+)?([A-Z][a-zç]{1,8})\s+(?:de\s+)?([12]\d{3})`

__Find: 20 de maio de 2015__
Regex Engine para que não devolva o grupo formado pelo de e por um whitespace
Regex pattern:`(?:de\s+)?`

__Find: 111.111.111-11 //Inicio__
__Dividindo em grupos__
Regex pattern:`\d{3}[-.]?\d{3}[.-]?\d{3}[.-]?(\d{2})`


__Find: Z171PZ7AZ23PZ7819AZ78GZ1AZ99IZ34O__
__Descubra a msg por grupos__

Regex pattern: `Z\d{1,}[0-9]?([A-Z])` , `Z\d+(\w)` e `[^Z\d]`


__Find: __ `super.mario@caelum.com.br`   __//extrai super.mario //__ `donkey.kong@alura.com.br` __// extrai donkey.kong //__ `bowser1@alura.com.br` __//extrai bowser1 __
Regex pattern:  `([a-z.]{5,15})\d?@(?:caelum.com.br|alura.com.br)$`

__Find:  `toad@kart...com wario@kart@nintendo.com yoshi@nintendo daisy@nintendo.br ..@email.com`  __
Regex pattern:`^([\w-]\.?)+@([\w-]+\.)+([A-Za-z]{2,4})+$`

__Find:Nico Steppat|14/05/1977|Rua Buarque de Macedo|50|22222-222|Rio de Janeiro__
	__Romulo Henrique|14/06/1993|Rua do Lins|120|12345-322|Rio de Janeiro__
    __Leonardo Cordeiro|01/01/1995|Rua de Campo Grande|01|00001-234|Rio de Janeiro__
Regex pattern:`([\w\s]+)\|(?:\d\d\/\d\d\/\d\d\d\d)\|([\w\s]+)\|(\d{1,4})\|(\d{5}-\d{3})\|(?:[\w\s]{10,})`

__Find: `<h2 class="text-lef">Expressões regulares </h2>`__
Regex pattern:`<(h2)[^>]+>.+</\1>`

__Find: \<h2 class="text-lef">Expressões regulares </h2>__
Regex pattern: `<(h1|h2).+?>([\s\wçõ]+)</\1>>` ou   `<(a)\s+href="(.+)"(?:>(.*)<\/\1>)` ou  


__ Exemplo __
`<(a)\s+href="(.+)"(?:>(.*)<\/\1>)`

> * iniciado com <
> * opcional o grupo contendo o valor a :(a)
> * \s seguido de espaços em branco, \n \r ou \t
> * + sendo uma ou mais vezes
> * contenha href="
> *  bloco com  .  que reconhece todos os tipos de caracteres, exceto o \n.
> *  " fecha o href =""
> * ?: >	Grupo de captura que não é salvo para rechamada posterio terminando em >
> * (.*)  grupo de  nenhum ou N de .
> * < o valor após o grupo
> * \/ a barra com escape
> * \1 referencia ao  primeiro grupo no caso (a)

JAVASCRIPT


    <script>

    var alvo = '12a22b33c';

    //var exp = new RegExp('(\\d\\d)(\\w)', 'g');
    var exp = /(\d\d)(\w)/g;
    // g padrão globalmente (varias vezes o partterns)

    // i independente sem ser sensitive case

    var resultado = exp.exec(alvo);

    console.log(resultado);

    console.log(exp.lastIndex);

    var anoMesDia = '2007-12-31';

    var exp = /-/g

    anoMesDia = anoMesDia.replace(exp, '/');

    var arquivo = '100,200-150,200;20';

    var valores = arquivo.split(',');

    var exp = /[,;\-]/;

    var valores = arquivo.split(exp);

    var codigos = 'A121B12112C12212F12G01';

    var exp = /[A-Za-z]\d+/g

    var codigosExtraidos = codigos.match(exp);

    </script>



   Html com pattern

    <!doctype html>
    <head>
    	<meta charset="UTF-8">
        <title>Testando pattern</title>
    </head>
    <body>
        <form>
            <input pattern="[0-9]*">
            <input type="submit" value="Enviar dados">
        </form>
    </body>

Ruby

    regex = /(\d\d)(\w)/
    alvo = "11a22b33c"
    resultado = regex.match(alvo)
    > resultado.begin 0 #inicio do match inteiro 11a
    > resultado.begin 1 #inicio do grupo 11
    > resultado.end 0 #fim do match inteiro 11a
    > resultado.end 1 #fim do grupo 11


    > regex = /(\d\d)(\w)/ #dois grupos
    > alvo = "12a34b56c"
    > resultados = alvo.scan regex
    => [["12", "a"], ["34", "b"], ["56", "c"]]

    cpfLimpo = "111.222.33396".gsub(/[.-]/,"")
    puts cpfLimpo
    11122233396

    cpf = "111.222.333-96"
    cpf.sub!(/[.-]/,"")
    puts cpf
    "111222.333-96"
PHP

    $string = '2007-12-31';
    $regex = '~(\d{4})-(\d{2})-(\d{2})~';
    $novoTexto = '$3-$2-$1';
    $resultado =  preg_replace($regex, $novoTexto, $string);
    echo $resultado;

    $string = '31-12-2007';
    $regex = '~-~';
    $novoTexto = '/';
    $resultado =  preg_replace($regex, $novoTexto, $string);
    echo $resultado; // 31/12/2007

PYTHON

    >>> import re
    >>> regex = re.compile(r'(\d\d)(\w)')
    >>> alvo = '11a22b33c'
     resultado = re.findall(regex, alvo)
     >>> print resultado
    [('11', 'a'), ('22', 'b'), ('33', 'c')]
    >>> resultado[0]
    ('11', 'a')
    >>> resultado[1]
    ('22', 'b')
    >>> resultado[2]
    ('33', 'c')
    >>> for grupo in resultado:
    ...     print grupo
    ...
    ('11', 'a')
    ('22', 'b')
    ('33', 'c')


    >>> for grupo in resultado:
    ...     print grupo[0] + grupo[1]
    ...
    11a
    22b
    33c

    >>> import re
    >>> regex = '\s-\s'
    >>> novotexto = ': '
    >>> alura = 'Alura - Regex'
    >>> resultado = re.sub(regex, novotexto, alura)
    >>> print resultado
    Alura: Regex
    alvo = '2007-12-31'
    >>> import re
    >>> regex = '-'
    >>> novotexto = '/'
    >>> alvo = '2007-12-31'
    >>> resultado = re.sub(regex, novotexto, alvo)

    >>> print resultado
    2007/12/31

C#
2007-12-31 para 31/12/2007?

    using System.Text.RegularExpressions;

    namespace Rextester
    {
        public class Program
        {
            public static void Main(string[] args)
            {
               string alvo = "2007-12-31";
               Regex regexp = new Regex(@"(\d{4})(-)(\d{2})(-)(\d{2})");

                MatchCollection resultados = regexp.Matches(alvo);
                foreach(Match resultado in resultados)
                {

                    string ano = resultado.Groups[1].Value;
                    string mes = resultado.Groups[3].Value;
                    string dia = resultado.Groups[5].Value;

                    string separador1 = resultado.Groups[2].Value;
                    string separador2 = resultado.Groups[4].Value;

                    Console.WriteLine(string.Format("{0}{1}{2}{3}{4}", dia, separador1, mes, separador2, ano));
                }
            }
        }
    }

"Alura".replaceAll("[Aa]", "*") //*lur*
Como podemos fazer para trocar o separador - por /?

    using System.Text.RegularExpressions;

    namespace Rextester
    {
        public class Program
        {
            public static void Main(string[] args)
            {
               string alvo = "2007-12-31";
               Regex regexp = new Regex(@"(\d{4})(-)(\d{2})(-)(\d{2})");

                MatchCollection resultados = regexp.Matches(alvo);
                foreach(Match resultado in resultados)
                {

                    string ano = resultado.Groups[1].Value;
                    string mes = resultado.Groups[3].Value;
                    string dia = resultado.Groups[5].Value;

                    string separador1 = resultado.Groups[2].Value;
                    string separador2 = resultado.Groups[4].Value;

                    string novaData = string.Format("{0}{1}{2}{3}{4}", dia, separador1, mes, separador2, ano).Replace("-", "/");
                    Console.WriteLine(novaData);
                }
            }
        }
    }
Java

## Regex  Samples and Rules to review

Podemos definir facilmente a classe de qualquer caractere com o  [A-Z] .
O símbolo + é um outro atalho para definir a quantidade e agora já conhecemos todos:

> * `?`      // zero ou uma vez.
> *  `*`      // zero ou mais vezes.
> *  `+`      // uma ou mais vezes.
> *  `{n}`    // exatamente n vezes.
> *  `{n,}`   // no mínimo n vezes.   
> *  `{n,m}`  //no mínimo n+1 vezes, no máximo m vezes.*

----------

    __\n INSERT [ \t\r\n\f] onde:__

O primeiro caractere é um espaço branco.
Quantifiers como   `?, +, * e {n}`  .

> A classe `\d` é equivalente à classe `[0-9]` A classe `\s` é
> equivalente à classe `[ \t\n\x0B\f\r]` A classe `\w` é equivalente à
> classe `[a-zA-Z_0-9]` A classe `.` reconhece todos os tipos de
> caracteres, exceto o `\n`.

**Exemplo:**

>   `\s // significa whitespace e é um atalho para  [ \t\r\n\f]`
 >   `\w  //significa word char e é uma atalho para  [A-Za-z0-9_] .`
 >   `\t  // é um tab.`
 >   `\r  // é carriage return.`
 >   `\n  // é newline.`
 >   `\f  // é form feed.`
 >   `\w // classe de wordchar  [A-Za-z0-9_]`
 >   `\s  // classe de whitspaces  [ \t\r\n\f]`
 >    `[A-Z] // significa de A até Z, sempre maiúscula.`
 >    `[a-z] // significa de a até z, sempre minúscula.`
 >    `[A-Za-z] // significa A-Z ou a-z.`  
 >    `[abc] // significa a, b ou c.`  
 >    `\b // Âncora que seleciona um word boundary, isso é o início ou fim da palavra.`
>     `\b // Existe a inversão do \b, **non-word-boundary**:\B` (B maiúsculo) .
>     `^ //é uma âncora que selecione o início da string alvo.`
>     `$ //é uma âncora que selecione o fim do alvo.`
>   `? logo //após o quantifier, deixamos ele preguiçoso.`
>   `\n // referência ao () // Declaramos um grupo com ().`

Podemos ter grupos e subgrupos.
Um grupo é retornado na hora de executar, são úteis para selecionar uma parte do match.
Através do  `?:`, dizemos que não queremos ver esse grupo na resposta

Quantifiers são gananciosos por padrão.
Colocando `?` logo após o quantifier, deixamos ele preguiçoso.
Com `\n` podemos referenciar o texto de um grupo dentro da regex, onde n é o número do grupo .


Declaramos um grupo com parênteses `( ).`
Podemos ter grupos e subgrupos, por exemplo: `(\d\d(\d\d))`.
Um grupo faz parte do retorno da regex (na hora de executar) e são úteis para selecionar uma parte do match.

Através do `?:` dizemos que não queremos ver esse grupo na resposta da regex

Definir classe de qualquer caractere com o colchetes
* Exemplo: a classe   `[a1-]`   define 3 caracteres: a,1e -
* Exemplo: a classe   `[A-Z]`   define letras maiúscula de A até Z.

Existem classes predefinidas como  `\w` ou `\s`.

Alguns exemplos de Regex
-------
__Find: CNPJ => 15.123.321/8883-22__
Regex pattern:   `\d{2}\.\d{3}\.\d{3}\/\d{4}\-\d{2}`

__Find:  IPs 126.1.112.34 | 128.126.12.244 | 192.168.0.34__
Regex pattern:   `\d{1,3}.\d{1,3}.\d{1,3}.\d{1,3}`   

__Find:  CEP João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro__
Regex pattern: `\d{5}-\d{3}`

__Find: Phone with DDD (21) 3216-2345__
Regex pattern: `\(\d{2}\)\s*\d{4}\-\d{4}`
__Find:`<code> </code`__
Regex pattern:  `\<\/?code>`

__Find: 09h32min16s.__
Regex pattern:  `\d{2}h\d{2}min\d{2}s` Ou `.{2}h.{2}min.{2}s`

__Find:KMG-8089__
Regex pattern: `[A-Z]{3}\-\d{4}`

__Find: 9.8 - Robson, 7.1 - Teresa, 4.5 - Armênio, 6.5 - Zulu, 7.7 - Stefania, 7.8, 5.0 -   Romeu, 7.2 - Pompilho, 3.1 - Reinaldo, 7.3 - Bernadete, 4.7 - Cinério:__
Regex pattern: `7\.[2-9] - \w+`  **__Regra para possível espaço a + na regra acima__**   `[7]\.[5-9]\s+-\s+\w+`    

__Find:BALEIRO GARROTE SERROTE GOLEIRO ROTEIRO__
**Match apenas com as palavras GARROTE, SERROTE e ROTEIRO.**
Regex pattern:  `[A-Z]*ROT[A-Z]+`

__Find: ?classes+poderosas*__
Regex pattern:`[a-z?*+]+`

__Find: 5asd - asdasd - ASDASD - asd3 - a4asd__
**__o primeiro sendo inválido devido começar com número__**
Regex pattern:`[a-zA-Z]{1}[A-Z, 0-9,a-z]*`

__Find: 11 de Abril de 1995__
Regex pattern:

    [0123]?\d\s+de\s+[A-Z][a-zç]{1,8}\s+de\s+[12]\d{3}
    var DIA  = "[0123]?\\d";
    var _DE_ = "\\s+de\\s+";
    var MES  = "[A-Za-z][a-zç]{1,8}";
    var ANO  = "[12]\\d{3}";

__Find: CPF 111.111.111-11__
Inicio da linha e final
Regex pattern: `^\d{3}\.\d{3}\.\d{3}\-\d{2}$`

__Find:  Caused by: com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure__
**Pegar a linha inciado com **Caused by:**
Regex pattern:  `^Caused by:.*`

__Find: Data: 02/09/1964 ou Data:02/09/1964.__
Regex pattern: `^Data:[\s]?[0-9]{2}\/[0-9]{2}\/[1-9]{4}$`

__Find:  Página: meu-site.html  exercicio.html index.htmlx  https://cursos.alura.com.br/curso.html  __
Regex pattern: .`*\.html$`


__Find: 21 Maio 1993 ,21 Maio de 1993 e 21 de Maio de 1993__

Regex pattern: `([0123]?\d)\s+(de\s+)?([A-Z][a-zç]{1,8})\s+(de\s+)?([12]\d{3})` e `([0123]?\d)\s+(?:de\s+)?([A-Z][a-zç]{1,8})\s+(?:de\s+)?([12]\d{3})`

__Find: 20 de maio de 2015__
Regex Engine para que não devolva o grupo formado pelo de e por um whitespace
Regex pattern:`(?:de\s+)?`

__Find: 111.111.111-11 //Inicio__
__Dividindo em grupos__
Regex pattern:`\d{3}[-.]?\d{3}[.-]?\d{3}[.-]?(\d{2})`


__Find: Z171PZ7AZ23PZ7819AZ78GZ1AZ99IZ34O__
__Descubra a msg por grupos__

Regex pattern: `Z\d{1,}[0-9]?([A-Z])` , `Z\d+(\w)` e `[^Z\d]`


__Find: __ `super.mario@caelum.com.br`   __//extrai super.mario //__ `donkey.kong@alura.com.br` __// extrai donkey.kong //__ `bowser1@alura.com.br` __//extrai bowser1 __
Regex pattern:  `([a-z.]{5,15})\d?@(?:caelum.com.br|alura.com.br)$`

__Find:  `toad@kart...com wario@kart@nintendo.com yoshi@nintendo daisy@nintendo.br ..@email.com`  __
Regex pattern:`^([\w-]\.?)+@([\w-]+\.)+([A-Za-z]{2,4})+$`

__Find:Nico Steppat|14/05/1977|Rua Buarque de Macedo|50|22222-222|Rio de Janeiro__
	__Romulo Henrique|14/06/1993|Rua do Lins|120|12345-322|Rio de Janeiro__
    __Leonardo Cordeiro|01/01/1995|Rua de Campo Grande|01|00001-234|Rio de Janeiro__
Regex pattern:`([\w\s]+)\|(?:\d\d\/\d\d\/\d\d\d\d)\|([\w\s]+)\|(\d{1,4})\|(\d{5}-\d{3})\|(?:[\w\s]{10,})`

__Find: `<h2 class="text-lef">Expressões regulares </h2>`__
Regex pattern:`<(h2)[^>]+>.+</\1>`

__Find: \<h2 class="text-lef">Expressões regulares </h2>__
Regex pattern: `<(h1|h2).+?>([\s\wçõ]+)</\1>>` ou   `<(a)\s+href="(.+)"(?:>(.*)<\/\1>)` ou  


__ Exemplo __
`<(a)\s+href="(.+)"(?:>(.*)<\/\1>)`

> * iniciado com <
> * opcional o grupo contendo o valor a :(a)
> * \s seguido de espaços em branco, \n \r ou \t
> * + sendo uma ou mais vezes
> * contenha href="
> *  bloco com  .  que reconhece todos os tipos de caracteres, exceto o \n.
> *  " fecha o href =""
> * ?: >	Grupo de captura que não é salvo para rechamada posterio terminando em >
> * (.*)  grupo de  nenhum ou N de .
> * < o valor após o grupo
> * \/ a barra com escape
> * \1 referencia ao  primeiro grupo no caso (a)

JAVASCRIPT


    <script>

    var alvo = '12a22b33c';

    //var exp = new RegExp('(\\d\\d)(\\w)', 'g');
    var exp = /(\d\d)(\w)/g;
    // g padrão globalmente (varias vezes o partterns)

    // i independente sem ser sensitive case

    var resultado = exp.exec(alvo);

    console.log(resultado);

    console.log(exp.lastIndex);

    var anoMesDia = '2007-12-31';

    var exp = /-/g

    anoMesDia = anoMesDia.replace(exp, '/');

    var arquivo = '100,200-150,200;20';

    var valores = arquivo.split(',');

    var exp = /[,;\-]/;

    var valores = arquivo.split(exp);

    var codigos = 'A121B12112C12212F12G01';

    var exp = /[A-Za-z]\d+/g

    var codigosExtraidos = codigos.match(exp);

    </script>



   Html com pattern

    <!doctype html>
    <head>
    	<meta charset="UTF-8">
        <title>Testando pattern</title>
    </head>
    <body>
        <form>
            <input pattern="[0-9]*">
            <input type="submit" value="Enviar dados">
        </form>
    </body>

Ruby

    regex = /(\d\d)(\w)/
    alvo = "11a22b33c"
    resultado = regex.match(alvo)
    > resultado.begin 0 #inicio do match inteiro 11a
    > resultado.begin 1 #inicio do grupo 11
    > resultado.end 0 #fim do match inteiro 11a
    > resultado.end 1 #fim do grupo 11


    > regex = /(\d\d)(\w)/ #dois grupos
    > alvo = "12a34b56c"
    > resultados = alvo.scan regex
    => [["12", "a"], ["34", "b"], ["56", "c"]]

    cpfLimpo = "111.222.33396".gsub(/[.-]/,"")
    puts cpfLimpo
    11122233396

    cpf = "111.222.333-96"
    cpf.sub!(/[.-]/,"")
    puts cpf
    "111222.333-96"
PHP

    $string = '2007-12-31';
    $regex = '~(\d{4})-(\d{2})-(\d{2})~';
    $novoTexto = '$3-$2-$1';
    $resultado =  preg_replace($regex, $novoTexto, $string);
    echo $resultado;

    $string = '31-12-2007';
    $regex = '~-~';
    $novoTexto = '/';
    $resultado =  preg_replace($regex, $novoTexto, $string);
    echo $resultado; // 31/12/2007

PYTHON

    >>> import re
    >>> regex = re.compile(r'(\d\d)(\w)')
    >>> alvo = '11a22b33c'
     resultado = re.findall(regex, alvo)
     >>> print resultado
    [('11', 'a'), ('22', 'b'), ('33', 'c')]
    >>> resultado[0]
    ('11', 'a')
    >>> resultado[1]
    ('22', 'b')
    >>> resultado[2]
    ('33', 'c')
    >>> for grupo in resultado:
    ...     print grupo
    ...
    ('11', 'a')
    ('22', 'b')
    ('33', 'c')


    >>> for grupo in resultado:
    ...     print grupo[0] + grupo[1]
    ...
    11a
    22b
    33c

    >>> import re
    >>> regex = '\s-\s'
    >>> novotexto = ': '
    >>> alura = 'Alura - Regex'
    >>> resultado = re.sub(regex, novotexto, alura)
    >>> print resultado
    Alura: Regex
    alvo = '2007-12-31'
    >>> import re
    >>> regex = '-'
    >>> novotexto = '/'
    >>> alvo = '2007-12-31'
    >>> resultado = re.sub(regex, novotexto, alvo)

    >>> print resultado
    2007/12/31

C#
2007-12-31 para 31/12/2007?

    using System.Text.RegularExpressions;

    namespace Rextester
    {
        public class Program
        {
            public static void Main(string[] args)
            {
               string alvo = "2007-12-31";
               Regex regexp = new Regex(@"(\d{4})(-)(\d{2})(-)(\d{2})");

                MatchCollection resultados = regexp.Matches(alvo);
                foreach(Match resultado in resultados)
                {

                    string ano = resultado.Groups[1].Value;
                    string mes = resultado.Groups[3].Value;
                    string dia = resultado.Groups[5].Value;

                    string separador1 = resultado.Groups[2].Value;
                    string separador2 = resultado.Groups[4].Value;

                    Console.WriteLine(string.Format("{0}{1}{2}{3}{4}", dia, separador1, mes, separador2, ano));
                }
            }
        }
    }

"Alura".replaceAll("[Aa]", "*") //*lur*
Como podemos fazer para trocar o separador - por /?

    using System.Text.RegularExpressions;

    namespace Rextester
    {
        public class Program
        {
            public static void Main(string[] args)
            {
               string alvo = "2007-12-31";
               Regex regexp = new Regex(@"(\d{4})(-)(\d{2})(-)(\d{2})");

                MatchCollection resultados = regexp.Matches(alvo);
                foreach(Match resultado in resultados)
                {

                    string ano = resultado.Groups[1].Value;
                    string mes = resultado.Groups[3].Value;
                    string dia = resultado.Groups[5].Value;

                    string separador1 = resultado.Groups[2].Value;
                    string separador2 = resultado.Groups[4].Value;

                    string novaData = string.Format("{0}{1}{2}{3}{4}", dia, separador1, mes, separador2, ano).Replace("-", "/");
                    Console.WriteLine(novaData);
                }
            }
        }
    }
Java

Como podemos, através de regex alterar o formato de uma data 2007-12-31 para 31-12-2007?

    public class TestandoRegex {

        public static void main(String[] args) {

            String data = "2007-12-31";
            Pattern pattern = Pattern.compile("(\\d{4})(-)(\\d{2})(-)(\\d{2})");
            Matcher matcher = pattern.matcher(data);

            if (matcher.matches()) {

                String ano = matcher.group(1);
                String mes = matcher.group(3);
                String dia = matcher.group(5);

                String separador1 = matcher.group(2);
                String separador2 = matcher.group(4);

                System.out.println(dia + separador1 + mes + separador2 + ano);
            }
        }
    }



"Caelum".replaceAll("[Cm]", "*") //*aelu*
Como podemos fazer para trocar o separador - por /?

    novaData.replaceAll("-", "/");
    // Devido String ser imutável
    novaData = novaData.replaceAll("-", "/");
