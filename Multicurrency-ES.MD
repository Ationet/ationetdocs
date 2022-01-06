![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|**Información del Documento**|.|
|--- |--- |
|**Archivo:**|Multicurrency-ES.MD|
|**Versión Doc:**|1.0|
|**Fecha Liberación:**|05, Ene 2022|
|**Autor:**|ATIONet LLC|


|**Bitácora de Cambios**|||
|--- |--- |--- |
|**Ver.**|**Fecha**|**Resumen de Cambios**|
|1.0|05/Ene/2022|- Version Inicial
<br>

# Contenido

- [Multimoneda](#multimoneda) 	
    - [Configuraciones](#configuraciones) 

<br>

# Multimoneda

### Objetivo
El propósito del documento es detallar cómo la funcionalidad de Multimoneda ayuda en la gestión diaria de combustible en ATIONET cuando se generan transacciones en diferentes monedas, buscando reducir procesos manuales que puedan realizar nuestros usuarios.

<br>

### Introducción
En los países o regiones en los cuales circulan varias monedas, la funcionalidad de multimoneda es estratégica e imprescindible. Proporciona la posibilidad de que sus clientes puedan abonar con distintas monedas de acuerdo al sitio o región donde se encuentren.

<br>

### Descripción
La funcionalidad de Multimoneda permite operar con diferentes divisas dentro del portal. Para poder utilizar esta funcionalidad es necesario realizar algunas configuraciones en la plataforma que permitirán realizar las conversiones requeridas en cada operación.

Intervienen 4 monedas:
- Moneda de operación: es la moneda de ocurrencia, en una transacción es la moneda configurada en el sitio, en un movimiento de cuenta corriente es la moneda elegida para el pago.
- Moneda de conversión: es la moneda pivot, utilizada para toda conversión desde la moneda de operación hacia cualquier otra moneda.
- Moneda de cuenta corriente: es la moneda en la que se administran los contratos, y por lo tanto la cuenta corriente.
- Moneda de conciliación: es la moneda utilizada para conciliar todas las cuentas corrientes, si la Network quisiera conciliar todos sus contratos. Si bien hoy se realizan estas conversiones, no se muestra este valor en ningún lado, en ningún reporte.

<br>


### Flujo de configuración inicial requerida
*En la sección Configuraciones del documento podrá encontrar el detalle de las configuraciones necesarias para habilitar la funcionalidad de Multimoneda.

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/flujomultimoneda.png)




### Vistas impactadas
A continuación, se detallan las vistas que se ven impactadas por la funcionalidad de Multimoneda:  
- Transacciones
- Movimientos de Cuenta Corriente
- Estado de Cuenta
- Configuración de Procesos de Liquidación
- Contrato de Comercio.
- Configuración de Red
- Sitio y Configuración

<br>


#### Vistas de transacciones
Se pueden identificar las monedas que interactúan en el circuito de autorización de una transacción como dato complementario en los campos que representan el valor monetario de la misma. 
Dentro de las vistas de transacciones se ven afectadas por la funcionalidad de multimoneda las siguientes:

- Transacciones
- Detalle de Transacciones
- Detalle de Excepciones
- Transacciones Despachadas
- Transacciones ERP
- Transacciones Rechazadas

<br>


##### Vista Transacciones

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Vista%20Transacciones.png)

<br>

##### Vista Detalle (Esta sección es igual en todas Transacciones y Excepciones)
![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Vista%20Detalle.png)

<br>

##### Vista Transacciones Despachadas
![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Vista%20Transacciones%20Despachadas.png)

<br>


##### Vista Transacciones ERP
![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Vista%20Transacciones%20ERP.png)

<br>


##### Vista Transacciones Rechazadas
![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Vista%20Transacciones%20Rechazadas.png)



<br>

### Vistas de transacciones agrupadas

Se pueden visualizar las monedas que interactúan en el circuito de autorización de una transacción como dato complementario en los campos que representan valor monetario de la misma. Las vistas en las que se ven reflejadas son las siguientes:



##### Vista Transacciones por conductor
![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Vista%20Transacciones%20por%20conductor.png)

<br>


##### Vista Transacciones por vehículo
![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Vista%20Transacciones%20por%20veh%C3%ADculo.png)

<br>

##### Vista Transacciones por flota
![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Vista%20Transacciones%20por%20flota.png)

<br>


##### Vista Transacciones por sitio
![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Vista%20Transacciones%20por%20sitio.png)

<br>



### Cotización en transacción
El motor de autorizaciones posee la lógica para considerar el cálculo de cotizaciones configuradas vigentes en los montos autorizados, y en la validación de disponible para transaccionar de los clientes, así como el impacto de los montos correspondientes en la moneda del contrato en la cuenta corriente del mismo. 

<br>

### Cotización en Cuenta Corriente
Permite realizar movimientos de Cuenta Corriente (depósitos) en Contratos de Compañía y/o Comercio y en subcuentas, en moneda distintas a las del contrato referido.

<br>

### Vista de Cuenta Corriente de Compañía
La columna Moneda se puede visualizar en la grilla de Cuenta corriente de Compañía, así como en la exportación a Excel de movimientos e impresión de los mismos. La moneda se visualizará siempre y cuando el contrato sea en importe.

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Vista%20de%20Cuenta%20Corriente%20de%20Compa%C3%B1%C3%ADa.png)

<br>

##### Reporte Excel de movimiento Cuenta corriente de Compañía

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Archivo%20Excel%20de%20movimiento%20Cuenta%20corriente%20de%20Compa%C3%B1%C3%ADa.png)

<br>

##### Nuevo movimiento de Cuenta Corriente de Compañía

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Nuevo%20movimiento%20de%20Cuenta%20Corriente%20de%20Compa%C3%B1%C3%ADa.png)

<br>


### Vista de Cuentas corrientes de Comercio
La columna Moneda se puede visualizar en la grilla de Cuentas corrientes de Comercio, así como en la exportación a Excel de movimientos. La moneda se visualizará siempre y cuando el contrato sea en importe.


##### Reporte Excel de movimiento Cuentas corrientes de Comercio

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Archivo%20Excel%20de%20movimiento%20Cuentas%20corrientes%20de%20Comercio.png)

<br>

##### Nuevo movimiento de Cuenta corriente de Comercio

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Nuevo%20movimiento%20de%20Cuenta%20corriente%20de%20Comercio.png)

<br>


### Valores en estados de cuenta
La funcionalidad de Multimoneda impacta en el proceso de generación de estados de cuenta lo que hace considerar los valores registrados de las transacciones basadas en las monedas involucradas para realizar los cálculos correspondientes y reflejarlos en el estado de cuenta.

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Valores%20en%20estados%20de%20cuenta.png)

<br>


### Vista Sitio y configuración
La configuración de moneda a nivel de Sitio es utilizada en el cálculo de conversiones de moneda en caso de que haya una moneda del Sitio, y una moneda de un Contrato de Compañía/Comercio. Es parte de la funcionalidad de multimoneda para transacciones internacionales u operaciones de contratos en monedas distintas.

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Vista%20Sitio%20y%20configuraci%C3%B3n.png)

<br>

#### Detalle Sitio

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Detalle%20Sitio.png)

<br>

Cabe aclarar, que el campo Moneda es obligatorio en la configuración de un Sitio, asimismo se incorporó una columna Moneda en el documento Excel que se descarga al exportar los sitios desde el portal de ATIONET.

<br>



### Moneda en contingencia
El campo de moneda del sitio se puede encontrar en la vista de listado, detalles, creación y edición de Contingencia. En la vista de creación y edición la moneda se carga automáticamente al elegir el sitio de ocurrencia de la transacción.

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Moneda%20en%20contingencia.png)

<br>


### Moneda en widget de pre-autorización manual
Al momento de querer generar una pre autorización por medio del widget, se indicará la moneda automáticamente una vez cargado el sitio donde se desea pre-autorizar una transacción.

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Moneda%20en%20widget%20de%20pre-autorizaci%C3%B3n%20manual.png)

<br>


### Moneda en widget de pre autorizaciones pendientes 
En la vista de widget de pre autorizaciones pendientes se puede visualizar el código de la moneda del Sitio.

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Moneda%20en%20widget%20de%20pre%20autorizaciones%20pendientes.png)

<br>


## Configuraciones

Las configuraciones necesarias para habilitar la funcionalidad de Multimoneda son las siguientes:


### Configuración de monedas en Network

En esta sección dentro de la configuración de la red se pueden configurar tres tipos de monedas (Contable, Conversión, Conciliación), como parte de la funcionalidad de multimoneda para transacciones internacionales.

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Anexo/Configuraci%C3%B3n%20de%20monedas%20en%20Network.png)

<br>


En las tres opciones seleccionar la moneda con la que va a gestionar la Network.


<br>


### Crear y configurar Cotización

Este paso es muy importante para poder operar con monedas diferentes: 

En Administración / Crear cotización de la moneda seleccionada en configuraciones con la otra moneda con la que se va gestionar:

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Anexo/Crear%20y%20configurar%20Cotizaci%C3%B3n.png)

<br>

Toda moneda que no sea la contable se tiene que agregar como cotización.

Tener en cuenta que en la grilla por defecto se ven las cotizaciones vigentes, en caso de requerir visualizar cotizaciones con vigencias Futuras o Pasadas se puede usar el filtro de Vigencia.

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Anexo/Crear%20y%20configurar%20Cotizaci%C3%B3n2.png)

<br>


### Configuración de monedas en Sitio

<br>


En esta vista al crear o editar un Sitio se puede configurar la moneda de operación.

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Anexo/Configuraci%C3%B3n%20de%20monedas%20en%20Sitio.png)

<br>

#### Editar Sitio

Al seleccionar la opción Editar se puede configurar la moneda en un sitio en que se requiera:

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Anexo/Editar%20Sitio.png)

<br>

Se habilita el detalle y en el campo Moneda seleccionar la que corresponda:

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Anexo/Se%20habilita%20el%20detalle.png)

<br>


#### Nuevo Sitio
Al crear un nuevo Sitio, en el campo Moneda se debe seleccionar la moneda que utilizará en el mismo.

<br>

![](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Functional%20Documentation/Multimoneda/Anexo/Nuevo%20Sitio.png)

<br>

La incorporación de configuración de moneda a nivel de Sitio tiene la finalidad de ser usada en el cálculo de conversiones de moneda si fuese el caso entre moneda del sitio y moneda de un contrato de compañía/comercio. Parte de la funcionalidad de operación multimoneda para transacciones internacionales u operaciones de contratos en monedas distintas.


[Arriba](#multimoneda) 	
