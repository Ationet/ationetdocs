![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

# Contenido

- [Tarjeta de Regalo](#Tarjeta-de-Regalo)
  - [Autorizaciones Pendientes](#Autorizaciones-Pendientes)
  - [Contingencias](#Contingencias)
  - [Movimientos](#Movimientos)
  - [Programas](#Programas)
  - [Tarjetas](#Tarjetas)
  - [Tarjetas Solicitadas](#Tarjetas-Solicitadas)
  - [Transacciones](#Transacciones)
  - [Transacciones Rechazadas](#Transacciones-Rechazadas)


 ## Autorizaciones Pendientes

 En ATIONet las autorizaciones pendientes son aquellas operaciones que aún no han recibido la transacción de finalización, pero que han sido preautorizadas. La información que se ve en esta vista son los despachos que están actualmente en curso.

INSERTAR IMAGEN 
 
Tenga en cuenta que en el momento de la pre-autorización, ATIONet congeló el importe de la autorización de la tarjeta asociada. Esta vista presenta todos los campos necesarios para identificar la transacción y la tarjeta. Si necesita ver más detalles, al hacer clic en el código de autorización accederá a la vista de detalles de la transacción.

INSERTAR IMAGEN

 <br/>
 
 ## Contingencias
 
En ATIONet una contingencia es una operación introducida manualmente. En esta sección puede consultar y crear contingencias. Tenga en cuenta que las contingencias son transacciones sin autorización previa.

INSERTAR IMAGEN

Para crear una contingencia, haga click en el botón **Nuevo**.

INSERTAR IMAGEN

Los campos a completar son los siguientes:

* **Motivo:** Introduzca el motivo por el cual se está realizando la contingencia.
* **Fecha:** Introduzca la fecha de la contingencia.
* **Hora:** Introduzca la hora de la contingencia.
* **Código de autorización:** Al introducir el código de autorización en la contingencia, se podrán cargar los datos de la misma.
* **Programa:** Introduzca el programa asociado a la contingencia
* **Tarjeta:** Introduzca la tarjeta asociada a la contingencia
* **Sitio:** Seleccione el sitio asociado a la contingencia.
* **Terminal/Controlador:** Seleccione el terminal/controlador asociado a la contingencia.
* **Combustible:** Seleccione el combustible asociado a la contingencia.
* **Volumen Despachado:** Introduzca el volumen asociado a la contingencia.
* **Precio Unitario:** Introduzca el precio unitario asociado a la contingencia.
* **Monto Despachado:** Introduzca el monto asociado a la contingencia.
* **Turno:** Introduzca el turno asociado a la contingencia.
* **Surtidor:** Introduzca la bomba asociada a la contingencia.
* **Odómetro:** Introduzca el odómetro del vehículo asociado a la contingencia.
* **Horas de Motor:** Introduzca las horas de motor del vehículo asociado a la contingencia.
* **Id Conductor:** Introduzca el identificador del conductor asociado a la contingencia.
* **Id Vehículo:** Introduzca el identificador del vehículo asociado a la contingencia.
* **Código de Encargado:** Introduzca el encargado asociado a la contingencia.
* **Misceláneos:** Introduzca el misceláneos del vehículo asociados a la contingencia.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

<br/>

 ## Movimientos

La sección de Movimientos se pueden visualizar todas las interacciones relacionadas al saldo de las tarjetas Para facilitar las consultas, hay un panel de filtros disponible. 

iNSERTAR IMAGEN

 <br/>
 
 ## Programas

 Dentro de esta sección puede consultar, editar o crear programas de las tarjetas de regalos

INSERTAR IMAGEN
 
Para crear un programa, haga clic en el botón **Nuevo**.

Los campos a completar son los siguientes:
* **Nombre:** Introduzca el nombre deseado para el programa
* **Descripción:** Introduzca la descripción del programa.
* **Rango del BIN:** Introduzca el rango del BIN asociado al programa.
* **Moneda:** Introduzca la moneda correspondiente al programa.
* **Activo Tarjetas:** Habilitando esta opción las tarjetas creadas con este programa serán activadas tras su creación.
* **Duración de Tarjetas:** Introduzca el periodo de duración para las tarjetas creadas con este programa.
* **Validar Sitios:** Habilitando esta opción, el programa solo operara en los sitios configurados
* **Uso único:** Activar esta función, hará que las tarjetas solo puedan ser utilizadas una sola vez, independiente mente del saldo restante. 
* **Valida fecha de expiración:** Habilitar esta opción permite configurar una fecha de expiración en las tarjetas que se validará para operar. Utilizar la fecha de creación en la fecha de vencimiento de las tarjetas: Al habilitar esta función, cuando los identificadores sean activados, la fecha de creación se utilizará para generar la fecha de vencimiento. En caso contrario, se utilizará su fecha de activación. 

Luego, se pueden configurar los siguientes apartados:

* **Valor:** En este apartado se puede configurar el valor de las tarjetas

INSERTAR IMAGEN

* **Combustibles:** En este apartado se pueden configurar con que combustibles podrán operar las tarjetas relacionadas a este programa

INSERTAR IMAGEN

* **Sitios:** En este apartado se pueden configurar los sitios y los combustibles con los que se operara en los sitios correspondientes

INSERTAR IMAGEN

* **Descuentos:** En este apartado se pueden configurar los descuentos

INSERTAR IMAGEN

* **Modelos de Identificador:** En este apartado se pueden configurar las características de la tarjeta como identificador

INSERTAR IMAGEN

* **Regla:** En este apartado se pueden configurar las reglas correspondientes a este programa

INSERTAR IMAGEN

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.


 <br/>
 
 ## Tarjetas

En este apartado se pueden visualizar las tarjetas creadas, así como se dispone de la opción para **habilitar/deshabilitar** tarjetas y llegado el caso para marcarlas como extraviadas.

INSERTAR IMAGEN

A su vez en la opción **“Acciones de Lote”**, se pueden Activar o Desactivar múltiples tarjetas simplemente seleccionando las tarjetas mediante la casilla de la izquierda.
Finalmente, en el botón de **“Actualizar”** se puede descargar un template desde el cual se puede realizar una actualización masiva de tarjetas, donde a diferencia de **“Acciones de Lote”**, esta no se ve limitada por el limite de 50 resultados de Ationet.

INSERTAR IMAGEN


 <br/>
 
 ## Tarjetas Solicitadas

 En este apartado se pueden visualizar los procesos de tarjetas solicitadas. Los mismos se encuentran ordenamos por numero de orden de manera predeterminada, pero al interactuar con el título de columna **“Orden de solicitud”** o **“Fecha de pedido”** los resultados se reorganizaran de menor a mayor dependiendo de con que título se haya interactuado.

INSERTAR IMAGEN

Para crear una nueva solicitud, interactúe con el botón **“Nueva solicitud”**. Tas seleccionar el programa asociado a dichas tarjetas y la cantidad de tarjetas deseada, haga click en el botón **“Crear”** y el mismo entrara en proceso.

INSERTAR IMAGEN

 <br/>
 
 ## Transacciones

La vista de transacciones es una de las más importantes en ATIONet. En esta vista puede ver todas las transacciones exitosas.

El panel de filtro tiene todos estos campos disponibles:

INSERTAR IMAGEN

* **Código de Autorización:** Introduzca el código de autorización asociado a la transacción.
* **Programa:** Seleccione el programa de flota asociado a la transacción.
* **Tarjeta:** Introduzca la tarjeta correspondiente a la transacción 
* **Sitio:** Seleccione el sitio asociado a la transacción.
* **Terminal/Controlador:** Seleccione la terminal asociada a la transacción.
* **Tipo de Fecha:** Seleccione el tipo de fecha asociado a la transacción (Controlador, Host, Suscripción o Sitio).
* **Tipo de Intervalo temporal:** Seleccione el tipo de intervalo temporal de la transacción (este puede ser actual, fijo o previo).
* **Fecha Desde/Hasta:** Introduzca las fechas de inicio y finalización asociadas a la transacción.
* **Hora Desde/Hasta:** Introduzca las horas de inicio y finalización asociadas a la transacción.
Una vez que haya filtrado, haga clic en Búsqueda y se listarán las transacciones que cumplen con el filtro.

Si quiere ver el detalle de la transacción, presione sobre el **Código de Autorización** y esto le llevará a una vista detallada de la transacción.

INSERTAR IMAGEN

 <br/>
 
 ## Transacciones Rechazadas

Las Transacciones Rechazadas son aquellas que lograron pasar las autenticaciones duras de ATIONET, pero fueron rechazadas por otras validaciones como una regla insatisfecha o una validación de saldo

INSERTAR IMAGEN


 <br/>

 [Volver al inicio](#contenido) 	:arrow_up:

