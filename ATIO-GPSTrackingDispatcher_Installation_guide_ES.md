# ATIONET - GPS Tracking Dispatcher

## Guia de instalación y configuración del servicio.


### Sobre este documento

Este documento detalla la forma de  instalación del servicio en el Local Agent (IGPC ICO 300 u otro). El mismo será el responsable de obtener las coordenadas de GPS enviadas por este agente a través del servicio ATIO Nano StoreAndForward instalado en él, para posteriormente enviarlas al servidor de ATIO para su posterior uso.

### Requisitos

Este servicio depende del servicio ATIO Nano StoreAndForward para su correcto funcionamiento. Adicionalmente se requerirá que por primera vez, previo a su uso, se configure un archivo donde se configurarán todas las variables de entorno necesarias para su correcto funcionamiento.

### Instalación

Para la instalación de este servicio, lo primero que necesitaremos será copiar la carpeta contenedora del mismo en nuestro Local Agent.
Luego, deberemos ingresar a la carpeta que acabamos de crear, buscar nuestro archivo de instalación llamado ‘installT1.bat’ y ejecutarlo para que realice la instalación del servicio.

``` 
Nota: Nuestro servicio se instalará para ejecutarse de manera automática cuando inicie nuestro agente local.
``` 

### Configuración del servicio

Previo a poder utilizar nuestro servicio deberemos realizar algunos cambios en nuestro archivo de configuración,para ello, deberemos dirigirnos a la carpeta desde donde ejecutamos el archivo de instalación, buscar un archivo llamado ‘appsettings’ y abrirlo con un editor de texto.
Dentro de la misma encontraremos los siguientes aspectos configurables:

* **IP:** Será la dirección ip que utilizaremos para conectarnos al servicio ‘ATIO Nano StoreAndForward’.

```
Nota: Si ambos servicios se encuentran instalados en nuestro agente local, la ip debería quedar configurada como 127.0.0.1
```

* **Port:** Al igual que la ip, será el puerto que utilizará para obtener las coordenadas GPS enviadas por request desde el servicio encargado de esto.

* **TrackingInterval:** Será el intervalo de tiempo entre cada request. El mismo se encuentra expresado en milisegundos. Por ejemplo, si queremos que espere un minuto entre cada petición, este campo deberá ser configurado en 60000

* **Url:** Será la dirección en la cual enviaremos nuestros request’s con la información obtenida para almacenarla.

* **Authorization:** Este campo se enviará en los request del punto anterior para poder autenticar la información del usuario que se encuentra realizando las peticiones.

* **DeviceID:** Este punto contendrá el número de identificación del dispositivo vinculado a este servicio.