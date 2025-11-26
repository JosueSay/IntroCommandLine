# Wildcards (Comodines)

Los **wildcards** son caracteres especiales que permiten usar patrones para búsquedas avanzadas y manipulación de archivos.

## Comodines Básicos

| **Wildcard** | **Descripción**                                                   | **Ejemplo**                                                                                   |
|--------------|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------|
| **`*`**      | Coincide con **cualquier número de caracteres**.                  | **`ls *.txt`**: Lista todos los archivos que terminan en `.txt`.                             |
| **`?`**      | Coincide con **un solo carácter**.                                | **`ls datos?`**: Lista archivos como `datos1`.                                              |
| **`[ ]`**    | Coincide con **un rango o conjunto de caracteres específicos**.   | **`ls [ad]*`**: Lista archivos que comienzan con `a` o `d`.                                  |
| **`[[:upper:]]`** | Coincide con caracteres **en mayúsculas**.                  | **`ls -d [[:upper:]]*`**: Lista directorios que comienzan con mayúsculas.                   |
| **`[[:lower:]]`** | Coincide con caracteres **en minúsculas**.                  | **`ls -d [[:lower:]]*`**: Lista directorios que comienzan con minúsculas.                   |

## Ejemplos Prácticos

### Usando `*` (Asterisco)

```bash
$ ls *.txt
dot.txt  dot2.txt  file.txt
```

```bash
$ ls datos*
datos1  datos123
```

### Usando `?` (Interrogación)

```bash
$ ls datos?
datos1
```

```bash
$ ls datos???
datos123
```

### Usando Rango de Caracteres `[ ]`

Lista directorios que comienzan con **mayúsculas**:

```bash
$ ls -d [[:upper:]]*
Lab4_CSS  Lab5_JS  LaptopUnveilingHTML  LaptopUnveilingHTML.rar  OverBlogWatch  OverBlogWatchApi
```

Lista directorios que comienzan con **minúsculas**:

```bash
$ ls -d [[:lower:]]*
abc     datos123  dir2     dot2.txt  go                           index.html    package-lock.json  postgresql.conf
datos1  dir1      dot.txt  file.txt  go1.22.5.linux-amd64.tar.gz  node_modules  package.json       snap
```

Filtrar por archivos/directorios que comienzan con letras específicas (`a` o `d`):

```bash
$ ls [ad]*
abc  datos1  datos123  dot.txt  dot2.txt
```

## Uso de Wildcards en Manipulación de Archivos

Los wildcards también son útiles con comandos como **`rm`**, **`cp`**, o **`mv`**:

- **`rm *.log`**: Elimina todos los archivos que terminan en `.log`.
- **`cp datos* backup/`**: Copia todos los archivos que comienzan con "datos" al directorio `backup`.
- **`mv [ad]* folder/`**: Mueve todos los archivos que comienzan con "a" o "d" al directorio `folder`.
