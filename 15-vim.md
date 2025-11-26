# Configuración de Vim

## **1. Instalación de vim-plug**

Se instaló el gestor de complementos **vim-plug** para facilitar la gestión e instalación de plugins en Vim.

### Proceso

1. Se agregó el bloque de configuración para **vim-plug** en el archivo `.vimrc`:

   ```bash
   call plug#begin('~/.vim/plugged')
   " Aquí se declaran los complementos
   call plug#end()
   ```

2. Se descargó **vim-plug** con el siguiente comando:

   ```bash
   curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
   https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
   ```

3. En este caso, se agregó el complemento `vim-commentary` para comentar y descomentar código fácilmente según el lenguaje. Luego se abrio nuevamente vim y se escribio el siguiente comando para instalar los plugins:

   ```bash
   :PlugInstall
   ```

## **2. Complementos instalados**

### `vim-commentary`

- Complemento para comentar y descomentar líneas o bloques de código.
- Instalación declarada en `.vimrc`:

   ```vim
   Plug 'tpope/vim-commentary'
   ```

- Uso:
  - **Comentar una línea:** `gcc`
  - **Comentar múltiples líneas:** Selección visual (`v`) + `gc`
  - **Descomentar:** Usar los mismos comandos (`gcc` o `gc`).

## **3. Configuración básica para mejorar Vim**

### Números de línea

```vim
set number             " Muestra números de línea
set relativenumber     " Muestra números relativos para facilitar movimientos
```

### Búsqueda mejorada

```vim
set hlsearch           " Resalta los resultados de búsqueda
set incsearch          " Realiza búsquedas incrementales mientras escribes
```

### Tabulación y espacios

```vim
set expandtab          " Usa espacios en lugar de tabs
set tabstop=4          " Tamaño de cada tabulación
set shiftwidth=4       " Cantidad de espacios para cada nivel de indentación
```

### Color y resaltado

```vim
set t_Co=256           " Habilita el soporte para 256 colores
syntax on              " Habilita resaltado de sintaxis
set background=dark    " Configura fondo oscuro
colorscheme desert     " Usa el tema 'desert' para colores
```

### Historial extenso para cambios

Se configuró un historial persistente para deshacer cambios.

```vim
set undofile           " Habilita el historial para deshacer
set undodir=~/.vim/undo " Define el directorio donde se guardará el historial
```

**Nota:** Se creó manualmente la carpeta para guardar el historial con:

```bash
mkdir -p ~/.vim/undo
```

### Habilitar el mouse

Permite usar el mouse para seleccionar texto o mover el cursor.

```vim
set mouse=a
```

### Mostrar modo

Indica si estás en modo normal, insertar, visual, etc.

```vim
set showmode
```

### Auto-indentación

Habilita la indentación automática según el contexto.

```vim
set autoindent
set smartindent
```

## **4. Configuración del portapapeles**

Se habilitó la opción para interactuar con el portapapeles del sistema:

```vim
set clipboard=unnamedplus
```

## **5. Atajos configurados**

### Copiar y pegar con `Ctrl+C` y `Ctrl+V`

Estos atajos permiten copiar y pegar texto usando el portapapeles del sistema.

```vim
noremap <C-c> "+y   " Copiar al portapapeles
noremap <C-v> "+p   " Pegar desde el portapapeles
```

## **6. Comandos útiles**

- **Guardar archivo:** `:w`
- **Cerrar archivo:** `:q`
- **Salir sin guardar:** `:q!`
- **Guardar y salir:** `:wq`
- **Seleccionar todo:** `ggVG`
- **Copiar al portapapeles:** `"+y` (después de seleccionar texto)
- **Pegar desde el portapapeles:** `"+p`
- **Comentar una línea o bloque (con `vim-commentary`):**
  - Una línea: `gcc`
  - Múltiples líneas: Selección visual + `gc`
- **Deshacer cambios:** `u`
- **Rehacer cambios:** `Ctrl+r`

## **Resultado final del archivo `.vimrc`**

```vim
call plug#begin('~/.vim/plugged')

" Complementos instalados
Plug 'tpope/vim-commentary'

call plug#end()

" Habilita números de línea
set number
set relativenumber

" Resalta la búsqueda y permite buscar incrementalmente
set hlsearch
set incsearch

" Usa espacios en lugar de tabulaciones
set expandtab
set tabstop=4
set shiftwidth=4

" Activa el soporte para 256 colores
set t_Co=256

" Habilita el mouse
set mouse=a

" Muestra el cursor en diferentes modos
set cursorline

" Colorea el texto al abrir archivos
syntax on

" Configuración de temas (colorscheme)
set background=dark
colorscheme desert

" Mostrar modo
set showmode

" Habilitar historial más extenso para cambios
set undofile
set undodir=~/.vim/undo

" Atajos
noremap <C-c> "+y   " Copiar al portapapeles con Ctrl+C
noremap <C-v> "+p   " Pegar desde el portapapeles con Ctrl+V

" Habilitar portapapeles del sistema
set clipboard=unnamedplus

" Habilitar sangría
set autoindent
set smartindent
```
