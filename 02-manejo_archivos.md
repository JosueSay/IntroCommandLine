# Manejo de archivos

## Sistema de Archivos

![Sistema de Archivos](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/sistema_archivos.png "Sistema de Archivos")

En los sistemas operativos basados en Unix, la carpeta **"Home"** es donde se almacena la información del usuario.

### Comandos Básicos

- **`ls`**: Lista las carpetas y archivos en el directorio actual.
- **`clear`** (o `Ctrl + L`): Limpia la terminal.
  
#### Opciones Comunes para `ls`

- **`ls -l`**: Muestra una lista detallada de archivos y carpetas en formato largo.
- **`ls -lh`**: Muestra tamaños de archivos en formato legible para humanos (por ejemplo, KB, MB).
- **`ls -a`**: Muestra archivos ocultos.
- **`ls -S`**: Ordena los archivos por tamaño.
- **`ls -r`**: Muestra los archivos en orden inverso por nombre.

### Navegación de Directorios

- **`cd`**: Cambia al directorio **Home** rápidamente.
- **`pwd`**: Muestra la ruta completa del directorio actual (ruta absoluta).
- **`cd ..`**: Retrocede al directorio anterior.
- **`cd .`**: Se mantiene en el directorio actual.

#### Rutas

- **Relativas**: Usan **`..`** o **`.`** para moverse dentro de la estructura de directorios.
- **Absolutas**: Usan la ruta completa desde la raíz, como **`/home/josue`**.

### Verificación del Tipo de Archivo

- **`file`**: Describe el tipo de archivo. Ejemplo:

```bash
$ file package.json
package.json: JSON data
```

### Comando `tree`

- Muestra la estructura de los archivos y carpetas en forma de árbol. Usa el parámetro **`-L`** para definir los niveles de profundidad:

```bash
tree -L 2
```

## Manipulación de Archivos y Directorios

| **Comando**  | **Descripción**                                                       |
|--------------|-----------------------------------------------------------------------|
| **`mkdir`**  | Crea un nuevo directorio. Si contiene espacios, usa comillas: `mkdir "Mi Directorio"`. Se pueden crear múltiples directorios a la vez: `mkdir dir1 dir2 dir3`. |
| **`touch`**  | Crea un archivo vacío. Se pueden crear múltiples archivos de una vez: `touch file1 file2`. |
| **`cp`**     | Copia archivos. Si no se especifica la ruta de destino, se copia en el mismo directorio: `cp file1 file_bk`. |
| **`mv`**     | Mueve archivos o carpetas. También se usa para renombrar: `mv file_bk ../dir2` o `mv file_bk fileCopy`. |
| **`rm`**     | Elimina archivos. Usa **`-i`** para confirmar la eliminación de manera interactiva: `rm -i fileCopy`. Para directorios usa **`-r`** (recursivo): `rm -r dir1`. La opción **`-f`** fuerza la eliminación sin confirmación: `rm -rf dir1`. Tambipen se pueden eliminar múltiples archivos o directorios a la vez como **`rm -r dir1 dir2`**|

## Contenido de un Archivo

| **Comando** | **Descripción**                                                                 |
|-------------|---------------------------------------------------------------------------------|
| **`head`**  | Muestra las primeras 10 líneas de un archivo. Se puede modificar con **`-n`**: `head archivo.md -n 15`. |
| **`tail`**  | Muestra las últimas 10 líneas de un archivo, se puede modificar igual que `head`. |
| **`less`**  | Permite explorar un archivo de manera interactiva. Usa las flechas o el scroll para moverse, y **`/`** para buscar una palabra o frase. Para salir presiona **`q`**. |

### Abrir un Archivo en una Terminal

Para abrir una terminal en una ruta específica, se puede usar el siguiente comando:

```bash
explorer.exe ruta
```

Este comando abre el explorador de archivos en la ruta especificada.
