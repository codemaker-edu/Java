# Caracteres y textos avanzados

Con caracteres y textos se pueden realizar muchas acciones en programación, muy habituales en campos como la Ciberseguridad.

## Cadenas de texto (`String`)

Para guardar texto (palabras, frases), usamos String. A diferencia de int o double, String no es un tipo primitivo, es una clase.

Esto tiene dos implicaciones fundamentales:
- **Tiene métodos**: Acciones ya programadas que podemos usar (saber su longitud, pasar a mayúsculas, etc.).
- **Se guarda en memoria como un objeto**: Internamente es como un array de caracteres (char), donde cada letra tiene una posición o índice que empieza siempre en 0.

### Métodos (funciones) útiles de `String`

Un String no se puede modificar (es inmutable). Si usas un método como los siguientes, no se cambia el `String` original. Si lo necesitas, puedes guardar lo que el método te devuelve (contesta) en un `String` nuevo.

Veamos los principales métodos en la siguiente tabla. Supongamos que tenemos la variable **`String frase = "Hola a todos";`**. Podemos usar los siguientes métodos:

| Método                            | Descripción                                      |Devuelve (contesta)    | Ejemplo                               |
| ---                               | ---                                              |---                    | ---                                                     |
| `length()`                        | Devuelve el número de caracteres.                |`int`                  | `frase.length()`  → `12`                                |
| `charAt(int i)`                   | Devuelve el carácter en el índice i.             |`char`                 | `frase.charAt(1)` → `o`                                 |
| `equals(String s)`                | Compara si el contenido es idéntico.             |`boolean`              | `frase.equals("Adios")` → `false`                       |
| `equalsIgnoreCase(String s)`      | Igual que equals pero ignora may/min.            |`boolean`              | `frase.equalsIgnoreCase("HoLa A ToDoS")` → `true`       |
| `toUpperCase()`                   | Devuelve una nueva cadena en mayúsculas.         |`String`               | `frase.toUpperCase()` → `"HOLA A TODOS"`                |
| `toLowerCase()`                   | Devuelve una nueva cadena en minúsculas.         |`String`               | `frase.toLowerCase()` → `"hola a todos"`                |
| `substring(int inicio, int fin)`  | Devuelve la subcadena desde inicio hasta fin-1.  |`String`               | `frase.substring(1, 3)` → `"ola"`                       |
| `indexOf(String s)`               | Devuelve el índice de la primera aparición de s. |`int`                  | `frase.indexOf("la")` → `2`                             |
| `contains(String s)`	            | Devuelve true si el texto contiene a s.	         |`boolean`              | `frase.contains("ol")` → `true`                         |
| `replace(char old, char new)`     |	Cambia unas letras por otras.	                   |`String`               | `frase.replace('a', 'o')` → `"Holo o todos"`            |
| `startsWith(String s)`	          | Comprueba si empieza por ese texto.              |`boolean`              | `frase.startsWith("H")` → `true`                        |
| `split(String s)`                 | Parte el String en trozos                        |`String[]`             | `frase.split(" ") → `{"Hola", "a", "todos"}`            |

### Errores comunes

**1. Comparar con `==`**: en Java, para comparar el contenido de dos textos no se usa `==`, si no `.equals()`.

**2. El índice fuera de rango**: si intentas acceder a una posición que no existe, el programa "explotará" con un error llamado `StringIndexOutOfBoundsException`.

### Secuencias de Escape

Para incluir caracteres especiales dentro de un String, usamos la barra invertida `\`:

- `\n`: Salto de línea.
- `\t`: Tabulador.
- `\"`: Comillas dobles (para poder poner comillas dentro del String).
- `\\`: Barra invertida (para poder poner la barra misma).

## Caracteres (`char`)

Cuando guardamos una variable `char`, Java no guarda realmente una letra o caracter, guarda en la memoria un número. Para saber qué número le corresponde a cada letra, podemos consultar la tabla ASCII.

| Num | Char | Num | Char | Num | Char | Num | Char |
|-----|------|-----|------|-----|------|-----|------|
| 32  | (sp) | 56  | 8    | 80  | P    | 104 | h    |
| 33  | !    | 57  | 9    | 81  | Q    | 105 | i    |
| 34  | "    | 58  | :    | 82  | R    | 106 | j    |
| 35  | #    | 59  | ;    | 83  | S    | 107 | k    |
| 36  | $    | 60  | <    | 84  | T    | 108 | l    |
| 37  | %    | 61  | =    | 85  | U    | 109 | m    |
| 38  | &    | 62  | >    | 86  | V    | 110 | n    |
| 39  | '    | 63  | ?    | 87  | W    | 111 | o    |
| 40  | (    | 64  | @    | 88  | X    | 112 | p    |
| 41  | )    | 65  | A    | 89  | Y    | 113 | q    |
| 42  | *    | 66  | B    | 90  | Z    | 114 | r    |
| 43  | +    | 67  | C    | 91  | [    | 115 | s    |
| 44  | ,    | 68  | D    | 92  | \    | 116 | t    |
| 45  | -    | 69  | E    | 93  | ]    | 117 | u    |
| 46  | .    | 70  | F    | 94  | ^    | 118 | v    |
| 47  | /    | 71  | G    | 95  | _    | 119 | w    |
| 48  | 0    | 72  | H    | 96  | `    | 120 | x    |
| 49  | 1    | 73  | I    | 97  | a    | 121 | y    |
| 50  | 2    | 74  | J    | 98  | b    | 122 | z    |
| 51  | 3    | 75  | K    | 99  | c    | 123 | {    |
| 52  | 4    | 76  | L    | 100 | d    | 124 | \|   |
| 53  | 5    | 77  | M    | 101 | e    | 125 | }    |
| 54  | 6    | 78  | N    | 102 | f    | 126 | ~    |
| 55  | 7    | 79  | O    | 103 | g    |     |      |

Sabiendo esto, podemos hacer algunas operaciones interesantes. Por ejemplo, podemos sumar o restar a un caracter:
```java
char letra = 'a';
System.out.println(letra+1); //Imprime 98
```
O pasar números a caracteres:
```java
System.out.println( (char)100 ); //Imprime 'd'
```
