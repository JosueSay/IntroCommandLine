# Comandos de Búsqueda

Los comandos de búsqueda son herramientas esenciales para localizar archivos, binarios, o patrones dentro de archivos de texto. Aquí se explica cómo usarlos eficazmente.

## Comando `which`

El comando `which` se utiliza para encontrar la ubicación de un binario (programa) en el sistema. Por ejemplo, para encontrar la ubicación de Visual Studio Code:

```bash
which code
```

Esto devolverá la ruta completa del binario `code` si está instalado en el sistema.

## Comando `find`

El comando `find` se usa para buscar archivos en un directorio o ruta específica. Su sintaxis es:

```bash
find <ruta de búsqueda inicial> -name <nombre_del_archivo>
```

Por ejemplo, para buscar todos los archivos llamados `documento.txt` dentro del directorio actual:

```bash
find ./ -name "documento.txt"
```

**Buscar por tipo**: Puedes especificar el tipo de archivo o directorio con los parámetros `-f` para archivos y `-d` para directorios. Por ejemplo:

```bash
find ./ -type f -name "*.log"  # Buscar archivos .log
find ./ -type d -name "logs"   # Buscar directorios llamados "logs"
```

**Buscar por tamaño**: Para encontrar archivos de un tamaño específico, puedes usar el parámetro `-size`. Por ejemplo, para encontrar archivos de 20 MB:

```bash
find ./ -size 20M
```

**Ejercicio**: Buscar archivos `.txt` y guardarlos en un archivo con un mensaje de éxito:

```bash
find ./ -name "*.txt" >> misArchivosTXT && echo "Archivos guardados exitosamente" || echo "No se pudo hacer la operación"
```

## Comando `grep`

El comando `grep` busca coincidencias de un patrón en archivos de texto. La sintaxis básica es:

```bash
grep <expresión_regular> <archivo>
```

**Ejemplo básico**:

```bash
grep Towers movies.csv
```

Este comando buscará la palabra "Towers" en el archivo `movies.csv`. Es sensible a mayúsculas y minúsculas por defecto.

**Ignorar mayúsculas/minúsculas**: Para hacer una búsqueda insensible a mayúsculas y minúsculas, agrega el parámetro `-i`:

```bash
grep -i the movies.csv
```

**Contar coincidencias**: Para contar cuántas veces aparece un patrón en el archivo, usa el parámetro `-c`:

```bash
echo "Hay $(grep -c the movies.csv) movies usando el comando grep -c the movies.csv" >> conteo_movies
echo "Hay $(grep -c -i the movies.csv) movies usando el comando grep -c -i the movies.csv" >> conteo_movies
```

**Comparar resultados con y sin `-i`**:

```bash
[ $(grep -c the movies.csv) -gt $(grep -c -i the movies.csv) ] && echo "Hay más películas sin el parámetro -i" || echo "Hay más películas con el parámetro -i" >> conteo_movies
```

**Buscar líneas que no coincidan con un patrón**: Usa el parámetro `-v` para excluir las coincidencias:

```bash
grep -vi towers movies.csv
```

## Comando `wc`

El comando `wc` (word count) cuenta palabras, líneas, y caracteres en un archivo. Por ejemplo:

```bash
wc movies.csv
```

Esto devuelve 4 números:

- **Número de líneas**
- **Número de palabras**
- **Número de caracteres**
- **Nombre del archivo**

**Contar líneas**:

```bash
wc -l movies.csv
```

**Contar palabras**:

```bash
wc -w movies.csv
```

**Contar caracteres**:

```bash
wc -c movies.csv
```
