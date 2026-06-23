
![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|**Información del Documento**|.|
|--- |--- |
|**Archivo:**|Procesos operativos para la terminal T650p Stand Alone de ATIONet-ES.md|
|**Versión del Doc.:**|1.0|
|**Fecha de Publicación:**|23, Junio 2026|
|**Autor:**|ATIONet LLC|



- [Introducción](#Introducción)
- [Operaciones](#Operaciones)
- [Menú de operaciones](#Menú-de-operaciones)
  - [Preautorización](#Preautorización)
  - [Confirmación](#Confirmación)
  - [Limpieza de preautorizaciones pendientes](#Limpieza-de-preautorizaciones-pendientes)
  - [Venta](#Venta)
  - [Consulta de saldo](#Consulta-de-saldo)
  - [Reembolso](#Reembolso)
  - [Imprimir último recibo](#Imprimir-último-recibo)
  - [Anular transacción](#Anular-transacción)
- [Menú de Tareas](#Menú-de-Tareas)
  - [Activar la tarjeta regalo](#Activar-la-tarjeta-regalo)
  - [Cierre de lote](#Cierre-de-lote)
  - [Cambio de PIN](#Cambio-de-PIN)
- [Menú de Fidelidad](#Menú-de-Fidelidad)
    - [Acumulación](#Acumulación)
    - [Cierre de lote Fidelidad](#Cierre-de-lote-Fidelidad)
- [Menú de Consumer Card](#Menú-de-Consumer-Card)
  - [Recargar de Consumer Card](#Recargar-de-Consumer-Card)
- [Mantenimiento](#Mantenimiento)
  - [Contraseña de supervisor](#Contraseña-de-supervisor)
  - [Crear o editar productos](#Crear-o-editar-productos)
  - [Sincronización con Terminal Management](#Sincronización-con-Terminal-Management)
  - [Enviar Logs](#Enviar-Logs)
  - [Configuración](#Configuración)
 
    
## Introducción
Este manual tiene como objetivo ayudar y guiar al usuario en el uso del terminal autónomo AtioNet T650p. Los terminales autónomos AtioNet permiten al usuario autorizar transacciones de flotas en los hosts de AtioNet.

## Operaciones
A continuación se detallan todas las operaciones disponibles en los terminales autónomos T650p:

**> Menú de Operaciones**
- Preautorización
- Confirmación
- Limpieza de preautorizaciones pendientes
- Venta
- Consulta de saldo
- Reembolso
- Imprimir último recibo
- Anular transacción

**> Menú de tareas**
- Activar la tarjeta regalo

**> Menú de Fidelidad**
- Acumulación
- Cierre de lote

**> Menú de Consumer card**
- Recargar de Consumer Card

**> Mantenimiento**
- Contraseña de supervisor
- Combustibles & SKUs
- Configuración

## Menú de operaciones

## Preautorización
Durante el funcionamiento normal, la transacción se divide en dos operaciones. Primero se realiza una preautorización desde el TPV para obtener la autorización para continuar con la transacción y el importe del envío máximo. Una vez realizado el envío, tiene lugar la confirmación, en la que se informa del importe real.

La preautorización implica la comunicación con el sistema central y la obtención del saldo que este autoriza. Además, la captura de este saldo implica que no puede utilizarse simultáneamente desde otro lugar. Esto significa que, SIEMPRE después de una preautorización, debe realizarse una finalización o una eliminación de preautorización pendiente para actualizar el saldo en el sistema central.

Inicie la operación seleccionando en el menú del panel táctil la opción AUTORIZACIÓN.
El sistema le pedirá ahora que presente la identificación asignada al vehículo/conductor. Para la introducción manual u otros métodos de lectura (por ejemplo, escáner), seleccione la opción Otros.
Seleccione el producto correspondiente que desea expedir.
Una vez introducidos todos los datos, el TPV mostrará el mensaje Procesando... mientras se comunica con el sistema central para solicitar la autorización.
Si la transacción no se autoriza, el sistema mostrará un mensaje de error y, tras seleccionar Aceptar, el terminal imprimirá el ticket.
Si la transacción se autoriza, el sistema responderá con un mensaje de confirmación y, a continuación, el terminal imprimirá un ticket de autorización. El ticket indica el importe autorizado para el envío correspondiente a ese identificador en esa transacción.
Realice el envío siguiendo las instrucciones indicadas en el albarán.


## Confirmación
Una vez completado el envío, es necesario confirmar la transacción en el sistema. Para ello, siga estos pasos:

Inicie la confirmación seleccionando en el menú del panel táctil la opción CONFIRMACIÓN.
Recuerda que el importe enviado no puede superar el importe autorizado en la preautorización.
Si introduce un importe superior al preautorizado, recibirá un mensaje de error y la transacción NO se confirmará. Pulse el botón verde para volver a introducir el importe correcto.

Si los datos introducidos son correctos, la operación se confirmará en el servidor.
La pantalla mostrará el mensaje Operación completada y el TPV imprimirá el ticket de la transacción.
Esta primera copia del ticket es para la estación y normalmente se solicita que la firme el cliente. A continuación, el terminal le pedirá que imprima una segunda copia para el cliente. Para ello, solo tiene que pulsar el botón verde para imprimir o el botón rojo para no hacerlo.


## Limpieza de preautorizaciones pendientes
Si por alguna razón se han realizado una o más preautorizaciones y no se han efectuado los correspondientes envíos, será necesario liberar el saldo de estas pre autorizaciones para normalizar el saldo de la cuenta.

Inicie la cancelación de la preautorización seleccionando en el menú del panel táctil la opción BORRAR PREAUTORIZACIÓN PENDIENTE.

El TPV solicitará que se presente la identificación asociada a la preautorización que se va a cancelar.

La identificación asignada al vehículo/conductor debe presentarse ahora a través del terminal.

Tras leer la identificación, el terminal muestra Procesando... mientras se comunica con los sistemas centrales para cancelar la pre autorización.

Cuando el servidor haya respondido confirmando la cancelación de la preautorización, la pantalla mostrará un mensaje de confirmación. El saldo de la preautorización ya está disponible para su uso de nuevo.

## Venta
En algunas circunstancias, puede darse el caso de que la venta ya se haya realizado y el envío se haya completado sin seguir el flujo normal de pre autorización y confirmación. Es importante tener en cuenta que, al procesar una venta, el sistema aplicará las mismas restricciones que se habrían aplicado en una preautorización; por lo tanto, si se intenta introducir una venta por un importe o volumen que no esté autorizado para ese identificador en ese momento, la venta será rechazada. Si esto ocurre, será necesario ponerse en contacto con el servicio de asistencia para determinar cómo proceder con la venta.

Inicie la venta seleccionando en el menú del panel táctil la opción VENTA.
El TPV solicitará que se presente la identificación asociada a la venta para ser registrada.
Tras leer la identificación, el terminal muestra Procesando... mientras se comunica con los sistemas centrales para notificar la venta.
Si la transacción no está autorizada, el sistema responderá con un mensaje de error y, tras seleccionar Aceptar, el terminal imprimirá el ticket.
Si los datos introducidos son correctos, la operación se confirmará en el servidor. La pantalla mostrará el mensaje OPERACIÓN COMPLETADA y el TPV imprimirá el ticket de la transacción.
Si la transacción es autorizada, el sistema responderá con un mensaje de confirmación como el del ejemplo e imprimirá un ticket de autorización.


## Consulta de saldo
Esta operación indica el importe máximo que se puede despachar en la siguiente transacción para una identificación específica. Realice esta consulta cuando se desconozcan los límites del vehículo en cuestión para evitar realizar múltiples intentos de preautorización que puedan ser denegados. Si el saldo indicado no se corresponde con la cantidad que el cliente cree tener, es necesario ponerse en contacto con el servicio de asistencia para determinar cómo proceder.

Inicie la venta seleccionando en el menú del panel táctil la opción CONSULTA DE SALDO.

El TPV le pedirá que presente la identificación asociada al vehículo/conductor cuyo saldo desea consultar.

Tras leer la identificación, el terminal muestra Procesando... mientras se comunica con los sistemas centrales para comprobar el saldo.

El sistema responde con el importe máximo disponible para el envío. Se muestra en pantalla y el TPV también imprime un ticket con dicha información.

## Reembolso
Si por algún motivo es necesario reembolsar una acumulación ya realizada, será necesario:

Iniciar la operación seleccionando en el menú del panel táctil la opción FIDELIDAD y, a continuación, REEMBOLSO DE ACUMULACIÓN.
El TPV solicitará ahora que se presente la identificación asociada a la transacción acumulada que se va a reembolsar.
A continuación, el sistema solicitará introducir el Código de autorización asociado a la transacción acumulada que se va a reembolsar.
Una vez introducidos todos los datos, el TPV mostrará el mensaje Procesando... mientras se comunica con el sistema central para procesar el reembolso de la acumulación.
Si la transacción se autoriza, el sistema responderá con un mensaje de confirmación y, a continuación, el terminal imprimirá el ticket de reembolso.


## Imprimir último recibo
Si por alguna razón es necesario volver a imprimir el último ticket emitido (normalmente cuando el papel de la impresora se ha atascado), esto se puede hacer desde este menú.

Inicie la operación seleccionando en el menú del panel táctil la opción IMPRIMIR ÚLTIMO TICKET.
El TPV imprimirá automáticamente una copia del último ticket emitido. No se puede volver a imprimir ningún otro ticket.


## Anular transacción
Si se produce un error al procesar una transacción en el sistema y el turno aún no se ha cerrado, esta opción permite anularlo y procesarlo correctamente.

Inicie la operación seleccionando en el menú del panel táctil la opción ANULAR TRANSACCIÓN.
El TPV solicitará el código de autorización de la transacción que se va a cancelar. El código de autorización se encuentra en el ticket. Pulse el botón verde para procesar la anulación de la transacción.
El TPV solicitará al sistema que anule la transacción. Durante ese proceso, se mostrará en pantalla Procesando….
Una vez completado correctamente el proceso de anulación, el TPV muestra un mensaje indicando e imprime un ticket de confirmación o uno de error si el proceso ha fallado.



## Menú de Tareas

## Activar la tarjeta regalo
Esta función permite a los usuarios activar su tarjeta regalo directamente desde el terminal sin tener que acceder al portal.

Inicie la operación seleccionando en el menú del panel táctil la opción ACTIVAR TARJETA REGALO.
Para poder continuar con la activación de la tarjeta regalo, se necesitan permisos del supervisor. 
Introduzca la contraseña del supervisor.
El terminal le pedirá ahora que presente la tarjeta regalo.
A continuación, el TPV solicitará al sistema que active la tarjeta. Durante ese proceso, aparecerá en pantalla el mensaje Procesando….
Una vez completado el proceso, el sistema activará la tarjeta regalo y el TPV mostrará un mensaje indicándolo.

## Cierre de lote
Este concepto permite agrupar un conjunto de transacciones para su posterior análisis y procesamiento. Por lo general, se recomienda realizar un cierre de lote al final de cada turno operativo en la gasolinera. De esta forma, se pueden conciliar fácilmente las transacciones que se pagaron con cualquiera de los medios de pago procesados por ATIONET.

Inicie la operación seleccionando en el menú del panel táctil la opción CIERRE POR LOTES.
Para proceder con el cierre de lote, se requieren permisos de supervisor. Introduzca la contraseña del supervisor.
El TPV solicitará al sistema central el cierre de un lote y su procesamiento. Durante ese proceso, se muestra en pantalla Procesando….
Cuando finaliza el proceso, el TPV muestra un mensaje que indica OPERACIÓN COMPLETADA e imprime el ticket de cierre.
El ticket de cierre incluye un número de identificación único generado por el servidor, el número de transacciones procesadas desde el último cierre, el total de ventas, las cancelaciones y el importe acumulado durante el periodo.

## Cambio de PIN

Esta opción permite realizar el cambio de PIN para un identificador en concreto

## Menú de Fidelidad

ATIOnet Loyalty mantiene una cuenta de fidelidad independiente para cada miembro del programa. El saldo de la cuenta se incrementa con las transacciones de acumulación y se reduce con los reembolsos de acumulación y las reglas de caducidad del programa. Las transacciones de ajuste y transferencia también pueden aumentar o reducir el saldo de la cuenta, dependiendo del signo de la operación.
Hay tres tipos de operaciones de fidelización dentro del TPV:

- Acumulación
- Reembolso de acumulación
- Consulta de saldo

En el punto de servicio (tienda, quiosco, tienda online, etc.), el proceso de acumulación suele estar relacionado con una operación de compra o pago, en la que los clientes obtienen puntos a cambio de su compra.

Un programa de fidelización determinado puede tener ninguna, una o varias reglas de acumulación. Las reglas de acumulación se procesan en tiempo real cuando se recibe una solicitud de transacción de acumulación e indican a ATIOnet Loyalty cuántos puntos deben añadirse a la cuenta del socio. No obstante, la captura también puede especificar una cantidad determinada de puntos que se deben otorgar a la cuenta, anulando las reglas del programa.

## Acumulación
Inicie la operación seleccionando en el menú del panel táctil la opción FIDELIDAD y, a continuación, ACUMULACIÓN.
El sistema le pedirá ahora que presente la identificación de fidelidad. Para la introducción manual u otros métodos de lectura (por ejemplo, un escáner), seleccione la opción Otros.
Seleccione el producto correspondiente con el que desea acumular puntos.
A continuación, el sistema le pedirá que introduzca la cantidad de la transacción.
Una vez introducidos todos los datos, el TPV mostrará el mensaje Procesando... mientras se comunica con el sistema central para procesar la acumulación.
Si la transacción se autoriza, el sistema responderá con un mensaje de confirmación y, a continuación, el terminal imprimirá un ticket de acumulación. El ticket indica la cantidad acumulada para ese identificador en esa transacción.

## Cierre de lote Fidelidad
Este concepto permite agrupar un conjunto de transacciones para su posterior análisis y procesamiento. Por lo general, se recomienda realizar un cierre de lote al final de cada turno operativo en la gasolinera. De esta forma, se pueden conciliar fácilmente las transacciones que se pagaron con cualquiera de los medios de pago procesados por ATIONET.

Inicie la operación seleccionando en el menú del panel táctil la opción CIERRE POR LOTES.
Para proceder con el cierre de lote, se requieren permisos de supervisor. Introduzca la contraseña del supervisor.
El TPV solicitará al sistema central el cierre de un lote y su procesamiento. Durante ese proceso, se muestra en pantalla Procesando….
Cuando finaliza el proceso, el TPV muestra un mensaje que indica OPERACIÓN COMPLETADA e imprime el ticket de cierre.
El ticket de cierre incluye un número de identificación único generado por el servidor, el número de transacciones procesadas desde el último cierre, el total de ventas, las cancelaciones y el importe acumulado durante el periodo.

## Menú de Consumer Card


## Recargar de Consumer Card
Si por alguna razón es necesario recargar una tarjeta de consumo directamente desde el terminal en lugar de desde el portal, esta opción le permitirá hacerlo.

Inicie la operación seleccionando en el menú del panel táctil la opción RECARGAR CC.
El terminal le pedirá que presente la tarjeta de consumidor que desea recargar.
A continuación, el terminal le pedirá que introduzca el importe que desea recargar en la tarjeta.
A continuación, el TPV solicitará al sistema que recargue la tarjeta con el importe introducido. Durante ese proceso, se mostrará en pantalla Procesando….
Una vez completada la operación, el sistema habrá añadido el importe a la Tarjeta de Consumidor y el TPV mostrará un mensaje indicándolo.


## Mantenimiento

## Cambiar contraseña de supervisor
Si por alguna razón es necesario modificar la contraseña de supervisor, se puede hacer desde este menú.

Inicie la operación seleccionando en el menú del panel táctil la opción CONTRASEÑA DE SUPERVISOR.
Introduzca la contraseña actual para realizar esta operación y, a continuación, pulse el botón verde para confirmar.
Introduzca la nueva contraseña y pulse el botón verde para continuar.
Una vez finalizado el proceso de cambio de contraseña, el TPV mostrará un mensaje de confirmación o un error si el proceso ha fallado.


## Crear o editar productos
Esta operación le permitirá configurar todos los combustibles disponibles para su dispensación. Desde aquí podrá configurar el nombre, el precio y el código del combustible. Es muy importante configurar el mismo código que en el sistema central, ya que es con este código con el que AtioNet reconoce el producto que se está dispensando.

Inicie la operación seleccionando en el menú del panel táctil la opción COMBUSTIBLES & SKUs.

Ahora dispondrá de dos listas una en la cual se podrán agregar los combustibles deseados y otra en la cual se podrán agregar los SKUs deseados. Para añadir uno nuevo, solo tiene que seleccionar el signo +.

El sistema le pedirá ahora que complete el nombre, el código y el precio del combustible. Una vez completado todo, seleccione la opción Crear.

Si por alguna razón es necesario modificar un combustible ya existente, solo tiene que seleccionar el combustible de la lista y el sistema le mostrará todos los detalles del mismo; a continuación, sólo tiene que editar los campos.

## Sincronización con Terminal Management

Comunicarse al correo de support@atioinc.com para recibir más detalles acerca del servicio de Terminal Management

## Enviar Logs

Para poder enviar Logs se debe haber hecho previamente la vinculación con ‘Terminal Management’

## Configuración
El menú de configuración permite modificar los parámetros del TPV. Estas operaciones no son habituales y requieren en todos los casos la contraseña del supervisor.

* Idioma
* Controladora
* ATIONET
* Módulos
* Configuración de Tickets 
* Otros

