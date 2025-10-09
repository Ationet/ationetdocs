![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

# Contenido

- [Consumer Card](#Consumer-Card)
  - [Autorizaciones Pendientes](#Autorizaciones-Pendientes)
  - [Contingencias](#Contingencias)
  - [Documentos de Cargos](#Documentos-de-Cargos)
  - [Documentos de Liquidaciones](#Documentos-de-Liquidaciones)
  - [Errores](#Errores)
  - [Estados de Cuenta](#Estados-de-Cuenta)
  - [Items Liquidados](#Items-Liquidados)
  - [Movimientos](#Movimientos)
  - [Procesos de Liquidación](#Procesos-de-Liquidación)
  - [Programas](#Programas)
  - [Recargas](#Recargas)
  - [Tarjetas](#Tarjetas)
  - [Tarjetas Solicitadas](#Tarjetas-Solicitadas)
  - [Transacciones](#Transacciones)
  - [Transacciones Rechazadas](#Transacciones-Rechazadas)
 
## Autorizaciones Pendientes

En ATIONet las autorizaciones pendientes son aquellas operaciones que aún no han recibido la transacción de finalización, pero que han sido preautorizadas. 
La información que se ve en esta vista son los despachos que están actualmente en curso. Si por alguna razón hay preautorizaciones antiguas, es probable que el TPV no haya enviado la transacción de finalización o la transacción de cancelación si el despacho no se ha completado.
 
Tenga en cuenta que en el momento de la preautorización, ATIONet congeló el importe de la autorización de la cuenta corriente para la subcuenta asociada. Esta vista presenta todos los campos necesarios para identificar la transacción y la subcuenta. 

Si necesita ver más detalles, al hacer clic en el **código de autorización** accederá a la vista de detalles de la transacción.

-Insertar Imagen

Si aparecen transacciones pendientes antiguas y está seguro de que no se trata de un envío en curso, puede cancelarlas y devolver el saldo a la cuenta corriente. 
Para ello existen 2 formas: De forma individual, pulsando el icono **X** a la derecha, o de forma masiva, seleccionando las transacciones, desplegando el menú Acciones en Lote y seleccionando Cancelar. 
Esto cancelará las transacciones y devolverá el saldo reservado a cada una de las cuentas corrientes. (para más detalles sobre el flujo de transacciones consulte este documento)

</br>

## Contingencias

En ATIONet una contingencia es una operación introducida manualmente. En esta sección puede consultar y crear contingencias. Tenga en cuenta que las contingencias son transacciones sin autorización previa.

IMAGEN

Para crear una contingencia, haga click en el botón **Nuevo.

IMAGEN

*	**Motivo:** Introduzca el motivo por el cual se está realizando la contingencia.
*	**Fecha:** Introduzca la fecha de la contingencia.
*	**Hora:** Introduzca la hora de la contingencia.
*	**Programa:** Introduzca el programa asociado a la tarjeta correspondiente
*	**Tarjeta:** Introduzca la tarjeta correspodiente a la contingencia
*	**Sitio:** Seleccione el sitio asociado a la contingencia.
*	**Terminal/Controlador:** Seleccione el terminal/controlador asociado a la contingencia.
*	**Combustible:** Seleccione el combustible asociado a la contingencia.
*	**Volumen Despachado:** Introduzca el volumen asociado a la contingencia.
*	**Precio Unitario:** Introduzca el precio unitario asociado a la contingencia.
*	**Monto Despachado:** Introduzca el monto asociado a la contingencia.
*	**Turno:** Introduzca el turno asociado a la contingencia.
*	**Surtidor:** Introduzca la bomba asociada a la contingencia.
*	**Odómetro:** Introduzca el odómetro del vehículo asociado a la contingencia.
*	**Horas de Motor:** Introduzca las horas de motor del vehículo asociado a la contingencia.
*	**Id Conductor:** Introduzca el identificador del conductor asociado a la contingencia.
*	**Id Vehículo:** Introduzca el identificador del vehículo asociado a la contingencia.
*	**Código de encargado:** Introduzca el codigo de encargado asociado a la contingencia.
*	**Misceláneos:** Introduzca el misceláneos del vehículo asociados a la contingencia.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

</br>

## Documentos de Cargos

En este apartado se pueden visualizar el resumen de los conceptos aplicados.
Al hacer click sobre el **Numero**, se podrá visualizar el detalle de cuales conceptos se aplicaron, así como el número de transacciones a las cuales se aplicaron dicho concepto.

INSERTAR IMAGEN

Para más detalle acerca de su configuración dirigirse al apartado [#Programas](#Programas)

</br>

## Documentos de Liquidaciones

En esta sección se pueden ver todos los estados de registro de los documentos de liquidación solicitados. 
Los estados posibles son: **Pendiente**, **Procesando**, **Finalizado** o **Finalizado con errores**.

INSERTAR IMAGEN

</br>

## Errores

En este apartado se pueden visualizar errores resultado de los procesos de liquidación terminados en errores

INSERTAR IMAGEN

## Estados de Cuenta

En esta sección podrá ver y descargar los estados de cuenta de su Network. También puede generar los estados de cuenta en **.PDF** uno a uno, o dentro de la "Acción en Lote" generando un paquete.
A su vez, al interactuar con el **Numero de Liquidación**, se podrán ver los detalles del estado de cuenta correspondiente.

INSERTAR IMAGEN

</br>

## Items Liquidados

En esta sección puede ver los conceptos aplicados para cada estado de cuenta.
En el apartado superior se encuentra un sistema de filtros el cual puede filtrar por el código de proceso de liquidación, así como por el numero de la liquidación, el cliente y fecha/hora.

Al interactuar con, la columna de fecha, se puede reordenar la lista de ítems liquidados por fecha

INSERTAR IMAGEN

</br>

## Movimientos

En la sección de **Movimientos** se pueden visualizar todas las interacciones relacionadas al saldo de las tarjetas
Para facilitar las consultas, hay un panel de filtros disponible:

INSERTAR IMAGEN

Para registrar un nuevo movimiento presione el boton **Nuevo**, para luego priorizar la siguiente informacion:

* **Tipo:** Seleccione el tipo de movieminto que desea realizar, el mismo puede ser desde una transaferencia de fondos entre dos tarjetas o el retiro de fondos para una subcuenta.
    * **En caso de seleccionar *"Transferencia de fondos entre tarjetas"***:
    
  *  INSERTAR IMAGEN
    
        - **Descripcion:** Ingrese una descripcion para el movimiento en concreto.
        - **Cliente:** Ingrese el cliente a quien corresponda el movimiento
        - **Tarjeta de Origen:** Ingrese la tarjeta desde la cual se extraeran los fondos
        - **Tarjeta de Destino:** Ingrese la tarjeta a la cual ingresaran los fondos enviados
        - **Monto:** Ingrese el monto deseado para la operacion
    * **En caso de seleccionar *"Retiro de fondos de subcuenta"***:

  *  INSERTAR IMAGEN

        - **Programa:** Ingrese el programa correspondiente de la tarjeta 
        - **Tarjeta:** Ingrese la tarjeta desde la cual se extraeran los fondos
        - **Monto:** Ingrese el monto deseado para la operacion

INSERTAR IMAGEN

Una vez finalizada la configuracion de dicho movimiento, presione **Crear**.

</br>

## Procesos de Liquidación

En esta sección puede ejecutar manualmente un proceso de facturación o ver el estado de todos los procesos de facturación. Los posibles estados de los procesos son: **Pendiente**, **Confirmado**, **Error** o **Confirmado con errores**.

INSERTAR IMAGEN

Adicionalmente, en la columna de detalles, se puede visualizar 4 opciones las cuales permiten facilitar el acceso a los apartados relacionados con este proceso.
Desde Izquierda a Derecha, los procesos son los siguientes:

* **Liquidaciones**: Al interactuar con esta opción, seremos redireccionados al apartado de “Documentos de Cargo” donde automáticamente se habrá aplicado el filtro de “Procesos”, resaltando así los resultados relacionados con el proceso de liquidación 

* **ítems Liquidados**: Al interactuar con esta opción, seremos redireccionados al apartado de “ítems liquidados” donde automáticamente se habrá aplicado el filtro de “Procesos”, resaltando así los resultados relacionados con el proceso de liquidación

* **Estados de cuenta**: Al interactuar con esta opción, seremos redireccionados al apartado de “Estados de cuenta” donde automáticamente se habrá aplicado el filtro de “Procesos”, resaltando así los resultados relacionados con el proceso de liquidación

* **Error**: Al interactuar con esta opción, seremos redireccionados al apartado de “Errores”.

</br>

## Programas

En este apartado, se puede visualizar, crear y editar los programas de consumer card.

INSERTAR IMAGEN

Para crear un nuevo programa presione el botón **NUEVO**

INSERTAR IMAGEN

Luego deberá completar con la siguiente información:

* **Nombre:** Ingrese el nombre deseado para el programa
* **Descripción:** Ingrese una descripción acerca del programa
* **Rango BIN:** Ingrese un rango BIN cuya disponibilidad es de 7 caracteres Alpha numéricos 
* **Fecha Inicio:** Ingrese la fecha de inicio del programa
* **Duración:** Ingrese la duración deseada del programa
* **Validar Sitios:** Habilitando esta opción, el programa solo operara en los sitios configurados
* **Descuento Requiere Registro:** Al activar esta check box, solo los usuarios finales los cuales están registrados en el Portal de Consumer Card podrán hacer uso de los descuentos configurados en el programa 
* **Validar fecha de expiración:** Habilitando esta opción, se podrá configurar una fecha de expiración para las tarjetas creadas con este programa
* **Nombre de Contacto:** Ingrese un nombre de contacto para el programa
* **Correo de Contacto:** Ingrese el correo del contacto del programa
* **Lista de Precios de Distribución:** Seleccione la lista de precios de distribución la cual será aplicada para el programa
* **Moneda:** Seleccione la moneda con la cual operaran las tarjetas de dicho programa.

Luego, se pueden configurar los siguientes apartados:

* **Combustibles:** En este apartado se pueden configurar con que combustibles podrán operar las tarjetas relacionadas a este programa

INSERTAR IMAGEN

* **Sitios:** En este apartado se pueden configurar los sitios y los combustibles con los que se operara en los sitios correspondientes

INSERTAR IMAGEN

* **Descuentos:** En este apartado se pueden configurar los descuentos 

INSERTAR IMAGEN

* **Liquidaciones:** En este apartado se pueden configurar la periodicidad de las liquidaciones para las tarjetas asociadas a este programa

INSERTAR IMAGEN

* **Conceptos:** En este apartado se pueden configurar los conceptos aplicables a las tarjetas asociadas con este programa

INSERTAR IMAGEN

* **Modelos de Identificador:** En este apartado se pueden configurar las características de la tarjeta como identificador

INSERTAR IMAGEN

* **Regla:** En este apartado se pueden configurar las reglas correspondientes a este programa

INSERTAR IMAGEN

* **Comercio:** En este apartado se pueden configurar los comercios asociados al programa

INSERTAR IMAGEN

Una ver termine de configurar el programa a voluntad presione **Guardar**

## Recargas

En este apartado es donde se pueden visualizar las recargas realizadas a las respectivas tarjetas.

INSERTAR IMAGEN

Por su parte, para realizar una recarga deberemos interactuar con botón **NUEVO**
Una vez en esta vista, deberemos completar con la información solicitada:

INSERTAR IMAGEN

* **Programa:** Ingrese el programa al cual la tarjeta se encuentra asociada.
* **Tarjeta:** Ingrese el numero de la tarjeta a la cual desea recargar
* **Monto:** Ingrese el monto correspondiente a la recarga
* **Encargado:** Ingrese el encargado asociado a la tarjeta.

Para finalizar, presione **Crear** para de esta manera completar el proceso de recarga.


## Tarjetas

En este apartado se pueden visualizar las tarjetas creadas, así como se dispone de la opción para editarlas y **habilitar/deshabilitar** tarjetas.

INSERTAR IMAGEN

A su vez en la opción **“Tarjetas Masivas”**, se pueden crear múltiples tarjetas simplemente seleccionando el programa al cual estas pertenecerán y la cantidad deseada

INSERTAR IMAGEN

Para crear una nueva tarjeta, interactúe con el botón “Nuevo” donde se deberán completar los siguientes campos:

INSERTAR IMAGEN 

*	**Programa:** Introduzca el programa al cual se asociará la tarjeta
*	**Apellidos:** Introduzca los apellidos del titular de la tarjeta
*	**Nombre:** Introduzca el nombre del titular de la tarjeta
*	**Correo:** Introduzca el correo del titular de la tarjeta
*	**Fecha de Nacimiento:** Introduzca la fecha de nacimiento del titular de la tarjeta
*	**País:** Introduzca el país al cual se asociará al usuario de la tarjeta
*	**Estado:** Introduzca el estado al cual se asociará al usuario de la tarjeta
*	**Ciudad:** Introduzca la ciudad al cual se asociará al usuario de la tarjeta
*	**Cod. Postal:** Introduzca el código postal correspondiente con el usuario de la tarjeta
*	**Calle:** Introduzca la calle principal asociada al usuario de la tarjeta
*	**Calle 2:** Introduzca la calle secundaria asociada al usuario de la tarjeta
*	**Teléfono 1:** Introduzca el teléfono principal asociada al usuario de la tarjeta
* **Teléfono 2:** Introduzca el teléfono secundario asociada al usuario de la tarjeta

</br>

## Tarjetas Solicitadas

En este apartado se pueden visualizar los procesos de tarjetas solicitadas. Los mismos se encuentran ordenamos por numero de orden de manera predeterminada, pero al interactuar con el título de columna **“Orden de solicitud”** o **“Fecha de pedido”** los resultados se reorganizaran de menor a mayor dependiendo de con que título se haya interactuado.

INSERTAR IMAGEN

Para crear una nueva solicitud, interactúe con el botón **“Nueva solicitud”**.
Tas seleccionar el programa asociado a dichas tarjetas y la cantidad de tarjetas deseada, haga click en el botón **“Crear”** y el mismo entrara en proceso.

INSERTAR IMAGEN 

</br>

## Transacciones

En esta vista se pueden visualizar todas las transacciones correspondientes a esta sección.

El panel de filtro tiene todos estos campos disponibles:

INSERTAR IMAGEN

*	**Código de Autorización:** Introduzca el código de autorización asociado a la transacción.
*	**Cliente:** Introduzca nombre del cliente asociado a la transacción
*	**Programa:** Seleccione el programa de consumer card asociado a la transacción.
*	**Sitio:** Seleccione el sitio asociado a la transacción.
*	**Terminal / Controlador:** Seleccione la terminal asociada a la transacción.
*	**Fecha desde/hasta:** Introduzca las fechas de inicio y finalización asociadas a la transacción.
*	**Hora desde/hasta:** Introduzca las horas de inicio y finalización asociadas a la transacción.

Una vez que haya filtrado, haga clic en **Búsqueda** y se listarán las transacciones que cumplen con el filtro.

INSERTAR IMAGEN

Si quiere ver el detalle de la transacción, presione sobre el **Código de Autorización** y esto le llevará a una vista detallada de la transacción

INSERTAR IMAGEN

</br>

## Transacciones Rechazadas

Las Transacciones Rechazadas son aquellas que lograron pasar las autenticaciones duras de ATIONET, pero fueron rechazadas por otras validaciones como una regla insatisfecha o una validación de saldo. 
En las columnas **Volumen Despachado**, **Precio unitario Despachado**, **Monto Despachado**, **Precio unitario de Contrato**, **Monto de Contrato** puede ver con que moneda fue realizada la transacción rechazada.

Insertar Imagen

</br>

[Volver al inicio](#contenido) 	:arrow_up:
