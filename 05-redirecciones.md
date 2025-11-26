# Redirecciones

![Redirecciones](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/redirecciones.png "Redirecciones")

Las redirecciones en la shell permiten manipular las salidas estándar, errores y entradas de los comandos. Cada flujo tiene un número asociado:

| **Flujo**             | **Número** |
|-----------------------|------------|
| **Entrada estándar**  | `0`        |
| **Salida estándar**   | `1`        |
| **Error estándar**    | `2`        |

Se utilizan los símbolos `>` y `>>` para redirigir o concatenar estos flujos hacia archivos o dispositivos.

## **Redirigir la Salida Estándar (`1`)**

Para guardar la salida de un comando en un archivo, usa el símbolo `>`:

```bash
ls Pictures > misFotos.txt
```

Esto captura la salida del comando `ls Pictures` y la guarda en el archivo `misFotos.txt`. Si el archivo ya existe, su contenido será sobrescrito.

## **Concatenar la Salida Estándar (`>>`)**

Si deseas **añadir** información al archivo en lugar de sobrescribirlo, utiliza `>>`:

```bash
ls Downloads >> misFotos.txt
```

Este comando agrega la salida del comando `ls Downloads` al final de `misFotos.txt` sin borrar el contenido existente.

## **Redirigir el Error Estándar (`2`)**

Para capturar errores de un comando en un archivo, usa `2>`:

```bash
ls skaond 2> error.txt
```

En este ejemplo, si el comando `ls skaond` genera un error, dicho error se guarda en el archivo `error.txt`.

## **Redirigir Ambos Flujos: Salida y Error**

Puedes redirigir simultáneamente la salida estándar y el error estándar a un solo archivo usando `2>&1`:

```bash
ls sjdoai > output.txt 2>&1
```

- **`> output.txt`**: Redirige la salida estándar al archivo `output.txt`.
- **`2>&1`**: Indica que el error estándar (`2`) debe redirigirse al mismo lugar que la salida estándar (`1`).

Esto asegura que tanto la salida como los errores se capturen en el archivo `output.txt`.

## **Usar la Entrada Estándar (`0`)**

Es posible redirigir datos desde un archivo o dispositivo hacia la entrada de un comando:

```bash
cat < archivo.txt
```

Aquí, `archivo.txt` se usa como entrada para el comando `cat`.

## **Combinaciones Avanzadas**

1. **Redirigir Salida Estándar y Error a Archivos Diferentes**:

   ```bash
   comando > salida.txt 2> errores.txt
   ```

   - `> salida.txt`: Guarda la salida estándar en `salida.txt`.
   - `2> errores.txt`: Guarda el error estándar en `errores.txt`.

2. **Silenciar la Salida Estándar**:

   Para descartar la salida estándar, redirígela a `/dev/null`:

   ```bash
   comando > /dev/null
   ```

   Esto elimina cualquier salida del comando.

3. **Silenciar Ambos Flujos**:

   Para descartar tanto la salida estándar como los errores:

   ```bash
   comando > /dev/null 2>&1
   ```

## **Resumen de Operadores de Redirección**

| **Operador**  | **Descripción**                                                                 |
|---------------|---------------------------------------------------------------------------------|
| `>`           | Redirige la salida estándar (sobrescribe el archivo de destino).               |
| `>>`          | Redirige la salida estándar (concatena al archivo de destino).                 |
| `2>`          | Redirige el error estándar (sobrescribe el archivo de destino).                |
| `2>>`         | Redirige el error estándar (concatena al archivo de destino).                  |
| `<`           | Redirige la entrada estándar desde un archivo.                                 |
| `/dev/null`   | Descartar la salida o errores (útil para silenciar comandos).                  |
| `2>&1`        | Combina la salida estándar y el error estándar en el mismo destino.            |

## **Ejemplo Completo**

```bash
ls archivos > salida.txt 2> errores.txt
```

En este ejemplo:

- La salida estándar de `ls archivos` se guarda en `salida.txt`.
- Los errores generados (si los hay) se guardan en `errores.txt`.
