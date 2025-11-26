# Operadores de Control

Los operadores de control en la shell son símbolos reservados que permiten ejecutar y encadenar múltiples comandos de diversas maneras. Estos operadores son útiles para controlar el flujo de ejecución, ejecutar comandos condicionalmente, o correr tareas en segundo plano.

## **Ejecución Secuencial con `;`**

El operador `;` permite ejecutar múltiples comandos de forma secuencial. Cada comando se ejecuta en orden, sin importar si el anterior tuvo éxito o no. Ejemplo:

```bash
ls; mkdir hola; cal
```

- **`ls`**: Lista los archivos del directorio actual.
- **`mkdir hola`**: Crea un directorio llamado `hola`.
- **`cal`**: Muestra el calendario del mes actual.

En este caso, todos los comandos se ejecutan uno tras otro, independientemente de su resultado.

## **Ejecución en Segundo Plano con `&`**

El operador `&` ejecuta comandos de manera asíncrona, es decir, cada comando se ejecuta en segundo plano en un hilo del procesador. Esto es útil para correr múltiples tareas simultáneamente.

```bash
ls & date & cal
```

Salida típica:

```bash
[1] 147207
[2] 147208
Wed Dec 18 14:20:49 CST 2024
Lab4_CSS                 OverBlogWatch                hola               postgresql.conf
Lab5_JS                  OverBlogWatchApi             node_modules       snap
LaptopUnveilingHTML      go                           package-lock.json
LaptopUnveilingHTML.rar  go1.22.5.linux-amd64.tar.gz  package.json
   December 2024
Su Mo Tu We Th Fr Sa
 1  2  3  4  5  6  7
 8  9 10 11 12 13 14
15 16 17 18 19 20 21
22 23 24 25 26 27 28
29 30 31

[1]-  Done                    ls --color=auto
[2]+  Done                    date
```

- **`ls &`**: Lista los archivos del directorio en segundo plano.
- **`date &`**: Muestra la fecha y hora actuales en segundo plano.
- **`cal &`**: Muestra el calendario en segundo plano.

Cada tarea genera un identificador de proceso (PID) y un indicador del estado (`Done` cuando termina).

## **Ejecución Condicional con `&&`**

El operador `&&` asegura que el segundo comando se ejecutará solo si el primero tiene éxito (código de salida `0`). Este operador es ideal para comandos que dependen del éxito de un paso previo.

```bash
mkdir test && cd test
```

- **`mkdir test`**: Crea un directorio llamado `test`.
- **`cd test`**: Cambia al directorio `test` si fue creado con éxito.

Si `mkdir test` falla (por ejemplo, si el directorio ya existe), `cd test` no se ejecutará.

## **Ejecución Alternativa con `||`**

El operador `||` ejecuta el segundo comando solo si el primero falla (código de salida distinto de `0`). Este operador es útil para definir acciones alternativas.

```bash
mkdir hola || echo "El directorio ya existe"
```

- **`mkdir hola`**: Intenta crear un directorio llamado `hola`.
- **`echo "El directorio ya existe"`**: Muestra un mensaje si `mkdir hola` falla.

## **Combinaciones de Operadores**

Es posible combinar múltiples operadores para lograr un flujo de control más complejo. Ejemplo:

```bash
mkdir nueva_carpeta && cd nueva_carpeta || echo "Error al crear o entrar en el directorio"
```

- **`mkdir nueva_carpeta && cd nueva_carpeta`**: Intenta crear un directorio y cambiar a él si tiene éxito.
- **`|| echo "Error al crear o entrar en el directorio"`**: Muestra un mensaje si cualquiera de los pasos falla.

## **Ejemplo Complejo**

Un flujo completo que combina varios operadores:

```bash
mkdir proyecto && cd proyecto && touch main.py || echo "Error al configurar el proyecto"
```

1. Crea el directorio `proyecto`.
2. Cambia al directorio `proyecto`.
3. Crea un archivo vacío `main.py`.
4. Si falla cualquiera de los pasos, muestra un mensaje de error.
