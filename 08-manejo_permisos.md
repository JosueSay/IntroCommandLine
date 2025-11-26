# Manejo de Permisos

En sistemas operativos basados en Unix/Linux, cada archivo o carpeta tiene asociados permisos que controlan quién puede acceder y qué acciones se pueden realizar sobre ellos. Cuando listamos archivos o carpetas con el comando `ls -l`, podemos observar una representación de permisos en el siguiente formato:

```bash
-rw-r--r--  1 usuario grupo  tamaño fecha nombre
```

## **Identificación de Archivos y Carpetas**

La primera columna de `ls -l` identifica si el elemento es un archivo (`-`) o una carpeta (`d`), seguida de una representación de los permisos.

![Tipos de Archivos](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/tipos_archivos.png "Tipos de Archivos")

![Permisos Ejemplo](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/permisos2.png "Permisos Ejemplo")

## **Usuarios en el Sistema**

Existen tres tipos de usuarios para cada archivo o carpeta:

1. **Dueño (user)**: Generalmente el creador del archivo.
2. **Grupo (group)**: Usuarios que pertenecen a un grupo asociado al archivo.
3. **Otros (others)**: Cualquier otro usuario no incluido en los dos anteriores.

![Permisos](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/permisos.png "Permisos")

## **Tipos de Permisos**

Cada usuario puede tener tres tipos de permisos:

- **Lectura (`r`)**: Permite leer el contenido del archivo o listar los contenidos de una carpeta.
- **Escritura (`w`)**: Permite modificar el archivo o agregar/eliminar elementos en una carpeta.
- **Ejecución (`x`)**: Permite ejecutar un archivo como un programa o acceder a una carpeta.

La forma en que estos permisos afectan archivos y carpetas puede variar:

![Permisos En Carpetas y Archivos](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/permisos3.png "Permisos En Carpetas y Archivos")

## **Representación Binaria y Octal de Permisos**

Los permisos se representan como un conjunto de tres bits para cada usuario (dueño, grupo, otros). Cada bit indica si el permiso está activado (`1`) o no (`0`):

- **Lectura (`r`)**: Bit más significativo.
- **Escritura (`w`)**: Bit intermedio.
- **Ejecución (`x`)**: Bit menos significativo.

| **Permiso** | **Binario** | **Octal** |
|-------------|-------------|-----------|
| Ninguno     | `000`       | `0`       |
| Ejecución   | `001`       | `1`       |
| Escritura   | `010`       | `2`       |
| Lectura     | `100`       | `4`       |

Ejemplo de representación octal para `rwxr-xr--`:

![Modo octal](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/octal_mode.png "Modo octal")

![Modo Octal](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/octal_mode2.png "Modo Octal")

## **Modificación de Permisos con `chmod`**

### **Usando el Modo Octal**

Con `chmod`, podemos establecer permisos directamente usando su representación octal. Por ejemplo:

```bash
chmod 755 archivo.txt
```

- **`7` (rwx)**: Permisos para el dueño.
- **`5` (r-x)**: Permisos para el grupo.
- **`5` (r-x)**: Permisos para otros.

Resultado:

```bash
-rwxr-xr-x 1 usuario grupo tamaño fecha archivo.txt
```

### **Usando el Modo Simbólico**

En el modo simbólico, podemos agregar o quitar permisos para tipos específicos de usuarios:

![Modo Simbolico](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/simbolic_mode.png "Modo Simbolico")

Ejemplo de eliminación y adición de permisos:

```bash
chmod u-r archivo.txt
ls -l
--wxr-xr-x 1 usuario grupo tamaño fecha archivo.txt

chmod u+r archivo.txt
ls -l
-rwxr-xr-x 1 usuario grupo tamaño fecha archivo.txt
```

Podemos combinar múltiples cambios en un solo comando:

```bash
chmod u-x,go=w archivo.txt
ls -l
-rw--w--w- 1 usuario grupo tamaño fecha archivo.txt
```

## **Comprobación de Usuarios y Grupos**

Para verificar información sobre el usuario actual:

- **`whoami`**: Muestra el nombre del usuario actual.
- **`id`**: Proporciona información detallada del usuario, incluyendo grupos.

## **Cambio de Usuario y Uso de `sudo`**

### **Cambio Temporal con `su`**

El comando `su` permite cambiar de usuario. Por ejemplo, para cambiar al usuario `root`:

```bash
sudo su root
```

### **Ejemplo de Archivos con Diferentes Dueños**

```bash
$ ls -l
-rw--w--w- 1 josue adduser 45 Dec 18 16:27 archivo.txt
-rw-r--r-- 1 root  root      0 Dec 18 20:36 archivo_root.txt
```

El archivo `archivo_root.txt` pertenece al usuario `root`. Si intentamos eliminarlo como un usuario sin permisos:

```bash
rm archivo_root.txt
rm: remove write-protected regular empty file 'archivo_root.txt'?
```

Con `sudo`, podemos eliminarlo otorgando permisos temporales:

```bash
sudo rm archivo_root.txt
```

## **Cambio de Contraseña**

El comando `passwd` permite cambiar la contraseña del usuario actual:

```bash
passwd
```

## **Links simbólicos**

Podemos crear archivos con enlaces simbólicos que actúan como accesos directos. Por ejemplo:

```bash
ln -s Documents/Dev Desarrollo
```

Esto creará un enlace simbólico llamado `Desarrollo` que apunta a la carpeta `Documents/Dev`. Al hacer `cd Desarrollo` y luego `ls`, veremos los archivos de la carpeta destino.
