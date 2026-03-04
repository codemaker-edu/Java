# Cadenas de Caracteres (Clase String)

Para guardar texto (palabras, frases), usamos String. A diferencia de int o double, String no es un tipo primitivo, es una clase.

Esto tiene dos implicaciones fundamentales:
- **Tiene métodos**: Acciones ya programadas que podemos usar (saber su longitud, pasar a mayúsculas, etc.).
- **Se guarda en memoria como un objeto**: Internamente es como un array de caracteres (char), donde cada letra tiene una posición o índice que empieza siempre en 0.

## Métodos (funciones) útiles de `String`

Un String no se puede modificar (es inmutable). Si usas un método como `toUpperCase()`, no cambias el `String` original, sino que devuelves uno nuevo en mayúsculas.

| Método                                    | Descripción                                      | Ejemplo                               |
| ---                                       | ---                                              | ---                                   |
| `int length()`                            | Devuelve el número de caracteres.                | `"Hola".length()`  → `4`    |
| `char charAt(int i)`                      | Devuelve el carácter en el índice i.             | `"Hola".charAt(1)` → `o`    |
| `boolean equals(String s)`                | Compara si el contenido es idéntico.             | `s1.equals(s2)`                       |
| `boolean equalsIgnoreCase(String s)`      | Igual que equals pero ignora may/min.            | `"HOLA".equalsIgnoreCase("hola")` → `true`       |
| `String toUpperCase()`                    | Devuelve una nueva cadena en mayúsculas.         | `"Hola".toUpperCase()` → `"HOLA"`  |
| `String toLowerCase()`                    | Devuelve una nueva cadena en minúsculas.         | `"Hola".toLowerCase()` → `"hola"`  |
| `String substring(int inicio, int fin)`   | Devuelve la subcadena desde inicio hasta fin-1.  | `"Hola".substring(1, 3)` → `"ol"`  |
| `int indexOf(String s)`                   | Devuelve el índice de la primera aparición de s. | `"Hola".indexOf("la")` → `2`       |
| `boolean contains(String s)`	            | Devuelve true si el texto contiene a s.	         | `"Hola".contains("ol")` → `true` |
| `String trim()`	                          | Borra los espacios en blanco de los extremos.	   | `" hola ".trim()` → `"hola"` |
| `String replace(char old, char new)`      |	Cambia unas letras por otras.	                   | `"casa".replace('a', 'o')` → `"coso"` |
| `boolean startsWith(String s)`	          | Comprueba si empieza por ese texto.              | `"Profe".startsWith("P")` → `true` |

## Errores comunes

**1. Comparar con `==`**: en Java, para comparar el contenido de dos textos no se usa `==`, si no `.equals()`.

**2. El índice fuera de rango**: si intentas acceder a una posición que no existe, el programa "explotará" con un error llamado `StringIndexOutOfBoundsException`.

## Secuencias de Escape

Para incluir caracteres especiales dentro de un String, usamos la barra invertida `\`:

- `\n`: Salto de línea.
- `\t`: Tabulador.
- `\"`: Comillas dobles (para poder poner comillas dentro del String).
- `\\`: Barra invertida (para poder poner la barra misma).
