
![ATIOnetLogo_250x70](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

|**Información del Documento**|.|
|--- |--- |
|**Archivo:**|R-EVOPOS Guia de Intalacion.md|
|**Versión del Doc.:**|1.0|
|**Fecha de Publicación:**|16, Julio 2025|
|**Autor:**|ATIONet LLC|

|**Registro de Cambios**|||
|--- |--- |--- |
|**Ver.**|**Fecha**|**Resumen de Cambios**|
|1.0|16/Jul/2025|- Versión Inicial


# Contenido

- [Introducción](#Introducción)
- [Hardware necesario](#Hardware-necesario)
- [Software necesario](#Software-necesario)
- [Descarga de Pre-requisitos y Aplicación](#Descarga-de-Pre-requisitos-y-Aplicación)
- [Instalación](#Instalación)

# Introducción

Este documento describe el procedimiento para instalar una aplicación Android utilizando ADB (Android Debug Bridge) a través de línea de comandos. 

# Hardware necesario

* Terminal contar con una carga de batería mayor al 25% 
* Cable USB

# Software necesario

* Android Debug Bridge, (ADB, adb_android_tools.zip)
* app-t650p-release.apk​

# Descarga de Pre-requisitos y Aplicación

* Extraer el archivo ADB en el computador
* Descargar y pegar el archivo APK ubicado en la carpeta ADB accesible

# Instalación

1. Abrir la línea de comandos. En Windows: presionar Win + R, escribir cmd y presionar Enter.

2. Navegar a la carpeta donde se encuentra ADB y la APK (cd C:\adb)

3. Presionar “Enter” 

4. Instalar el SetSponsor217485.tgz Ingresar el siguiente comando: adb install -r SetSponsor217485.tgz

5. Confirmar instalación exitosa. (ADB mostrará el mensaje: Success)

![Requisitos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/R-EVOPOS%20Guia%20de%20Intalacion/Requisitos.png)

6. Instalar la APK en el dispositivo. Ingresar el siguiente comando: adb install -r revopos-t650p-release.apk 
 
7. Confirmar instalación exitosa.(ADB mostrará el mensaje: Success). Posteriormente, la aplicación debe estar disponible en el menú de aplicaciones del dispositivo Android. 

8. Abrir la aplicación 

9. Se informará la siguiente pantalla, presionar OK en la misma 

![Resultados](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/R-EVOPOS%20Guia%20de%20Intalacion/Resultados.png)
