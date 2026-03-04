# Bloque 2 - Estructuras de control

## Concepto
Las estructuras de control permiten **modificar el flujo de ejecución** de un programa.
Con ellas podemos, especialmente:
- Tomar decisiones (seleccionar si se ejecuta un código u otro en función de un valor o condición).
- Repetir bloques de código (bucles).

Según el teorema de la estructura, todo programa puede construirse únicamente con:
- **Secuencia**: instrucciones ejecutadas en orden.
- **Selección**: permite bifurcaciones en función de condiciones.
- **Iteración**: repite un bloque de instrucciones.

## Operadores

Los operadores son símbolos que se utilizan habitualmente para comprobar condiciones.

### Operadores de comparación
Operadores para comparar datos
- `==` → igual que  
- `!=` → distinto que  
- `>`  → mayor que  
- `<`  → menor que  
- `>=` → mayor o igual que  
- `<=` → menor o igual que 

### Operadores lógicos
Operadores utilizados para poder hacer más de una comprobación
- `&&` → AND (true si ambas condiciones son verdaderas)
- `||` → OR (true si al menos una condición es verdadera)
- `!` → NOT (niega la condición)

## Estructuras condicionales en Java

### Condicional simple – `if`

Cuando solo queremos comprobar si se cumple una condición para realizar una acción.

```java
if (edad >= 18) {
   // programación si se cumple
}
```

### Condicional doble – `if-else`

Cuando queremos realizar una acción si se cumple la condición, y otra acción si no se cumple.

```java
if (edad >= 18) {
   // programación si se cumple
} else {
   // programación si no se cumple
}
```
### Condicional múltiple - `if - else if - else`

Cuando queremos realizar diferentes acciones en función del resultado de la condición.

```java
if (edad >= 18) {
    // programación que se ejecuta si es mayor de 18 años
} else if (edad >= 16 && edad < 18) {
    // programación que se ejecuta si tiene entre 16 y 18 años
} else {
    // programación que se ejecuta si no ha cumplido ninguna de las anteriores condiciones (en este caso, si es menor de 16 años)
}
```

### Condicional múltiple – `switch`

Permite ejecutar un código u otro en función del valor que tenga una variable. Similar al `if - else if - else`, pero aquí no se compara (no hay símbolos `<`, `>`, `==`, etc.), solo se mira qué hay en la variable y en cada caso se realiza una acción.

```java
String estacion = "Verano";

switch (estacion) {
   case "Verano":
      System.out.println("hace calor");
      break;
   case "Invierno":
      System.out.println("hace frio");
      break;
   default:
      System.out.println("no se reconoce esa estación"); //Valores distintos a los anteriores
}
```

### Operador ternario

Es una forma compacta de hacer un if-else, que utilizan usuarios más avanzados. No es necesario que aprendas a usarla todavía, pero está bien saber que existe.

```java
variable = (condición) ? valor_si_verdadero : valor_si_falso;
```

## Estructuras iterativas (bucles)

### Bucle `for`

Se usa cuando se conoce el número exacto de iteraciones (*Ejemplo: repetir 10 veces*).

```java
for (int i = 0; i < 10; i++) {
   // rogramación que se repetirá 10 veces
}
```
En este bucle podemos ver:
- `int i = 0`: creamos la variable contador
- `i < 10`: decimos que se repita mientras la i sea menor que 10
- `i++`: decimos que la `i` vaya aumentando de 1 en 1.

### Bucle `while`

Se trata de un bucle que se repite mientras se cumpla una determinada condición. Deja de repetirse la instrucción cuando la condición deje de cumplirse. Es decir, es un *mientras*, no un *hasta*.

```java
while (puntos > 0) {
   // programación que se repetirá mientras puntos sea mayor que cero
}
```

### Bucle `do-while`

Exactamente igual que el bucle `while`, con la única diferencia de que primero ejecuta la instrucción que tiene en su interior, y después comprueba si la condición se cumplía. Esto asegura que las instrucciones internas se ejecuten al menos una vez.

```java
do {
   // programación que se repetirá mientras puntos sea mayor que cero
} while (puntos > 0);
```

### Sentencias de salto

Un bucle, e incluso otras estructuras, pueden interrumpirse con las siguientes instrucciones:

- `break` → interrumpe un bucle o switch.
- `continue` → salta a la siguiente iteración del bucle.

### Equivalencias entre bucles

Todos los bucles (while, do-while, for) son equivalentes en potencia. Esto quiere decir que un mismo problema podrá resolverse con diferentes bucles. Se recomienda elegirlos según el problema:
- `for` → se repite un número exacto de veces.
- `while` → se repite mientras se cumpla una condición.
- `do-while` → se repite mientras se cumpla una condición, asegurando que se ejecuta al menos una vez aunque no se cumpla.
