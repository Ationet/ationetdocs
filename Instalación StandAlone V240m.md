# Introducción

En este Manual procederemos a realizar una breve explicación de cómo actualizar las terminales StandAlone V240m. La instalación puede ser realizada mediante Wifi o con el cable de programación + USB pendrive.

# Hardware necesario

- Terminal V240m
- Conectividad a Wifi/Tarjeta SIM
- Cable de Programación de V240m (opcional)
- USB pendrive 8GB (opcional)

# Software necesario

- V240m pre-requisitos
- Mx Downloader 2.9.0

# Descarga de Pre-requisitos y Aplicación

Descargue los archivos necesarios para la instalación desde aquí. Los archivos a descargar son:

- Aplicación StandAlone para terminal V240m
- Sistema operativo
- Librería
- Remover MAC
- Librería Cámara
- Mx Downloader

# Configuración Fecha/Hora &amp; Wifi

Con la terminal encendida ingrese al menú Supervisor presionando las teclas **1+5+9** simultáneamente. De esta manera podrá ver el siguiente menú:

![](RackMultipart20210308-4-1fe69wp_html_a17f57682edf9bd3.png)

Ingresando a **supervisor** le solicitará una contraseña. La contraseña de supervisor por defecto es **166831**. Desde este menú iremos a **Administration – Date/Time** y actualizaremos la fecha y la hora de la terminal.

![](RackMultipart20210308-4-1fe69wp_html_865639e4b434fb68.png)

Configurada la fecha y hora, iremos a **Administration - Communications - WiFi - WiFi Scan** y encenderemos el WiFi para que pueda escanear por las redes disponibles.

![](RackMultipart20210308-4-1fe69wp_html_61697734628955f5.png)

Una vez finalizado el escaneo, seleccione la red a utilizar dentro de la lista de redes disponibles.

![](RackMultipart20210308-4-1fe69wp_html_844703c56decab5d.png)

Volvemos al Menú de **WiFi** utilizando las flechas de la esquina superior izquierda e ingresamos a **WiFi Configuration**.

![](RackMultipart20210308-4-1fe69wp_html_cf70d0f645d2278d.png)

Ingresar en el campo **PSK** la contraseña de la red y presionar **Enter** (tecla verde).

![](RackMultipart20210308-4-1fe69wp_html_3f3a6f993ae902f9.png)

Retornar al menú de **WiFi** e ingresar a la opción **WiFi Interface IPv4**.

![](RackMultipart20210308-4-1fe69wp_html_c44ebe27423c1f46.png)

Aquí configuraremos las opciones **Mode=&quot;DHCP&quot;** , **AutoStart=&quot;Once&quot;** y luego hacer clic en la conexión en rojo.

![](RackMultipart20210308-4-1fe69wp_html_27f0dfd451afb48e.png)

Una vez conectado correctamente a la red, el icono de conexión ubicado en la sección superior derecha de la pantalla, se mostrará en verde e indicará la IP que se le asigna a la terminal en el campo **IP address**.

![](RackMultipart20210308-4-1fe69wp_html_c0bea99206d1978c.png)

IMPORTANTE: En caso de tener una versión anterior instalada, retornar al menú inicial e ingresar a la opción **Remove user bundle** y seleccionar **Remove all** ( **NO** seleccionar opción **Remove Users** ).

Finalizada esta configuración podremos proceder a instalar los pre-requisitos y aplicación StandAlone en la terminal.

# Instalación

Primeramente, dejaremos la terminal en modo carga para poder recibir los archivos de instalación. Para eso debemos ingresar desde el menú de supervisor a **Update - Netloader - wlan0**.

![](RackMultipart20210308-4-1fe69wp_html_82f8f56b7bf156b5.png)

Luego, desde una PC dentro de la misma red que la terminal, debemos abrir la aplicación **MxDownloader**. Vamos a la pestaña **Network** y completaremos los campos:

- **File to send:** Seleccionar el archivo a instalar.
- **Destination IP:** Ingresar la IP de la terminal V240m.
- **Download Type:** Seleccionar la opción **Full**.
- **Post-Download:** Seleccionar la opción **Run App**.

![](RackMultipart20210308-4-1fe69wp_html_4c7ca121f0f15e53.png)

Una vez completado todos los campos correspondientes haremos clic en **Send** , lo que enviará el archivo a la terminal y se instalará automáticamente. Luego de la instalación la terminal procederá a reiniciarse (caso contrario forzar reinicio manualmente).

Este procedimiento debe repetirse con cada archivo específicamente en el siguiente orden:

- Sistema operativo
- Librería
- Remover MAC
- Librería Cámara
- Aplicación StandAlone para V240m

IMPORTANTE: Si la terminal V240m no tiene una cámara en la parte superior de la misma, entonces el pre-requisito **Librería Cámara** no debe ser instalado.

# Configuración

Una vez instalado todo procederemos a configurar la terminal. Al iniciar la aplicación nos dirigimos al símbolo de configuración en la esquina superior a la derecha.

![](RackMultipart20210308-4-1fe69wp_html_948d2615370d01a0.png)

NOTA: En caso de no haber podido hacer click en **configuración** a tiempo, podemos ingresar a la misma desde **Mantenimiento**** – Configuración – Parámetros** dentro de la aplicación en si.

Una vez aquí la terminal nos solicitara clave (ingresar la clave por defecto **123456** ).

Desde aquí tendremos las 3 secciones de configuración: **Terminal** , **Sites** y **Ationet**.

![](RackMultipart20210308-4-1fe69wp_html_9ffd7e3de2a0aeb8.png)

## Terminal

Los parámetros para configurar en esta sección son los siguientes:

- _ **Language:** _ Idioma (SPA español - ENG inglés)
- _ **Password:** _ Contraseña inicial de supervisor de la aplicación. Una vez modificado por aplicación, el campo queda invalidado por más que se modifique o no sea el mismo configurado.
- _ **iButton:** _ 0 Deshabilitado - 1 Habilitado (Lector de iButton)
- _ **Bar code:** _ 0 Deshabilitado - 1 Habilitado (Scanner)
- _ **Chip card:** _ 0 Deshabilitado - 1 Habilitado (Lector de Chip)
- _ **NFC card:** _ 0 Deshabilitado - 1 Habilitado (RFID)
- _ **MSR card:** _ 0 Deshabilitado - 1 Habilitado (Lector de Tarjetas)
- _ **Receipt number:** _ 1
- _ **Ping:** _ 3
- _ **Ping threshold:** _ 3
- _ **SSL:** _ 1

**Parámetros para NFC**

- _ **CTLS:** _ 1
- _ **EMV debug:** _ 0
- _ **VAS:** _ 0
- _ **WI-FI:** _ ON – _ **GSM:** _ OFF

**Parámetros para GSM**

- _ **APN:** _ APN proveedor

**Parámetros para WI-FI**

  - _ **DHCP:** _ 1
  - _ **IP:** _ 0.0.0.0
  - _ **Subnetmask:** _ 0.0.0.0
  - _ **Gateway:** _ 0.0.0.0
  - _ **DNS1:** _ 0.0.0.0
  - _ **DNS2:** _ 0.0.0.0
  - _ **NETWORK NAME:** _ Nombre de la red WiFi (SSID)
  - _ **NETWORK PASSWORD:** _ Contraseña de la red WiFi

## Sites

Los parámetros para configurar en esta sección son los siguientes:

_ **Site code:** _ Código del sitio

_ **Site address:** _ Dirección del sitio

_ **Site name:** _ Nombre del sitio

_ **Site cuit:** _ Id Tributario del sitio

_ **Main header:** _ Texto de cabecera primario

_ **Secondary header:** _ Texto de cabecera secundario

_ **Main footer:** _ Texto de pie de página primario

_ **Secondary footer:** _ Texto de pie de página secundario

## Ationet

Los parámetros para configurar en esta sección son los siguientes:

_ **Sale in money:** _ 0

_ **Default prompt:** _ 0

_ **Attendant Id:** _ 0 Deshabilitar función de Encargado - 1 Habilitar función de Encargado

_ **Driver ID:** _ 0

_ **Vehicle ID:** _ 0

_ **Odometer:** _ 0

_ **Engine hours:** _ 0

_ **Trailer:** _ 0

_ **Miscellaneous:** _ 0

_ **Truck unit:** _ 0

_ **Secondary track:** _ 0

_ **Primary pin:** _ 0

_ **Secondary pin:** _ 0

_ **Native URL:** _ Dirección de ATIONet ambiente Beta o Producción

_ **Maintenance URL:** _ Dirección de ATIONet ambiente Beta o Producción

_ **User name:** _ Usuario de fidelidad configurado en ATIONet (Siempre en mayúscula)

_ **Password:** _ Contraseña del usuario de fidelidad configurado en ATIONet

_ **Terminal ID:** _ ID de terminal configurado en ATIONet

_ **Local agent:** _ 0

_ **Local agent IP:** _ 0.0.0.0
