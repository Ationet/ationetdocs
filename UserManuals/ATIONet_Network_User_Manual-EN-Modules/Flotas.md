![image](https://github.com/user-attachments/assets/3474a3bf-1fdc-4f1a-89d2-492f90cd5620)![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

# Contenido

- [Flotas](#flotas)
	- [Alertas de Fraude](#alertas-de-fraude)
	- [Aprobaciones de Workflows de Flota](#aprobaciones-de-workflows-de-flota)
	- [Autorizaciones Pendientes](#autorizaciones-pendientes)
	- [Conceptos](#conceptos)
	- [Configuración de Alertas de Fraude](#configuración-de-alertas-de-fraude)
	- [Configuración de Fast Track](#configuración-de-fast-track)
	- [Contingencia](#contingencia)
	- [Contratos de Comercio](#contratos-de-comercio)
	- [Contrtos de Compañía](#contratos-de-compañía)
	- [Cuentas Corrientes de Comercio](#cuentas-corrientes-de-comercio)
	- [Cuentas Corrientes de Compañía](#cuentas-corrientes-de-compañía)
	- [Encargados](#encargados)
	- [Excepciones](#excepciones)
	- [Facturas](#facturas)
	- [Familias de Conceptos](#familias-de-conceptos)
	- [Fast Tracks](#fast-tracks)
	- [Identificadores Solicitados](#identificadores-solicitados)
	- [Planificador de Identificadores](#planificador-de-identificadores)
	- [Programas](#programas)
	- [Reglas](#reglas)
	- [Sobregiro](#sobregiro)
	- [Tarjeta de Regalo](#tarjeta-de-regalo)
	- [Tarjetas de Regalo Solicitadas](#tarjetas-de-regalo-solicitadas)
	- [Tipo de Comprobante](#tipo-de-comprobante)
	- [Transacciones](#transacciones)
	- [Transacciones Desconocidas](#transacciones-desconocidas)
	- [Transacciones Despachadas](#transacciones-despachadas)
	- [Transacciones ERP](#transacciones-ERP)
	- [Transacciones por Conductor](#transacciones-por-conductor)
	- [Transacciones por Flota](#transacciones-por-flota)
	- [Transacciones por Sitio](#transacciones-por-sitio)
	- [Transacciones por Vehículo](#transacciones-por-vehículo)
	- [Transacciones por Rechazadas](#transacciones-rechazadas)
	- [Transacciones Sin Control](#transacciones-sin-control)
	- [Vales](#Vales)
	- [Vales - Administración](#Vales-_-Administración)

# Flotas
Dentro de este módulo se pueden gestionar los Contratos de Compañía y Comercios, los Conceptos, las Contingencias y las Transacciones entre otras cosas.

## Alertas de Fraude
Dentro de esta sección puede ver una lista de todos los fraudes realizados por la Network. Para configurar cómo/cuándo alertar de los fraudes, vaya a [Configuración de Alertas de Fraude](#configuración-de-alertas-de-fraude).

![Alertas de fraude](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Alertas%20de%20Fraude.PNG)

</br>

## Aprobaciones de Workflows de Flota

</br>

## Autorizaciones Pendientes
En ATIONet las autorizaciones pendientes son aquellas operaciones que aún no han recibido la transacción de finalización, pero que han sido preautorizadas. La información que se ve en esta vista son los despachos que están actualmente en curso. Si por alguna razón hay preautorizaciones antiguas, es probable que el TPV no haya enviado la transacción de finalización o la transacción de cancelación si el despacho no se ha completado.

Tenga en cuenta que en el momento de la preautorización, ATIONet congeló el importe de la autorización de la cuenta corriente para la subcuenta asociada. Esta vista presenta todos los campos necesarios para identificar la transacción y la subcuenta. Si necesita ver más detalles, al hacer clic en el código de autorización accederá a la vista de detalles de la transacción.

![Autorización pendiente](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Autorizaciones%20Pendientes.PNG)

Si aparecen transacciones pendientes antiguas y está seguro de que no se trata de un envío en curso, puede cancelarlas y devolver el saldo a la cuenta corriente.
Para ello hay 2 formas: de forma individual, pulsando el icono **X** a la derecha, o de forma masiva, seleccionando las transacciones, desplegando el menú **Acciones en Lote** y seleccionando **Cancelar**. Esto cancelará las transacciones y devolverá el saldo reservado a cada una de las cuentas corrientes. (para más detalles sobre el flujo de transacciones consulte este [documento](AN-Transaction_Flows-TechGuide.md))

</br>

## Conceptos
Los conceptos en ATIONet hacen referencia a los impuestos o comisiones que se pueden añadir a los contratos de compañía o del comercio. En esta sección puede consultar, crear y editar conceptos.

![Conceptos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Conceptos.PNG)

Para crear un concepto, haga clic en el botón **Nuevo**.

![Conceptos Nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Conceptos%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Tipo de concepto:** Seleccione el tipo de concepto (Producto, Descuento o Comisión).
* **Código:** Introduzca el código único del concepto.
* **Nombre:** Introduzca el nombre del concepto.
* **Familia del concepto:** Seleccione la familia asociada al concepto.
* **Clase:** Seleccione la clase asociada al concepto.
* **Tipo:** Introduzca el tipo de concepto.
* **Modelo:** Introduzca el modelo del concepto.
* **Impuestos Incluidos:** Marque esta opción si los impuestos están incluidos en el importe de la operación.

En la sección del lista de precios rellene los siguientes campos:

* **Fecha de inicio:** Introduzca la fecha de inicio del concepto.
* **Moneda:** Introduzca la moneda del concepto.
* **Precio:** Introduzca el precio del concepto.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

## Configuración de Alertas de Fraude
En esta sección puede consultar y configurar cómo y cuándo se activan las alertas de fraude para la Network.

![Configuración de las alertas de fraude](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Configuraci%C3%B3n%20de%20Alertas%20de%20Fraude.PNG)

Para crear una configuración, haga clic en el botón **Nuevo**.

![Configuración de Alertas de Fraude Nueva](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Configuraci%C3%B3n%20de%20Alertas%20de%20Fraude%20Nuevo.PNG)

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

</br>

## Configuración de Fast Track
Un Fast Track en ATIONet es una forma de configurar una autorización de un solo uso para una cantidad específica a una subcuenta de flota ya existente. En esta sección puede configurar hasta 10 campos personalizados para Fast Tracks.

![Configuración de Fast Track](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Configuraci%C3%B3n%20de%20Fast%20Track.PNG)

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

</br>

## Contingencia
En ATIONet una contingencia es una operación introducida manualmente. En esta sección puede consultar y crear contingencias. Tenga en cuenta que las contingencias son transacciones sin autorización previa.

![Contingencia](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contingencias.PNG)

Para crear una contingencia, haga click en el botón **Nuevo**.

![Contingencias Nueva](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contingencias%20Nueva.PNG)

Los campos a completar son los siguientes:

* **Fecha:** Introduzca la fecha de la contingencia.
* **Hora:** Introduzca la hora de la contingencia.
* **Sitio:** Seleccione el sitio asociado a la contingencia.
* **Terminal/Controlador:** Seleccione el terminal/controlador asociado a la contingencia.
* **Cuenta primaria:** Seleccione la subcuenta primaria asociada a la contingencia.
* **Cuenta secundaria:** Seleccione la subcuenta secundaria asociada a la contingencia.
* **Combustible:** Seleccione el combustible asociado a la contingencia.
* **Moneda:** Introduzca la moneda de la contingencia.
* **Volumen Despachado:** Introduzca el volumen asociado a la contingencia.
* **Precio Unitario:** Introduzca el precio unitario asociado a la contingencia.
* **Monto Despachado:** Introduzca el monto asociado a la contingencia.
* **Turno:** Introduzca el turno asociado a la contingencia.
* **Surtidor:** Introduzca la bomba asociada a la contingencia.
* **Odómetro:** Introduzca el odómetro del vehículo asociado a la contingencia.
* **Horas de Motor:** Introduzca las horas de motor del vehículo asociado a la contingencia.
* **Id Conductor:** Introduzca el identificador del conductor asociado a la contingencia.
* **Id Vehículo:** Introduzca el identificador del vehículo asociado a la contingencia.
* **Encargado:** Introduzca el encargado asociado a la contingencia.
* **Lado de la Bomba:** Introduzca el lado de la bomba asociado a la contingencia.
* **Misceláneos:** Introduzca el misceláneos del vehículo asociados a la contingencia.
* **Número de Comprobante:** Introduzca el número de comprobante asociado a la contingencia.
* **Número de Orden de Compra:** Introduzca el número de orden de compra asociado a la contingencia.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

</br>

## Contratos de Comercio
En ATIONet el término comercio se refiere a la entidad propietaria de los sitios. En esta sección puede consultar, editar y crear contratos de comercio. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Contratos de Comerio](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Comercio.PNG)

Para crear un contrato de comercio, haga clic en el botón **Nuevo**.

![Contrato de Comercio Nuevo](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Comercio%20Nuevo.PNG)

Los campos a rellenar son los siguientes:

* **Código:** Introduzca el código del contrato.
* **Generado automáticamente:** Marque esta opción para que ATIONet genere automáticamente el código del contrato.
* **Descripción:** Introduzca la descripción del contrato.
* **Comercio:** Seleccione el comercio asociado al contrato.
* **Usuario del Comercio:** Introduzca el usuario de contacto del comercio.
* **Fecha de inicio:** Introduzca la fecha de inicio del contrato.
* **Duración:** Introduzca la duración del contrato.
* **Modo de Cuenta Corriente:** Seleccione la modalidad de cuenta corriente (Producto o Dinero).
* **Lista de Precios de Distribución:** Seleccione la lista de precios del contrato.

Después de rellenar estos campos, debe configurar las pestañas de Sitio, Combustible, Precios, Modficadores, Liquidaciones y Conceptos. 

1. **Sitios:** Seleccione los sitios asociados al contrato.

![Contrato Comercio Nuevo - Sitios](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Comercio%20Nuevo%20-%20Sitio.PNG)


2. **Combustibles:** Seleccione los combustibles asociados al contrato.

![Contrato Comercio Nuevo - Combustible](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Comercio%20Nuevo%20-%20Combustibles.PNG)


3. **Precios:** Seleccione los precios asociados al contrato.

![Contrato Comercio Nuevo - Precios](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Comercio%20Nuevo%20-%20Precios.PNG)


3. **Modificadores:** Seleccione los modificadores asociados al contrato.

![Contrato Comercio Nuevo - Modificadores](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Comercio%20Nuevo%20-%20Modificadores.PNG)


4. **Liquidaciones:** Seleccione los modificadores asociados al contrato.

![Contrato Comercio Nuevo - Liquidaciones](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Comercio%20Nuevo%20-%20Liquidaciones.PNG)


5. **Conceptos:** Seleccione los modificadores asociados al contrato.

![Contrato Comercio Nuevo - Conceptos](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Comercio%20Nuevo%20-%20Conceptos.PNG)

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

</br>

## Contratos de Compañía
En ATIONet el término compañía se refiere a la entidad que gestiona la flota. En esta sección podrá crear, editar o consultar todos los contratos de compañía. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Contratos de Compañía](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Compa%C3%B1%C3%ADa.PNG)

Para crear un contrato de empresa, haga clic en el botón **Nuevo**.

![Contratos de Compañía Nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Compa%C3%B1%C3%ADa%20Nuevo.PNG)

El primer paso para crear un nuevo contrato es completar la información general:

* **Activo:** Marque esta opción para activar/desactivar el contrato.
* **Código:** Introduzca el código asociado al contrato.
* **Compañía:** Seleccione la empresa asociada al contrato.
* **Monto de reactivación:** Introduzca el importe mínimo necesario para la reactivación automática (si el contrato está desactivado y se ha realizado un depósito por ese importe o superior).
* **Descripción:** Introduzca la descripción del contrato.
* **Fecha de inicio:** Introduzca la fecha de inicio del contrato.
* **Duración:** Introduzca la duración del contrato.
* **Modo de la cuenta corriente:** Seleccione la modalidad de cuenta corriente asociada al contrato (Producto o Dinero).
* **Moneda:** Seleccione la moneda asociada al contrato (esta opción sólo se activa si el **modo de cuenta corriente** es **Dinero**).
* **Modo:** Seleccione la modalidad del contrato (Crédito, Débito o Efectivo).
* **Límite:** Introduzca el límite de crédito asociado al contrato.
* **Modo de Saldo:** Seleccione la modalidad de saldo asociada al contrato:
	* ***Dispersión:*** El saldo se gestiona a nivel de subcuenta.
	* ***No dispersar:*** El saldo se gestiona a nivel de contrato.
	* ***Llenado Automático:*** No hay saldo.
* **Validar Sitios:** Marque esta opción para activar/desactivar la validación de sitios (el contrato sólo puede operar dentro de los sitios asignados).
* **Validar Combustibles:** Marque esta opción para activar/desactivar la validación de combustible (el contrato sólo puede operar con los combustibles asignados).
* **Utilizar Precios de Distribución:** Marque esta opción para activar/desactivar el uso de precios de distribución (el contrato sólo utilizará los precios de distribución cuando no haya precios configurados en el contrato).
* **Validar Programas:**
* **Valores Subsidiados:** Marcar esta opción para indicar que el contrato se genera con Subsidio.

Una vez completada la información general, tiene diferentes pestañas para configurar:

1. **Combustibles:** Seleccione los combustibles asociados al contrato.

![Contrato de Compañía Nuevo - Combustibles](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Compa%C3%B1%C3%ADa%20Nuevo%20-%20Combustible.PNG)

2. **Sitios:** Seleccione los sitios asociados al contrato.

![Contrato Compañía Nuevo - Sitios](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Compa%C3%B1%C3%ADa%20Nuevo%20-%20Sitios.PNG)

3. **Precios:** Configure los precios asociados al contrato.

![Contrato de Compañía Nuevo - Precios](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Compa%C3%B1%C3%ADa%20Nuevo%20-%20Precios.PNG)

* ***Combustible:*** Seleccionar el combustible asociado al precio.
* ***Valor:*** Introduzca el valor del precio.
* ***Sitio:*** Seleccione el sitio asociado al precio.
* ***Fecha Desde:*** Introduzca la fecha de inicio del precio.
* ***Hora Desde:*** Introduzca la hora de inicio del precio.
* ***Fecha Hasta:*** Introduzca la fecha de finalización del precio.
* ***Fecha Hasta:*** Introduzca la hora de finalización del precio.

4. **Modificadores:** Configurar los modificadores asociados al contrato.

![Contrato de Compañía Nuevo - Modificadores](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Compa%C3%B1%C3%ADa%20Nuevo%20-%20Modificadores.PNG)

* ***Descripción:*** Introduzca la descripción del modificador.
* ***Clase:*** Seleccionar la clase de modificador (Descuento o Recarga).
* ***Tipo:*** Seleccione el tipo de modificador (Porcentual, Fijo por Transacción o Fijo por Unidad).
* ***Valor:*** Introduzca el valor del modificador.
* ***Combustible:*** Seleccione el combustible asociado al modificador.
* ***Sitio:*** Seleccione el sitio asociado al modificador.
* ***Fecha Desde:*** Introduzca la fecha de inicio del modificador.
* ***Hora Desde:*** Introduzca la hora de inicio del modificador.
* ***Fecha Hasta:*** Introduzca la fecha de finalización del modificador.
* ***Fecha Hasta:*** Introduzca la hora de finalización del modificador.

5. **Liquidación:** Configurar el proceso de facturación asociado al contrato.

![Contrato de Compañía Nuevo - Liquidación](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Compa%C3%B1%C3%ADa%20Nuevo%20-%20Liquidaciones.PNG)

* ***Tipo de Proceso de Facturación:*** Seleccionar el tipo de proceso de liquidación asociado al contrato (EdiFactMx es sólo para el cliente de México)
* ***Activo:*** Marque esta opción para activar/desactivar el proceso de liquidación.
* ***Días de vencimiento:*** Ingrese la cantidad de días de vencimiento asociados al estado de cuenta.
* ***Periodicidad:*** Introduzca la frecuencia con la que se generan los extractos.
* ***Manual:*** Marque esta opción para activar/desactivar el proceso manual del proceso de liquidación.
* ***Cargos Deducen el Saldo de las Cuentas:*** Marque esta opción para habilitar/deshabilitar que ATIONet reste automáticamente los conceptos de los saldos de las cuentas.
* ***Documento de Cargos Separados:*** Marque esta opción para habilitar/deshabilitar que ATIONet separe cada concepto asociado al estado de cuenta.
* ***Emails de los Destinatarios:*** Introduzca las direcciones de correo electrónico que recibirán los estados de cuenta.
* ***ID del contribuyente:*** Introduzca el ID del contribuyente asociado a la estado de cuenta.
* ***Nombre:*** Introduzca el nombre asociado al estado de cuenta.
* ***Calle 1:*** Introduzca la calle principal asociada al estado de cuenta.
* ***Calle 2:*** Introduzca la calle secundaria asociada al estado de cuenta.
* ***Código Postal:*** Introduzca el código postal asociado al estado de cuenta.
* ***Ciudad:*** Introduzca la ciudad asociada al estado de cuenta.
* ***País:*** Introduzca el país asociado al estado de cuenta.
* ***Estado:*** Introduzca el estado asociado al estado de cuenta.

6. **Conceptos:** Seleccione el concepto asociado al contrato. Para más información sobre los conceptos acceda a [aquí]().

![Contratos de Compañía Nuevo - Conceptos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Compa%C3%B1%C3%ADa%20Nuevo%20-%20Conceptos.PNG)
	
7. **Documentos:** Suba cualquier documento asociado al contrato (por ejemplo: un pdf del propio contrato físico).

![Contratos de Compañía Nuevo - Documentos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Compa%C3%B1%C3%ADa%20Nuevo%20-%20Documentos.PNG)

8. **Bloqueos:** Configurar los bloqueos asociados al contrato

![Contratos de la Compañía Nuevo - Bloqueos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Compa%C3%B1%C3%ADa%20Nuevo%20-%20Bloqueos.PNG)

* ***Tipo:*** Seleccione **Fijo** para bloquear la operación en fechas concretas, o seleccione **Fijo** para bloquear la operación en días concretos de cada mes. 
* ***Fecha desde:*** Introduzca la fecha de inicio del bloqueo.
* ***Fecha Hasta:*** Introduzca la fecha de finalización del bloqueo.
* ***Día desde:*** Introduzca el día de inicio de cada mes para el bloqueo.
* ***Día Hasta:*** Introduzca el día final de cada mes para el bloqueo.

9. **Sobregiro:** Configure los sobregiros asociados al contrato.

![Contratos de la Compañía Nuevo - Sobregiro](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Compa%C3%B1%C3%ADa%20Nuevo%20-%20Sobregiro.PNG)

* ***Tipo:*** Seleccione el tipo de sobregiro (Porcentaje o Importe).
* ***Valor:*** Introduzca el valor asociado al sobregiro.
* ***Fecha Desde:*** Introduzca la fecha de inicio del sobregiro.
* ***Fecha Hasta:*** Introduzca la fecha de finalización del sobregiro.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

</br>

## Cuentas Corrientes de Comercio
La vista de cuentas corrientes de los comercios es donde se consultan los saldos y movimientos de todos los comercios.

Para facilitar las consultas se dispone de un panel de filtros y la primera opción del panel es el tipo de informe que se quiere ver (Lista de Contratos, Movimientos de Contratos, Lista de Sitios y Movimientos de Sitios).
En la columna Moneda de la grilla puede ver en que moneda se realiza cada movimiento. Sí se tienen configurada la funcionalidad de Multimoneda, puede ver las diferentes divisas en cada movimiento.

![Cuentas Corrientes de Comercio](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Cuentas%20Corrientes%20de%20Comercio.PNG)

</br>

## Cuentas Corrientes de Compañía
La sección de Cuentas Corrientes de Compañía es la vista del saldo disponible de las subcuentas y/o contratos, y también la vista de todos los movimientos de las subcuentas y/o contratos.
En la columna Moneda de la grilla puede ver en que moneda se realiza cada movimiento. Sí se tienen configurada la funcionalidad de Multimoneda, puede ver las diferentes divisas en cada movimiento.

Para facilitar las consultas, hay un panel de filtros disponible. La primera opción del panel de filtros es el tipo de informe:

![Cuentas Corrientes de la Compañía](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Cuentas%20Corrientes%20de%20Compa%C3%B1%C3%ADa.PNG)

1. **Lista de Contratos:** Esta opción lista todos los contratos con sus respectivos saldos, pero no da detalles de los movimientos.

![Cuentas Corrientes de Compañía - Lista de Contratos](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Cuentas%20Corrientes%20de%20Compa%C3%B1%C3%ADa%20-%20Lista%20de%20Contratos.PNG)

2. **Movimientos de Contratos:** Esta opción muestra todos los movimientos de los contratos.

![Cuentas Corrientes de Compañía - Movimientos de Contratos](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Cuentas%20Corrientes%20de%20Compa%C3%B1%C3%ADa%20-%20Movimientos%20de%20Contratos.PNG)

3. **Lista de Subcuentas:** Esta opción lista todas las subcuentas con sus respectivos saldos, pero no da detalles de los movimientos.

![Cuentas Corrientes de Compañía - Lista de Subcuentas](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Cuentas%20Corrientes%20de%20Compa%C3%B1%C3%ADa%20-%20Lista%20de%20Subcuentas.PNG)

4. **Movimientos de Subcuentas:** Esta vista lista todos los movimientos de las subcuentas.  

![Cuentas Corrientes de Compañía - Movimientos de Subcuentas](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Cuentas%20Corrientes%20de%20Compa%C3%B1%C3%ADa%20-%20Movimientos%20de%20Subcuentas.PNG)

5. **Recargas de Subcuentas:** Esta vista lista todass las recargas de las subcuentas.  

![Cuentas Corrientes de Compañía - Recargas de Subcuentas](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Cuentas%20Corrientes%20de%20Compa%C3%B1%C3%ADa%20-%20Recargas%20de%20Subcuentas.PNG)

## Encargados
En ATIONet el término encargado se refiere a la persona responsable de hacer el despacho, el que opera las bombas. En esta sección se pueden ver, crear y editar todos los encargados. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Encargados](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Encargados.PNG)

Para crear un encargado, haga clic en el botón **Nuevo**.

![Encargados Nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Encargados%20Nuevo.PNG)

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

</br>

## Excepciones
ATIONet separa las transacciones no autorizadas en 2 secciones: **Excepciones** y [Transacciones Rechazadas] (#transacciones-rechazadas). Las excepciones son aquellas transacciones que no pasaron las validaciones duras del sistema o las que se detectan como posibles fraudes.

![Excepciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Excepciones.PNG)

En esta vista, al principio se puede filtrar por el tipo de excepción. Los tipos de excepciones disponibles son los siguientes:

![Excepciones Filtros](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Excepciones%20Filtros.PNG)

Algunas transacciones permanecen en estado de **Revisión** en algunas situaciones, como cuando se envía más de lo autorizado (debido a un error del controlador o del TPV). En estos casos es necesario aprobar o rechazar la transacción utilizando uno de los dos iconos a la derecha de cada registro.

</br>

## Facturas

</br>

## Familias de Conceptos
Las familias de conceptos en ATIONet son una forma de agrupar varios conceptos. En esta sección puedes consultar, crear o editar conceptos de familias.

![Familias de Conceptos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Famlia%20de%20Conceptos.PNG)

Para crear una familia de conceptos, haz clic en el botón **Nuevo**.

![Familias de Conceptos Nueva](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Famlia%20de%20Conceptos%20Nuevo.PNG)

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

</br>

## Fast Tracks

</br>

## Identificadores Solicitados
En este apartado podrá consultar las identificaciones solicitadas por la compañía y solicitar la identificación de la flota y/o fidelidad. También puede realizar acciones como establecer las identificaciones como en producción o como entregadas.

También dispone de un panel para filtrar las identificaciones solicitadas y así facilitar la búsqueda.

![Identificadores solicitados](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Identificadores%20Solicitados.PNG)

</br>

En la vista detallada se podrá visualizar la dirección de entrega que se haya configurado para la compañía.
![Identificadores solicitados vista detallada](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Identificadores%20Solicitados%20-%20Vista%20detallada.PNG)

</br>

Para solicitar una identificación de flota, haga clic en el botón **Nueva solicitud** y seleccione **Solicitar identificadores de flota**. Al hacerlo, se abrirá un formulario.


![Identificadores solicitados - Nueva flota](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Identificadores%20Solicitados%20Nuevo.PNG)

* **Tipo:** Seleccione el tipo de identificadores (Tarjeta, TAG, Chipkey, Tarjeta ATIOnet, TAG ATIOnet, Código de barras y QR).
* **Modelo:** Seleccione el modelo de identificadores.
* **Compañía:** Seleccione la compañía asociada a los identificadores.
* **Contrato:** Seleccione el contrato de la compañía asociado a los identificadores.
* **Programa:** Seleccionar el programa asociado a los identificadores.
* **Cantidad:** Introduzca la cantidad de identificadores a solicitar.

Cuando haya terminado de rellenar los campos, presione el botón **Solicitar Identificadores**.

Para cambiar el estado de los identificadores solicitados, haga clic en el botón **Acción en Lote** y seleccione la opción **Poner en Producción** o **Poner como Entregado**. Puede hacer que **Todas** las solicitudes cambien el estado o sólo las **Seleccionadas**.

</br>

## Planificador de Identificadores

</br>

## Programas
Dentro de esta sección puede consultar, editar o crear programas de flota. Para cada Network ATIONet ya tiene un programa CLÁSICO creado por defecto. Un programa de flota en ATIONet permite a los identificadores ignorar algunos de sus comportamientos, como por ejemplo Modo de Balance, Soporte de Contingencia, Soporte Offline, etc.

![Programas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Programas.PNG)

Para crear un programa, haga clic en el botón **Nuevo**.

![Programas Nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Programas%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Descripción:** Introduzca la descripción del programa.
* **Rango del BIN:** Introduzca el rango del BIN asociado al programa.
* **Aplicación de los sitios contractuales:** Seleccione si la validación del sitio se aplica o no en el programa.
* **Modo de Balance:** Seleccione el modo de balance para el programa (Contrato, Disperso, No Disperso o Auto Llenado).
* **Soporte de Contingencias:** Seleccione si la creación de contingencias se aplica o no en el programa.
* **Soporte Offline:** Seleccione si el módulo offline se aplica o no en el programa.
* **Tipo:** Seleccione el tipo de programa (Flota o Vales).
* **Soporte de Productos Secos:** Marque esta opción si el programa soporta SKUs.
**Valida la Fecha de Caducidad:** Marque esta opción si el programa valida las fechas de caducidad de los identificadores.
* **Vencimiento de Identificadores:** Introduzca la duración de la identificación.

Una vez completada la información general, también puede configurar las reglas de solicitud y localización para el programa:

![Programas Nuevos - Reglas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Programas%20Nuevo%20Reglas.PNG)

Para más información sobre las reglas vaya [aquí](#reglas).

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

</br>

## Reglas
En ATIONet las reglas se refieren a los límites que pueden ser configurados por la compañía y asociados a diferentes entidades. Dentro de esta vista se pueden consultar, crear o editar reglas. Existen diferentes tipos de reglas: Cuota, Rango de Fechas, Ubicación, Combustible, Límite por Transacciones, DíasHora, Solicitud, Límite de Transacciones Secas y Límite de Cuotas Secas.

Tenga en cuenta que todas las reglas pueden ser **No Bloqueantes**, lo que significa que ATIONet no rechazará la transacción aunque se cumplan los parámetros.

![Reglas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Reglas.PNG)

1. **Cuota:** En esta regla puede limitar la cantidad de transacciones, el volumen y/o el dinero en una frecuencia específica.

![Reglas - Cuota](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Reglas%20-%20Cuota.PNG)

2. **Rango de fechas:** En esta regla puede limitar las transacciones que se harán en rangos de fecha y hora específicos.

![Reglas - Rango de fechas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Reglas%20-%20Rango%20de%20Fechas.PNG)

3. **Ubicación:** En esta regla puede limitar las transacciones que se realicen en sitios y zonas específicas.

![Reglas - Ubicación](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Reglas%20-%20Ubicaci%C3%B3n.PNG)

4. **Combustible:** En esta regla puede limitar las transacciones que se realicen para combustibles específicos y grupos de maestros de combustibles.

![Reglas - Combustible](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Reglas%20-%20Combustible.PNG)

5. **Límite por Transacciones:** En esta regla puede limitar el volumen de cada transacción y/o el dinero.

![Reglas - Límite por Transacciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Reglas%20-%20Limite%20por%20Transacci%C3%B3n.PNG)

6. **Días/Hora:** En esta regla puede limitar las transacciones a realizar en días y horas específicas de la semana.

![Reglas - Días/Hora](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Reglas%20-%20D%C3%ADaHora.PNG)

7. **Solicitud:** En esta regla se puede configurar la solicitud de información para las transacciones, como la identificación del conductor/vehículo, el PIN del conductor/vehículo, etc.

![Reglas - Solicitud](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Reglas%20-%20Solicitudes.PNG)

8. **Límite de Producto por Transacción:** En esta regla se puede limitar el dinero de las transacciones de cada SKU.

![Reglas - Límite de Producto por Transacción](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Reglas%20-%20Limite%20de%20Producto%20por%20Transacci%C3%B3n.PNG)

9. **Cuota por Producto:** En esta regla puede limitar el dinero de las transacciones en una frecuencia específica.

![Reglas - Cuota por Producto](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Reglas%20-%20Cuota%20por%20Producto.PNG)

Después de configurar cualquier tipo de regla, el último paso es asociar la regla a una entidad. Se pueden aplicar reglas a: Flotas, Vehículos, Conductores, Sitios y Combustibles.

![Reglas - Asociación](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Reglas%20-%20Aplicacion.PNG)

</br>

## Sobregiro
En esta sección puede consultar o crear sobregiros para los contratos de compañía. El sobregiro en ATIONet se refiere a una cantidad que las subcuentas pueden sobrepasar de sus saldos.

![Sobregiro](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Sobregiro.PNG)

Para crear un sobregiro, haga clic en el botón **Nuevo**.

![Sobregiro Nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Sobregiro%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Compañía:** Seleccione la compañía asociada al sobregiro.
* **Contrato:** Seleccione el contrato de la compañía asociado al sobregiro.
* **Fecha desde:** Introduzca la fecha de inicio del sobregiro.
* **Fecha hasta:** Introduzca la fecha de finalización del sobregiro.
* **Tipo:** Seleccione el tipo de sobregiro (Porcentaje o Importe).
* **Valor:** Introduzca el valor del sobregiro.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

</br>

## Tarjeta de Regalo

</br>

## Tarjetas de Regalo Solicitadas

</br>

## Tipo de Comprobante

</br>

## Transacciones
La vista de transacciones es una de las más importantes en ATIONet. En esta vista puede ver todas las transacciones exitosas.

El panel de filtro tiene todos estos campos disponibles:

![Trasacciones - Filtro](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Filtros.PNG)

* **Código de Autorización:** Introduzca el código de autorización asociado a la transacción.
* **Turno:** Introduzca el número de turno asociado a la transacción.
* **Vehículo:** Seleccione el vehículo asociado a la transacción.
* **Conductor:** Seleccione el conductor asociado a la transacción.
* **Comercio:** Seleccione el comercio asociado a la transacción.
* **Sitio:** Seleccione el sitio asociado a la transacción.
* **Terminal/Controlador:** Seleccione la terminal asociada a la transacción.
* **Combustible:** Seleccione el combustible asociado a la transacción.
* **Programa:** Seleccione el programa de flota asociado a la transacción.
* **Contrato:** Seleccione el contrato de la empresa asociado a la transacción.
* **Número de Comprobante:** Introduzca el número de comprobante asociado a la transacción.
* **Tipo de Fecha:** Seleccione el tipo de fecha asociado a la transacción (Controlador, Host, Suscripción o Sitio).
* **Fecha Desde/Hasta:** Introduzca las fechas de inicio y finalización asociadas a la transacción.
* **Hora Desde/Hasta:** Introduzca las horas de inicio y finalización asociadas a la transacción.
* **Modo:** Seleccione el modo de transacción (Contingencia, Fuera de línea o Estándar).
* **Mostrar Transacciones Completadas en Cero:** Marque esta opción para ver las transacciones en las que no se despachó combustible.
* **Valores Subsidiados:** Seleccione la opción correspondiente a la transacción (Si/No).

Una vez que haya filtrado, haga clic en ***Búsqueda*** y se listarán las transacciones que cumplen con el filtro.

![Transacciones](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones.PNG)

Si quiere ver el detalle de la transacción, presione sobre el **Código de Autorización** y esto le llevará a una vista detallada de la transacción.

![Transacciones Detalles](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Detalles.PNG)

Con la incorporación de Multimoneda, dentro de Detalles de Transacción encontrara tres nuevas secciones: Moneda del Sitio, Moneda de la Compañía y Moneda de Comercio, las cuales son configurables como se explica en el documento de [Multimoneda](https://github.com/nuchavez/ationetdocs/blob/master/Multicurrency-ES.MD). 

## Transacciones Desconocidas
Las transacciones desconocidas son aquellas que la Compañía dice desconocer.

En esta sección se pueden consultar las transacciones desconocidas, listadas por código, fecha, motivo, estado, número de transacción, compañía, sitio. También está el comentario de la compañía, del comercio y de la network.

![Transacciones desconocidas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Desconocidas.PNG)

## Transacciones Despachadas
En esta sección puede ver todas las transacciones que han sido dispensadas. Con la incorporación de la funcionalidad de Multimoneda, en la columna Monto despachado se podrá visualizar la moneda con que se realizó cada transacción. 

![Transacciones Despachadas](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Despachadas.PNG)

## Transacciones ERP

## Transacciones por Conductor
En esta vista puede ver las transacciones agrupadas por el conductor que las realizó. Los botones de la parte superior izquierda sirven para imprimir la tabla o crear un archivo Excel a partir de la misma, respectivamente.
Dentro de la grilla en la columna Moneda puede ver en que divisa se realiza cada transacción. En caso de tener habilitada la funcionalidad Multimoneda, en el listado de transacciones se indicarán las diferentes divisas de acuerdo a cada una de ellas.

![Transacciones por Conductor](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20por%20Conductor.PNG)

## Transacciones por Flota
En esta vista puede ver las transacciones agrupadas por la flota que las realizó. Los botones de la parte superior izquierda sirven para imprimir la tabla o crear un archivo Excel a partir de la misma, respectivamente.
Dentro de la grilla en la columna Moneda puede ver en que divisa se realiza cada transacción. En caso de tener habilitada la funcionalidad Multimoneda, en el listado de transacciones se indicarán las diferentes divisas de acuerdo a cada una de ellas.

![Transacciones por Flota](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20por%20Flota.PNG)

## Transacciones por Sitio
En esta vista se pueden ver las transacciones agrupadas por el sitio donde se realizaron. Los botones de la parte superior izquierda sirven para imprimir la tabla o crear un archivo Excel a partir de ella, respectivamente.
Dentro de la grilla en la columna Moneda puede ver en que divisa se realiza cada transacción. En caso de tener habilitada la funcionalidad Multimoneda, en el listado de transacciones se indicarán las diferentes divisas de acuerdo a cada una de ellas.

![Transacciones por Sitio](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20por%20Sitio.PNG)

## Transacciones por Vehículo
En esta vista puede ver las transacciones agrupadas por el vehículo que las realizó. Los botones de la parte superior izquierda sirven para imprimir la tabla o crear un archivo Excel a partir de la misma, respectivamente.
Dentro de la grilla en la columna Moneda puede ver en que divisa se realiza cada transacción. En caso de tener habilitada la funcionalidad Multimoneda, en el listado de transacciones se indicarán las diferentes divisas de acuerdo a cada una de ellas.

![Transacciones por Vehículo](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20por%20Veh%C3%ADculo.PNG)

## Transacciones Rechazadas
ATIONet separa las transacciones no autorizadas en 2 secciones: [Excepciones](#excepciones) y **Transacciones Rechazadas**.

Las Transacciones Rechazadas son aquellas que lograron pasar las autenticaciones duras de ATIONET, pero fueron rechazadas por otras validaciones como una regla insatisfecha o una validación de saldo.
En las columnas Volumen Despachado, Precio unitario Despachado, Monto Despachado, Precio unitario de Contrato, Monto de Contrato puede ver con que moneda fue realizada la transacción rechazada.

![Transacciones Rechazadas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Rechazadas.PNG)

En esta vista, al principio se puede filtrar por el tipo de rechazo. Los tipos de rechazo disponibles son los siguientes:

![Transacciones Rechazadas Filtros](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Rechazadas%20Filtros.PNG)

## Transacciones Sin Control
Las transacciones sin control son aquellas que se generan porque el controlador detecta una diferencia en los indicadores y envía una transacción por la diferencia. Estas transacciones no contienen datos sobre la identificación, ya que se generaron automáticamente y no se iniciaron con la presentación de un identificador. Al no tener un identificador asignado, no tienen impacto en ninguna cuenta corriente ni cuentan para el cálculo de las reglas.

![Transacciones sin control](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Sin%20Control.PNG)

</br>

## Vales

</br>

## Vales - Administración

</br>

[Volver al inicio](#contenido) 	:arrow_up:
