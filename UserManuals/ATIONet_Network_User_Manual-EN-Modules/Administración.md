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
  - [Locaciones](#Locaciones)
  - [Métodos de Pago](#métodos-de-pago)
  - [Modelos de Identificadores](#modelos-de-identificadores)
  - [Notificaciones](#notificaciones)
  - [Precios de Distribución](#precios-de-distribución)
  - [Procesos de renovacion de Identificadores](#Procesos-de-renovacion-de-Identificadores)
  - [Proveedores de Identificadores](#proveedores-de-identificadores)
  - [Sitios](#sitios)
  - [SKUs](#skus)
  - [Terminales/Controladores](#terminales--controladores)
  - [Vehículos](#vehículo)
  - [Workflow de Aprovaciones](#Workflow-de-Aprovaciones)
  - [Zonas](#zonas)

# Administración
Dentro de este módulo podrá gestionar Compañías, Comercios, Sitios, Identificadores, Métodos de Pago y Usuarios entre otras cosas.

## Banderas
En ATIONET el término bandera se refiere al nombre de cada combustible maestro disponible en ATIONET. En esta sección se pueden consultar y crear banderas.

![Baderas Menu](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Banderas.PNG)

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

![Combustibles Menu](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Combustibles%20Menu.PNG)

Para crear un mapeo de combustible, haga clic en el botón **Nuevo**.

![Combustibles Config](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Combustibles%20Config.PNG)

Los campos a completar son los siguientes:

* **Sitio:** Seleccione el sitio asociado al mapeo de combustible.
* **Combustibles Maestros:** Seleccione el combustible maestro asociado al mapeo de combustible.
* **Código:** Introduzca el código asociado al mapeo de combustible.

Cuando haya terminado de rellenar los campos, pulse el botón **Guardar**.

## Comercios
En ATIONET el término comercio se refiere a la empresa propietaria de los sitios. En esta sección puede ver, crear y editar todos los comercios. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![comercio menu](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/comercio%20menu.PNG)

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

![Compañia](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Compa%C3%B1ia.PNG)

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
En este apartado se puede configurar la cotización de múltiples divisas.
![Cotizaciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Cotizaciones.PNG)

<br>

![Cotizaciones Nueva](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Cotizaciones%20Nuevo.PNG)

Las secciones por configurar son las siguientes:
*	**Moneda Origen:** Seleccione la moneda del país de origen
*	**Moneda de Destino:** Seleccione la moneda del país de destino
*	**Valor de Conversión:** Introduzca el valor de conversión de la divisa
*	**Fecha de Inicio:** Introduzca la fecha en la cual se comenzará a realizar este proceso
*	**Hora desde:** Introduzca la hora en la cual se comenzará a realizar este proceso

## Depositos
En esta sección puede crear/editar depositos. El deposito es donde se almacenan los identificadores instalados.

![Depositos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Depositos.PNG)

Para crear un Deposito, haga clic en el botón **Nuevo**.

![Depositos nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Depositos%20Nuevo.PNG)

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.


## Documentos Externos

La vista "Documentos Externos", le permitirá a la Network alojar cualquier documentación, o reportaría cuyo origen sea ajeno a procesos del portal ATIONET. Por su parte, las compañías o comercios podrán visualizar y descargar dichos archivos. 

Para hacer uso de esta función, se requerirá una integración para consumir la API correspondiente.

![Documentos Externos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Documentos%20Externos.PNG)

## Grupos de Combustibles Maestros
Esta vista muestra todos los grupos de combustibles creados. Esta opción permite agrupar varios combustibles maestros en uno solo. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Grupos de Combustibles Maestros](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Grupos%20de%20Combustibles%20Maestros.PNG)

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

![Grupos de compañias](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Grupos%20de%20compa%C3%B1ias.PNG)

Para crear un grupo de compañías, haga clic en el botón **Nuevo**.

![Grupos de compañias config](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Grupos%20de%20compa%C3%B1ias%20config.PNG)

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

Los campos por completar son los siguientes:

- **Tipo:** Puede ser Tarjeta, TAG, Chipkey, Entrada Manual, Tarjeta ATIONET o TAG ATIONET.
- **Modelo:** El modelo del tipo de identificador seleccionado en **Tipo**.
- **Tipo de uso:** Este se divide entre flota, fidelidad o dual.
- **Programa:** El programa al que se asignará esta identificación en caso de haber elegido “Tipo de uso: Flota/dual”.
- **Comunidad:** La comunidad al que se asignará este identificador en caso de haber elegido “Tipo de uso: Fidelidad/dual”.
- **Etiqueta:** El nombre de la tarjeta (por ejemplo, Pablo Pérez).
- **Track:** El track es la información que tiene grabada el identificador en su interior. Se divide en tres partes. En este campo se puede editar lo que contiene el segundo campo de la pista.
- **PAN:** Un número entre 1 y 19 caracteres que se encuentra en el identificador.
- **Generador Automático:** Al marcar esta opción, se generarán automáticamente los campos de **etiqueta**, **track** y **PAN**
- **PIN:** El PIN del identificador (esta opción sólo estará disponible si el modelo de identificador tiene activada la opción **PIN**).

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
* **Activo:** Indica si esta activo con "Si" o "No".
* **Opciones:** Editar el impuesto.

![Impuestos](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Impuestos.PNG)

Para crear un impuesto, haga clic en el botón **Nuevo**.

![Impuestos Nuevos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Impuestos%20Nuevos.PNG)

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

![instalacion nueva](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/instalacion%20nueva.PNG)

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

</br>

## Locaciones

“Locaciones” es un apartado en el cual los usuarios pueden agregar ubicaciones concretas para las cuales se habilite un tipo puntual de identificador

![LOCACIONES](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/LOCACIONES.PNG)

En la opción de “Nuevo”, se agregan las locaciones, para las cuales se requiere un mínimo de información:

![LOCACIONES 2](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/LOCACIONES%202.PNG)

- **Código:** Se requiere un patrón alfanumérico.
- **País/Estado/ Ciudad/ Calle:** Se precisa la ubicación semi exacta de el lugar que se desea ingresar.
- **Teléfono de Contacto:** Se precisa el teléfono/móvil de un referente de dicha locación.
- **Tipo de Identificador:** Se precisa el tipo de Identificador deseado para dicha locación.
- **Modelo de Identificador:** Se precisa el modelo de Identificador deseado para dicha locación.

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
Los modelos de identificador varían según la necesidad del cliente. 
**_Estos pueden ser de los siguientes tipos:_**
- **Card:** Identificadores de tipo tarjeta. La misma puede ser de banda magnetica o de lectura por aproximacion.
- **TAG:** Identificador del tipo imagen (comunmente en formato QR). Generalmente se utiliza como sticker pegado al parabrisas del vehiculo.
- **Chipkey:** Identificador de tipo llave, utilizado por un sistema especifico de terminales.

![Modelo de Identificador (Menu)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Modelo%20de%20Identificador%20(Menu).PNG)

Los campos a completar son los siguientes:
![Modelo de Identificador (Nuevo)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Modelo%20de%20Identificador%20(Nuevo).PNG)
- **Tipo:** Puede ser Tarjeta, TAG, Chipkey o Tipo de entrada manual.
- **Descripción:** La descripción del nuevo modelo de identificadores.
- **Instalable:** Los identificadores con esta característica solo pueden ser asignados mediante una instalación.
- **Personalizado:** Si está personalizado o no.
- **Reutilizable:** Los identificadores con esta función activa podrán ser reutilizados en caso de ser desasignados (de otro modo quedarían deshabilitados).
- **Admite múltiples asignaciones:** Esta opción permite al conductor/vehículo tener múltiples identificadores de este modelo.
- **Fecha de caducidad válida:** Si valida la fecha de caducidad o no.
- **Ignorar el comportamiento de ID vehículo en la terminal:** Al activar esta opción, se ignorar el comportamiento de la identificación relacionado vehículo en el terminal. Es decir, si para una transacción se fuese a realizar alguna solicitud, esta será omitida.
Una situación donde se pueda aplicar dicha función es para una "Tarjeta de regalo". Estas no poseen ningún ID de vehículo, por lo que si se desease operar en un sitio el cual solicite un ID de vehículo, sin esta función, la Tarjeta de regalo, seria rechazada.
- **Track Personalizado:** Activada esta opción, permite determinar un número de Track a voluntad en lugar de que este se genere automáticamente
- **Uso único:** Activada esta opción, permite que dicho modelo de identificador no pueda usarse múltiples veces.
- **Notificar asignación:** Al activar esta función, le llegara un mail a la entidad a la cual se le asigne dicho identificador.
  - Al activar esta función se habilitará la opción **“Archivo adjunto en notificación”,** la cual permite que el QR llegue adjunto en un archivo PDF
    - Finalmente, en caso de que se habilite la función anterior, una tercera función se habilitara llamada, **“Archivo adjunto encriptado”.** Esta permitirá que al llegar el archivo se solicitara una contraseña, siendo esta el código del vehículo.
![Modelo de Identificador (Notificar Asignacion)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Modelo%20de%20Identificador%20(Notificar%20Asignacion).PNG)
- **No soporta Offline:** Esta función permite que solamente opere cuando el sistema se encuentra en estado Online.
- **Requiere PIN:** Esta función nos permite determinar si requiere PIN, a su vez que nos exige establecer la cantidad de números solicitados para el PIN
  - Al activar esta función se habilitará una nueva función llamada **“Requiere cambio de PIN”** la cual es una opción puntual para terminales las cuales permitan establecer un PIN directamente desde la estación.
![Modelo de Identificador (Requiere PIN)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Modelo%20de%20Identificador%20(Requiere%20PIN).PNG)
- **Valida periodo de inactividad:** Esta función nos permite evaluar la inactivación automática de un identificador correspondiente a este modelo de acuerdo con el periodo establecido.
![Modelo de Identificador (Inactividad)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Modelo%20de%20Identificador%20(Inactividad).PNG)
  - Al activar esta función, se habilitará una caja en la cual se podrá establecer el periodo en cuestión.
- **Tipo de Track personalizado:** Al habilitar esta función permite establecer un Prefijo y un Sufijo al Track.
- **Encriptación de Track:** Esta función les otorga a los identificadores de este modelo, la capacidad de ser verificados con un track encriptado y el mismo será reconocido por ATIONET y validado en caso de que exista. Para que aplique la lectura del track encriptado, se deberá configurar la propiedad correspondiente en la terminal.

![Modelo de Identificador (Track)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Modelo%20de%20Identificador%20(Track).PNG)

Cuando haya terminado de rellenar los campos, pulse el botón **Guardar**.

## Notificaciones
En esta sección cada usuario puede seleccionar sus propias notificaciones para recibirlas por correo electrónico o sms.

1. **_Inventario_**

![Notificaciones (Inventario)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Notificaciones%20(Inventario).PNG)
- **Notificación de nueva entrega:** Recibe una notificación por cada entrega detectada.
- **Notificación de inventario bajo:** Recibe una notificación cuando el inventario es bajo.
- **Alerta de notificación de volumen de agua:** Recibe una notificación cuando el agua está baja.

2. **_Contrato_**

![Notificaciones (contrato)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Notificaciones%20(contrato).PNG)
- **Notificación de saldo de contrato bajo:** Recibe una notificación cuando el saldo de un contrato es bajo.
- **Notificación de saldo de contrato vacío:** Recibe una notificación cuando un contrato no tiene saldo.
- **Notificación de porcentaje de crédito:** Recibe una notificación cuando se alcanza un porcentaje de crédito (haga click en el lápiz para configurar el porcentaje).
- **Notificación de saldo bajo:** Recibe una notificación cuando se alcanza un monto (haga clic en el lápiz para configurar el monto).
- **Depósito de contrato de la compañía:** Recibe una notificación cuando se detecta un depósito a un contrato.

3. **_Identificadores_**

![Notificaciones (Identificacion)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Notificaciones%20(Identificacion).PNG)
- **Notificación de Identificadores en riesgo de caducidad:** Recibe una notificación cuando un identificador está a punto de caducar.

4. **_Fidelidad_**

![Notificaciones (fidelidad)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Notificaciones%20(fidelidad).PNG)
- **Notificación de nueva cuenta de fidelidad:** Recibe una notificación cuando se detecta un nuevo programa de fidelidad.
- **Notificación de acumulación de puntos de fidelidad:** Recibe una notificación cuando se detecta una acumulación.
- **Notificación de excepciones de fidelidad:** Recibe una notificación cuando se detecta una excepción.

5. **_Liquidación_**

![Notificaciones (liquidaciones)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Notificaciones%20(liquidaciones).PNG)
- **Notificación de proceso de liquidación:** Recibe una notificación cuando se detecta un proceso de liquidación.
- **Cargos del comercio:** Recibe una notificación cuando se detectan cargos del comercio.
- **Cargos externos:** Recibe una notificación cuando se detectan cargos externos.

6. **_Transacciones_**

![Notificaciones (transacciones)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Notificaciones%20(transacciones).PNG)
- **Notificación de nuevas transacciones de contingencia:** Recibe una notificación cuando se detecta una nueva contingencia.
- **Notificación de transacción a revisar:** Recibe una notificación cuando se detectó una excepción marcada para ser revisada.
- **Excepción de salida de combustible:** Recibe una notificación cuando se detectó una excepción de salida de combustible.
- **Excepción de transacción:** Recibe una notificación cuando se detecta una excepción.
- **PIN incorrecto:** Recibe una notificación cuando se detecta una transacción rechazada por un PIN incorrecto.
- **Transacción rechazada:** Recibe una notificación cuando se detecta una transacción rechazada.
- **Transacciones impugnadas:** Recibe una notificación cuando se detecta una transacción impugnada.

7. **_Compañía_**

![Notificaciones (compañia)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Notificaciones%20(compa%C3%B1ia).PNG)
- **_Activación/Desactivación de Compañía:_** Recibe una notificación cuando se detecta el cambio en el estado de una compañía.

8. **_Comercio:_**

![Notificaciones (comercio)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Notificaciones%20(comercio).PNG)
- **_Activación/ Desactivación de Comercio:_** Recibe una notificación cuando se detecta el cambio en el estado de un Comercio
- **_Máximo de transacciones Offline del sitio alcanzado:_** Recibe una notificación cuando se detecte que el sitio alcanzo el máximo posible de transacciones Offline.

9. **_Workflow de Flota:_**

![Notificaciones (Workflow de Flota)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Notificaciones%20(Workflow%20de%20Flota).PNG)
- **_Wrokflow de Flota creado:_** Recibe una notificación cuando se detecte que el workflow de flota a sido creado.

### Notificaciones de compañía
En esta sección los usuarios de la compañía pueden configurar sus propias notificaciones (dentro de sus perfiles de compañía en ATIONET).

![Notificaciones Comapañia](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Notificaciones%20Comapa%C3%B1ia.PNG)

1. **_Contrato_**
    - **_Notificación de saldo de contrato bajo:_** Recibe una notificación cuando el saldo de un contrato es bajo.
    - **_Notificación de saldo de contrato vacío:_** Recibe una notificación cuando un contrato no tiene saldo.
    - **_Notificación de porcentaje de crédito:_** Recibe una notificación cuando se alcanza un porcentaje de crédito (haga clic en el lápiz para configurar el porcentaje).
    - **_Notificación de saldo bajo:_** Recibe una notificación cuando se alcanza un monto (haga clic en el lápiz para configurar el monto).
    - **_Depósito de contrato de la compañía:_** Recibe una notificación cuando se detecta un depósito a un contrato.
2. **_Liquidación_**
    - **_Cargos externos:_** Recibe una notificación cuando se detectan cargos externos.
3. **_Transacciones_**
    - **_Excepción de transacción:_** Recibe una notificación cuando se detecta una excepción.
    - **_Autorización de reglas no bloqueantes:_** Recibe una notificación cuando se detecta una autorización de regla no bloqueante.
    - **_Identificación habilitada/deshabilitada:_** Recibe una notificación cuando un identificador fue habilitado/deshabilitado.
    - **_Identificadores solicitados:_** Recibe una notificación cuando se detecta una solicitud de identificación.
    - **_Transacción rechazada:_** Recibe una notificación cuando se detecta una transacción rechazada.
    - **_Transacciones Disputadas:_** Recibe una notificación cuando se detecta una transacción disputada.
4. **_Flota de vehículos_**
    - **_Límite de Odómetro del Vehículo:_** Recibe una notificación cuando se alcanza el odómetro de un vehículo (haga clic en el botón Lista de Vehículos para configurar el odómetro y seleccionar el vehículo asociado a la notificación).
5. **_Compañía_**
    - **_Activación/Desactivación de Compañía:_** Recibe una notificación cuando se detecta el cambio en el estado de una compañía.


## Precios de Distribución
En esta sección puede ver todos los precios de distribución generados. Estos precios se utilizan cuando un contrato de compañía no tiene precios configurados (siempre y cuando la opción de precios de distribución esté habilitada dentro de la configuración del contrato de compañía).
![Precios de distribucion](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Precios%20de%20distribucion.PNG)
1. **_Nuevo Precio de distribución_**
![Precios de distribucion informacion](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Precios%20de%20distribucion%20informacion.PNG)

- **_Nombre:_** Introduzca un nombre para identificar el precio
- **_Código:_** Introduzca un código para identificar el precio
- **_Moneda:_** Introduzca la moneda de cambio deseada
- **_Tipo de agrupamiento:_** Esta opción habilita la posibilidad de configurar también el combustible por **zonas** (estas se crean en el apartado de Administración>Zonas).

2. **_Precios por combustible:_**

![Precios de distribucion Combustible](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Precios%20de%20distribucion%20Combustible.PNG)
- **_Combustible:_** Introduzca los combustibles para los cuales se aplicarán dichos precios
- **_Valor:_** Introduzca el valor de los precios
- **_Fecha y Hora:_** Introduzca la fecha y hora desde la que se comenzara a aplicar dicho precio. (Es opcional configurar una fecha y hora para la cual se deje de aplicar dicho precio)

3. **_Precios por combustible y sitio:_**

![Precios de distribucion Combustible y Sitio](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Precios%20de%20distribucion%20Combustible%20y%20Sitio.PNG)
- **_Combustible:_** Introduzca los combustibles para los cuales se aplicarán dichos precios
- **_Valor:_** Introduzca el valor de los precios
- **_Sitio:_** Introduzca una sitio para el que se apliquen dichos precios.
- **_Fecha y Hora:_** Introduzca la fecha y hora desde la que se comenzara a aplicar dicho precio. (Es opcional configurar una fecha y hora para la cual se deje de aplicar dicho precio)

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

## Procesos de renovacion de Identificadores
En este apartado se pueden visualizar y realizar la renovación de identificadores. En la opción de filtros, se puede filtrar por los estados de ejecución, estados de proceso y los horarios correspondientes en los que se ejecutó el proceso.
![Proceso de renovacion de identificadores](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Proceso%20de%20renovacion%20de%20identificadores.PNG)

- **_Lanzar Proceso:_** Al confirmar este proceso se procederán a renovar identificadores ya existentes de manera masiva.

## Proveedores de Identificadores
En este apartado podrá consultar y crear cualquier proveedor que desee para enviar sus identificadores a producción. Para facilitar las consultas, hay un panel de filtros en la parte superior.
Para crear un proveedor, haga click en el botón **Nuevo**.

![Proveedores de Identificadores](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Proveedores%20de%20Identificadores.PNG)

Los campos por completar son los siguientes:

- **Nombre:** Introduzca el nombre correspondiente al proveedor.
- **Correo electrónico:** Introduzca el correo electrónico de contacto del proveedor.
- **Plantilla de correo electrónico:** Introduzca el cuerpo del correo electrónico que desea enviar a su proveedor.
- **Etiqueta de entrega:** Este campo es opcional. Al marcarlo como activo, aparecerá una opción para cargar un archivo el cual será usado como plantilla.
- **Notificar agrupado:** Al marcar este campo como activo, se anexara al principio del cuerpo del mail un resumen de las configuraciones de agrupados que se ejecutaron en el proceso del planificador de identificadores.
- **Configuración del archivo para la exportación:** Seleccione el formato en el que desea enviar la información de los identificadores a su proveedor. Puede enviarlo como Excel, CSV o Texto. También puede seleccionar qué información enviar en el archivo (Nombre, Apellido, Número de tarjeta, Número de track, etc.).

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

## Sitios
En ATIONET el sitio representa la estación de servicio. Esta sección muestra los sitios ya creados, así como la posibilidad para editarlos y también crear nuevos. A su vez, se pueden añadir impuestos a los sitios directamente desde la columna Opciones. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Sitios Menu](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Sitios%20Menu.PNG)

Para crear un sitio, haga clic en el botón **Nuevo**.

![Sitios Info](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Sitios%20Info.PNG)
Los campos a completar son los siguientes:
**Información**

- **Comercio:** Seleccione el comercio asociado al sitio.
- **Código:** Introduzca un código alfanumérico (cuyo limite son 50 caracteres) el cual estará asociado al sitio.
- **Zona:** Seleccione la zona asociada al sitio.
- **Generado automáticamente:** Marque esta opción para que el **código** se genere automáticamente.
- **Bandera:** Seleccione la bandera asociada al sitio.
- **Idioma:** Seleccione el idioma asociado al sitio.
- **Nombre corto:** Introduzca el nombre corto del sitio.
- **Nombre completo:** Introduzca el nombre completo del sitio.
- **Calle 1:** Introduzca la calle principal del sitio.
- **Calle 2:** Introduzca la calle secundaria del sitio.
- **Industria:** Seleccione la industria asociada al sitio.
- **Zona horaria:** Seleccione la zona horaria correspondiente al sitio.
- **Código postal:** Introduzca el código postal del sitio.
- **Ciudad:** Introduzca la ciudad del sitio.
- **País:** Introduzca el país del sitio.
- **Estado:** Introduzca el estado del sitio.
- **Número de teléfono 1:** Introduzca el número de teléfono principal del sitio.
- **Número de teléfono 2:** Introduzca el número de teléfono secundario del sitio.
- **Requiere mapeo de combustible:** Marque esta opción si es necesario configurar códigos de combustible específicos para el sitio (sino, se utilizará [ATIONet Master Fuel Codes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/C%C3%B3digos%20Maestros%20de%20Combustible.PNG)).
- **Emails de los destinatarios:** Introduzca las direcciones de correo electrónico asociadas al sitio (recibirán los estados de cuenta del sitio).
- **Latitud:** Introduzca la latitud del sitio.
- **Longitud:** Introduzca la longitud del sitio.
- **Moneda:** Seleccione la moneda asociada al sitio.

**Notificación - Regla de Alerta**

- **Notificación de inventario bajo:** Introduzca la cantidad de inventario bajo. Cuando se alcance, los contactos en **correos electrónicos del destinatario** recibirán una notificación.
- **Alerta de notificación de volumen de agua:** Introduzca el volumen de agua bajo. Cuando se alcance, los contactos en **los correos electrónicos de los destinatarios** recibirán una notificación.

**Servicios**

![Sitios servicios](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Sitios%20servicios.PNG)

Seleccione un Sitio para dar de alta. Tras esto, se asignará la lista de servicios que dicho sitio posee y se eliminara el actual. Por su parte, en la pestaña de “Servicios” se puede seleccionar uno de los servicios habilitados para dicho sitio.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.



## SKUs
Las Unidades de Mantenimiento de Stock (SKUs - Stock Keeping Units) son productos no combustibles. En esta sección puede consultar los SKUs creados, editarlos y también crear nuevos. Para facilitar las consultas, hay un panel de filtros en la parte superior. 

![SKU menu](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/SKUs.PNG)

Para crear un SKU, haga clic en el botón **Nuevo**.

![SKU info](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/SKU%20info.PNG)

**Los campos a completar son los siguientes:**

- **Código:** Introduzca un código alfanumérico (cuya capacidad máxima es de 20 caracteres) para el SKU.
- **Descripción:** La descripción del SKU.
- **Descripción corta:** Una versión acortada de la descripción del SKU.
- **Descripción Extra Corta:** Una descripción aún más acortada del del SKU.
- **Tipo de producto de la SKU:** Seleccione el tipo de producto.
- **Producto combustible:** Marque esta opción si el SKU es un producto de combustible.
- **Categoría SKU:** Introduzca la categoría a la que pertenece el SKU.
- **Unidad de medida:** Introduzca la unidad en la que se mide el SKU (Litros, Metro cubico, galones, etc.)
- **Valor referencial por unidad:** Indique el valor y moneda por unidad del producto.
- **Vendible:** Marque esta opción si el SKU es vendible.
- **Pesable:** Marque esta opción si el SKU es pesable.
- **Fraccionable:** Marque esta opción si el SKU es fraccionable.
- **Almacenable:** Marque esta opción si el SKU es almacenable.
- **Consignación:** Marque esta opción si el SKU está en consignación.
- **Disponibilidad Desde/Hasta:** Seleccione las fechas entre las que está disponible el SKU.
- **Es POS:** Marque esta opción si el SKU se vende en el punto de venta.
- **Flota seca:** Marque esta opción si el SKU es un producto seco.
- **Recompensa:** Marque esta opción si el SKU puede ser canjeado por puntos de recompensa.
- **Servicio:** Marque esta opción si el SKU es un servicio.
- **Fidelidad:** Marque esta opción si el SKU acumula puntos.

**Artículos:**

![SKU items e impuestos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/SKU%20items%20e%20impuestos.PNG)

- **Formato del código del POS:** Seleccione el formato del código del punto de venta.
- **Código del POS:** Introduzca un código de punto de venta.

Cuando haya terminado de rellenar estos dos campos, presione el botón **Añadir**.

- **Impuestos:** Introduzca el código de impuestos del SKU.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

</br>


## Terminales / Controladores
Dentro de esta sección puede ver, crear y editar todos los terminales/controladores. El terminal es el punto de venta del sitio y el controlador gestiona los surtidores. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Terminal y Controladores menu](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Terminal%20y%20Controladores%20menu.PNG)

Para crear un Terminal/Controlador, haga clic en el botón **Nuevo**.


![Terminal y Controladores Info](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Terminal%20y%20Controladores%20Info.PNG)

Los campos a completar son los siguientes:

- **Comercio:** Seleccione el comercio asociado al terminal/controlador.
- **Sitio:** Seleccione el sitio asociado al terminal/controlador.
- **Activo:** Marque la casilla para activar/desactivar el terminal/controlador.
- **Tipo de terminal/controlador:** Seleccione el tipo de terminal/controlador (ATIO-ControlGas, ATIO-NanoCPI, ATIO StandAlone, VF-Commander, etc.).
- **Modelo:** Seleccione el modelo de terminal/controlador.
- **Código:** Introduzca el código del terminal/controlador, el cual puede ser un código alfanumérico de hasta 50 caracteres
- (ATIONET genera uno automáticamente, pero puede editarlo. Excepto los 3 primeros caracteres, ya que representan el código de suscripción a la red).
- **Descripción:** Introduzca una descripción correspondiente al terminal/controlador.
- **Solo Pre Autorizaciones Asistidas:** Marque la casilla para activar que la terminal este habilitada para realizar preautorizaciones asistidas.
- **Lector de TAGs presente:** Marque esta opción si el terminal es capaz de leer TAGs.
- **Uso del Id. del Conductor:** Seleccione la acción que ATIONet tomará asociada al Id. del Conductor de las transacciones (Ninguna, Track Secundaria o Validación de Código).
- **Uso de la Identificación del Vehículo:** Seleccione la acción que ATIONet tomará asociada al Id. del Vehículo de las transacciones (Ninguna, Track Secundaria o Validación de Código).
- **Corte de Volumen Máximo:** Introduzca el volumen máximo que el terminal/controlador autorizará.
- **Corte de Importe Máximo:** Introduzca el importe máximo que autorizará el terminal/controlador.
- **Sistema operativo:** Introduzca el sistema operativo del terminal/controlador.
- **Número de serie:** Introduzca el número de serie del terminal/controlador.
- **Encriptación de Track:** Al introducir un valor, la terminal será capaz de reconocer un track encriptado y el mismo será reconocido por ATIONET como un valor si existe. (IMPORTANTE: Para que dicha lectura aplique el modelo de identificador deberá ser configurado con la propiedad correspondiente)

**Configuración**

En esta sección se puede indicar que la terminal operará en el modo fuera línea (con el Local Agent) con la misma configuración que posee estando en línea. 
Campos a completar: Mensaje, Nombre de la Propiedad, Configuración Factor, Configuración Modificador, Tipo de transacción.

Cuando haya terminado de rellenar los campos, presione el botón **Alta** en caso de completar la configuración, y para finalizar **Guardar**.

</br>

## Vehículo
Esta vista muestra todos los vehículos que han sido creados. Recuerde que no es obligatorio cargar los vehículos para poder operar, sólo es necesario si decide asociar las identificaciones a los vehículos. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Vehículos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Veh%C3%ADculos.PNG)

En la columna **Opciones** puede:

* **Asignar Identificadores:** Asignar/desasignar identificadores al vehículo.  
* **Renovación de Identificadores:** Renovar los identificadores asociados al vehículo.
* **Hoja de Servicio:** Establezca el servicio realizado por el vehiculo correspondiente
* **Favoritos:** Añadir el vehículo al módulo de **favoritos**.

## Workflow de Aprovaciones

En este apartado se pueden visualizar las contingencias pendientes de Aprovacion de la seccion de fidelidad.

## Zonas
En esta sección puede crear/editar zonas. Las zonas son áreas a las que se asocian varios sitios. Generalmente un TM (Territory Manager) está asociado a una(s) zona(s) específica(s). Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Zonas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Zonas.PNG)

Para crear una zona, haga clic en el botón **Nuevo**.

![Zonas nuevas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Zonas%20Nueva.PNG)

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

<br>

[Volver al inicio](#contenido) 	:arrow_up:
