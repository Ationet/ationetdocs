
![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|**Información del Documento**|.|
|--- |--- |
|**Archivo:**|Procesos operativos para la terminal T650p Stand Alone de ATIONET-ES.md|
|**Versión del Doc.:**|1.0|
|**Fecha de Publicación:**|23, Junio 2026|
|**Autor:**|ATIONET LLC|



- [Introducción](#Introducción)
- [Operaciones](#Operaciones)
- [Menú de Flota](#Menú-de-Flota)
  - [Autorizacion](#Autorizacion)
  - [Finalizacion](#Finalizacion)
  - [PostPago](#PostPago)
  - [Recibo](#Recibo)
  - [Consulta de Saldo](#Consulta-de-Saldo)
  - [Eliminar transacciones pendientes](#Eliminar-transacciones-pendientes)
  - [Anular transaccion](#Anular-transaccion)
- [Menú de Tareas](#Menú-de-Tareas)
  - [Cambiar PIN](#Cambiar-PIN)
  - [Cierre de Lote](#Cierre-de-Lote)
- [Menú de Fidelidad](#Menú-de-Fidelidad)
  - [Fidelizar](#Fidelizar)
  - [Consulta de Saldo Fidelidad](#Consulta-de-Saldo-Fidelidad)
  - [Redencion de Puntos](#Redencion-de-Puntos)
  - [Canje de Premios](#Canje-de-Premios)
  - [Cierre de lote Fidelidad](#Cierre-de-lote-Fidelidad)
  - [Reversa de Acumulacion](#Reversa-de-Acumulacion)
  - 
- [Mantenimiento](#Mantenimiento)
  - [Cambias la constraseña del suprevisor](#Cambias-la-constraseña-del-suprevisor)
  - [Crear o editar productos](#Crear-o-editar-productos)
  - [Sincronizar ahora](#Sincronizar-ahora)
  - [Enviar Logs](#Enviar-Logs)
  - [Configuración](#Configuración)
      - [Idioma](#Idioma)
      - [Controlador](#Controlador)
      - [ATIONET](#ATIONET)
      - [Módulos](#Módulos)
      - [Configuración de Tickets](#Configuración-de-Tickets)
      - [Otros](#Otros)

     
## Introducción
Este manual tiene como objetivo ayudar y guiar al usuario en el uso del terminal autónomo ATIONET T650p. Los terminales autónomos ATIONET permiten al usuario autorizar transacciones de flotas en los hosts de ATIONET.

## Operaciones
A continuación se detallan todas las operaciones disponibles en los terminales autónomos T650p:

**> Menú de Flota**
- Autorizacion
- Finalizacion
- PostPago
- Recibo
- Consulta de Saldo
- Eliminar transacciones pendientes
- Anular transaccion

**> Menú de tareas**
- Cambiar PIN
- Cierre de Lote

**> Menú de Fidelidad**
- Fidelizar
- Consulta de Saldo Fidelidad
- Redencion de Puntos 
- Canje de Premios
- Cierre de Lote Fidelidad
- Reversa de Acumulacion 

**> Mantenimiento**
- Cambias la constraseña del suprevisor
- Crear o editar productos
- Sincronizar ahora
- Enviar logs
- Configuracion


## Menu de Flota

## Autorizacion
Durante el funcionamiento normal, la transacción se divide en dos operaciones. Primero se realiza una preautorización desde el TPV para obtener la autorización para continuar con la transacción y el importe del envío máximo. Una vez realizado el envío, tiene lugar la confirmación, en la que se informa del importe real.

La preautorización implica la comunicación con el sistema central y la obtención del saldo que este autoriza. Además, la captura de este saldo implica que no puede utilizarse simultáneamente desde otro lugar. Esto significa que, SIEMPRE después de una preautorización, debe realizarse una finalización o una eliminación de preautorización pendiente para actualizar el saldo en el sistema central.

Inicie la operación seleccionando en el menú del panel táctil la opción AUTORIZACIÓN.
El sistema le pedirá ahora que presente la identificación asignada al vehículo/conductor ya sea de manera manual o utilizando otros metodos de lectura.
Seleccione el producto correspondiente que desea expedir.
Una vez introducidos todos los datos, el TPV mostrará el mensaje Procesando... mientras se comunica con el sistema central para solicitar la autorización.
Si la transacción no se autoriza, el sistema mostrará un mensaje de error y, tras seleccionar Aceptar, el terminal imprimirá el ticket.
Si la transacción se autoriza, el sistema responderá con un mensaje de confirmación y, a continuación, el terminal imprimirá un ticket de autorización. El ticket indica el importe autorizado para el envío correspondiente a ese identificador en esa transacción.


## Finalizacion

Una vez completado el envío, es necesario confirmar la transacción en el sistema. Para ello, siga estos pasos:

Inicie la confirmación seleccionando en el menú del panel táctil la opción FINALIZACION.
Recuerda que el importe enviado no puede superar el importe autorizado en la preautorización.
Si introduce un importe superior al preautorizado, recibirá un mensaje de error y la transacción NO se confirmará.

Si los datos introducidos son correctos, la operación se confirmará en el servidor.
La pantalla mostrará el mensaje Operación completada y el TPV imprimirá el ticket de la transacción.


## PostPago

En algunas circunstancias, puede darse el caso de que la venta ya se haya realizado y el envío se haya completado sin seguir el flujo normal de pre autorización y confirmación. Es importante tener en cuenta que, al procesar una operacion postpago, el sistema aplicará las mismas restricciones que se habrían aplicado en una preautorización; por lo tanto, si se intenta introducir una venta por un importe o volumen que no esté autorizado para ese identificador en ese momento, la venta será rechazada. Si esto ocurre, será necesario ponerse en contacto con el servicio de asistencia para determinar cómo proceder con la venta.

Inicie la venta seleccionando en el menú del panel táctil la opción POSTPAGO.
El TPV solicitará que se presente la identificación asociada a la venta para ser registrada.
Tras leer la identificación, el terminal muestra Procesando... mientras se comunica con los sistemas centrales para notificar la venta.
Si la transacción no está autorizada, el sistema responderá con un mensaje de error y, tras seleccionar Aceptar, el terminal imprimirá el ticket.
Si los datos introducidos son correctos, la operación se confirmará en el servidor. La pantalla mostrará el mensaje OPERACIÓN COMPLETADA y el TPV imprimirá el ticket de la transacción.
Si la transacción es autorizada, el sistema responderá con un mensaje de confirmación como el del ejemplo e imprimirá un ticket de autorización.


## Recibo
Si por alguna razón es necesario volver a imprimir el último ticket emitido, esto se puede hacer desde este menú.

Inicie la operación seleccionando en el menú del panel táctil la opción RECIBO.
En la pantalla se veran reflejas las ultimas DOS operaciones. Al presionar en cualquiera de esos dos, la TPV imprimirá automáticamente una copia del ticket indicado.


## Consulta de Saldo

Esta operación indica el importe máximo que se puede despachar en la siguiente transacción para una identificación específica. Realice esta consulta cuando se desconozcan los límites del vehículo en cuestión para evitar realizar múltiples intentos de preautorización que puedan ser denegados. Si el saldo indicado no se corresponde con la cantidad que el cliente cree tener, es necesario ponerse en contacto con el servicio de asistencia para determinar cómo proceder.

Inicie la venta seleccionando en el menú del panel táctil la opción CONSULTA DE SALDO.

El TPV le pedirá que presente la identificación asociada al vehículo/conductor cuyo saldo desea consultar.

Tras leer la identificación, el terminal muestra Procesando... mientras se comunica con los sistemas centrales para comprobar el saldo.

El sistema responde con el importe máximo disponible para el envío. Se muestra en pantalla y el TPV también imprime un ticket con dicha información.


## Eliminar transacciones pendientes

Si por alguna razón se han realizado una o más preautorizaciones y no se han efectuado los correspondientes envíos, será necesario liberar el saldo de estas pre autorizaciones para normalizar el saldo de la cuenta.

Inicie la cancelación de la preautorización seleccionando en el menú del panel táctil la opción ElLIMINAR TRANSACCIONES PENDIENTES.

El TPV solicitará que se presente la identificación asociada a la preautorización que se va a cancelar.

Tras leer la identificación, el terminal muestra la operacion correspondiente y para avanzar hay que presionar el boton de **¡Eliminar!**. Tras esto la TPV se comunicara con los sistemas centrales para cancelar la pre autorización.

Cuando el servidor haya respondido confirmando la cancelación de la preautorización, la pantalla mostrará un mensaje de confirmación. El saldo de la preautorización ya está disponible para su uso de nuevo.


## Anular transaccion
Si se produce un error al procesar una transacción en el sistema y el turno aún no se ha cerrado, esta opción permite anularlo y procesarlo correctamente.

Inicie la operación seleccionando en el menú del panel táctil la opción ANULAR TRANSACCIÓN.
El TPV solicitará la contraseña del supervisor y una vez ingresada, nos solicitara el código de autorización de la transacción que se va a cancelar. 
Ante de proceder con la eliminacion se nos consultara una última vez antes de anularla, para proceder hay que darle al boton de **SI**.
Posteriormente, el TPV solicitará al sistema que anule la transacción. Durante ese proceso, se mostrará en pantalla Procesando….
Una vez completado correctamente el proceso de anulación, el TPV muestra un mensaje indicando e imprime un ticket de confirmación o uno de error si el proceso ha fallado.


## Menu de Tareas

## Cambiar PIN

Esta opción permite realizar el cambio de PIN para un identificador en concreto.
Para esto presione el boton en el menu CAMBIAR PIN.
Posteriormente introduzca el identificador el cual recibira el correspondiente cambio, introduzca el antiguo PIN y posteriormente introduzca el NUEVO PIN y presione acceptar.


## Cierre de Lote
Este concepto permite agrupar un conjunto de transacciones para su posterior análisis y procesamiento. Por lo general, se recomienda realizar un cierre de lote al final de cada turno operativo en la gasolinera. De esta forma, se pueden conciliar fácilmente las transacciones que se pagaron con cualquiera de los medios de pago procesados por ATIONET.

Inicie la operación seleccionando en el menú del panel táctil la opción CIERRE POR LOTES.
Para proceder con el cierre de lote, se requieren permisos de supervisor. Introduzca la contraseña del supervisor.
Posteriormente, se presenta un breve paso de verificacion, en el cual luego de presionar el boton **SI**, se procedera con el cierre correspondiene y una vez que la operacion sea completada, el TPV mostrara un mensaje que indica OPERACIÓN COMPLETADA e imprime el ticket de cierre.


## Menu de Fidelidad

ATIONET Loyalty mantiene una cuenta de fidelidad independiente para cada miembro del programa. El saldo de la cuenta se incrementa con las transacciones de acumulación y se reduce con los reembolsos de acumulación y las reglas de caducidad del programa. Las transacciones de ajuste y transferencia también pueden aumentar o reducir el saldo de la cuenta, dependiendo del signo de la operación.

En el punto de servicio (tienda, quiosco, tienda online, etc.), el proceso de acumulación suele estar relacionado con una operación de compra o pago, en la que los clientes obtienen puntos a cambio de su compra.

Un programa de fidelización determinado puede tener ninguna, una o varias reglas de acumulación. Las reglas de acumulación se procesan en tiempo real cuando se recibe una solicitud de transacción de acumulación e indican a ATIONET Loyalty cuántos puntos deben añadirse a la cuenta del socio. No obstante, la captura también puede especificar una cantidad determinada de puntos que se deben otorgar a la cuenta, anulando las reglas del programa.


## Fidelizar
Inicie la operación seleccionando en el menú del panel táctil la opción FIDELIZAR y, a continuación, introducimos el identificador de fidelidad correspondiente mediante la introducción manual u otros métodos de lectura. Luego procederemos a elegir entre la acumulacion de punto o la aplicacion del descuento, para despues elegir el tipo de producto (Combustible o secos) y el monto o cantidad correspondiente.
Una vez introducidos todos los datos, el TPV mostrará el mensaje Procesando... mientras se comunica con el sistema central para procesar la acumulación.
Si la transacción se autoriza, el sistema responderá con un mensaje de confirmación y, a continuación, el terminal imprimirá un ticket de acumulación. El ticket indica la cantidad acumulada o el descuento aplicado para ese identificador dependiendo del tipo de operacion que hayamos deseado realizar.


## Consulta de Saldo Fidelidad
Esta operación indica el importe máximo que se puede despachar en la siguiente transacción para una identificación fidelizada. Realice esta consulta cuando se desconozcan los límites del vehículo en cuestión para evitar realizar múltiples intentos de preautorización que puedan ser denegados. Si el saldo indicado no se corresponde con la cantidad que el cliente cree tener, es necesario ponerse en contacto con el servicio de asistencia para determinar cómo proceder.

Inicie la venta seleccionando en el menú del panel táctil la opción CONSULTA DE SALDO.

El TPV le pedirá que presente la identificación asociada al identificador cuyo saldo desea consultar.

Tras leer la identificación, el terminal muestra Procesando... mientras se comunica con los sistemas centrales para comprobar el saldo.

El sistema responde con el importe máximo disponible para el envío. Se muestra en pantalla y el TPV también imprime un ticket con dicha información.


## Redencion de Puntos 
En este apartado se puede realizar el intercambio de los puntos disponibles por multiples recompensas.
Al precionar el boton de **REDENCION DE PUNTOS**, la controladora solicitara el identificador de fidelidad correspondiente. Posteriormente, seleccionamos el producto a reclamar y despues seleccionamos la cantidad del mismo. Finalmente, presionamos en el boton de **Confirmar** y el TPV tras procesar lo solicitado, imprimira el ticket con la informacion correspondiente a la redencion


## Canje de Premios
En este apartado se puede realizar el canje de premios mediante las funciones de la camara.
Primero presionamos el boton de **Canje de Premios**, lo cual habilitara la camara del dispositivo.
Luego escaneamos el QR con el premio correspondiente y finalmente, si se tienen los puntos necesarios, se efectua el canje.
Posteriormente, se imprimira el ticket mostrando los detalles del canje realizado.


## Cierre de Lote Fidelidad
Este concepto permite agrupar un conjunto de transacciones para su posterior análisis y procesamiento. Por lo general, se recomienda realizar un cierre de lote al final de cada turno operativo en la gasolinera. De esta forma, se pueden conciliar fácilmente las transacciones que se pagaron con cualquiera de los medios de pago procesados por ATIONET.

Inicie la operación seleccionando en el menú del panel táctil la opción CIERRE POR LOTES.
Para proceder con el cierre de lote, se requieren permisos de supervisor. Introduzca la contraseña del supervisor.
El TPV nos preguntar por ultima vez si queremos realizar el cierre. Luego este solicitará al sistema central el cierre de un lote y su procesamiento. Durante ese proceso, se muestra en pantalla Procesando….
Cuando finaliza el proceso, el TPV muestra un mensaje que indica OPERACIÓN COMPLETADA e imprime el ticket de cierre.
El ticket de cierre incluye un número de identificación único generado por el servidor, el número de transacciones procesadas desde el último cierre, el total de ventas, las cancelaciones y el importe acumulado durante el periodo.


## Reversa de Acumulacion 
Si se produce un error al procesar una acumulacion en el sistema, esta opción permite anularlo y procesarlo correctamente.

Inicie la operación seleccionando en el menú del panel táctil la opción REVERSA DE TRANSACCIÓN.
El TPV solicitará la contraseña del supervisor y una vez ingresada, nos solicitara el código de autorización de la operacion que se va a cancelar. 
Antes de proceder con la eliminacion se nos consultara una última vez antes de anularla, para proceder hay que darle al boton de **SI**.
Posteriormente, el TPV solicitará al sistema que anule la acumulacion. Durante ese proceso, se mostrará en pantalla Procesando….
Una vez completado correctamente el proceso de anulación, el TPV muestra un mensaje indicando e imprime un ticket de confirmación o uno de error si el proceso ha fallado.


## Mantenimiento

## Cambias la constraseña del suprevisor
Si por alguna razón es necesario modificar la contraseña de supervisor, se puede hacer desde este menú.

Inicie la operación seleccionando en el menú del panel táctil la opción CONTRASEÑA DE SUPERVISOR.
Introduzca la nueva contraseña de supervisor y luego vuelva a inroducirla para confirmar.
Una vez finalizado el proceso de cambio de contraseña, el TPV mostrará un mensaje de confirmación o un error si el proceso ha fallado.


## Crear o editar productos
Esta operación le permitirá configurar todos los combustibles disponibles para su dispensación. Desde aquí podrá configurar el nombre, el precio y el código del combustible. Es muy importante configurar el mismo código que en el sistema central, ya que es con este código con el que ATIONET reconoce el producto que se está dispensando.

Inicie la operación seleccionando en el menú del panel táctil la opción COMBUSTIBLES & SKUs.

Ahora dispondrá de dos listas una en la cual se podrán agregar los combustibles deseados y otra en la cual se podrán agregar los SKUs deseados. Para añadir uno nuevo, solo tiene que seleccionar el signo +.

El sistema le pedirá ahora que complete el nombre, el código y el precio del combustible. Una vez completado todo, seleccione la opción Crear.

Si por alguna razón es necesario modificar un combustible ya existente, solo tiene que seleccionar el combustible de la lista y el sistema le mostrará todos los detalles del mismo; a continuación, sólo tiene que editar los campos.


## Sincronizar ahora
Este apartado se utiliza para establecer una vinculación con el servicio de Terminal Management. Este servicio permite, administrar, configurar y actualizar terminales a distancia, así como monitorear múltiples terminales.
Comunicarse al correo de support@atioinc.com para recibir más detalles acerca del servicio de Terminal Management


## Enviar logs
Para poder enviar Logs se debe haber hecho previamente la vinculación con el servicio de ‘Terminal Management’, ya que es con este boton con el cual se pueden enviar los Logs de la terminal.


## Configuracion
El menú de configuración permite modificar los parámetros del TPV. Estas operaciones no son habituales y requieren en todos los casos la contraseña del supervisor para ingresar.

> [!NOTE]
Es importante aclarar que las imagenes solo reflejan la vista inicial del apartado, deberan desplazarse hacia abajo en la pantalla para ver el resto de la configuracion de cada apartado


## ***Idioma***
En este apartado se podra configurar el idioma deseado para la terminal. Para ello, debera presionar el boton con el idioma indicado y elegir el idioma de preferencia.
(Actualmente la terminal cuanta con el Ingles y Español).
  
## ***Controlador***
En este apartado se podra seleccionar el tipo de controladora que se utilizara para operar en la estacion. Para ello, debera desplazarse hacia la derecha he izquierda para navergar entre los tipos de sistemas disponibles.
(Actualmente la terminal cuanta con los sistemas de Stand Alone Y Fusion Business Service).
En caso de seleccionar el servicio de FUSION, debera ser necesario introducir la IP, el puerto y el codigo de tipo de pago correspondientes a la terminal.

## ***ATIONET***
En este apartado se configurara la informacion relacionada al sistema de ATIONET.

Se debera completar la siguiente informacion: 

* URL Nativa: Introduzca la URL del ambiente correspondiente
    - URL de BETA: https://native-beta.ationet.com/
    - URL de PRODUCTIVA: https://native.ationet.com/
  
* Identifiacacion de la terminal: Introduzca el mismo codigo de terminal configurado su subscripcion del portal de ATIONET.

* Establecer por defecto montó en lugar de cantidad: Habilia que por default se muestre primero la opción de introducir montó en lugar de volumen.

* Solicitudes fijas en operaciones: Al activar esta opción, se desplegara un menú con múltiples opciones, las cuales al ser activadas, esta se solicitarán siempre que se lleven a cabo operaciones.

La información que se puede solicitar es la siguiente:

- Identificación del asistente
- Identificación del conductor
- Identificacion del vehiculo
- Odómetro
- Horas de motor
- Remolque
- Misceláneos
- Unidad de camión
- Identificación secundaria
- PIN primario
- PIN secundario


## ***Módulos***
En este apartado se puede seleccionar los modulos con los cuales se operaran. Habilitar o deshabilitar modulos va a modificar la vista principal del menu.
Para seleccionar un modulo, debera desplazarse hacia la derecha he izquierda para navergar entre los distintos modulos y presionar el boton de "Habilitar Operaciones" para habilitar asi el modulo.
Adicionalmente, en modulo de Fidelidad, hay que agregar un usuario el cual tenga el rol de Loyalty API en el portal de ATIONET. Adicionalmente se puede seleccionar el tipo de sistema fidelidad con el que se quiera operar. (Es posible operar con Descuentos, Puntos o con ambos).


## ***Configuración de Tickets***
En este apartado se configura la información principal del sitio, siendo el **Código** y el **Nombre** lo mas importante.
Estas son las opciones de configuracion del sitio:

- Código de Sitio
- Nombre de Sitio
- Dirección de Sitio
- CUIT del Sitio

Posteriormente, se puede configurar qué información va a aparecer al momento de imprimir el ticket. 
La información que se podrá visualizar es la siguiente:

- Identificación del conductor
- Identificacion del vehiculo
- Nombre de la empresa
- Identificación primaria
- Identificación secundaria
- Precio de compañía

Adicionalmente se puede personalizar cierta información del ticket, como los son el título, el subtítulo, el pie de página y la nota inferior.

* Imprimir detalles de la transacción en columnas: Al activar esta opción, se verán los detalles de la transacción en columnas en lugar de un orden de lista.

La última opción disponible a configurar es una opción la cual permite mostrar número de factura en lugar de código de autorización.
Finalmente al pie de esta sección, se encuentra una previsualización del resultado final del ticket en base a la configuración realizada, la cual puede ser impresa para tener una versión física del mismo. 


## ***Otros***
En este apartado se permitira configurar informacion como la unidad de medida del combustible/GNC y el tipo de moneda con el que se transaccionara.
Adicionalmente, se encuentra el boton de "Imprimir Configuraciones", el cual al presionarlo generara que la terminal imprima ciertas configuraciones adicionales como lo son el tipo de version instalada en la terminal o el ID de sistema.

