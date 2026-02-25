## 1. Arrays Unidimensionales (Vectores)
Un array (también llamado vector) es una estructura de datos que nos permite almacenar un conjunto de elementos del mismo tipo en posiciones de memoria contiguas. Puedes verlo como una *lista de variables* por ahora.
Piénsalo como un mueble con un número fijo de cajones:
- El mueble es el array.
- Cada cajón es una posición (hueco).
- Lo que guardas en cada cajón es el dato.

> [!Important]
> En Java, los arrays solo pueden guardar datos de un mismo tipo y con una cantidad fija (es decir, si decimos que serán 10 Strings, ni podremos meter luego un int, ni podremos meter 11 Strings).

### Crear array sin valores
Para usar un array, debemos seguir dos pasos: declararlo y luego inicializarlo (darle un nombre e indicarle el tamaño)

```java
// Creamos (declaramos) el array e indicamos cuántos huecos tendrá (inicializamos)
int[] notas = new int[10]; // Un array para 10 notas de tipo int
```

### Crear array con valores
Si ya sabes qué valores va a contener, podemos indicarlos directamente al crearlo:

```java
// Java crea automáticamente un array de tamaño 4
String[] diasSemana = {"Lunes", "Martes", "Miércoles", "Jueves", "Viernes"}; 
```

### Acceso y Modificación (Índices)

Accedemos a cada "cajón" (elemento) usando su índice, que se escribe entre corchetes [].

> [!Important]
> Los índices en Java (y en la mayoría de lenguajes) empiezan siempre en 0.

Si un array tiene 5 elementos, sus índices van del 0 al 4.
- `notas[0]` es el primer elemento.
- `notas[4]` es el último elemento.

Con esto, podemos hacer dos cosas:
- Consultar y mostrar un elemento: `System.out.println( notas[3] );`
- Guardar o cambiar valores: `notas[2] = 7;`

Para saber el tamaño de un array, podemos usar la propiedad `.length` (sin paréntesis).

### Recorriendo un array (Bucle for)

La forma más común y eficiente de "visitar" cada elemento de un array es usando un bucle for. Combinamos el bucle con la propiedad .length para que se repita la cantidad exacta de veces (tantas como elementos tenga el array).

```java
for (int i = 0; i < notas.length; i++) {
System.out.print(notas[i]); //Imprime la nota[0], después la nota[1]...
}
```

### Recorriendo un array (Bucle for-each)

Existe una variante más moderna y legible del bucle for, conocida como for-each (o "bucle mejorado"). Esta estructura está diseñada específicamente para recorrer todos los elementos de un array, desde el primero hasta el último, sin necesidad de manejar contadores ni índices manualmente.

```java
double[] notas = {4.5, 8.0, 6.5, 9.0};

for (double nota : notas) {
//La variable 'nota' va tomando el valor de cada posición
System.out.print(nota + " ");
} 
```

### ¿Cuándo usar un bucle u otro?

Usa el `for` normal (con índice i) cuando:
- Necesitas saber la posición del elemento (por ejemplo, para decir "La nota del alumno 1 es...").
- Necesitas modificar el contenido del array (ej: notas[i] = 5;).
- No quieres recorrer el array completo (por ejemplo, solo la mitad inversa).

Usa el `for-each` cuando:
- Solo quieres leer todos los datos uno por uno.
- Quieres un código más limpio y evitar errores de "índice fuera de límites".

¡Ojo! En un bucle for-each, la variable temporal (ej. nota) es una copia del valor. Si modificas nota dentro del bucle, NO se modifica el array original. Para modificar el array, necesitas obligatoriamente el índice (i) del bucle for clásico.

## 2. Arrays Bidimensionales (Matrices)

Un array bidimensional es, simplemente, un "array de arrays". Nos sirve para representar datos en una cuadrícula (filas y columnas). Piénsalo como un tablero de ajedrez o una hoja de cálculo.

### Declaración e Inicialización
Al igual que con los arrays anteriores (unidimensionales) podemos crearlos sin datos (vacíos) o ya con los datos rellenos. En ambos casos, usamos dobles corchetes `[][]` para indicar que es bidimensional.

```java
// Creamos el array vacío, 3 filas y 4 columnas
int[][] tablero = new int[3][4];

// Guardamos un dato (fila 1, columna 2) (Recuerda: índice 0)
tablero[1][2] = 100;
```
```java
// Creamos el array ya con los datos
int[][] tablero = {
    {1, 2, 3},  // Fila 0
    {4, 5, 6},  // Fila 1
    {7, 8, 9}   // Fila 2
};
```

### Recorrido de Matrices (Bucles anidados)

Para recorrer una matriz, necesitamos un bucle for anidado:
- El bucle exterior recorre las filas.
- El bucle interior recorre las columnas de cada fila.
```java
public class EjemploMatriz {
    public static void main(String[] args) {

        int[][] matriz = {
            {1, 2, 3},
            {4, 5, 6}
        };

        for (int i = 0; i < matriz.length; i++) {
            for (int j = 0; j < matriz[i].length; j++) {
                System.out.print( matriz[i][j] );
            }
            System.out.println(); 
        }
    }
}
```

Hagamos algunas observaciones de lo que está haciendo este código:
1. Crea una matriz de 2 filas y 3 columnas, ya rellena de números enteros.
2. Un bucle principal (el de la `i`) recorre las filas.
3. Un bucle interno (el de la `j`) recorre cada elemento de cada fila (es decir, cada columna) y lo imprime (con `print`, sin `ln` para que se impriman seguidos en la misma linea).
4. Al terminar cada fila, y antes de pasar a la siguiente, se hace un `println` vacío solo para saltar de línea.

