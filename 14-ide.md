# Editores de Texto en Terminal

Algunas opciones populares para editar texto en la terminal son **vim**, **emacs**, y **nano**.

En el caso de **vim**, existen dos versiones principales: **vi** (versión antigua) y **vim** (versión moderna). Aquí hay algunos detalles para comenzar con vim:

- **Crear un archivo de texto**: Utiliza el comando `vim index.html` para abrir o crear el archivo.
- **Editar texto**: Presiona `i` para entrar en el modo de inserción y comenzar a editar.
- **Resaltado de sintaxis**: Vim resalta la sintaxis dependiendo del lenguaje automáticamente.
- **Salir de la edición**: Presiona `ESC` para salir del modo de inserción.
- **Salir de vim**: Usa `:q` para salir.
- **Buscar palabras**: Usa `/palabra` para buscar y posicionarte en la primera coincidencia (no resalta las palabras).
- **Eliminar líneas**: Ve al inicio de la línea en el modo de navegación y presiona `d`.

## Personalizar la Terminal de Comandos

[**Oh My Posh**](https://ohmyposh.dev/) es una herramienta excelente para personalizar la apariencia de la terminal. Aquí se explica cómo hacerlo dependiendo de la configuración:

### **PowerShell**

**Video referencia**: [PowerShell Video](https://www.youtube.com/watch?v=6SGIFVJ5Izs)

1. **Instalar la terminal de Microsoft Store**: Descarga la herramienta "Terminal" para manejar múltiples shells en una sola aplicación.
2. **Verificar que Winget esté instalado**: En versiones modernas de Windows (> Windows 10) debería estar incluido. Confírmalo con:

   ```bash
   winget --version
   ```

3. **Configurar la terminal**:
   - Abre **Settings** y configura las siguientes opciones base:
     - **Startup**:
       - Establece la shell predeterminada.
       - Define si la terminal debe abrirse automáticamente al iniciar la PC.
       - ![Settings](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/settings1.png "Settings")
     - **Color schemes**:
       - Crea una paleta de colores personalizada. Aquí tienes un ejemplo:

         ```json
         {
           "background": "#2A2B37",
           "black": "#21222C",
           "blue": "#BD93F9",
           "brightBlack": "#6272A4",
           "brightBlue": "#D6ACFF",
           "brightCyan": "#A4FFFF",
           "brightGreen": "#69FF94",
           "brightPurple": "#FF92DF",
           "brightRed": "#FF6E6E",
           "brightWhite": "#FFFFFF",
           "brightYellow": "#FFFFA5",
           "cursorColor": "#FF79C6",
           "cyan": "#8BE9FD",
           "foreground": "#F8F8F2",
           "green": "#50FA7B",
           "name": "schemaPersonality",
           "purple": "#FF79C6",
           "red": "#FF5555",
           "selectionBackground": "#44475A",
           "white": "#F8F8F2",
           "yellow": "#F1FA8C"
         }
         ```

         - Coloca este esquema en el archivo JSON de configuración de la terminal en el aparatado `Profile` y subapartado del listado de `schemes`, que puedes abrir desde **"Open JSON file"** en la sección de settings. Luego, cierra el archivo json y en settings selecciona tu nuevo esquema en **Color schemes** y hazlo predeterminado.

         ![Settings Default](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/settings_default.png "Settings Default")

     - **Defaults**:
       - Cambia el esquema de color por defecto.
       - Configura una fuente (recomendado usar una Nerd Font para íconos).
       - Ajusta la transparencia, el cursor, el padding y más.

   - ¡Explora las configuraciones para personalizar cada shell individualmente!

      ![Settings Bash1](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/settings_bash1.png "Settings Bash1")

      ![Settings Bash2](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/settings_bash2.png "Settings Bash2")

#### **Instalar Oh My Posh**

1. Instala **Oh My Posh** con Winget:

   ```bash
   winget install JanDeDobbeleer.OhMyPosh -s winget
   ```

2. Instala fuentes compatibles con Nerd Icons:

   ```bash
   oh-my-posh font install
   ```

   - Selecciona una fuente como **Fira Code Nerd Font** o cualquier otra.
   - Configura la fuente en **Settings/Appearance/Font face**.

3. Configura un tema:
   - Revisa los temas disponibles: [Oh My Posh Themes](https://ohmyposh.dev/docs/themes).
   - Visualiza ejemplos en la terminal:

     ```bash
     Get-PoshTheme
     ```

   - Para aplicar un tema siempre al iniciar PowerShell:
     - Abre el perfil con:

       ```bash
       notepad $PROFILE
       ```

       Si hay un error, cierra el notepad y crea el perfil con:

       ```bash
       New-Item -Path $PROFILE -Type File -Force
       ```

       Luego, ingresa nuevamente el comando:

       ```bash
       notepad $PROFILE
       ```

     - Dentro del notepad pega este comando, reemplazando `<user>` y `<name_theme>` con tu nombre de usuario de tu maquina y el tema escogido:

       ```bash
       (@(& 'C:/Users/<user>/AppData/Local/Programs/oh-my-posh/bin/oh-my-posh.exe' init pwsh --config='C:\Users\<user>\AppData\Local\Programs\oh-my-posh\themes\<name_theme>.omp.json' --print) -join "`n") | Invoke-Expression
       ```

#### **Añadir Íconos y Texto Predictivo**

1. **Íconos**:

   - Instala la librería necesaria:

      ```bash
      Install-Module -Name Terminal-Icons -Repository PSGallery
      ```

   - Añade el siguiente comando en el notepad con el comando anterior `notepad $PROFILE`:

      ```bash
      Import-Module Terminal-Icons
      ```

2. **Texto Predictivo**:

   - Instala la librería necesaria:

      ```bash
      Install-Module -Name PSReadLine -Force -SkipPublisherCheck
      ```

   - Añade el siguiente comando en el notepad con el comando anterior `notepad $PROFILE`:

      ```bash
      Set-PSReadLineOption -PredictionViewStyle ListView
      ```

![Prediction Commands](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/prediction_commands.png "Prediction Commands")

![Icons Powershell](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/icons_powershell.png "Icons Powershell")

### **WSL (Windows Subsystem for Linux)**

**Video referencia**: [WSL Video](ttps://www.youtube.com/watch?v=2VlleD1Dj-4&t=780s)

#### **Instalación de Oh My Posh**

Para instalar Oh My Posh en WSL, sigue estos pasos:  

1. **Descarga e instalación del binario de Oh My Posh:**

   ```bash
   sudo wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/posh-linux-amd64 -O /usr/local/bin/oh-my-posh
   sudo chmod +x /usr/local/bin/oh-my-posh
   ```

2. **Descarga y configuración de los temas:**

   ```bash
   mkdir ~/.poshthemes
   wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/themes.zip -O ~/.poshthemes/themes.zip
   unzip ~/.poshthemes/themes.zip -d ~/.poshthemes
   chmod u+rw ~/.poshthemes/*.json
   rm ~/.poshthemes/themes.zip
   ```

3. **Preparación de las fuentes:**
   Asegúrate de tener la fuente adecuada descargada, luego:

   ```bash
   cd ~
   mkdir .fonts
   unzip ~/Descargas/fuente_escogida.zip -d ~/.fonts/fuente_escogida
   fc-cache -fv
   ```

   Suponiendo que el archivo zip de las fuentes estan en "Descargas" y para descargar las fuentes se pueden obtener de [Nerd Fonts](https://www.nerdfonts.com/font-downloads)

4. **Visualización de un tema:**
   Puedes cargar un tema específico con el siguiente comando:

   ```bash
   eval "$(oh-my-posh --init --shell bash --config ~/.poshthemes/nombre-del-tema.omp.json)"
   ```

5. **Hacer persistente la configuración:**
   Para que el tema cargue automáticamente al iniciar la terminal, agrega el comando anterior al final del archivo `.bashrc`:

   ```bash
   nano ~/.bashrc
   ```

   Luego añade:

   ```bash
   eval "$(oh-my-posh --init --shell bash --config ~/.poshthemes/nombre-del-tema.omp.json)"
   ```

   Guarda los cambios y recarga el archivo con:

   ```bash
   source ~/.bashrc
   ```

### **Integración con VS Code**

Al realizar la configuración de Oh My Posh en WSL o cualquier otra shell, la terminal integrada de VS Code heredará los temas y configuraciones personalizadas. Sin embargo, para evitar problemas con los iconos o fuentes, sigue estos pasos:

1. Ve a la configuración de VS Code y busca "Font Ligatures".

   ![Configuración en VS Code](https://raw.githubusercontent.com/JosueSay/ImageDocs/main/IntroCommandLine/configuracion_vs_code.png "Configuración en VS Code")

2. Edita el archivo `settings.json` y añade las siguientes líneas:

   ```json
   {
       "terminal.integrated.fontFamily": "fuente_escogida",
       "editor.fontLigatures": true,
       "editor.fontFamily": "fuente_escogida, Consolas, 'Courier New', monospace"
   }
   ```

3. Si los iconos no se muestran correctamente, verifica que la fuente instalada soporte los iconos de Oh My Posh.  

Con estas configuraciones, VS Code adaptará la terminal a los temas usados en WSL y otras personalizaciones realizadas.
