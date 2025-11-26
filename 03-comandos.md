# Comandos

![Comandos](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/comando.png "Comandos")

## Ver la Naturaleza de un Comando

El comando **`type`** permite verificar la naturaleza de un comando. Ejemplo:

```bash
$ type cd
cd is a shell builtin
```

Algunos comandos son **alias**. Por ejemplo, el comando `ls` utiliza un alias para habilitar colores en la terminal:

```bash
$ type ls
ls is aliased to `ls --color=auto'
```

## Crear Alias

Puedes crear alias personalizados usando el comando **`alias`**. Ejemplo:

```bash
alias l="ls -lh"
```

> **Nota**: Estos alias son **temporales**. Más adelante se explicará cómo crear alias permanentes.

## Obtener Ayuda de Comandos

Hay varias formas de obtener ayuda sobre los comandos:

| **Comando**          | **Descripción**                                                                                   |
|-----------------------|---------------------------------------------------------------------------------------------------|
| **`help <comando>`**  | Muestra ayuda básica sobre un comando.                                                           |
| **`man <comando>`**   | Abre el manual completo de un comando.                                                           |
| **`info <comando>`**  | Proporciona información más resumida que `man`.                                                  |
| **`whatis <comando>`**| Proporciona una descripción breve del comando.                                                   |

Ejemplos:

```bash
help cd
cd --help
man ls
info ls
whatis cd
```
