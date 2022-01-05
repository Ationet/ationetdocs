![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|**Información del Documento**|.|
|--- |--- |
|**Archivo:**|ATIONet_Network_User_Manual-ES.md|
|**Versión Doc:**|1.0|
|**Fecha Liberación:**|05, Ene 2022|
|**Autor:**|ATIONet LLC|


|**Bitácora de Cambios**|||
|--- |--- |--- |
|**Ver.**|**Fecha**|**Resumen de Cambios**|
|1.0|05/Ene/2022|- Funcionalidad Multimoneda

# Contenido

- [Funcionalidades Destacadas](#funcionalidades-destacadas)
    - [Multimoneda](#multimoneda) 	
        - [Anexo](#anexo) 

# Funcionalidades destacadas

## Multimoneda

### Objetivo
El propósito del documento es detallar cómo la funcionalidad de Multimoneda ayuda en la gestión diaria de combustible en ATIONET cuando se generan transacciones en diferentes monedas, buscando reducir procesos manuales que puedan realizar nuestros usuarios.

### Introducción
En los países o regiones en los cuales circulan varias monedas, la funcionalidad de multimoneda es estratégica e imprescindible. Proporciona la posibilidad de que sus clientes puedan abonar con distintas monedas de acuerdo al sitio o región donde se encuentren.

### Descripción
La funcionalidad de Multimoneda permite operar con diferentes divisas dentro del portal. Para poder utilizar esta funcionalidad es necesario realizar algunas configuraciones en la plataforma que permitirán realizar las conversiones requeridas en cada operación.

Intervienen 4 monedas:
- Moneda de operación: es la moneda de ocurrencia, en una transacción es la moneda configurada en el sitio, en un movimiento de cuenta corriente es la moneda elegida para el pago.
- Moneda de conversión: es la moneda pivot, utilizada para toda conversión desde la moneda de operación hacia cualquier otra moneda.
- Moneda de cuenta corriente: es la moneda en la que se administran los contratos, y por lo tanto la cuenta corriente.
- Moneda de conciliación: es la moneda utilizada para conciliar todas las cuentas corrientes, si la Network quisiera conciliar todos sus contratos. Si bien hoy se realizan estas conversiones, no se muestra este valor en ningún lado, en ningún reporte.

### Flujo de configuración inicial requerida

![Flujomultimoneda](ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/flujomultimoneda.PNG)
*En el anexo del documento podrá encontrar el detalle de las configuraciones necesarias para habilitar la funcionalidad de Multimoneda.

### Vistas impactadas
A continuación, se detallan las vistas que se ven impactadas por la funcionalidad de Multimoneda:  
- Transacciones
- Movimientos de Cuenta Corriente
- Estado de Cuenta
- Configuración de Procesos de Liquidación
- Contrato de Comercio.
- Configuración de Red
- Sitio y Configuración

#### Vistas de transacciones
Se pueden identificar las monedas que interactúan en el circuito de autorización de una transacción como dato complementario en los campos que representan el valor monetario de la misma. 
Dentro de las vistas de transacciones se ven afectadas por la funcionalidad de multimoneda las siguientes:

- Transacciones
- Detalle de Transacciones
- Detalle de Excepciones
- Transacciones Despachadas
- Transacciones ERP
- Transacciones Rechazadas

##### Vista Transacciones


##### Vista Detalle (Esta sección es igual en todas Transacciones y Excepciones)


##### Vista Transacciones Despachadas


##### Vista Transacciones ERP


##### Vista Transacciones Rechazadas


### Vistas de transacciones agrupadas

Se pueden visualizar las monedas que interactúan en el circuito de autorización de una transacción como dato complementario en los campos que representan valor monetario de la misma. Las vistas en las que se ven reflejadas son las siguientes:


##### Vista Transacciones por conductor

##### Vista Transacciones por vehículo

##### Vista Transacciones por flota

##### Vista Transacciones por sitio

### Cotización en transacción
El motor de autorizaciones posee la lógica para considerar el cálculo de cotizaciones configuradas vigentes en los montos autorizados, y en la validación de disponible para transaccionar de los clientes, así como el impacto de los montos correspondientes en la moneda del contrato en la cuenta corriente del mismo. 

### Cotización en Cuenta Corriente
Permite realizar movimientos de Cuenta Corriente (depósitos) en Contratos de Compañía y/o Comercio y en subcuentas, en moneda distintas a las del contrato referido.

### Vista de Cuenta Corriente de Compañía
La columna Moneda se puede visualizar en la grilla de Cuenta corriente de Compañía, así como en la exportación a Excel de movimientos e impresión de los mismos. La moneda se visualizará siempre y cuando el contrato sea en importe.

##### Archivo Excel de movimiento Cuenta corriente de Compañía


##### Nuevo movimiento de Cuenta Corriente de Compañía

### Vista de Cuentas corrientes de Comercio
La columna Moneda se puede visualizar en la grilla de Cuentas corrientes de Comercio, así como en la exportación a Excel de movimientos. La moneda se visualizará siempre y cuando el contrato sea en importe.


##### Archivo Excel de movimiento Cuentas corrientes de Comercio


##### Nuevo movimiento de Cuenta corriente de Comercio


### Valores en estados de cuenta
La funcionalidad de Multimoneda impacta en el proceso de generación de estados de cuenta lo que hace considerar los valores registrados de las transacciones basadas en las monedas involucradas para realizar los cálculos correspondientes y reflejarlos en el estado de cuenta.

### Vista Sitio y configuración
La configuración de moneda a nivel de Sitio es utilizada en el cálculo de conversiones de moneda en caso de que haya una moneda del Sitio, y una moneda de un Contrato de Compañía/Comercio. Es parte de la funcionalidad de multimoneda para transacciones internacionales u operaciones de contratos en monedas distintas.

Cabe aclarar, que el campo Moneda es obligatorio en la configuración de un Sitio, asimismo se incorporó una columna Moneda en el documento Excel que se descarga al exportar los sitios desde el portal de ATIONET.


### Moneda en contingencia
El campo de moneda del sitio se puede encontrar en la vista de listado, detalles, creación y edición de Contingencia. En la vista de creación y edición la moneda se carga automáticamente al elegir el sitio de ocurrencia de la transacción.

### Moneda en widget de pre-autorización manual
Al momento de querer generar una pre autorización por medio del widget, se indicará la moneda automáticamente una vez cargado el sitio donde se desea pre-autorizar una transacción.

### Moneda en widget de pre autorizaciones pendientes 
En la vista de widget de pre autorizaciones pendientes se puede visualizar el código de la moneda del Sitio.

## Anexo

Las configuraciones necesarias para habilitar la funcionalidad de Multimoneda son las siguientes:


### Configuración de monedas en Network

En esta sección dentro de la configuración de la red se pueden configurar tres tipos de monedas (Contable, Conversión, Conciliación), como parte de la funcionalidad de multimoneda para transacciones internacionales.

##### Agregar Imagen

En las tres opciones seleccionar la moneda con la que va a gestionar la Network.


### Crear y configurar Cotización

Este paso es muy importante para poder operar con monedas diferentes: 

En Administración / Crear cotización de la moneda seleccionada en configuraciones con la otra moneda con la que se va gestionar:

##### Agregar Imagen

Toda moneda que no sea la contable se tiene que agregar como cotización.

Tener en cuenta que en la grilla por defecto se ven las cotizaciones vigentes, en caso de requerir visualizar cotizaciones con vigencias Futuras o Pasadas se puede usar el filtro de Vigencia.
##### Agregar Imagen

### Configuración de monedas en Sitio

En esta vista al crear o editar un Sitio se puede configurar la moneda de operación.
##### Agregar Imagen

#### Editar Sitio

Al seleccionar la opción Editar se puede configurar la moneda en un sitio en que se requiera:
##### Agregar Imagen

Se habilita el detalle y en el campo Moneda seleccionar la que corresponda:
##### Agregar Imagen

#### Nuevo Sitio
Al crear un nuevo Sitio, en el campo Moneda se debe seleccionar la moneda que utilizará en el mismo.

##### Agregar Imagen

La incorporación de configuración de moneda a nivel de Sitio tiene la finalidad de ser usada en el cálculo de conversiones de moneda si fuese el caso entre moneda del sitio y moneda de un contrato de compañía/comercio. Parte de la funcionalidad de operación multimoneda para transacciones internacionales u operaciones de contratos en monedas distintas.
