# Cadenas de Caracteres (Clase String)

Para guardar texto (palabras, frases), usamos String. A diferencia de int o double, String no es un tipo primitivo, es una clase.

Esto tiene dos implicaciones fundamentales:
- **Tiene métodos**: Acciones ya programadas que podemos usar (saber su longitud, pasar a mayúsculas, etc.).
- **Se guarda en memoria como un objeto**: Internamente es como un array de caracteres (char), donde cada letra tiene una posición o índice que empieza siempre en 0.

## Métodos (funciones) útiles de `String`

Un String no se puede modificar (es inmutable). Si usas un método como `toUpperCase()`, no cambias el `String` original, sino que devuelves uno nuevo en mayúsculas.

| Método                                    | Descripción                                      |Devuelve (contesta)    | Ejemplo                               |
| ---                                       | ---                                              |---                    | ---                                   |
| `length()`                            | Devuelve el número de caracteres.                |`int`                  | `"Hola".length()`  → `4`    |
| `charAt(int i)`                      | Devuelve el carácter en el índice i.             |`char`                 | `"Hola".charAt(1)` → `o`    |
| `equals(String s)`                | Compara si el contenido es idéntico.             |`boolean`              | `s1.equals(s2)`                       |
| `equalsIgnoreCase(String s)`      | Igual que equals pero ignora may/min.            |`boolean`              | `"HOLA".equalsIgnoreCase("hola")` → `true`       |
| `toUpperCase()`                    | Devuelve una nueva cadena en mayúsculas.         |`String`               | `"Hola".toUpperCase()` → `"HOLA"`  |
| `toLowerCase()`                    | Devuelve una nueva cadena en minúsculas.         |`String`               | `"Hola".toLowerCase()` → `"hola"`  |
| `substring(int inicio, int fin)`   | Devuelve la subcadena desde inicio hasta fin-1.  |`String`               | `"Hola".substring(1, 3)` → `"ol"`  |
| `indexOf(String s)`                   | Devuelve el índice de la primera aparición de s. |`int`                  | `"Hola".indexOf("la")` → `2`       |
| `contains(String s)`	            | Devuelve true si el texto contiene a s.	         |`boolean`              | `"Hola".contains("ol")` → `true` |
| `replace(char old, char new)`      |	Cambia unas letras por otras.	                   |`String`               | `"casa".replace('a', 'o')` → `"coso"` |
| `startsWith(String s)`	          | Comprueba si empieza por ese texto.              |`boolean`              | `"Profe".startsWith("P")` → `true` |
| `split(String s)`                 | Parte el String en trozos                        |`String[]`             | `"Hola a todos".split(" ") → `{"Hola", "a", "todos"}` |

## Errores comunes

**1. Comparar con `==`**: en Java, para comparar el contenido de dos textos no se usa `==`, si no `.equals()`.

**2. El índice fuera de rango**: si intentas acceder a una posición que no existe, el programa "explotará" con un error llamado `StringIndexOutOfBoundsException`.

## Secuencias de Escape

Para incluir caracteres especiales dentro de un String, usamos la barra invertida `\`:

- `\n`: Salto de línea.
- `\t`: Tabulador.
- `\"`: Comillas dobles (para poder poner comillas dentro del String).
- `\\`: Barra invertida (para poder poner la barra misma).
