# Introducción a Java

## Estructura general de un programa Java
Un programa Java siempre tiene al menos una clase pública y un método `main`, que es el punto de entrada (por donde empieza el programa cuando lo ejecutamos).

```java
public class MiPrograma {
    public static void main(String[] args) {
        // Aquí comienza la ejecución del programa
        System.out.println("Hola mundo!");
    }
}
```

En este código podemos ver:

- `public class MiPrograma`: define una clase llamada MiPrograma. Por ahora, pensaremos en una clase como un *fichero* de Java, aunque más adelante veremos lo que son realmente.
- `public static void main(String[] args)`: método principal, fragmento de código por el que se inicia el programa.

## Variables y tipos

Una variable es un espacio en memoria que se utiliza para guardar un dato. En Java (y en casi todos los lenguajes), los tipos de datos básicos (llamados técnicamente *primitivos*), son:

- `int`: números enteros.
- `double`: números decimales.
- `boolean`: valores lógicos (true/false).
- `char`: un carácter.
- `String`: cadenas de texto, (palabras, frases, contraseñas...). Técnicamente no es un tipo primitivo, pero en principio lo usaremos como si lo fuese.
- Otros: también existen otros que se usan solo cuando queremos que se ocupe más o menos memoria, como `long` (números enteros pero más largos) o `float` (números decimales más cortos).

Ejemplo:
```java
int edad = 18;
double altura = 1.75;
boolean mayor = true;
String nombre = "Ana";
```

> Observa que el símbolo `=` en programación no se usa como *igualdad*, tal y como se hace en matemáticas, si no que se utiliza como operador de *asignación* para darle valores a variables. Esto será muy relevante más adelante.

Si añadimos `final` delante del tipo de variable al crearla, esto no será una variable, si no una constante (que es lo mismo, un dato guardado en memoria, pero del que no se puede modificar su valor después).

## Conversión de tipos (casting)

A veces necesitamos cambiar un tipo de dato por otro. Existen varios tipos de conversiones, en función del tipo de dato original y el tipo de dato al que queremos convertirlo:

- **Implícito** (automático): hay veces (cuando no hay pérdida de información), que Java puede hacerlo automáticamente. Por ejemplo:
    ```java
    int x = 5;
    double y = x;
    // Conversión implícita: int → double
    // Puede hacerlo porque no se pierde información (al revés sí, se perderían decimales)
    ```

- **Explícito** (casting): otras veces (cuando sí puede haber pérdida de información), debe ser el programador quien indique a qué tipo se desea convertir. Se usa la sintaxis `(tipoDeseado) variable`. Por ejemplo:
    ```java
    double a = 9.7;
    int b = (int) a;
    // Conversión explícita: double → int (pierde decimales, por eso debemos indicarlo nosotros)
    ```

- **Conversión de String a números***:
Muy habitual cuando pedimos datos por consola. Para convertir textos (String) a valores numéricos usamos métodos algo más complejos, cuya explicación técnica veremos más adelante:
    ```java
    String texto1 = "123";
    int numero = Integer.parseInt(texto1);
    // "123" → 123

    String texto2 = "3.14";
    float decimal = Float.parseFloat(texto2);
    // "3.14" → 3.14 (tipo float)
    ```

## Operadores matemáticos

Los operadores matemáticos permiten hacer operaciones con variables numéricas. Encontramos los siguientes:

- Suma → `+`
- Resta → `-`
- Multiplicación → `*`
- División → `/`
- Resto de división → `%`
- Incremento/Decremento → `++`, `--` (suman o restan 1 directamente)
- Suma y asignación / resta y asignación → `+=` , `-=` (suman/restan el valor que pongamos después y guardan el resultado en la variable)

Ejemplo:
```java
int a = 7;
int b = 2;
System.out.println(a + b); // 9
System.out.println(a / b); // 3 (solo muestra parte entera porque estamos diviendo numeros enteros, por lo que entiende Java que el resultado deberá ser entero)
System.out.println(a % b); // 1 (resto)
```

Cuidado con los incrementos y decrementos (`++`, `--`). Éstos modifican el valor de la variable (+1 o -1), pero dependiendo de si ponen antes de la variable (pre-incremento o pre-decremento) o después (post-incremento o post-decremento), la incrementan antes o después de usarla.

Veámoslo más claro en un ejemplo:

```java
int a = 5;
System.out.println(++a); //Cambia valor a 6 y luego la imprime (imprime, por lo tanto, 6).
```
```java
int a = 5;
System.out.println(a++); //Imprime, y después cambia el valor (imprime, por lo tanto, 5).
```


## Entrada y salida por consola

Para que nuestros programas puedan interactuar con el usuario, deben mostrar y pedir información por consola.

- **Salida de datos**: mostrar información al usuario.
    ```java
    System.out.println("Hola mundo");
    ```

- **Entrada de datos**: leer información que escribe el usuario.
    ```java
    System.console().readLine("Como te llamas?");
    //Ojo, probablemente quieras guardar la respuesta del usuario en una variable String para poder usarla después
    ```


## Comentarios

Los comentarios sirven para documentar el código y no afectan a la ejecución (se obvian al compilar). En Java, se pueden crear comentarios:
- De una línea:
    ```java
    // Esto es un comentario de una línea
    ```
- De varias líneas:
    ```java
    /* Esto es un comentario
   que ocupa varias líneas */
   ```
