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

Descargue los archivos necesarios para la instalación desde [aquí](https://github.com/Ationet/ationetdownloads/blob/master/README.md). Los archivos a descargar son:

- Aplicación StandAlone para terminal V240m
- Sistema operativo
- Librería
- Remover MAC
- Librería Cámara
- Mx Downloader

# Configuración Fecha/Hora &amp; Wifi

Con la terminal encendida ingrese al menú Supervisor presionando las teclas **1+5+9** simultáneamente. De esta manera podrá ver el siguiente menú:

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/Supervisor%20Menu.png)

Ingresando a **supervisor** le solicitará una contraseña. La contraseña de supervisor por defecto es **166831**. Desde este menú iremos a **Administration – Date/Time** y actualizaremos la fecha y la hora de la terminal.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/Date%20and%20Time.png)

Configurada la fecha y hora, iremos a **Administration - Communications - WiFi - WiFi Scan** y encenderemos el WiFi para que pueda escanear por las redes disponibles.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/WiFi%20Scan.png)

Una vez finalizado el escaneo, seleccione la red a utilizar dentro de la lista de redes disponibles.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/WiFi%20List.png)

Volvemos al Menú de **WiFi** utilizando las flechas de la esquina superior izquierda e ingresamos a **WiFi Configuration**.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/WiFi%20Menu%20-%20Configuration.png)

Ingresar en el campo **PSK** la contraseña de la red y presionar **Enter** (tecla verde).

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/WiFi%20Configuration.png)

Retornar al menú de **WiFi** e ingresar a la opción **WiFi Interface IPv4**.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/WiFi%20Menu%20-%20IPv4.png)

Aquí configuraremos las opciones **Mode=&quot;DHCP&quot;** , **AutoStart=&quot;Once&quot;** y luego hacer clic en la conexión en rojo.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/WiFi%20IPv4.png)

Una vez conectado correctamente a la red, el icono de conexión ubicado en la sección superior derecha de la pantalla, se mostrará en verde e indicará la IP que se le asigna a la terminal en el campo **IP address**.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/WiFi%20Connected.png)

```IMPORTANTE: En caso de tener una versión anterior instalada, retornar al menú inicial e ingresar a la opción "Remove user bundle" y seleccionar "Remove all" (NO seleccionar opción "Remove Users").```

Finalizada esta configuración podremos proceder a instalar los pre-requisitos y aplicación StandAlone en la terminal.

# Instalación

Primeramente, dejaremos la terminal en modo carga para poder recibir los archivos de instalación. Para eso debemos ingresar desde el menú de supervisor a **Update - Netloader - wlan0**.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/Waiting%20for%20Download.png)

Luego, desde una PC dentro de la misma red que la terminal, debemos abrir la aplicación **MxDownloader**. Vamos a la pestaña **Network** y completaremos los campos:

- **File to send:** Seleccionar el archivo a instalar.
- **Destination IP:** Ingresar la IP de la terminal V240m.
- **Download Type:** Seleccionar la opción **Full**.
- **Post-Download:** Seleccionar la opción **Run App**.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/Mx%20Downloader.png)

Una vez completado todos los campos correspondientes haremos clic en **Send**, lo que enviará el archivo a la terminal y se instalará automáticamente. Luego de la instalación la terminal procederá a reiniciarse (caso contrario forzar reinicio manualmente).

Este procedimiento debe repetirse con cada archivo específicamente en el siguiente orden:

- Sistema operativo
- Librería
- Remover MAC
- Librería Cámara
- Aplicación StandAlone para V240m

```IMPORTANTE: Si la terminal V240m no tiene una cámara en la parte superior de la misma, entonces el pre-requisito "Librería Cámara" no debe ser instalado.```

# Configuración

Una vez instalado todo procederemos a configurar la terminal. Al iniciar la aplicación nos dirigimos al símbolo de configuración en la esquina superior a la derecha.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/Application%20Configuration.png)

```NOTA: En caso de no haber podido hacer click en botón de "configuración" a tiempo, podemos ingresar a la misma desde "Mantenimiento – Configuración – Parámetros" dentro de la aplicación en si.```

Una vez aquí la terminal nos solicitara clave (ingresar la clave por defecto **123456**).

Desde aquí tendremos las 3 secciones de configuración: **Terminal** , **Sites** y **Ationet**.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/Parameters.png)

## Terminal

Los parámetros para configurar en esta sección son los siguientes:

- **Language:** Idioma (SPA español - ENG inglés)
- **Password:** Contraseña inicial de supervisor de la aplicación. Una vez modificado por aplicación, el campo queda invalidado por más que se modifique o no sea el mismo configurado.
- **iButton:** 0 Deshabilitado - 1 Habilitado (Lector de iButton)
- **Bar code:** 0 Deshabilitado - 1 Habilitado (Scanner)
- **Chip card:** 0 Deshabilitado - 1 Habilitado (Lector de Chip)
- **NFC card:** 0 Deshabilitado - 1 Habilitado (RFID)
- **MSR card:** 0 Deshabilitado - 1 Habilitado (Lector de Tarjetas)
- **Receipt number:** 1
- **Ping:** 3
- **Ping threshold:** 3
- **SSL:** 1

**Parámetros para NFC**

- **CTLS:** 1
- **EMV debug:** 0
- **VAS:** 0
- **WI-FI:** ON – **GSM:** OFF

**Parámetros para GSM**

- **APN:** APN proveedor

**Parámetros para WI-FI**

  - **DHCP:** 1
  - **IP:** 0.0.0.0
  - **Subnetmask:** 0.0.0.0
  - **Gateway:** 0.0.0.0
  - **DNS1:** 0.0.0.0
  - **DNS2:** 0.0.0.0
  - **NETWORK NAME:** Nombre de la red WiFi (SSID)
  - **NETWORK PASSWORD:** Contraseña de la red WiFi

## Sites

Los parámetros para configurar en esta sección son los siguientes:

**Site code:** *Código del sitio*

**Site address:** *Dirección del sitio*

**Site name:** *Nombre del sitio*

**Site cuit:** *Id Tributario del sitio*

**Main header:** *Texto de cabecera primario*

**Secondary header:** *Texto de cabecera secundario*

**Main footer:** *Texto de pie de página primario*

**Secondary footer:** *Texto de pie de página secundario*

## Ationet

Los parámetros para configurar en esta sección son los siguientes:

**Sale in money:** 0 *Venta en volumen* - 1 *Venta en monto*

**Default prompt:** 0 *La terminal no solicita parámetros extra* - 1 *La terminal solicita parámetros extra*

**Attendant Id:** 0 *Deshabilitar función de Encargado* - 1 *Habilitar función de Encargado*

**Driver ID:** 0 *Parámetro de solicitud* (0 deshabilitado - 1 habilitado)

**Vehicle ID:** 0 *Parámetro de solicitud* (0 deshabilitado - 1 habilitado)

**Odometer:** 0 *Parámetro de solicitud* (0 deshabilitado - 1 habilitado)

**Engine hours:** 0 *Parámetro de solicitud* (0 deshabilitado - 1 habilitado)

**Trailer:** 0 *Parámetro de solicitud* (0 deshabilitado - 1 habilitado)

**Miscellaneous:** 0 *Parámetro de solicitud* (0 deshabilitado - 1 habilitado)

**Truck unit:** 0 *Parámetro de solicitud* (0 deshabilitado - 1 habilitado)

**Secondary track:** 0 *Parámetro de solicitud* (0 deshabilitado - 1 habilitado)

**Primary pin:** 0 *Parámetro de solicitud* (0 deshabilitado - 1 habilitado)

**Secondary pin:** 0 *Parámetro de solicitud* (0 deshabilitado - 1 habilitado)

**Native URL:** *Dirección de ATIONet ambiente Beta o Producción*

**Maintenance URL:** *Dirección de ATIONet ambiente Beta o Producción*

**User name:** *Usuario de fidelidad configurado en ATIONet*

**Password:** *Contraseña del usuario de fidelidad configurado en ATIONet*

**Terminal ID:** *ID de terminal configurado en ATIONet*

**Local agent:** 0 

**Local agent IP:** 0.0.0.0
