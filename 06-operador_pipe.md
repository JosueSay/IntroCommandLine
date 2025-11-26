# Operador Pipe (`|`)

El operador **pipe** (`|`) permite redirigir la salida estándar de un comando hacia la entrada estándar de otro. Es una herramienta poderosa para crear flujos de procesamiento en la shell, facilitando la manipulación de datos sin necesidad de archivos intermedios.

## **Comandos Básicos Usados con Pipe**

1. **`echo`**:
   Muestra texto o variables en la salida estándar:

   ```bash
   echo "Hola, mundo"
   ```

2. **`cat`**:
   Muestra el contenido de un archivo o combina múltiples archivos en la salida estándar:

   ```bash
   cat archivo.txt
   ```

   También puede redirigir su entrada desde un archivo:

   ```bash
   cat < archivo.txt
   ```

## **Usando el Operador Pipe**

El pipe toma la salida estándar de un comando y la redirige como entrada estándar de otro. Ejemplo básico:

```bash
ls -lh | less
```

- **`ls -lh`**: Genera una lista detallada de archivos.
- **`less`**: Permite explorar la salida de forma interactiva (avanzar, retroceder y buscar).

## **Creando Archivos con `tee`**

El comando `tee` guarda la salida estándar en un archivo y simultáneamente la pasa como entrada a otro comando. Ejemplo:

```bash
ls -lh | tee output.txt | less
```

- **`ls -lh`**: Lista archivos.
- **`tee output.txt`**: Guarda la salida en el archivo `output.txt` y la envía a `less`.
- **`less`**: Muestra la salida en una interfaz interactiva.

Esto evita la necesidad de realizar múltiples redirecciones manualmente.

## **Ejemplo Complejo con `sort`**

Podemos combinar varios comandos con pipes. Por ejemplo, ordenar una lista, guardarla y visualizarla interactivamente:

```bash
ls -lh | sort | tee output.txt | less
```

- **`sort`**: Ordena alfabéticamente la salida de `ls`.
- **`tee`**: Guarda el resultado en `output.txt`.
- **`less`**: Permite interactuar con el resultado.

## **Mostrando Mensajes en Colores**

Los pipes también funcionan con comandos para personalizar la salida. Por ejemplo:

```bash
cowsay "Hola mundo" | lolcat
```

- **`cowsay`**: Genera un mensaje dentro de un bocadillo de texto acompañado de una vaca ASCII.
- **`lolcat`**: Aplica colores degradados al texto.

Salida:

```markdown
 ____________
< hola mundo >
 ------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

### **Librería `sharutils`**

La biblioteca **sharutils** proporciona herramientas para codificar y decodificar archivos en formatos especiales, como `uuencode` y `uudecode`, usados para empaquetar y compartir archivos en sistemas UNIX.

### **Instalación**

Para instalar la biblioteca en sistemas basados en Debian:

```bash
sudo apt install sharutils
```

### **Codificar un Archivo: `uuencode`**

El comando `uuencode` convierte un archivo en un formato seguro para transmisión (por ejemplo, por correo electrónico). Ejemplo:

```bash
uuencode archivo.txt archivo_codificado.txt > archivo.uu
```

- **`archivo.txt`**: Archivo original.
- **`archivo_codificado.txt`**: Nombre que tendrá el archivo después de ser decodificado.
- **`archivo.uu`**: Salida codificada.

### **Decodificar un Archivo: `uudecode`**

Para recuperar un archivo codificado con `uuencode`, usa `uudecode`:

```bash
uudecode archivo.uu
```

Esto genera el archivo original (`archivo_codificado.txt`) en el directorio actual.

### **Flujo Completo**

1. Codificar un archivo:

   ```bash
   uuencode archivo.txt archivo.txt > archivo.uu
   ```

2. Compartir el archivo `archivo.uu`.

3. Decodificar en otro sistema:

   ```bash
   uudecode archivo.uu
   ```

El archivo original estará disponible con el mismo nombre especificado durante la codificación.
