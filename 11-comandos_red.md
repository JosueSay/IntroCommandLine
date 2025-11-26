# Utilidades de Red

Existen varios comandos útiles para interactuar con la red y obtener información sobre la conexión y el estado de los recursos en línea.

## Comando `ifconfig`

El comando `ifconfig` se utiliza para mostrar la configuración de red, incluyendo las interfaces de red activas, las direcciones IP y otros detalles de la red. Este comando es común en sistemas basados en Unix.

## Comando `ping`

El comando `ping` permite verificar si un sitio web o una dirección IP está activa. Envía paquetes ICMP y muestra el tiempo que tarda en recibir una respuesta.

```bash
ping www.google.com
```

Si se recibe una respuesta, significa que el servidor está activo.

## Comando `curl`

El comando `curl` se utiliza para transferir datos a través de la red, obteniendo archivos o contenido de una URL. Por ejemplo, puedes obtener el HTML de una página web de la siguiente manera:

```bash
curl www.google.com
```

## Comando `wget`

`wget` es una herramienta de línea de comandos utilizada para descargar archivos desde la web. A diferencia de `curl`, que generalmente obtiene datos, `wget` guarda directamente los archivos en el sistema local. Por ejemplo:

```bash
wget www.google.com
```

Esto descargará la página principal de Google.

## Comando `traceroute`

`traceroute` muestra la ruta que toman los paquetes a través de diferentes dispositivos de red hasta llegar a su destino. Es útil para diagnosticar problemas de conectividad y ver el trayecto que siguen los paquetes.

```bash
traceroute www.google.com
```

Ejemplo de salida:

```bash
traceroute to www.google.com (172.217.2.196), 30 hops max, 60 byte packets
 1  192.168.160.1 (192.168.160.1)  0.353 ms  0.276 ms  0.326 ms
 2  192.168.0.1 (192.168.0.1)  3.517 ms  3.906 ms  4.947 ms
 3  100.64.253.3 (100.64.253.3)  19.726 ms 100.64.253.2 (100.64.253.2)  19.577 ms 100.64.253.3 (100.64.253.3)  22.443 ms
 4  100.64.234.109 (100.64.234.109)  20.451 ms  22.559 ms 100.64.234.105 (100.64.234.105)  19.741 ms
...
14  mia09s02-in-f4.1e100.net (172.217.2.196)  47.082 ms  43.462 ms  48.621 ms
```

## Comando `netstat -i`

El comando `netstat -i` muestra una lista de las interfaces de red y sus estadísticas, como el número de paquetes transmitidos y recibidos, errores, y otras métricas relacionadas con la red.

```bash
netstat -i
```
