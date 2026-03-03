![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|**Información del Documento**|.|
|--- |--- |
|**Archivo:**|ATIONet-StandAlone_650p_Terminal_Installation_Guide-ES.md|
|**Versión del Doc.:**|1.0|
|**Fecha de Publicación:**|11, Febrero 2026|
|**Autor:**|ATIONet LLC|


# Contenido

- [Introducción](#Introducción)
- [Hardware necesario](#Hardware-necesario)
- [Software necesario](#Software-necesario)
- [Descarga de Pre-requisitos y Aplicación](#Descarga-de-Pre-requisitos-y-Aplicación)
- [Instalación](#Instalación)
- [Actualizacion](#Actualizacion)
- [Configuración](#Configuración) 

# Introducción

En este Manual procederemos a realizar una breve explicación de cómo instalar y actualizar las terminales StandAlone T650p. 
La instalación debe ser realizada descargando los archivos desde una computadora a la memoria interna de la terminal. Para esto, haremos uso de un Pendrive y un cable USB hembra a tipo C macho

# Hardware necesario

- Terminal Verifone T650p
- Cable USB [HEMBRA] a tipo C [MACHO] ([Ejemplo del tipo de cable requerido](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Ejemplo%20del%20tipo%20de%20cable%20requerido.webp))
- USB pendrive
- Ordenador

# Descarga de Pre-requisitos y Aplicación

Descargue los archivos necesarios para la instalación desde [aquí](https://downloads.ationet.com). Los archivos a descargar son:

- OTA Secure
- SetSponsor
- SDI
- Versión de Terminal T650p

# Instalación

Primero deberán descargar los archivos previamente indicados **(OTA Secure, SetSponsor, SDI y la Versión de Terminal T650p)** en el pendrive para posteriormente hacer uso del cable USB (HEMBRA) a tipo C (MACHO) para poder cargarlos en la terminal.
Una vez realizado este paso, deberán abrir la parte posterior de la terminal donde se podrá visualizar la batería. 

![Parte de Atras de la terminal](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Parte%20de%20Atras%20de%20la%20terminal.jpg)

Debajo de la misma se encuentra un pequeño botón para el cual deberán introducir un clip de papel u otro objeto de volumen similar.
Al mantener presionado este botón por 3 segundos habían ingresado al menú de operadores de la terminal desde el cual accederemos al menú de supervisor.

![Menu de Supervisor](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor.PNG)

Ahora deberan seleccionar la opción de ***"Supervisor"*** para la cual se les solicitará una contraseña, la misma por default es **1668311**

![Menu de Supervisor (Password)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor%20(Password).PNG)

Posteriormente, deberemos seleccionar las opciones **"Device"** > **"Load Update Package"**.

![Menu de Supervisor (Devices)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor%20(Devices).PNG)
![Menu de Supervisor (Load Update Package)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor%20(Load%20Update%20Package).PNG)

En esta vista presionaremos el ícono de las 3 líneas para seleccionar la opción **"Choose Files"** donde finalmente deberemos seleccionar la opción de **"Memoria Interna"** (Esto debido a que ya pasamos los archivos de instalación a la memoria interna de la terminal).
En este apartado podremos visualizar los distintos pre-requisitos, los cuales deberán ser instalados en el siguiente orden:

***OTA Secure > SetSponsor > SDI > APK (Ultima versión de la terminal 650p)***

>  [!NOTE]
> ***Una vez subido el primer archivo se reiniciará la terminal, por lo que se deberá repetir el proceso de instalación por cada archivo a subir***

Tras haber realizado estos pasos, se mostrará una pantalla la cual indicará ***“Buscando actualizaciones”***. 
Para avanzar de este apartado deberá presionar las 4 esquinas de la pantalla en el siguiente orden:

* **Esquina superior izquierda** 
* **Esquina superior derecha** 
* **Esquina inferior derecha**
* **Esquina inferior izquierda**


## Actualizacion

Para actualizar la terminal T650p, será necesario resetear de fábrica la terminal.
Para realizar este paso, deberán abrir la parte posterior de la terminal donde se podrá visualizar la batería. 
Debajo de la misma se encuentra un pequeño botón para el cual deberán introducir un clip de papel u otro objeto de volumen similar.
Al mantener presionado este botón por 3 segundos habían ingresado al menú de operadores de la terminal desde el cual accederemos al menú de supervisor.

![Parte de Atras de la terminal](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Parte%20de%20Atras%20de%20la%20terminal.jpg)

Ahora deberan seleccionar la opción de ***"Supervisor"*** para la cual se les solicitará una contraseña, la misma por default es **1668311**

![Menu de Supervisor](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor.PNG)

Posteriormente, deberemos presionar en los 3 puntos ubicados en la esquina superior izquierda de la pantalla y seleccionaremos la opción ***“Android Settings”***.

![Menu de Supervisor (Android Settings)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor%20(Android%20Settings).PNG)

Dentro de este menú seleccionaremos las opciones ***“Sistema”*** y dirigirnos a  ***“Opcion de Recuperacion”***.

![Menu de Supervisor (System)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor%20(System).PNG)
![Menu de Supervisor (Reset options)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor%20(Reset%20options).PNG)

Una vez en esta visita realizaremos la siguiente selección: ***“Borrar datos de Fábrica” > “Restablecer” > “Borrar Todo”***

![Menu de Supervisor (Reset de fabrica)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor%20(Reset%20de%20fabrica).PNG)

Una vez, finalizado esto, para instalar la nueva versión se deberán repetir los pasos realizados en el apartado de [Instalación](#Instalación).


# Configuración

En esta sección indicaremos la configuración necesaria para poder empezar a operar con la terminal T650p

>  [!NOTE]
> *La única información que se detalla en esta sección es la información MÍNIMA para poder operar con la terminal*

1. Iniciaremos Ingresando al apartado de ***"Mantenimiento"*** en la parte inferior derecha de la pantalla

![Config (Manteinance)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Manteinance).PNG)

2. Posteriormente, ingresamos la contraseña de supervisor, la cual por default es ***Ationet@1*** (En caso de no poder ingresar con esta contraseña, comuníquese con support@atioinc.com)

![Config (Password)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Password).PNG)

3. Luego ingresamos al menú de ***"Configuraciones"***

![Config (Settings)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Settings).PNG)

4. Una vez en este menú, nos dirigimos a la sección ***"Ationet"***

![Config (Ationet)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Ationet).PNG)

5. Finalmente, deberemos configurar los siguientes parámetros:

* **"Native URL"**: Esta es la Url que apunta a uno de los dos siguientes ambientes:

    - https://native-beta.ationet.com/ (BETA)

    - https://native.ationet.com/ (PROD)

* **Terminal Identification**: En este apartado deberán configurar el código de terminal correspondiente con la del portal

    - **Terminal code:** "Los primeros 3 caracteres del código de suscripción" + "Código particular de la terminal"

![Config (Ationet - Terminal de ejemplo)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Ationet%20-%20Terminal%20de%20ejemplo).PNG)

6. Una vez finalizada esta configuración, debemos **guardar** y **salir**.

![Config (Ationet - Save)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Ationet%20-%20Save).PNG)

7. Finalmente, deberemos ingresar al apartado de ***"Configuración de Producto/SKU"*** y configurar los productos con los cuales vamos a operar.

![Config (Products)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Products).PNG)

8. Aquí deberemos seleccionar "Añadir nuevo Producto/SKU" e introducir la siguiente información:

* **Código de Producto/SKU**: Introduzca el código del Producto/SKU correspondiente con el del portal de flota
  
* **Nombre del Producto/SKU**: Introduzca un nombre referencial para el Producto/SKU
  
* **Precio del Producto/SKU**: Introduzca el precio deseado para el Producto/SKU

![Config (Products - New)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Products%20-%20New).PNG)

"Una vez completada esta información presione **Guardar** y con esto habrá completado la configuración principal de la terminal T650p"



[Volver al inicio](#contenido) 	:arrow_up:



