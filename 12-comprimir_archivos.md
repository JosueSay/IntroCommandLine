# Comprimir Archivos

## Crear una carpeta y archivos para comprimir

Puedes crear una carpeta con archivos para comprimir:

```bash
mkdir ToCompress
cd ToCompress
touch file1 file2 file3
cd ..
tree ToCompress
```

## Comprimir archivos con `tar`

El comando `tar` es comúnmente utilizado para crear archivos comprimidos. Para comprimir una carpeta llamada `ToCompress` en un archivo `.tar`:

```bash
tar -cvf ToCompress.tar ToCompress
```

- `c` para crear un archivo comprimido
- `v` para mostrar los detalles del proceso
- `f` para especificar el nombre del archivo comprimido

## Comprimir archivos con formato `.tar.gz`

Para crear un archivo comprimido en formato `.tar.gz`, añade la opción `z`:

```bash
tar -cvzf ToCompress.tar.gz ToCompress
```

## Descomprimir archivos `.tar.gz`

Para descomprimir un archivo `.tar.gz`, usa el siguiente comando:

```bash
tar -xzvf ToCompress.tar.gz
```

- `x` para extraer
- `z` para descomprimir formato `.gz`
- `v` para mostrar detalles
- `f` para especificar el archivo

## Comprimir archivos con `zip`

El comando `zip` se puede utilizar para comprimir directorios en formato `.zip`:

```bash
zip -r ToCompressInZip.zip ToCompress
```

## Descomprimir archivos `.zip`

Para descomprimir un archivo `.zip`, usa el siguiente comando:

```bash
unzip ToCompressInZip.zip
```

## Diferencias entre formatos para comprimir

| **Comando** | **Formato**        | **Uso Principal**                                                                 | **Comprimir**                             | **Descomprimir**                          | **Ventajas**                                                                                 | **Desventajas**                                                                                       |
|-------------|--------------------|-----------------------------------------------------------------------------------|------------------------------------------|-------------------------------------------|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| `tar`       | `.tar`             | Archivo empaquetado sin compresión. Ideal para combinar varios archivos en uno solo. | `tar -cvf archivo.tar directorio`        | `tar -xvf archivo.tar`                    | Puede empaquetar muchos archivos y directorios en un solo archivo.                              | No comprime los archivos, solo los empaqueta.                                                           |
| `tar.gz`    | `.tar.gz`          | Archivo empaquetado y comprimido en formato gzip. Comúnmente usado para respaldo.   | `tar -cvzf archivo.tar.gz directorio`    | `tar -xzvf archivo.tar.gz`                | Proporciona compresión con un buen ratio de compresión.                                           | Puede ser más lento para comprimir y descomprimir en comparación con `zip`.                           |
| `zip`       | `.zip`             | Archivo comprimido. Muy usado en Windows y compatible con muchas plataformas.      | `zip -r archivo.zip directorio`          | `unzip archivo.zip`                       | Es ampliamente utilizado, especialmente en sistemas Windows.                                         | La compresión no es tan eficiente como `tar.gz` en la mayoría de los casos.                          |
