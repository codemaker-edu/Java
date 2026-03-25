# Bloque 4: Flujos y Ficheros para guardar datos

En el desarrollo de aplicaciones reales, rara vez trabajamos solo con datos introducidos por el usuario durante la ejecución. Muchas veces es necesario guardar información para usarla más adelante (como resultados, configuraciones, listas de usuarios o registros), o bien leer datos almacenados previamente para procesarlos. Recuerda que las variables se guardan en memoria RAM, por lo que cuando apagues y enciendas nuevamente tu app, se habrá borrado (si le preguntas a un usuario su nombre, mañana tu app no lo recordará).

Para ello, los programas deben poder acceder a ficheros del sistema, leer y escribir información en ellos, e incluso comunicarse con otros dispositivos mediante flujos de datos. Dominar estas operaciones es fundamental para crear programas útiles, persistentes y que puedan conectarse con otras apps.

### 1. La clase File para gestionar ficheros

Antes de leer o escribir datos en ficheros, es importante conocer la clase `File` de Java. Esta clase no permite acceder directamente al contenido del archivo, pero sí proporciona **métodos para trabajar con el archivo como objeto del sistema de ficheros**.

Con `File` podemos:
- Comprobar si un archivo existe y obtener información del archivo (nombre, ruta, tamaño, etc., pero no su contenido).
```java
File fichero = new File("datos.txt");
if (fichero.exists()) {
    System.out.println("El archivo existe.");
    System.out.println("Nombre: " + fichero.getName());
    System.out.println("Ruta absoluta: " + fichero.getAbsolutePath());
    System.out.println("Tamaño: " + fichero.length() + " bytes");
} else {
    System.out.println("El archivo no existe.");
}
```
- Crear nuevos archivos.
```java
File fichero = new File("datos.txt");
try {
    if (fichero.createNewFile()) {
        System.out.println("Archivo creado correctamente.");
    } else {
        System.out.println("No se pudo crear (ya existe).");
    }
} catch (IOException e) {
    System.out.println("Error al crear el archivo: " + e.getMessage());
}
```
- Crear una carpeta:
```java
File carpeta = new File("documentos");
if (!carpeta.exists()) {
    carpeta.mkdir();
}
//Cuidado: mkdir() intentará crear la carpeta, y devuelve true o false en función de si la ha conseguido crear o no, por lo que podríamos ejecutarlo en un if para tener constancia. Si no consigue crearla, no lanza excepción.
```
- Listar archivos de una carpeta:
```java
File carpeta = new File("documentos");
if (carpeta.exists() && carpeta.isDirectory()) {
    File[] archivos = carpeta.listFiles();
    System.out.println("Contenido de la carpeta:");
    for (File archivo : archivos) {
        System.out.println("- " + archivo.getName());
    }
}
```

La clase File es especialmente útil para verificar que un archivo existe antes de abrirlo, o para crear archivos y carpetas en tiempo de ejecución. La usaremos para este tipo de operaciones, pero para leer o guardar el contenido de los archivos deberemos crear flujos de datos, como vamos a ver a continuación.

### 2. Lectura y escritura de datos

Un **flujo** es un canal de comunicación por el que circulan datos desde una fuente hacia un destino. Java clasifica los flujos en dos tipos principales:

- **Flujos de entrada (Input)**: para leer datos desde una fuente (como un fichero).
- **Flujos de salida (Output)**: para escribir datos hacia un destino (como un fichero).

Los flujos de entrada y salida pueden manejar los datos en distintos formatos, lo cual implica que tengamos flujos de bytes y flujos de caracteres:

#### Flujos de bytes
- Manejan **datos binarios crudos** (imágenes, vídeos, ficheros comprimidos...).
- Cada byte se procesa tal cual.
- Clases más usadas:
  - `FileInputStream`: para leer bytes de un fichero.
  - `FileOutputStream`: para escribir bytes en un fichero.

#### Flujos de caracteres
- Manejan **datos de texto** (caracteres Unicode).
- Convertidos automáticamente desde bytes.
- Clases más usadas:
  - `FileReader`: para leer caracteres de un fichero.
  - `FileWriter`: para escribir caracteres en un fichero.

#### ¿Cuándo usar cada uno?
- Usa **flujos de bytes** si estás trabajando con **datos binarios**. Ejemplos:
  - Guardar una imagen (`.jpg`, `.png`) que el usuario sube en una aplicación.
  - Leer un archivo de audio (`.mp3`) para reproducirlo.
  - Copiar cualquier tipo de archivo sin alterar su contenido.
- Usa **flujos de caracteres** si estás trabajando con **texto plano**. Ejemplos:
  - Leer un fichero `.txt` con instrucciones o datos.
  - Guardar las notas de un alumno en un archivo `.csv`.
  - Escribir un informe de errores en un archivo `.log`.

#### Mejorar del rendimiento con `Buffered`

Los `Buffered` consiguen almacenar datos en memoria temporal, reduciendo el número de accesos físicos al disco. Esto permite reducir el número de accesos físicos al disco y, por tanto, mejorar notablemente el rendimiento en las operaciones de lectura y escritura. En la práctica, usaremos Buffered en la mayoría de ocasiones.

Java cuenta con las clases `BufferedReader`, `BufferedWriter`, `BufferedInputStream` y `BufferedOutputStream` que sustituyen a las vistas anteriormente cuando queremos trabajar con búfers:

| Clase básica          | Clase con buffer              | Tipo de datos     | Mejoras                                                |
|-----------------------|-------------------------------|-------------------|--------------------------------------------------------|
| `FileReader`          | `BufferedReader`              | Texto (lectura)   | Lee por bloques o líneas en vez de caracter a caracter.|
| `FileWriter`          | `BufferedWriter`              | Texto (escritura) | Escribe por bloques en vez de caracter a caracter.     |
| `FileInputStream`     | `BufferedInputStream`         | Binario (lectura) | Útil para copiar o leer archivos grandes en binario.   |
| `FileOutputStream`    | `BufferedOutputStream`        | Binario (escritura)| Útil para escribir cantidades grandes en binario.     |

En resumen, aunque podemos usar ambos tipos, usaremos las clases `Buffered` cuando se espera leer o escribir más de unos pocos bytes o caracteres, dejando las clases básicas solo para tareas muy simples (lectura o escritura de un solo caracter, por ejemplo).

#### Excepciones típicas

Al leer y escribir en ficheros a través de flujos, hay una serie de excepciones que pueden darse. Las más habituales son:

- `FileNotFoundException`: el fichero no existe o no se puede acceder.
- `IOException`: error de lectura o escritura general.


#### Ejemplos de código

Ejemplo 1: Leer un archivo de texto línea por línea con BufferedReader:

```java
try {
    BufferedReader br = new BufferedReader(new FileReader("texto.txt"));
    String linea;
    while ((linea = br.readLine()) != null) {
        System.out.println(linea);
    }
    br.close();
} catch (IOException e) {
    System.out.println("Error al leer el archivo: " + e.getMessage());
}
```

Ejemplo 2: Escribir varias líneas en un archivo de texto con BufferedWriter:

```java
try {
    BufferedWriter bw = new BufferedWriter(new FileWriter("salida.txt"));
    bw.write("Primera línea");
    bw.newLine();
    bw.write("Segunda línea");
    bw.close();
} catch (IOException e) {
    System.out.println("Error al escribir en el archivo: " + e.getMessage());
}

```

---
