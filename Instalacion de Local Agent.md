# **Guía de instalación de Local Agent**

# **Herramientas necesarias**

- Pendrive
- Teclado
- Mouse
- Monitor

# **Pasos de instalación**

Para la instalación del servicio, existen ciertos prerrequisitos. Los programas con prerrequisitos para instalar Local Agent son los siguientes:

- .Net Framework 4.5
- Sql Express 2008 - Atio Custom Instance
- Windows Installer 3.1
- Windows Installer 4.5

Cada programa se puede descargar directamente de la página oficial de Microsoft, sin embargo, en nuestro repositorio oficial podemos conseguir estos prerrequisitos junto con el instalador de local agent, el cual instala todos los programas automáticamente, de una sola vez sin la necesidad de ir instalando un por uno por separado.

La página para poder descargar esta información es la siguiente:

downloads.ationet.com

Desde este portal podrá localizar los siguientes archivos para descargar:

![](RackMultipart20210310-4-1qq9bh0_html_ec49aefe5b908546.png)

Una vez descargado el paquete de archivos, vamos a ver los siguientes ejecutables:

![](RackMultipart20210310-4-1qq9bh0_html_e6b5e6058cf67c7.png)

El ejecutable &quot;Setup.exe&quot;, se encarga de ejecutar todos los instaladores con los prerrequisitos. Es importante que los archivos de prerrequisitos estén en la misma carpeta que el ejecutable &quot;Setup.exe&quot;

El equipo va chequear si tenemos todo instalado en caso de no tenerlo el programa de instalación se encargada de agregar todos los prerrequisitos que hagan falta. Una vez llegado el momento de la instalación del local agent veremos la siguiente imagen:

![](RackMultipart20210310-4-1qq9bh0_html_dfa4d423dd1753f1.png)

Hacemos click en siguiente, luego de eso nos preguntara la ubicación de donde instalara los datos del servicio, en este caso utilizaremos la default.

![](RackMultipart20210310-4-1qq9bh0_html_5d6266039c357f77.png)

Damos siguiente una vez más y el local agent va a pedir confirmación nuevamente. Una vez confirmado el instalador llegara al 75% de la instalación. Una vez alcanzado este punto el local agent abre una ventana con el pedido de un archivo, este mismo es el &quot;install.config&quot;. ![](RackMultipart20210310-4-1qq9bh0_html_ccd6c6cdd1cfcdf4.png)

Procedemos a buscar el archivo, lo seleccionamos y le damos &quot;open&quot;.

![](RackMultipart20210310-4-1qq9bh0_html_f9eb4157edcbc657.png)

Una vez encontrado el archivo la instalación del LA continuara.

Cuando finalice la instalación hacemos click en &quot;Finalizar&quot; para terminar con la instalación del mismo.

## **Como armar el archivo install.config**

El archivo install.config es un archivo de texto que se puede realizar con bloc de notas.

Abrimos un bloc de notas nuevo.

![](RackMultipart20210310-4-1qq9bh0_html_99e0682df14ff1bc.png)

Abrimos el bloc de notas y procedemos a adjuntar la siguiente información:

![](RackMultipart20210310-4-1qq9bh0_html_7562c357cf9c14ed.png)

Breve aclaración sobre los apartados del Install.config

\&lt;Local\_Agent\_Configuration\&gt;

![](RackMultipart20210310-4-1qq9bh0_html_733f5c83f4e60b4d.gif)

_En esta sección podemos ingresar el código de suscripción del TERMINAL/CONTROLADOR que figura en Ationet._

\&lt;Configuration\&gt;

![](RackMultipart20210310-4-1qq9bh0_html_69a54ba8c20f0a66.gif)

\&lt;Subscriber\_Code\&gt;3M1\&lt;/Subscriber\_Code\&gt;

![](RackMultipart20210310-4-1qq9bh0_html_d9d95f76b0dff9c5.gif)

_En esta sección configuramos a la URL que va a enviar la data. En este caso es producción, si fuese beta la URL_ _ **https://native-beta.ationet.com/v1/\&lt;/** _

![](RackMultipart20210310-4-1qq9bh0_html_69a54ba8c20f0a66.gif)

\&lt;ATIOnet\_URL\&gt;https://native.ationet.com/v1/\&lt;/ATIOnet\_URL\&gt;

![](RackMultipart20210310-4-1qq9bh0_html_69a54ba8c20f0a66.gif) ![](RackMultipart20210310-4-1qq9bh0_html_c64100fd2d243c7b.gif)

_Este es el puerto de entrada del Local Agent. Siempre se utiliza el 33173_

\&lt;Native\_Socket\_Port\&gt;33173\&lt;/Native\_Socket\_Port\&gt;

![](RackMultipart20210310-4-1qq9bh0_html_1619a7e19488d5a2.gif) ![](RackMultipart20210310-4-1qq9bh0_html_56e7c4fba9afd8f2.gif)

_Esta sección de la configuración define el usuario que se va a utilizar para poder comunicarse el servicio de ATG de la Nano CPI. El cual se encarga de subir la data de tanques y delivery&#39;s._

_El usuario y la contraseña se sacan de la sección de Usuarios. Se tiene que crear un usuario del tipo FMSAPI_

\&lt;FMSAPIUser\&gt;\&lt;/FMSAPIUser\&gt;

\&lt;FMSAPIPassword\&gt;\&lt;/FMSAPIPassword\&gt;

\&lt;FMSAPIPasswordSalt\&gt;\&lt;/FMSAPIPasswordSalt\&gt;

![](RackMultipart20210310-4-1qq9bh0_html_56e7c4fba9afd8f2.gif)

_La última sección de la configuración define la comunicación con el servicio de Payware. Los valores son:_

_PaywareURL:_ [_http://vm-ationetiso01.cloudapp.net_](http://vm-ationetiso01.cloudapp.net/)

_PaywareSocketPort: 33176 BETA / 33166 PROD_

_UseSerialPort: false_

![](RackMultipart20210310-4-1qq9bh0_html_1619a7e19488d5a2.gif)\&lt;PaywareURL\&gt;\&lt;/ PaywareURL \&gt;

\&lt;PaywareSocketPort\&gt;\&lt;/ PaywareSocketPort \&gt;

\&lt;UseSerialPort\&gt;\&lt;/ UseSerialPort \&gt;

\&lt;/Configuration\&gt;

\&lt;/Local\_Agent\_Configuration\&gt;

Para que nuestro equipo se pueda conectar con el portal de Ationet deberemos modificar el \&lt;Subscriber\_Code\&gt;, para descubrir cuál es el de nuestro sitio para ello deberemos ingresar en el portal de Ationet, luego ingresamos al apartado Administrador \&gt; Terminal / Controladora.

![](RackMultipart20210310-4-1qq9bh0_html_5b5a0995c884023f.gif) ![](RackMultipart20210310-4-1qq9bh0_html_b9fdf20d4cf1eebe.png)

Una vez estemos en este apartado deberemos copiar los primero tres dígitos que se encuentran en el apartado de Código (En este ejemplo copiaremos 3M1, por lo general los primeros 3 dígitos se utilizan para todos los códigos de las Terminales / Controladoras), luego lo colocaremos en el apartado de \&lt;Subscriber\_Code\&gt;, quedaría de la siguiente manera:

\&lt;Local\_Agent\_Configuration\&gt;

\&lt;Configuration\&gt;

\&lt;Subscriber\_Code\&gt;3M1\&lt;/Subscriber\_Code\&gt;

\&lt;ATIOnet\_URL\&gt;native.ationet.com/v1/\&lt;/ATIOnet\_URL\&gt;

\&lt;Native\_Socket\_Port\&gt;33173\&lt;/Native\_Socket\_Port\&gt;

\&lt;FMSAPIUser\&gt;\&lt;/FMSAPIUser\&gt;

\&lt;FMSAPIPassword\&gt;\&lt;/FMSAPIPassword\&gt;

\&lt;FMSAPIPasswordSalt\&gt;\&lt;/FMSAPIPasswordSalt\&gt;

\&lt;PaywareURL\&gt;\&lt;/PaywareURL\&gt;

\&lt;PaywareSocketPort\&gt;\&lt;/PaywareSocketPort\&gt;

\&lt;UseSerialPort\&gt;false\&lt;/UseSerialPort\&gt;

\&lt;/Configuration\&gt;

\&lt;/Local\_Agent\_Configuration\&gt;

## **Revisión de logs luego de la instalación**

Una vez finalizada la instalación procedemos a verificar los logs para ver si completó la descarga de datos correspondiente para la base offline.

Los logs se encuentran ubicados normalmente en:

C:\Program Files (x86)\ATIONet\ATIONet Local Agent\logs

# **Estadisticas**

La siguiente información compartida es en un ambiente de prueba. Estos son los tiempos de espera de subida de datos del Local Agent cuando pasa de modo OFFLINE a ONLINE.

| **NANO APP:** | 4.4.20 | **Versión de Windows:** | Windows 10 Enterprise LTSC V1809 |
| --- | --- | --- | --- |
| **NANO CORE:** | 1.5.0 | **Driver Wireless:** | Qualcomm Atheros AR5BWB225 Wireless Network Adapter 3.0.2.201 |
| **Estructura del Laboratorio** |
| Nano CPI2 + TWC+ LC IQ+ EMR3+ Probeta torrix+PWC+ICO100 La comunicación de la nano con Local Agent es mediante cable de red conectado directamente de la ICO 100 a la NANO CLI 2. La salida de datos se realiza por WIFI. |
|
| |
| **Proceso** | **Tiempo de espera** |
| Primera bajada de paquetes luego de la instalación | El proceso inicia a las 13:43 con un volumen de paquetes de 293. Demora 1 min en completar la actualización completa. |
| 2 despachos ONLINE | Ambas autorizaciones demoran 2 segundos en recibir respuesta. |
| **2** despachos OFFLINE | Primer despacho presenta demora de 15 segundos. Segundo despacho presenta demora de 2 segundos. |
| Subida de despachos realizados OFFLINE | Subida de paquetes presenta demora de 3 segundos al cargar los 2 despachos OFFLINE. |
| **5** despachos OFFLINE | En los 2 primeros despachos se rechaza por timeout (20s - 30s). Los siguientes 3 despachos presentan demora de 2 segundos. |
| Subida de despachos realizados OFFLINE | Subida de paquetes presenta demora de 5 segundos al cargar los 5 despachos OFFLINE. |
| **10** despachos OFFLINE | Todos los despachos presentan demora de 2 segundos en el proceso de autorización. |
| Subida de despachos realizados OFFLINE | Subida de paquetes demora 8 segundos al cargar los 10 despachos OFFLINE. |
| Subida de delivery | Subida de delivery presenta una demora de 5 segundos. |
