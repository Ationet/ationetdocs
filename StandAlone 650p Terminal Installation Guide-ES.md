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
    - [Terminal](#Terminal)
    - [Sites](#Sites)
    - [Ationet](#Ationet)
 

# Introducción

En este Manual procederemos a realizar una breve explicación de cómo instalar y actualizar las terminales StandAlone T650p. 
La instalación debe ser realizada descargando los archivos desde una computadora a la memoria interna de la terminal. Para esto, haremos uso de un Pendrive y un cable USB hembra a tipo C macho

# Hardware necesario

- Terminal Verifone T650p
- Cable USB (Hembra) a tipo C (Macho) ([Ejemplo del tipo de cable requerido](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Ejemplo%20del%20tipo%20de%20cable%20requerido.webp)
- USB pendrive
- Dispositivo desde el cual realizar la descarga de archivos

# Descarga de Pre-requisitos y Aplicación

Descargue los archivos necesarios para la instalación desde [aquí](https://downloads.ationet.com). Los archivos a descargar son:

- Ota_Secure v3.45.1
- SetSponsor
- SDI
- Versión de Terminal T650p

# Instalación

Primero deberán descargar los archivos previamente indicados **(Ota_Secure v3.45.1, SetSponsor, SDI y la Versión de Terminal T650p)** en el pendrive para posteriormente hacer uso del cable USB (hembra) a tipo C (Macho) para poder cargarlos en la terminal.
Una vez realizado este paso, deberán abrir la parte posterior de la terminal donde se podrá visualizar la batería. 

IMAGEN 

Debajo de la misma se encuentra un pequeño botón para el cual deberán introducir un clip de papel u otro objeto de volumen similar.
Al mantener presionado este botón por 3 segundos habían ingresado al menú de operadores de la terminal desde el cual accederemos al menú de supervisor.

IMAGEN

Ahora deberan seleccionar la opción de ***"Supervisor"*** para la cual se les solicitará una contraseña, la misma por default es **1668311**

IMAGEN

Posteriormente, deberemos seleccionar las opciones **"Device"** > **"Load Update Package"**.

IMAGEN

En esta vista presionaremos el ícono de las 3 líneas para seleccionar la opción **"Choose Files"** donde finalmente deberemos seleccionar la opción de **"Memoria Interna"** (Esto debido a que ya pasamos los archivos de instalación a la memoria interna de la terminal).
En este apartado podremos visualizar los distintos pre-requisitos, los cuales deberán ser instalados en el siguiente orden:

***Ota_Secure > SetSponsor > SDI > APK (Ultima versión de la terminal 650p)***

IMAGEN

Tras haber realizado estos pasos, se mostrará una pantalla la cual indicará ***“Buscando actualizaciones”***. 
Para avanzar de este apartado deberá presionar las 4 esquinas de la pantalla en el siguiente orden:

* **Esquina superior izquierda** 
* **Esquina superior derecha** 
* **Esquina inferior derecha**
* **Esquina inferior izquierda**


## Actualizacion

Para actualizar la terminal T650p, será necesario resetear de fábrica la terminal.
Para realizar este paso, deberán abrir la parte posterior de la terminal donde se podrá visualizar la batería. 

IMAGEN 

Debajo de la misma se encuentra un pequeño botón para el cual deberán introducir un clip de papel u otro objeto de volumen similar.
Al mantener presionado este botón por 3 segundos habían ingresado al menú de operadores de la terminal desde el cual accederemos al menú de supervisor.

IMAGEN

Ahora deberan seleccionar la opción de ***"Supervisor"*** para la cual se les solicitará una contraseña, la misma por default es **1668311**

IMAGEN

Posteriormente, deberemos presionar en los 3 puntos ubicados en la esquina superior izquierda de la pantalla y seleccionaremos la opción ***“Android Settings”***.

IMAGEN

Dentro de este menú seleccionaremos las opciones ***“Sistema”*** y dirigirnos a  ***“Opcion de Recuperacion”***.

IMAGEN

Una vez en esta visita realizaremos la siguiente selección: ***“Borrar datos de Fábrica” > “Restablecer” > “Borrar Todo”***

IMAGEN

Una vez, finalizado esto, para instalar la nueva versión se deberán repetir los pasos realizados en el apartado de [Instalación](#Instalación).



# Configuración



## Terminal



## Sites



## Ationet






