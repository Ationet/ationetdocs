![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

# Contenido

- [Administración](#administración)
  - [Banderas](#banderas)
  - [Categorías de SKUs](#categorías-de-skus)
  - [Combustibles](#combustibles)
  - [Comercios](#comercios)
  - [Compañías](#compañías)
  - [Conductores](#conductores)
  - [Cotizaciones](#cotizaciones)
  - [Depositos](#depositos)
  - [Documentos Externos](#documentos-externos)
  - [Grupos de Combustibles Maestros](#grupos-de-combustibles-maestros)
  - [Grupos de Compañías](#grupos-de-compañías)
  - [Grupos de Compañías - Movimientos](#grupos-de-compañías---movimientos)
  - [Identificadores](#identificadores)
  - [Impuestos](#impuestos)
  - [Instalaciones](#instalaciones)
  - [Métodos de Pago](#métodos-de-pago)
  - [Modelos de Identificadores](#modelos-de-identificadores)
  - [Notificaciones](#notificaciones)
  - [Precios de Distribución](#precios-de-distribución)
  - [Proveedores de Identificadores](#proveedores-de-identificadores)
  - [Sitios](#sitios)
  - [SKUs](#skus)
  - [Terminales/Controladores](#terminales--controladores)
  - [Usuarios](#usuarios)
  - [Vales](#vales)
  - [Vehículos](#vehículo)
  - [Zonas](#zonas)

# Administración
Dentro de este módulo podrá gestionar Compañías, Comercios, Sitios, Identificadores, Métodos de Pago y Usuarios entre otras cosas.

## Banderas
En ATIONET el término bandera se refiere al nombre de cada combustible maestro disponible en ATIONET. En esta sección se pueden consultar y crear banderas.

![Banderas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Banderas.PNG)

Para cada Network ATIONET ya tiene una bandera **DEFAULT** creada con los siguientes combustibles:

![Bandera DEFAULT](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Banderas%20DEFAULT.PNG)

Para crear una bandera, haga clic en el botón **Nuevo**:

![Bandera Nueva](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Banderas%20Nueva.PNG)

Los campos a completar son los siguientes:

* **Nombre:** El nombre de la nueva bandera.
* **Combustible:** Seleccione el combustible maestro de ATIONET al que desea cambiar el nombre.
* **Nombre del combustible:** Introduzca el nuevo nombre de su combustible.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

## Categorías de SKUs
En esta sección puede consultar las categorías de SKUs (Stock Keeping Units) ya creadas, editarlas o crear nuevas. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Categorías de SKUs](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Categorias%20SKU.PNG)

Para crear una categoría SKU, haga clic en el botón **Nuevo**.

![Categorías SKU nueva](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Categorias%20SKU%20Neueva.PNG)

Los campos a completar son los siguientes:

* **Código:** El código de la categoría SKU.
* **Nombre:** El nombre de la categoría SKU.
* **Descripción corta:** Una breve descripción de la categoría SKU.
* **Primera/segunda categoría madre:** Por ejemplo, si la categoría SKU fuera "Cigarrillos Camel", la primera categoría padre sería "Tabaco" y la segunda sería "Cigarrillos".
* **Es POS:** Marque esta opción si la categoría SKU puede ser adquirida en el punto de venta.
* **Flota seca:** Marque esta opción si la categoría SKU es flota seca.
* **Recompensa:** Marque esta opción si se puede canjear por puntos de fidelidad.
* **Servicio:** Marque esta opción si se trata de un servicio.
* **Fidelidad:** Marque esta opción si la compra del producto acumula puntos de fidelidad.

Cuando haya terminado de rellenar los campos, pulse el botón **Guardar**.

## Combustibles
Esta vista enumera las asignaciones de combustible y su respectivo código para todos los sitios que tienen activada la opción **Mapeo de Combustible Requerido** (para más información sobre el mapeo de combustible haga clic [aquí](#sitios)). Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Combustibles](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Combustibles.PNG)

Para crear un mapeo de combustible, haga clic en el botón **Nuevo**.

![Combustibles nuevos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Combustibles%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Sitio:** Seleccione el sitio asociado al mapeo de combustible.
* **Combustibles Maestros:** Seleccione el combustible maestro asociado al mapeo de combustible.
* **Código:** Introduzca el código asociado al mapeo de combustible.

Cuando haya terminado de rellenar los campos, pulse el botón **Guardar**.

## Comercios
En ATIONET el término comercio se refiere a la empresa propietaria de los sitios. En esta sección puede ver, crear y editar todos los comercios. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Comercios](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Comercios.PNG)

Para crear un comercio, haga clic en el botón **Nuevo**.

![Comercios nuevos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Comercios%20Nuevo.PNG)

Los campos a completar son los siguientes:
* **Id Contribuyente:** Introduzca el identificador del contribuyente del comercio.
* **Activo:** Marcar para activar/desactivar del comercio.
* **Código:** Introduzca el código único del comercio.
* **Nombre:** Introduzca el nombre del comercio.
* **Generado automáticamente:** Marque esta opción para que el código se genere automáticamente.
* **Calle 1:** Introduzca la calle principal del comercio.
* **Calle 2:** Introduzca la calle secundaria del comercio.
* **Código postal:** Introduzca el código postal del comercio.
* **Ciudad:** Introduzca la ciudad del comercio.
* **País:** Introduzca el país del comercio.
* **Estado:** Introduzca el estado del comercio.
* **Nombre de contacto:** Introduzca el nombre de contacto del comercio.
* **Correo electrónico de contacto:** Introduzca el correo electrónico de contacto del comercio.
* **Número de teléfono 1:** Introduzca el número de teléfono principal del comercio.
* **Número de teléfono 2:** Introduzca el número de teléfono secundario del comercio.

Cuando haya terminado de rellenar los campos, haga clic en el botón **Guardar**.

## Compañías
En ATIONET el término compañías se refiere a la entidad propietaria de la flota. En esta sección puedes ver las compañías existentes con sus detalles, editarlas y/o crear nuevas. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Compañías](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Compa%C3%B1%C3%ADas.PNG)

Para crear una compañía, haga clic en el botón **Nuevo**.

![Compañías nueva](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Compa%C3%B1%C3%ADas%20Nueva.PNG)

Los campos a completar son los siguientes:

* **ID Contribuyente:** Introduzca la identificación del contribuyente de la compañía.
* **Activo:** Marcar para activar/desactivar la compañía del grupo.
* **Código:** Introduzca el código único de la compañía.
* **Nombre:** Introduzca el nombre de la compañía.
* **Generado Automáticamente:** Marque esta opción para que el código se genere automáticamente.
* **Sector:** Seleccione el sector asociado a la compañía.
* **Calle 1:** Introduzca la calle principal de la compañía.
* **Calle 2:** Introduzca la calle secundaria de la compañía.
* **Código postal:** Introduzca el código postal de la empresa.
* **Ciudad:** Introduzca la ciudad de la compañía.
* **País:** Introduzca el país de la compañía.
* **Estado:** Introduzca el estado de la compañía.
* **Categoría de Contribuyente:** Seleccione la categoría de contribuyente de la compañía.
* **Nombre de contacto:** Introduzca el nombre de contacto de la compañía.
* **Correo electrónico de contacto:** Introduzca el correo electrónico de contacto de la compañía.
* **Número de teléfono 1:** Introduzca el número de teléfono principal de la compañía.
* **Número de teléfono 2:** Introduzca el número de teléfono secundario de la compañía.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

## Conductores
En esta vista se listan los conductores que han sido creados. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Conductores](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Conductores.PNG)

## Cotizaciones

![Cotizaciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Cotizaciones.PNG)

<br>

![Cotizaciones Nueva](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Cotizaciones%20Nuevo.PNG)

## Depositos
En esta sección puede crear/editar depositos. El deposito es donde se almacenan los identificadores instalados.

![Depositos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Depositos.PNG)

Para crear un Deposito, haga clic en el botón **Nuevo**.

![Depositos nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Depositos%20Nuevo.PNG)

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.


## Documentos Externos


## Grupos de Combustibles Maestros
Esta vista muestra todos los grupos de combustibles creados. Esta opción permite agrupar varios combustibles maestros en uno solo. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Grupos maestros de combustibles](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Grupo%20Maestro%20de%20Combustibles.PNG)

Para crear un nuevo grupo, haga clic en el botón **Nuevo**.

![Grupos de combustibles nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Grupo%20Maestro%20de%20Combustibles%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Código:** Introduzca el código del grupo maestro de combustibles.
* **Nombre:** Introduzca el nombre del grupo maestro de combustibles.
* **Descripción:** Introduzca una descripción para el grupo maestro de combustibles.
* **Combustible:** Seleccione todos los combustibles asociados al grupo maestro de combustibles.
* **Coeficiente de emisión de CO2:** Introduzca el coeficiente de emisión de CO2 de todos los combustibles del grupo maestro.

Cuando haya terminado de rellenar los campos, pulse el botón **Guardar**.

# Grupos de Compañías
Esta sección muestra todos los grupos de compañías creados. Esta función le permitirá agrupar las compañías en una sola. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Grupos de Compañías](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Grupos%20de%20Compa%C3%B1%C3%ADas.PNG)

Para crear un grupo de compañías, haga clic en el botón **Nuevo**.

![Grupos de Compañías Nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Grupos%20de%20Compa%C3%B1%C3%ADas%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **ID Contribuyente:** Introduzca la identificación del Contribuyente del grupo de compañías.
* **Activo:** Marcar para activar/desactivar el grupo de compañías.
* **Código:** Introduzca el código único del grupo de compañías.
* **Nombre:** Introduzca el nombre del grupo de compañías.
* **Industria:** Seleccione el sector del grupo de compañías.
* **Tipo:** Seleccione el tipo de grupo de compañías (flota, tarjeta de regalo o comercio).
* **Calle 1:** Introduzca la calle principal del grupo de compañías.
* **Calle 2:** Introduzca la calle secundaria del grupo de compañías.
* **Código postal:** Introduzca el código postal del grupo de compañías.
* **Ciudad:** Introduzca la ciudad del grupo de compañías.
* **País:** Introduzca el país del grupo de compañías.
* **Estado:** Introduzca el estado del grupo de compañías.
* **Categoría de contribuyente:** Seleccione la categoría de contribuyente del grupo de compañías.
* **Nombre de contacto:** Introduzca el nombre de contacto del grupo de compañías.
* **Correo electrónico de contacto:** Introduzca el correo electrónico de contacto del grupo de compañías.
* **Número de teléfono 1:** Introduzca el número de teléfono principal del grupo de la compañías.
* **Número de teléfono 2:** Introduzca el número de teléfono secundario del grupo de compañías.
* **Modo de cuenta actual:** Seleccione el modo de cuenta actual del grupo de compañías.
* **Moneda:** Seleccione la moneda del grupo de compañías.
* **Modo:** Seleccione el modo del grupo de compañías (crédito o débito).
* **Límite:** Introduzca el límite del grupo de compañías.

<br>

* **Compañía:** Seleccione la compañía o compañías que están incluidas en el Grupo de Compañías.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

## Grupos de Compañías - Movimientos
En esta sección se listan todos los movimientos (ingresos, retiros, finalizaciones, etc.) de todos los Grupos de Empresas.

![Movimientos de Grupos de Compañías](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Grupos%20de%20Compa%C3%B1%C3%ADas%20Movimientos.PNG)

Tenga en cuenta que primero debe completar el campo **Grupo de Compañías** y luego hacer clic en el botón **Búsqueda** para poder ver todos sus movimientos.

Para crear un movimiento, haga clic en el botón **Nuevo**:

![Grupos de Compañías Movimientos Nuevos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Grupos%20de%20Compa%C3%B1%C3%ADas%20Movimientos%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Descripción:** Introduzca una breve descripción del movimiento.
* **Grupo de Compañías:** Seleccione el Grupo de Compañías asociado al movimiento.
* **Tipo:** Seleccione el tipo de movimiento (depósito o retiro).
* **Importe:** Introduzca el importe asociado al movimiento.

Cuando haya terminado de rellenar los campos, pulse el botón **Crear**.

## Identificadores
El identificador es el medio físico utilizado por ATIONET para identificar un vehículo o conductor. El identificador es compatible con varios tipos de identificación, tales como tarjeta, TAG, chip, tarjeta ATIONET, entrada manual, código de barras y iButton. Cuando se asocia un identificador a un Vehículo o Conductor, se crea una subcuenta.

En esta sección aparecerán los identificadores ya creados. En la columna de opciones se puede editar el identificador, activarlo o desactivarlo y liberarlo. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Identificadores](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Identificadores.PNG)

Para crear un identificador, haga clic en el botón **Nuevo**.

![Identificadores Nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Identificador%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Tipo:** Puede ser Tarjeta, TAG, Chipkey, Entrada Manual, Tarjeta ATIONET o TAG ATIONET.
* **Modelo:** El modelo del tipo de identificador seleccionado en **Tipo**.
* **Tipo de uso:** Puede ser flota, fidelidad o dual.
* **Programa:** El programa al que se asignará esta identificación.
* **Programa de fidelidad:** El programa de fidelidad al que se asignará este identificador.
* **Etiqueta:** El nombre de la tarjeta (por ejemplo Pablo Pérez).
* **Track:** El track es la información que tiene grabada el identificador en su interior. Se divide en tres partes. En este campo se puede editar lo que contiene el segundo campo de la pista.
* **PAN:** Un número entre 1 y 19 caracteres que se encuentra en el identificador. 
* **PIN:** El PIN del identificador (esta opción sólo estará disponible si el modelo de identificador tiene activada la opción **PIN**).

Cuando haya terminado de rellenar los campos, pulse el botón **Guardar**.

## Impuestos
Dentro de esta sección puedes consultar todos los impuestos creados, editarlos o crear nuevos.

La tabla de impuestos muestra:
* **Código:** Código del impuesto.
* **Descripción:** Descripción del impuesto.
* **Tipo:** Tipo de impuesto (Puede ser un impuesto fijo, un impuesto porcentual o un impuesto fijo por unidad).
* **Monto:** El monto del impuesto (En el caso del impuesto porcentual, el porcentaje).
* **Fecha Desde / Fecha Hasta:** Rango de fechas.
* **Modo:** Modo del impuesto (puede ser un impuestos, percepcioes, retenciones, otras).
* **Modo de Uso:** Modo de uso que corresponde al impuesto.
* **Incluido:** Indica si esta incluido con "Si" o "No".
* **Activo:** MIndica si esta activo con "Si" o "No".
* **Opciones:** Editar el impuesto.

![Impuestos](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Impuestos.PNG)

Para crear un impuesto, haga clic en el botón **Nuevo**.

![Impuestos nuevo](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Impuestos%20Nuevo.PNG) 

Los campos a completar son los siguientes:

* **Código:** El código del nuevo impuesto.
* **Descripción:** La descripción del nuevo impuesto.
* **Tipo:** Tipo de impuesto (Puede ser un impuesto fijo, un impuesto porcentual o un impuesto fijo por unidad).
* **Modo:** Seleccionar el modo (impuestos, percepcioes, retenciones, otras).
* **Modo de Uso:** Seleccionar el modo de uso que corresponda al impuesto.
* **Activo:** Marcar para activar el impuesto.
* **Incluido:** Marcar para incluir el impuesto.

</br>

**Vigencias:**

* **Fecha desde:** La fecha en que el impuesto entra en vigor.
* **Hora desde:** La hora en que el impuesto entra en vigor.
* **Importe:** El importe del impuesto (En el caso del impuesto porcentual, el porcentaje).

Después de rellenar los campos **Fecha desde**. **Hora desde** e **Importe**, presione el botón **Alta**. 

</br>

**Configuración del Impuesto para Edifact** 

Si en configuraciones de red esta habilitada esta opciòn se visualizarà la secciòn **Configuración del Impuesto para Edifact**

![Configuraciòn Edifacto](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Impuestos%20Nuevo%20-%20Configuraci%C3%B3n%20Edifact%20.PNG) 



</br>

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

</br>

## Instalaciones
En ATIONET el hecho de que los identificadores deban ser colocados por un técnico se conoce como **Instalaciones**.

En este apartado podrá consultar todas las instalaciones realizadas, listadas por Fecha, Orden de Trabajo, los identificadores instalados, el vehículo en el que se instaló el identificador, el depósito del que se retiró el identificador y el técnico que lo instaló.

![Instalaciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Instalaciones.PNG)

Para crear una instalación, haga clic en el botón **Nueva**.

![Instalaciiones nueva](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Instalaciones%20Nueva.PNG)

Los campos a completar son los siguientes:

* **Orden de trabajo:** El número único relacionado con el documento de la orden de trabajo.
* **Técnico:** El técnico que ha realizado la instalación.
* **Empresa:** La compañía de la que formaba parte el vehículo al que se le hizo la instalación.
* **Fecha:** La fecha en la que se realizó la instalación.
* **Contrato:** El contrato al que está vinculado el vehículo.
* **Vehículo:** El vehículo al que se realizó la instalación.
* **Depósito:** El depósito es el lugar físico donde se retiró el identificador para colocarlo.
* **Tiene OBD:** Marque esta opción si el vehículo dispone de On-Board Diagnostics.

Si tiene OBD, se mostrarán más campos:

* **ID:** Introduzca el ID del OBD.
* **Modelo:** Seleccione el modelo de OBD.
* **Sensor:** Tilde esta opción si el OBD tiene un sensor.
* **Odómetro inicial:** Introduzca el odómetro inicial.
* **Proporción:** Introduzca las proporciones del OBD.

Luego, en la sección de Identificadores seleccione el Identificador. Al terminar, haga clic en el botón **Guardar**.

## Métodos de pago
Los métodos de pago son las diferentes formas en que se puede pagar una transacción: efectivo, tarjeta de crédito, tarjeta de débito, tarjetas de regalo, etc. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Métodos de pago](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/M%C3%A9todos%20de%20Pago.PNG)

Para crear un método de pago, haga clic en el botón **Nuevo**.

![Método de pago nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/M%C3%A9todos%20de%20Pago%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Código:** El código del nuevo método de pago.
* **Descripción:** La descripción del nuevo método de pago.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

## Modelos de Identificadores
Los modelos de identificador varían según la necesidad del cliente. Pueden ser del tipo Card (una tarjeta magnética), TAG, Chipkey o Manual Entry (un código introducido a mano). 

![Modelos de identificadores](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Modelos%20de%20Identificador.PNG)

Para crear un modelo de identificador, haga clic en el botón **Nuevo**.

![Nuevo modelo de identificadores](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Modelos%20de%20Identificador%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Tipo:** Puede ser Tarjeta, TAG, Chipkey o Tipo de entrada manual.
* **Descripción:** La descripción del nuevo modelo de identificadores.
* **Instalable:** Si es instalable o no.
* **Personalizado:** Si está personalizado o no.
* **Reutilizable:** Si es reutilizable o no.
* **Admite múltiples asignaciones:** Si admite múltiples asignaciones o no.
* **Fecha de caducidad válida:** Si valida la fecha de caducidad o no.
* **Ignorar el comportamiento de ID vehículo en la terminal:** Ignorar el comportamiento de la identificación del vehículo en el terminal o no.
* **Requiere PIN:** Si requiere PIN o no.

Cuando haya terminado de rellenar los campos, pulse el botón **Guardar**.

## Notificaciones
En esta sección cada usuario puede seleccionar sus propias notificaciones para recibirlas por correo electrónico o sms.

![Notificaciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Notificaciones.PNG)

1. ***Inventario***
   * **Notificación de nueva entrega:** Recibe una notificación por cada entrega detectada.
   * **Notificación de inventario bajo:** Recibe una notificación cuando el inventario es bajo.
   * **Alerta de notificación de volumen de agua:** Recibe una notificación cuando el agua está baja.
2. ***Contrato***
   * **Notificación de saldo de contrato bajo:** Recibe una notificación cuando el saldo de un contrato es bajo.
   * **Notificación de saldo de contrato vacío:** Recibe una notificación cuando un contrato no tiene saldo.
   * **Notificación de porcentaje de crédito:** Recibe una notificación cuando se alcanza un porcentaje de crédito (haga click en el lápiz para configurar el porcentaje).
   * **Notificación de saldo bajo:** Recibe una notificación cuando se alcanza un monto (haga clic en el lápiz para configurar el monto).
   * **Depósito de contrato de la compañía:** Recibe una notificación cuando se detecta un depósito a un contrato.
3. ***Identificadores***
   * **Notificación de Identificadores en riesgo de caducidad:** Recibe una notificación cuando un identificador está a punto de caducar.
4. ***Fidelidad***
   * **Notificación de nueva cuenta de fidelidad:** Recibe una notificación cuando se detecta un nuevo programa de fidelidad.
   * **Notificación de acumulación de puntos de fidelidad:** Recibe una notificación cuando se detecta una acumulación.
   * **Notificación de excepciones de fidelidad:** Recibe una notificación cuando se detecta una excepción.
5. ***Liquidación***
   * **Notificación de proceso de liquidación:** Recibe una notificación cuando se detecta un proceso de liquidación.
   * **Cargos del comercio:** Recibe una notificación cuando se detectan cargos del comercio.
   * **Cargos externos:** Recibe una notificación cuando se detectan cargos externos.
6. ***Transacciones***
   * **Notificación de nuevas transacciones de contingencia:** Recibe una notificación cuando se detecta una nueva contingencia.
   * **Notificación de transacción a revisar:** Recibe una notificación cuando se detectó una excepción marcada para ser revisada.
   * **Excepción de salida de combustible:** Recibe una notificación cuando se detectó una excepción de salida de combustible.
   * **Excepción de transacción:** Recibe una notificación cuando se detecta una excepción.
   * **PIN incorrecto:** Recibe una notificación cuando se detecta una transacción rechazada por un PIN incorrecto.
   * **Transacción rechazada:** Recibe una notificación cuando se detecta una transacción rechazada.
   * **Transacciones impugnadas:** Recibe una notificación cuando se detecta una transacción impugnada.

### Notificaciones de compañía
En esta sección los usuarios de la compañía pueden configurar sus propias notificaciones (dentro de sus perfiles de compañía en ATIONET).

![Notificaciones Compañía](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Notificaciones%20Compa%C3%B1%C3%ADas.PNG)

1. ***Contrato***
   * **Notificación de saldo de contrato bajo:** Recibe una notificación cuando el saldo de un contrato es bajo.
   * **Notificación de saldo de contrato vacío:** Recibe una notificación cuando un contrato no tiene saldo.
   * **Notificación de porcentaje de crédito:** Recibe una notificación cuando se alcanza un porcentaje de crédito (haga clic en el lápiz para configurar el porcentaje).
   * **Notificación de saldo bajo:** Recibe una notificación cuando se alcanza un monto (haga clic en el lápiz para configurar el monto).
   * **Depósito de contrato de la compañía:** Recibe una notificación cuando se detecta un depósito a un contrato.
2. ***Liquidación***
   * **Cargos externos:** Recibe una notificación cuando se detectan cargos externos.
3. ***Transacciones***
   * **Excepción de transacción:** Recibe una notificación cuando se detecta una excepción.
   * **Autorización de reglas no bloqueantes:** Recibe una notificación cuando se detecta una autorización de regla no bloqueante.
   * **Identificación habilitada/deshabilitada:** Recibe una notificación cuando un identificador fue habilitado/deshabilitado.
   * **Identificadores solicitados:** Recibe una notificación cuando se detecta una solicitud de identificación.
   * **Transacción rechazada:** Recibe una notificación cuando se detecta una transacción rechazada.
   * **Transacciones Disputadas:** Recibe una notificación cuando se detecta una transacción disputada.
4. ***Flota de vehículos***
   * **Límite de Odómetro del Vehículo:** Recibe una notificación cuando se alcanza el odómetro de un vehículo (haga clic en el botón **Lista de Vehículos** para configurar el odómetro y seleccionar el vehículo asociado a la notificación).

## Precios de Distribución
En esta sección puede ver todos los precios de distribución generados. Estos precios se utilizan cuando un contrato de compañía no tiene precios configurados (siempre y cuando la opción de precios de distribución esté habilitada dentro de la configuración del contrato de compañía).

![Precios de distribución](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Precios%20de%20Distribuci%C3%B3n.PNG)

Para crear un precio de distribución, haga click en el botón **Nuevo**.

![Precios de distribución nuevos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Precios%20de%20Distribuci%C3%B3n%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Combustible:** Seleccione el combustible asociado al precio.
* **Valor:** Introduzca el valor del precio del combustible.
* **Fecha desde:** Introduzca la fecha de inicio del precio del combustible.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

## Proveedores de Identificadores
En este apartado podrá consultar y crear cualquier proveedor que desee para enviar sus identificadores a producción. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Proveedores de identificaciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Proveedores%20de%20Identificadores.PNG)

Para crear un proveedor, haga click en el botón **Nuevo**.

![Proveedores de identificación nuevos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Proveedores%20de%20Identificadores%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Nombre:** Introduzca el nombre del proveedor.
* **Correo electrónico:** Introduzca el correo electrónico de contacto del proveedor.
* **Plantilla de correo electrónico:** Introduzca el cuerpo del correo electrónico que desea enviar a su proveedor.

<br>

* **Configuración del archivo para la exportación:** Seleccione el formato en el que desea enviar la información de los identificadores a su proveedor. Puede enviarlo como Excel, CSV o Texto. También puede seleccionar qué información enviar en el archivo (Nombre, Apellido, Número de tarjeta, Número de track, etc.).

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

## Sitios
En ATIONET el sitio representa la estación de servicio. Esta sección muestra los sitios ya creados, editarlos y también crear nuevos. También puede añadir impuestos a los sitios directamente desde la columna **Opciones**. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Sitios](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Sitios.PNG)

Para crear un sitio, haga clic en el botón **Nuevo**.

![Sitios nuevos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Sitios%20Nuevo.PNG)

Los campos a completar son los siguientes:

**Información**

* **Comercio:** Seleccione el comercio asociado al sitio.
* **Código:** Introduzca el código único asociado al sitio.
* **Zona:** Seleccione la zona asociada al sitio.
* **Generado automáticamente:** Marque esta opción para que el **código** se genere automáticamente.
* **Bandera:** Seleccione la bandera asociada al sitio.
* **Idioma:** Seleccione el idioma asociado al sitio.
* **Nombre corto:** Introduzca el nombre corto del sitio.
* **Nombre completo:** Introduzca el nombre completo del sitio.
* **Calle 1:** Introduzca la calle principal del sitio.
* **Calle 2:** Introduzca la calle secundaria del sitio.
* **Industria:** Seleccione la industria asociada al sitio.
* **Zona horaria:** Seleccione la zona horaria asociada al sitio.
* **Código postal:** Introduzca el código postal del sitio.
* **Ciudad:** Introduzca la ciudad del sitio.
* **País:** Introduzca el país del sitio.
* **Estado:** Introduzca el estado del sitio.
* **Número de teléfono 1:** Introduzca el número de teléfono principal del sitio.
* **Número de teléfono 2:** Introduzca el número de teléfono secundario del sitio.
* **Requiere mapeo de combustible:** Marque esta opción si es necesario configurar códigos de combustible específicos para el sitio (sino, se utilizará [ATIONet Master Fuel Codes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/C%C3%B3digos%20Maestros%20de%20Combustible.PNG)).
* **Emails de los destinatarios:** Introduzca las direcciones de correo electrónico asociadas al sitio (recibirán los estados de cuenta del sitio).
* **Latitud:** Introduzca la latitud del sitio.
* **Longitud:** Introduzca la longitud del sitio.
* **Moneda:** Seleccione la moneda asociada al sitio.

<br>

**Notificación - Regla de Alerta**

* **Notificación de inventario bajo:** Introduzca la cantidad de inventario bajo. Cuando se alcance, los contactos en **correos electrónicos del destinatario** recibirán una notificación.
* **Alerta de notificación de volumen de agua:** Introduzca el volumen de agua bajo. Cuando se alcance, los contactos en **los correos electrónicos de los destinatarios** recibirán una notificación.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.



## SKUs
Las Unidades de Mantenimiento de Stock (SKUs - Stock Keeping Units) son productos no combustibles. En esta sección puede consultar los SKUs creados, editarlos y también crear nuevos. Para facilitar las consultas, hay un panel de filtros en la parte superior. 

![SKUs](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/SKUs.PNG)

Para crear un SKU, haga clic en el botón **Nuevo**.

![SKUs Nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/SKUs%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Código:** El código del SKU.
* **Descripción:** La descripción del SKU.
* **Descripción corta:** Una breve descripción del SKU.
* **Descripción Extra Corta:** Una descripción muy corta del SKU.
* **Tipo de producto de la SKU:** Seleccione el tipo de producto.
* **Producto combustible:** Marque esta opción si el SKU es un producto de combustible.
* **Categoría SKU:** Introduzca la categoría a la que pertenece el SKU.
* **Unidad de medida:** Introduzca la unidad en la que se mide el SKU.
* **Vendible:** Marque esta opción si el SKU es vendible.
* **Pesable:** Marque esta opción si el SKU es pesable.
* **Fraccionable:** Marque esta opción si el SKU es fraccionable.
* **Almacenable:** Marque esta opción si el SKU es almacenable.
* **Consignación:** Marque esta opción si el SKU está en consignación.
* **Disponibilidad Desde/Hasta:** Seleccione las fechas entre las que está disponible el SKU.
* **Es POS:** Marque esta opción si el SKU se vende en el punto de venta.
* **Flota seca:** Marque esta opción si el SKU es un producto seco.
* **Recompensa:** Marque esta opción si el SKU puede ser canjeado por puntos de recompensa.
* **Servicio:** Marque esta opción si el SKU es un servicio.
* **Fidelidad:** Marque esta opción si el SKU acumula puntos.

Precio:

* **Sitio:** Seleccione el sitio en el que cargará el precio del SKU.
* **Fecha desde:** Seleccione la fecha de inicio del SKU.
* **Precio:** Indique el precio del SKU.
* **Moneda:** Seleccione la moneda en la que se cotiza el SKU.

Artículos:

* **Formato del código del POS:** Seleccione el formato del código del punto de venta.
* **Código del POS:** Introduzca un código de punto de venta.

Cuando haya terminado de rellenar estos dos campos, presione el botón **Añadir**.

* **Impuestos:** Introduzca el código de impuestos del SKU.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

</br>


## Terminales / Controladores
Dentro de esta sección puede ver, crear y editar todos los terminales/controladores. El terminal es el punto de venta del sitio y el controlador gestiona los surtidores. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Terminales](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Terminales%20-%20Controladores.PNG)

Para crear un Terminal/Controlador, haga clic en el botón **Nuevo**.

![Terminales nuevos](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Terminales%20-%20Controladores%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Comercio:** Seleccione el comercio asociado al terminal/controlador.
* **Sitio:** Seleccione el sitio asociado al terminal/controlador.
* **Activo:** Marque la casilla para activar/desactivar el terminal/controlador.
* **Tipo de terminal/controlador:** Seleccione el tipo de terminal/controlador (ATIO-ControlGas, ATIO-NanoCPI, ATIO StandAlone, VF-Commander, etc.).
* **Modelo:** Seleccione el modelo de terminal/controlador.
* **Código:** Introduzca el código del terminal/controlador (ATIONET genera uno automáticamente, pero puede editarlo. Excepto los 3 primeros caracteres, ya que representan el código de suscripción a la red).
* **Descripción:** Introduzca la descripción del terminal/controlador.
* **Solo Pre Autorizaciones Asistidas:** Marque la casilla para activar que la terminal este habilitada para realizar preautorizaciones asistidas.
* **Lector de TAGs presente:** Marque esta opción si el terminal es capaz de leer TAGs.
* **Uso del Id. del Conductor:** Seleccione la acción que ATIONet tomará asociada al Id. del Conductor de las transacciones (Ninguna, Track Secundaria o Validación de Código).
* **Uso de la Identificación del Vehículo:** Seleccione la acción que ATIONet tomará asociada al Id. del Vehículo de las transacciones (Ninguna, Track Secundaria o Validación de Código).
* **Corte de Volumen Máximo:** Introduzca el volumen máximo que el terminal/controlador autorizará.
* **Corte de Importe Máximo:** Introduzca el importe máximo que autorizará el terminal/controlador.
* **Sistema operativo:** Introduzca el sistema operativo del terminal/controlador.
* **Número de serie:** Introduzca el número de serie del terminal/controlador.

</br>

**Configuración**

En esta sección se puede indicar que la terminal operará en el modo fuera línea (con el Local Agent) con la misma configuración que posee estando en línea. Campos a completar: Mensaje, Nombre de la Propiedad, Configuración Factor, Configuración Modificador, Tipo de transacción.

![Terminales configuración](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Terminales%20-%20Controladores%20Nuevo%20-%20Configuracion.PNG)


Cuando haya terminado de rellenar los campos, presione el botón **Alta** en caso de completar la configuración, y para finalizar **Guardar**.

</br>

## Usuarios
En esta sección puede ver, crear o editar usuarios para la Network. Puede editarlos haciendo clic en el icono del lápiz en la columna de opciones, activar/desactivar un usuario haciendo clic en el icono del candado y restablecer la contraseña con el icono de la estrella.

![Usuarios](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Usuarios.PNG)

Para crear un usuario, haga clic en el botón **Nuevo**.

![Usuarios nuevos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Usuarios%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Correo del usuario:** La dirección de correo electrónico del usuario.
* **Nombre:** El nombre del usuario.
* **Seguridad Social:** El documento del usuario.
* **Calle 1:** La calle donde reside el usuario.
* **Calle 2:** Otra calle de referencia, como puede ser la de la esquina.
* **País:** El país del usuario.
* **Estado:** El estado del país del usuario.
* **Código postal:** El código postal de la localidad donde reside el usuario.
* **Número de teléfono 1:** El teléfono del usuario.
* **Número de teléfono:** El otro teléfono del usuario si está disponible.

<br>

* **Rol:** El rol que asumirá el nuevo usuario.
* **Entidad:** La entidad asignada al usuario.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

## Vales
Dentro de esta sección se puede ver un listado de todos los vales creados por las compañías. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Vales](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Vales.PNG)

## Vehículo
Esta vista muestra todos los vehículos que han sido creados. Recuerde que no es obligatorio cargar los vehículos para poder operar, sólo es necesario si decide asociar las identificaciones a los vehículos. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Vehículos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Veh%C3%ADculos.PNG)

En la columna **Opciones** puede:

* **Asignar Identificadores:** Asignar/desasignar identificadores al vehículo.  
* **Renovación de Identificadores:** Renovar los identificadores asociados al vehículo.
* **Favoritos:** Añadir el vehículo al módulo de **favoritos**.

## Zonas
En esta sección puede crear/editar zonas. Las zonas son áreas a las que se asocian varios sitios. Generalmente un TM (Territory Manager) está asociado a una(s) zona(s) específica(s). Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Zonas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Zonas.PNG)

Para crear una zona, haga clic en el botón **Nuevo**.

![Zonas nuevas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Zonas%20Nueva.PNG)

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

<br>

[Volver al inicio](#contenido) 	:arrow_up:
