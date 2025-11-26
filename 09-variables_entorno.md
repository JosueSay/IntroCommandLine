# Variables de Entorno

Las variables de entorno son una herramienta poderosa en sistemas operativos tipo Unix. Permiten configurar el entorno del usuario y realizar tareas automatizadas mediante scripts. A continuación, se explica cómo utilizarlas y gestionarlas.

## Ver variables de entorno

Para listar las variables de entorno disponibles, usamos:

```bash
printenv
```

Si queremos consultar una variable específica, utilizamos:

```bash
echo $NOMBRE_VARIABLE
```

Por ejemplo:

```bash
echo $HOME
```

Esto imprimirá la ruta del directorio personal del usuario.

## Variable `PATH`

La variable `PATH` contiene las rutas donde el sistema busca los ejecutables. Al instalar ciertos programas o paquetes, puede ser necesario añadir su ubicación a `PATH`. Esto se hace con el siguiente comando:

```bash
PATH=$PATH:/ruta_a_binarios
```

Por ejemplo, si instalamos un paquete cuyo binario está en `/usr/local/mybin`, lo añadimos así:

```bash
PATH=$PATH:/usr/local/mybin
```

## Modificar variables de entorno

Para persistir cambios en las variables de entorno, editamos el archivo de configuración de la shell que estamos utilizando. Por ejemplo:

- **Bash**: Archivo `.bashrc`.
- **Zsh**: Archivo `.zshrc`.

## Crear alias

Un alias permite asignar un comando a una palabra clave para simplificar tareas frecuentes. Por ejemplo:

```bash
alias repositorios='cd /mnt/d/GitHub\ Repositorios'
```

Después de guardar el alias en el archivo `.bashrc` o `.zshrc`, lo cargamos con:

```bash
source ~/.bashrc
```

Ahora, escribir `repositorios` ejecutará el comando completo.

## Crear variables de entorno personalizadas

Para crear una variable personalizada:

```bash
WELCOME="Hola Mundo"
```

Si queremos asegurarnos de que la variable esté disponible en nuevas sesiones, añadimos esta línea al archivo `.bashrc` o `.zshrc`. Luego, cargamos los cambios:

```bash
source ~/.bashrc
```

Y verificamos con:

```bash
$echo $WELCOME
Hola Mundo
```
