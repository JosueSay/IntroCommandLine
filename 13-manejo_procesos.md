# Manejo de procesos

## **Comando `ps`**

El comando `ps` muestra los procesos que están en ejecución en el sistema, proporcionando información como el PID (Process ID). Por ejemplo:

```bash
ps aux
```

Esto lista todos los procesos con detalles como el usuario que los ejecuta, el PID, el uso de CPU y memoria, etc.

## **Comando `kill`**

Para eliminar un proceso, se usa el comando `kill` seguido del PID del proceso que quieres finalizar:

```bash
kill <PID>
```

Si el proceso no se detiene, se puede usar `kill -9 <PID>` para forzar su terminación.

## **Comando `top`**

El comando `top` abre una interfaz interactiva donde puedes ver los procesos en tiempo real. Puedes hacer filtros, por ejemplo, presionando `u` y luego ingresando el nombre del usuario del proceso para ver solo los procesos de ese usuario. Para obtener ayuda en esta interfaz, puedes presionar `h`.

## Procesos en Foreground y Background

### **Foreground**

Cuando un proceso está en el "foreground", significa que se ejecuta directamente en la terminal y bloquea la entrada de nuevos comandos hasta que termine. Por ejemplo, al ejecutar:

```bash
cat > mi_nota.txt
```

Esto actúa como un editor de texto temporal, y para finalizar y guardar el archivo, presionamos `CTRL + D`.

### **Background**

Un proceso en "background" se ejecuta sin ocupar la terminal, permitiendo que puedas seguir trabajando en otros comandos. Para enviar un proceso al background, puedes usar `CTRL + Z`, lo cual suspende el proceso, y luego usar el comando `bg` para reanudarlo en segundo plano:

```bash
bg <id_job>
```

Donde `<id_job>` es el identificador del proceso en segundo plano. Puedes ver la lista de trabajos con el comando `jobs`.

### **Ejemplo con "&"**

Otra manera de enviar un proceso al background es añadiendo el símbolo `&` al final del comando:

```bash
cat > mi_nota.txt &
```

Este comando ejecuta el proceso en segundo plano desde el principio.

### **Comandos adicionales**

Cuando un proceso está en background, puedes enviarlo nuevamente al foreground con:

```bash
fg <id_job>
```

Por ejemplo, si abres un navegador y luego lo suspendes con `CTRL + Z`, puedes reanudarlo en segundo plano usando:

```bash
bg <id_job_navegador>
```

Esto permitirá que el navegador siga ejecutándose en segundo plano mientras puedes usar la terminal para otras tareas.
