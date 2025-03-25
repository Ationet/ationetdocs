![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# Ationet Fleet Mobile Payment - Fleet Authorization #

|Información de Documento||
|--- |--- |
|Archivo:|ATIONet - Fleet Mobile Payment Fleet Authorization|
|Doc Version:|1.0|
|Fecha:|25-03-2025|
|Autor:|Alexis E. Yañez|

|Control de Cambios |||
|--- |--- |--- |
|Ver.|Fecha|Cambios|
|1.0|25-03-2025|Initial version.|

## Contenido ##
- [Introducción](#Introducción)
- [Mensajería de Configuración](#MensajeríadeConfiguración)
  - [Flujo de Inicialización ](#FlujodeInicialización)




## Introducción
Este documento describe la operación para efectuar una transacción con una autorización por medio del autorizador de flota de Ationet a travez de nuestra aplicación móvil.

## Mensajería de Configuración

### Flujo de Inicialización 

<p align="center">
![image](https://github.com/user-attachments/assets/1a3643c2-3583-4efc-afa3-407f0b6ebfeb)
</p>
### Connection

Relative URL : /connection
Method: POST
Input : application/json
Output : application/json

Uso : Verificación de conexión y heartbeat. El Site System enviará este mensaje periódicamente cada 45 segundos. En caso de no recibir respuesta, se cerrará la conexión SSE, la cual se establecerá nuevamente tan pronto como el MPPA responda satisfactoriamente a este mensaje.
En caso de recibir respuesta y que el Status Code sea un 400 (Bad Request), el Site System cerrará la conexión SSE (en caso de tenerlo abierto) y se establecerá una nueva conexión.

Body:
```json
{
  "applicationSender": "{{SiteCode}}",
  "workstationID": "{{SiteCode}}",
  "timestamp": "2009-11-20T17:30:50",
  "interfaceVersion": "1.0"
}
```
Definición de Campos:
applicationSender: Debe contener el SiteCode del sitio que se encuentra operando.
workstationID:  Debe contener el SiteCode del sitio que se encuentra operando.
timestamp: fecha y hora de la solicitud
interfaceVersion: valor fijo





