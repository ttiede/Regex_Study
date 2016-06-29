# Regex  Samples and Rules to review

Podemos definir facilmente a classe de qualquer caractere com o ``` [A-Z] ```.


O símbolo + é um outro atalho para definir a quantidade e agora já conhecemos todos:

* ``` ?      // zero ou uma vez.```
* ``` *      // zero ou mais vezes. ```
* ``` +      // uma ou mais vezes.```
* ``` {n}    // exatamente n vezes.```
* ``` {n,}   // no mínimo n vezes. ```  
* ``` {n,m}  //no mínimo n+1 vezes, no máximo m vezes.```

##### ``` [ \t\r\n\f]```  onde:

O primeiro caractere é um espaço branco.
Quantifiers como  ``` ?, +, * e {n}  ```.
*  ```\s // significa whitespace e é um atalho para  [ \t\r\n\f] ```
*  ``` \w  //significa word char e é uma atalho para  [A-Za-z0-9_] ```.
* ``` \t  // é um tab.```
* ``` \r  // é carriage return.```
* ``` \n  // é newline.```
* ``` \f  // é form feed.```
* ``` \w // classe de wordchar  [A-Za-z0-9_] ```
* ``` \s  // classe de whitspaces  [ \t\r\n\f] ```
*  ``` [A-Z] // significa de A até Z, sempre maiúscula. ```
*  ``` [a-z] // significa de a até z, sempre minúscula. ```
*  ``` [A-Za-z] // significa A-Z ou a-z.  ```
*  ``` [abc] // significa a, b ou c.  ```
*  ``` \b //é uma âncora que seleciona um word boundary, isso é o início ou fim da palavra.```
*  ```  \b // Existe a inversão do \b, **non-word-boundary**:\B` (B maiúsculo) .```
*  ``` ^ //é uma âncora que selecione o início da string alvo.```
*  ``` $ //é uma âncora que selecione o fim do alvo.```
*  ```? logo // após o quantifier, deixamos ele preguiçoso.```
* ``` \n // referência ao grupo /\1```
* ```() // Declaramos um grupo com ().```
Podemos ter grupos e subgrupos.
Um grupo é retornado na hora de executar, são úteis para selecionar uma parte do match.
Através do  ```?:```, dizemos que não queremos ver esse grupo na resposta

Quantifiers são gananciosos por padrão.
Colocando ? logo após o quantifier, deixamos ele preguiçoso.
Com \n podemos referenciar o texto de um grupo dentro da regex, onde n é o número do grupo .


Declaramos um grupo com parênteses ( ).
Podemos ter grupos e subgrupos, por exemplo: (\d\d(\d\d)).
Um grupo faz parte do retorno da regex (na hora de executar) e são úteis para selecionar uma parte do match.

Através do ?: dizemos que não queremos ver esse grupo na resposta da regex

Definir classe de qualquer caractere com o colchetes
* Exemplo: a classe  ``` [a1-]  ``` define 3 caracteres: a,1e -
* Exemplo: a classe  ``` [A-Z]  ``` define letras maiúscula de A até Z.

Existem classes predefinidas como  ```\w``` ou ```\s```.

### Samples

__Find__: ```CNPJ => 15.123.321/8883-22```

**Regex pattern:**   ```\d{2}\.\d{3}\.\d{3}\/\d{4}\-\d{2}```

__Find__: ``` IPs 126.1.112.34 | 128.126.12.244 | 192.168.0.34```

**Regex pattern:**  ``` \d{1,3}.\d{1,3}.\d{1,3}.\d{1,3} ```  

__Find__: ``` CEP
    João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro```

**Regex pattern:** ```\d{5}-\d{3}```

__Find__: ```Phone with DDD (21) 3216-2345```

**Regex pattern:**``` \(\d{2}\)\s*\d{4}\-\d{4}```

__Find__:```<code> </code```

**Regex pattern:** ``` \<\/?code> ```

__Find__: ```09h32min16s.```

**Regex pattern:** ``` \d{2}h\d{2}min\d{2}s```
 Ou
``` .{2}h.{2}min.{2}s ```

__Find__:```KMG-8089```

**Regex pattern:**: ```[A-Z]{3}\-\d{4}```

__Find__:``` 9.8 - Robson, 7.1 - Teresa, 4.5 - Armênio, 6.5 - Zulu, 7.7 - Stefania, 7.8, 5.0 -   
      Romeu, 7.2 - Pompilho, 3.1 - Reinaldo, 7.3 - Bernadete, 4.7 - Cinério:```

**Regex pattern:**:``` 7\.[2-9] - \w+ ```
  __Regra para possível espaço a + na regra acima__  
``` [7]\.[5-9]\s+-\s+\w+ ```   

__Find__:```BALEIRO GARROTE SERROTE GOLEIRO ROTEIRO``` **Match apenas com as palavras GARROTE, SERROTE e ROTEIRO.**

**Regex pattern:**: ``` [A-Z]*ROT[A-Z]+ ```

__Find__: ```?classes+poderosas*```

**Regex pattern:**:```pattern:[a-z?*+]+```

__Find__: ```5asd - asdasd - ASDASD - asd3 - a4asd```
**o primeiro sendo inválido devido começar com número**

**Regex pattern:**:```[a-zA-Z]{1}[A-Z, 0-9,a-z]*```


__Find__: ```11 de Abril de 1995```

**Regex pattern:**
```
[0123]?\d\s+de\s+[A-Z][a-zç]{1,8}\s+de\s+[12]\d{3}
var DIA  = "[0123]?\\d";
var _DE_ = "\\s+de\\s+";
var MES  = "[A-Za-z][a-zç]{1,8}";
var ANO  = "[12]\\d{3}";
```
__Find__: ```CPF 111.111.111-11 //Inicio da linha e final ```

**Regex pattern:**:
```
^\d{3}\.\d{3}\.\d{3}\-\d{2}$
```

__Find__: ``` Caused by: com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure```
**Pegar a linha inciado com **Caused by:**

**Regex pattern:**:
```
^Caused by:.*
```

__Find__: ```Data: 02/09/1964 ou Data:02/09/1964.```

**Regex pattern:**:
```
^Data:[\s]?[0-9]{2}\/[0-9]{2}\/[1-9]{4}$
```

__Find__: ```Leonardo criou a página meu-site.html  exercicio.html index.htmlx  https://cursos.alura.com.br/curso.html```

**Regex pattern:**: ```.*\.html$```


__Find__: ```21 Maio 1993```
,
```21 Maio de 1993```
 e
 ```21 de Maio de 1993```

**Regex pattern:**: ```([0123]?\d)\s+(de\s+)?([A-Z][a-zç]{1,8})\s+(de\s+)?([12]\d{3})```

```([0123]?\d)\s+(?:de\s+)?([A-Z][a-zç]{1,8})\s+(?:de\s+)?([12]\d{3})```


__Find__: ```20 de maio de 2015```

 Regex Engine para que não devolva o grupo formado pelo de e por um whitespace

**Regex pattern:**:
```
 (?:de\s+)?
 ```

__Find__: ```111.111.111-11 //Inicio```

__Dividindo em grupos__

 **Regex pattern:**:
 ```
  \d{3}[-.]?\d{3}[.-]?\d{3}[.-]?(\d{2})
  ```

__Find__:```Z171PZ7AZ23PZ7819AZ78GZ1AZ99IZ34O```

__Descubra a msg por grupos__

**Regex pattern:**:
   ```
   Z\d{1,}[0-9]?([A-Z])
   Z\d+(\w)
   [^Z\d]
   ```

__Find__:``` super.mario@caelum.com.br //extrai super.mario
   donkey.kong@alura.com.br extrai donkey.kong
   bowser1@alura.com.br extrai bowser1 ```


**Regex pattern:**: ``` ([a-z.]{5,15})\d?@(?:caelum.com.br|alura.com.br)$ ```

__Find__: ``` toad@kart...com wario@kart@nintendo.com yoshi@nintendo daisy@nintendo.br ..@email.com ```

**Regex pattern:**:```^([\w-]\.?)+@([\w-]+\.)+([A-Za-z]{2,4})+$```

__Find__:```
Nico Steppat|14/05/1977|Rua Buarque de Macedo|50|22222-222|Rio de Janeiro

Romulo Henrique|14/06/1993|Rua do Lins|120|12345-322|Rio de Janeiro

Leonardo Cordeiro|01/01/1995|Rua de Campo Grande|01|00001-234|Rio de Janeiro```

**Regex pattern:**:
```
([\w\s]+)\|(?:\d\d\/\d\d\/\d\d\d\d)\|([\w\s]+)\|(\d{1,4})\|(\d{5}-\d{3})\|(?:[\w\s]{10,})
```

__Find__: ```<h2 class="text-lef">Expressões regulares </h2>```

**Regex pattern:**:```<(h2)[^>]+>.+</\1>```

__Find__: ```<h2 class="text-lef">Expressões regulares </h2>```

**Regex pattern:**:```<(h1|h2).+?>([\s\wçõ]+)</\1>>```


### JAVASCRIPT ###

```
<script>

var alvo = '12a22b33c';

var exp = new RegExp('(\d\d)(\w)', 'g');

// g padrão globalmente (varias vezes o partterns)

// i independente sem ser sensitive case

var resultado = exp.exec(textoTarget;)

console.log(resultado);

console.log(exp.lastIndex);

</script>
```
