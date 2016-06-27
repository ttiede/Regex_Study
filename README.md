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

Quantifiers como  ``` ?, +, * e {n}  ```.
*  ```\s // significa whitespace e é um atalho para  [ \t\r\n\f] ```
*  ``` \w  //significa word char e é uma atalho para  [A-Za-z0-9_] ```.

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
