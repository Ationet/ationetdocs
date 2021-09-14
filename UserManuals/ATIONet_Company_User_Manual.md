![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

|**Información del Documento**|.|
|--- |--- |
|**Archivo:**|ATIONet_Company_User_Manual-ES.md|
|**Versión Doc:**|1.0|
|**Fecha Liberación:**|14, Sep 2021|
|**Autor:**|ATIONet LLC|


|**Bitácora de Cambios**|||
|--- |--- |--- |
|**Ver.**|**Fecha**|**Resumen de Cambios**|
|1.0|14/Sep/2021|- Versión Inicial  

# Contenido

# Resumen
ATIONet se basa en la premisa de que las comunicaciones en línea entre los sitios y el portal web son posibles, sin embargo, proporciona sólidos procedimientos de contingencia en caso de un error de comunicación.
La plataforma ATIONet es un servicio de gestión de flotas con una oferta innovadora y única en el mercado. Procesamiento en la nube, 100% basado en la web, acceso multiusuario, disponibilidad y compartición de datos, actualizaciones instantáneas, seguridad, copia de seguridad automática y reducción del papeleo.
ATIONet es un portal web para empresas de servicios de flotas que permite el procesamiento de transacciones desde cualquier aplicación de punto de venta a través de una interfaz sencilla y fiable. 
ATIONet puede instalarse en cualquier estación de servicio con uno o varios programas de servicio de flotas. El portal web permite a los gestores de flotas un acceso completo a la información de sus vehículos.
ATIONet hace posible que el gestor de la flota opere, supervise, cambie y edite la información de la flota en tiempo real.


# Definiciones

## Contrato 
El contrato es la relación que existe entre la Network y el cliente, en la que se orienta, por ejemplo, si será de cantidad o volumen, el precio al que se va a vender el combustible, en qué sitios se puede cargar, entre otros.

## Subcuenta
Cada vez que se asocia un identificador a un vehículo o conductor, se crea una subcuenta. La subcuenta es en definitiva quien va a tener una cuenta corriente, la subcuenta va a poder recibir depósitos de dinero o producto. Las reglas también afectan a la subcuenta.
Las subcuentas dependen jerárquicamente del contrato.

## Compañía
En ATIONet la compañía se refiere a la entidad propietaria de la flota. Es la que gestiona los vehículos, los conductores y las reglas de la flota.

## Identificador
El identificador es el medio físico utilizado por ATIONet para identificar un vehículo o conductor. ATIONet soporta varios tipos de identificadores, como tarjeta, TAG, chip, tarjeta ATIONet, entrada manual, código de barras e iButton. Cuando se asocia un identificador a un vehículo o conductor, se crea una subcuenta.

## Sitio
El Sitio representa la estación de servicio. A un sitio se le asigna un terminal/controlador y también puede tener reglas de localización asociadas.

## Vehículo 
Los vehículos pueden estar asociados o agrupados por una flota, pueden tener reglas asociadas y en el momento de relacionarse con un identificador se crea una subcuenta. También pueden tener un conductor asociado.

## Conductor
El conductor en ATIONet es la persona que se identifica como chófer. Si a este conductor se le asigna un identificador, se crea una subcuenta. Los conductores también pueden tener reglas asociadas.

## Terminal
El terminal (o controlador) es la representación del controlador del dispensador, que debe ser parametrizado de forma particular según el tipo de terminal. Los terminales que maneja ATIONet son: ATIO-NanoCPI, ATIO-Standalone, ATIO-CG, VF-Sapphire, VF-Commander, VF-Ruby, ControlGas, entre otros.


# Menú Navegación
ATIONet tiene un menú de acceso rápido situado en la parte izquierda de la web. Desde este menú se puede acceder a diferentes opciones. El menú está dividido en: Tablero, Favoritos, Reportes, Administración, Flotas, Liquidación, Configuración y Bitácora de Auditoria.

# Mis Preferencias
Dentro de esta sección cada usuario puede personalizar sus preferencias del portal.
1. **Rol por Defecto:** Seleccione el rol por defecto al iniciar la sesión.

![Rol por defecto](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Mis%20Preferencias/Rol%20por%20Defecto.PNG)

2. **Imagen de Perfil:** Cambia la imagen de perfil de tu usuario.

![Imagen de perfil](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Mis%20Preferencias/Foto%20de%20Perfil.PNG)

3. **Cambiar la Contraseña:** Cambia la contraseña de tu usuario.

![Cambiar contraseña](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Mis%20Preferencias/Cambio%20Contrase%C3%B1a.PNG)

Para editar su contraseña, haga clic en el enlace ***change password***.

![Cambiar contraseña nueva](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Mis%20Preferencias/Cambio%20Contrase%C3%B1a%20Nuevo.PNG)

4. **Configuración de Widgets:** Selecciona los widgets que se mostrarán en tu panel de control.

![Configuración de widgets](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Mis%20Preferencias/Widgets.PNG)

# Tablero
El Tablero es una página donde tendrás una visión global del funcionamiento de tu Network. El tablero cuenta con widgets específicos que le ayudarán a tomar decisiones preventivas o correctivas en función de la información y los datos que muestran. Los datos que se muestran en el Tablero son datos en tiempo real y algunos de los widgets se actualizan automáticamente.
Estos pueden ser eliminados o añadidos según las necesidades del usuario en la opción **Mis Preferencias**. También se pueden colocar en el tablero según el nivel de visibilidad que se quiera dar a cada uno.
La lista completa de widgets disponibles para las suscripciones a la Network es la siguiente:

## Estado General
Este widget es muy importante a la hora de poner en marcha la Network. Este widget nos da información de los parámetros que necesitamos configurar para estar operativos. Nos avisa cuando, por ejemplo, no tenemos vehículos o identificaciones creadas entre otros parámetros.
Este widget puede mostrar **Avisos** (icono amarillo) cuando el funcionamiento de la red no está en juego, pero si muestra una cruz roja indica que la red no está operativa.

![Estado General](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Estado%20General.PNG)

## Unidades/Mes
Las "Unidades/Mes" indican la cantidad de cada combustible dispensado en el último mes. El último mes son los últimos 30 días desde el día de la fecha. Este widget tiene la capacidad de filtrar por Sitio, Ciudad y Flota. Debe seleccionar el filtro y luego introducir el valor por el que se debe filtrar. Este último campo es de tipo "autocompletado".

![Unidades/Meses](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Unidades-Mes.PNG)

## Transacciones del Día
Este widget contiene un gráfico circular que muestra muy rápidamente cuántas transacciones fueron aprobadas y cuántas fueron rechazadas durante el día.

![Transacciones del Día](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Transacciones%20del%20D%C3%ADa.PNG)

## Lista de Pre-Autorizaciones Pendientes
Este widget de lista muestra todas las pre-autorizaciones que aún no han recibido la finalización de venta. (Para más detalles sobre el flujo de transacciones consulte este [documento]( https://github.com/Ationet/ationetdocs/blob/master/AN-Transaction_Flows-TechGuide.md)).

Muestra 7 columnas:

1. **Código de autorización:** El código de autorización asignado a la transacción.
2. **Compañía:** La empresa a la que pertenece el vehículo en cuestión.
3. **Subcuenta:** La subcuenta que solicitó la pre-autorización.
4. **Sitio:** El sitio donde se realizó la transacción.
5. **Autorizado:** El importe que se autorizó en la pre-autorización.
6. **Pos:** Posición o bomba informada por el punto de venta o controlador.
7. **Age:** El tiempo en minutos que ha estado vigente esta pre-autorización.

Las pre-autorizaciones pendientes deben ser despachos en curso, si hay registros en este widget con una Age alta, significa que el punto de venta o controlador no envió la transacción de finalización o la transacción de cancelación en el caso de que el combustible no haya sido despachado.

![Lista de autorizaciones pendientes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Lista%20de%20Pre-Autorizaciones%20Pendientes.PNG)

## Transacciones Marcadas en el Mes Actual
A continuación se muestran todas las transacciones que fueron rechazadas por alguna de las validaciones realizadas por ATIONet en el proceso de autorización. Ya sea por falta de saldo o por reglas entre otras validaciones.

![Transacciones marcadas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Transacciones%20Marcadas%20en%20el%20Mes%20Actual.PNG)

## Contratos sin Actividad
Muestra la lista de contratos que nunca estuvieron activos.

![Contratos sin actividad](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Contratos%20sin%20Actividad.PNG)

## Transacciones Recientes
A continuación se muestran las últimas 20 transacciones realizadas. Muestra los datos más relevantes para poder identificarla, en caso de necesitar más información sobre la transacción puede pulsar sobre el código de autorización, que le llevará a la vista de detalles de la transacción.

![Transacciones recientes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Transacciones%20Recientes.PNG)

## Listado de Contratos con Bajo Saldo
Muestra la lista de contratos con saldo bajo para operar 4 días más. Este cálculo se basa en el uso. La columna **Días restantes** muestra el número de días que le quedan al contrato basado en el análisis de uso. Este número no es exacto y puede variar si el patrón de uso cambia.

![Listado de Saldo Bajo de Contrato](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Contratos%20con%20Bajo%20Saldo.PNG)

## Actualizaciones de Identificadores del Último Mes
Este widget muestra la actividad de la administración de identificadores, muestra el número de identificadores que fueron modificados agrupados por estado.

1. **Asignado:** El número de identificaciones que cambiaron al estado **Asignado**.
2. **Disponible:** El número de identificadores que cambiaron al estado **Disponible**.
3. **Cancelado:** El número de identificaciones que cambiaron al estado **Cancelado**.
4. **Reportado:** El número de identificaciones que cambiaron al estado **Reportado**.
5. **Suspendido:** El número de identificaciones que han pasado al estado **Suspendido**.

![Actualizaciones de identificadores del último mes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Actualizaciones%20de%20Identificadores.PNG)

## Estado de Terminales
Todos los terminales que están conectados de forma nativa a ATIONet envían un mensaje regular indicando que están activos. Si el terminal informó del estado en las últimas 5 horas, el terminal se mostrará con el icono verde, si no informó en las últimas 5 horas el icono será rojo.
La columna **Edad** muestra el número de minutos transcurridos desde la última vez que se informó del terminal. 

![Estado del terminal](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Estado%20Terminales.PNG)


# Favoritos
Los vehículos, los conductores, los sitios y las flotas son entidades que pueden requerir un seguimiento diario por parte de ciertos usuarios. Para facilitar esta tarea se pueden añadir algunas de estas secciones a la lista de **Favoritos**. Una vez introducida una sección a esta lista, el acceso es más rápido y directo, sin necesidad de introducir filtros cada vez que se quiera buscar.
Una vez dentro de la página de Favoritos, al hacer clic en el enlace de la columna **Tipo**, será redirigido a la vista detallada de esa sección.
Si desea eliminar una sección de la lista de Favoritos, haga clic en el icono de la derecha con forma de cruz.

![Favoritos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Favoritos.PNG)

# Reportes
En ATIONet se consideran reportes aquellos listados de información que van a ser impresos y archivados en formato físico. Cuando se imprimen, ATIONet añade automáticamente una cabecera con el logotipo de la suscripción.

## Conductor
El informe de Conductores se puede filtrar por nombre/código del conductor o por identificador.
Una vez seleccionado el filtro pulse el botón ***Imprimir***, esto mostrará una ventana emergente con la información seleccionada.
La información se muestra en un formato listo para imprimir, incluyendo el logotipo de la suscripción y la fecha y hora de generación del informe.

Esta ventana emergente tiene un botón de impresión que al ser pulsado abre la ventana de impresión por defecto del navegador de Internet.

![Conductores](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Reports/Driver.PNG)

## Detalle de actividad por Vehículo ****


## Transacciones
Este informe muestra la lista de transacciones realizadas, ordenadas por fecha. Este informe tiene varios filtros para ajustar la búsqueda. El primer campo del panel de filtros indica por qué campo se ordenará la lista, el campo seleccionado en esta lista se mostrará en la primera columna.

![Transacciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Reportes/Transacciones%20Filtro.PNG)

Una vez seleccionado el filtro pulse el botón ***Imprimir***, esto mostrará una ventana emergente con la información seleccionada.
La información se muestra en un formato listo para imprimir, incluyendo el logotipo de la suscripción y la fecha y hora de generación del informe.

Esta ventana emergente tiene un botón de impresión que al ser pulsado abre la ventana de impresión por defecto del navegador de Internet.

![Transacciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Reportes/Transacciones.PNG)

## Vehículo
Este informe muestra la lista de vehículos. Este informe dispone de varios filtros para ajustar la búsqueda. El primer campo del panel de filtros indica por qué campo se ordenará la lista, el campo seleccionado en esta lista se mostrará en la primera columna.

![Vehículos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Reportes/Veh%C3%ADculo%20Filtro.PNG)

Una vez seleccionado el filtro pulse el botón ***Imprimir***, esto mostrará una ventana emergente con la información seleccionada.
La información se muestra en un formato listo para imprimir, incluyendo el logotipo de la suscripción y la fecha y hora en que se generó el informe.

Esta ventana emergente tiene un botón de impresión que al ser pulsado abre la ventana de impresión por defecto del navegador de Internet.

![Vehículos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Reportes/Veh%C3%ADculo.PNG)

# Administración
Dentro de este módulo podrá gestionar Compañías, Conductores, Vehículos, Flotas y Notificaciones entre otras cosas.

## Clases de Vehículos
En esta sección podrá ver las clases de vehículo existentes con sus detalles, editarlas y/o crear nuevas.

![Clases de Vehículos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Clase%20de%20Veh%C3%ADculo.PNG)

Para crear una clase de vehículo, haga click en el botón **Nuevo**.

![Clases de Vehículos Nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Clase%20de%20Veh%C3%ADculo%20Nuevo.PNG)

Los campos a completar son los siguientes:
* **Tipo:** Seleccione el tipo de vehículo asociado a la clase de vehículo.
* **Consumo teórico (Distancia * Volumen):** Introduzca el consumo teórico asociado a la clase de vehículo.
* **Marca:** Introduzca la marca asociada a la clase de vehículo.
* **Modelo:** Introduzca el modelo asociado a la clase de vehículo.
* **Kilometraje mínimo:** Introduzca el kilometraje mínimo asociado a la clase de vehículo.
* **Kilometraje máximo:** Introduzca el kilometraje máximo asociado a la clase de vehículo.
<br>
* **Combustibles:** Seleccione el combustible asociado a la clase de vehículo.
	* ***Capacidad del tanque:*** Introduzca la capacidad del tanque para cada combustible agregado.

## Compañías
En ATIONet el término compañías se refiere a la entidad propietaria de la flota. En esta sección puedes ver los detalles de su compañía.

![Compañías](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Compa%C3%B1%C3%ADas.PNG)

## Conductores
En esta sección podrá ver los conductores existentes con sus detalles, editarlos y/o crear nuevos. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Conductores](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Conductores.PNG)

Desde esta vista tiene algunos atajos rápidos bajo la columna **Opciones**:
* **Asignar Identificadores:** Seleccione el contrato y el identificador a asignar al conductor.
* **Asignar Regla:** Asigne o cree una regla de flota al conductor.
* **Eliminar:** Solo se pueden eliminar conductores que no tienen ningún tipo de actividad dentro ATIONet.
* **Habilitar/Deshabilitar:** Confirme si desea habilitar/deshabilitar el conductor.

Para crear un conductor, haga clic en el botón **Nuevo**.

![Conductores Nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Conductores%20Nuevo.PNG)

Los campos a completar son los siguientes:
* **Código:** Introduzca el código único asociado al conductor.
* **Generado Automáticamente:** Marque esta opción para que el código se genere automáticamente.
* **Apellido:** Introduzca el apellido del conductor.
* **Nombre:** Introduzca el nombre del conductor.
* **Licencia:** Introduzca la licencia del conductor.
* **Lic. País:** Introduzca el país asociado a la licencia.
* **Lic. Provincia:** Introduzca la provincia asociada a la licencia.
* **Teléfono 1:** Introduzca el número de teléfono principal del conductor.
* **Teléfono 2:** Introduzca el número de teléfono secundario del conductor.
* **Correo:** Introduzca el correo electrónico del conductor.
* **Fecha de Nacimiento:** Introduzca la fecha de nacimiento del conductor.
* **Ciudad:** Introduzca la ciudad del conductor.
* **Cod. Postal:** Introduzca el código postal del conductor.
* **Calle:** Introduzca la calle principal del conductor.
* **Calle 2:** Introduzca la calle secundaria del conductor.
<br>
* **Vehículos:** Seleccione el vehículo asociado al conductor.
<br>
* **Reglas:** Seleccione la regla asociada al conductor.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

Para creación masiva de Conductores, presione el botón **Importar**. Aquí podrá descargar la planilla a cargar con los datos de conductores, seleccionar **Solicitar Identificaciones** (si necesario) y seleccionar el archivo a importar.

![Conductores Importar](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Condcutores%20Importar.PNG)

Cuando haya terminado de rellenar los campos, presione el botón **Importar**.

### Solicitud de Identificadores – Conductor
Desde esta misma vista se puede realizar el proceso de **Solicitud de Identificadores** para conductores. Para ello debe:

1. Seleccionar los conductores a los cuales desea realizar el procedimiento de solicitud de identificadores.
2. Presionar el botón **Acciones en Lote** y escoger **Seleccionado**.
3. En la nueva ventana deberá completar los siguientes datos:
	* **Contrato:** Seleccione el contrato asociado al identificador.
	* **Tipo:** Seleccione el tipo del identificador.
	* **Modelo:** Seleccione el modelo del identificador.
	* **Programa:** Seleccione el programa de flota del identificador.
4. Haga click en **Solicitar Identificadores** y confirme los conductores.

Cuando haya terminado de rellenar los campos, presione el botón **Confirmar**.

![Solicitud de Identificadores - Conductor](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Solicitud%20de%20Identificadores%20-%20Conductor.PNG)

## Dispersión****
## Documentos Externos****

## Flotas
En ATIONet la flota se refiere al grupo de vehículos dentro de una Compañía. En esta sección podrá ver las flotas existentes, editarlas y/o crear nuevas.

![Flotas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Flotas.PNG)

Para crear una flota, haga click en el botón **Nuevo**.

![Flotas nueva](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Flotas%20Nueva.PNG)

Los campos a completar son los siguientes:
* **Código:** Introduzca el código único de la flota.
* **Generado Automáticamente:** Marque esta opción para que el código se genere automáticamente.
* **Nombre:** Introduzca el nombre asociado a la flota.
<br>
* **Reglas:** Seleccione la regla asociada a la flota.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

## Notificaciones
En esta sección los usuarios de la compañía pueden configurar sus propias notificaciones.

![Notificaciones Compañía](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Notificaciones%20Compa%C3%B1%C3%ADas.PNG)

1. ***Contrato***
   * **Notificación de contrato con saldo bajo:** Recibe una notificación cuando el saldo de un contrato es bajo.
   * **Notificación de contrato sin saldo:** Recibe una notificación cuando un contrato no tiene saldo.
   * **Notificación porcentual de crédito:** Recibe una notificación cuando se alcanza un porcentaje de crédito (haga clic en el lápiz para configurar el porcentaje).
   * **Notificación bajo saldo por monto:** Recibe una notificación cuando se alcanza un monto (haga clic en el lápiz para configurar el monto).
   * **Depósito en contrato de compañía:** Recibe una notificación cuando se detecta un depósito a un contrato
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

## Sitios
En esta vista se listan los sitios que han sido creados. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Sitios](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Sitios.PNG)

Desde aquí también puede visualizar los sitios directamente desde un mapa interactivo. Para ello, haga click en el ícono del **pin**. Esta funcionalidad de búsqueda de sitios abre un mapa interactivo. En este mapa se indica una dirección, lo cual señalará los sitios en un radio cercano a la ubicación seleccionada.

![Sitios Mapa](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Sitios%20Mapa.PNG)

## Usuarios
En esta sección puede ver, crear o editar usuarios para la Compañía. Puede editarlos haciendo click en el ícono del lápiz en la columna de opciones, activar/desactivar un usuario haciendo click en el ícono del candado y restablecer la contraseña con el ícono del asterisco.

![Usuarios](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Usuarios.PNG)

Para crear un usuario, haga clic en el botón **Nuevo**.

![Usuarios nuevos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Usuarios%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Correo del usuario:** La dirección de correo electrónico del usuario.
* **Nombre:** El nombre del usuario.
* **Documento:** El documento del usuario.
* **Calle 1:** La calle donde reside el usuario.
* **Calle 2:** Otra calle de referencia, como puede ser la de la esquina.
* **País:** El país del usuario.
* **Estado:** El estado del país del usuario.
* **Código postal:** El código postal de la localidad donde reside el usuario.
* **Número de teléfono 1:** El teléfono del usuario.
* **Número de teléfono 2:** El otro teléfono del usuario si está disponible.
<br>
* **Rol:** El rol que asumirá el nuevo usuario.
* **Entidad:** La entidad asignada al usuario.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

## Vehículos
En esta sección podrá ver los vehículos existentes con sus detalles, editarlos y/o crear nuevos. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Vehículos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Veh%C3%ADculos.PNG)

Desde esta vista tiene algunos atajos rápidos bajo la columna **Opciones**:
* **Asignar Identificadores:** Seleccione el contrato y el identificador a asignar al vehículo.
* **Asignar Regla:** Asigne o cree una regla de flota al vehículo.
* **Eliminar:** Solo se pueden eliminar vehículos que no tienen ningún tipo de actividad dentro ATIONet.
* **Habilitar/Deshabilitar:** Confirme si desea habilitar/deshabilitar el vehículo.

Para crear un vehículo, haga clic en el botón **Nuevo**.

![Vehículos Nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Veh%C3%ADculos%20Nuevo.PNG)

Los campos a completar son los siguientes:
* **Código:** Introduzca el código único asociado al vehículo.
* **Flota:** Seleccione la flota asociada al vehículo.
* **Patente:** Introduzca la patente del vehículo.
* **Clase de vehículo:** Seleccione la clase de vehículo.
* **Tipo:** Seleccione el tipo de vehículo.
* **Año:** Introduzca el año del vehículo.
* **Marca:** Introduzca la marca del vehículo.
* **Modelo:** Introduzca el modelo del vehículo.
* **Sub-Modelo:** Introduzca el sub-modelo del vehículo.
* **Color:** Introduzca el color del vehículo.
* **Tipo de servicio:** Seleccione el tipo de servicio asociado al vehículo.
* **Descripción de servicio:** Introduzca una breve descripción del servicio asociado al vehículo.
* **Número motor:** Introduzca el número de motor del vehículo.
* **Número chasis:**Introduzca el número de chasis del vehículo.
* **Odómetro inicial:** Introduzca el odómetro inicial del vehículo.
* **Odómetro actual:** Introduzca el odómetro actual del vehículo.
* **Fecha de último odómetro:** Introduzca la fecha del último odómetro del vehículo.
* **Horas de motor actuales:** Introduzca las horas de motor actual del vehículo.
* **Fecha de última hora de motor:** Introduzca la fecha de las últimas horas de motor del vehículo.
<br>
* **Conductores:** Seleccione el conductor asociado al vehículo.
<br>
* **Reglas:** Seleccione la regla asociada al vehículo.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

Para creación masiva de vehículos, presione el botón **Importar**. Aquí podrá descargar la planilla a cargar con los datos de vehículos, seleccionar **Solicitar Identificaciones** (si necesario) y seleccionar el archivo a importar.

![Vehículos Importar](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Veh%C3%ADculos%20Importar.PNG)

Cuando haya terminado de rellenar los campos, presione el botón **Importar**.

### Solicitud de Identificadores – Vehículo
Desde esta misma vista se puede realizar el proceso de **Solicitud de Identificadores** para vehículos. Para ello debe:

1. Seleccionar los vehículos a los cuales desea realizar el procedimiento de solicitud de identificadores.
2. Presionar el botón **Acciones en Lote** y escoger **Seleccionado**.
3. En la nueva ventana deberá completar los siguientes datos:
	* **Contrato:** Seleccione el contrato asociado al identificador.
	* **Tipo:** Seleccione el tipo del identificador.
	* **Modelo:** Seleccione el modelo del identificador.
	* **Programa:** Seleccione el programa de flota del identificador.
4. Haga click en **Solicitar Identificadores** y confirme los vehículos.

Cuando haya terminado de rellenar los campos, presione el botón **Confirmar**.

![Solicitud de Identificadores - Vehículos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Solicitud%20de%20Identificadores%20-%20Veh%C3%ADculo.PNG)

# Flotas
Dentro de este módulo se pueden gestionar los Contratos de Compañía, Cuentas Corrientes, Reglas de flota y las Transacciones entre otras cosas.

## Autorizaciones Pendientes
En ATIONet las autorizaciones pendientes son aquellas operaciones que aún no han recibido la transacción de finalización, pero que han sido preautorizadas. La información que se ve en esta vista son los despachos que están actualmente en curso. Si por alguna razón hay preautorizaciones antiguas, es probable que el TPV no haya enviado la transacción de finalización o la transacción de cancelación si el despacho no se ha completado.

Tenga en cuenta que, en el momento de la preautorización, ATIONet congeló el importe de la autorización de la cuenta corriente para la subcuenta asociada. Esta vista presenta todos los campos necesarios para identificar la transacción y la subcuenta. Si necesita ver más detalles, al hacer clic en el código de autorización accederá a la vista de detalles de la transacción.

![Autorización pendiente](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Autorizaciones%20Pendientes.PNG)

## Contratos de Compañía
En ATIONet el término compañía se refiere a la entidad que gestiona la flota. En esta sección podrá consultar todos los contratos de su compañía. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Contratos de Compañía](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contratos%20de%20Compa%C3%B1%C3%ADa.PNG)

## Cuentas Corrientes de Compañía
La sección de Cuentas Corrientes de Compañía es la vista del saldo disponible de las subcuentas y/o contratos, y también la vista de todos los movimientos de las subcuentas y/o contratos.

Para facilitar las consultas, hay un panel de filtros disponible. La primera opción del panel de filtros es el tipo de informe:

![Cuentas Corrientes de la Compañía](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Cuentas%20Corrientes%20de%20Compa%C3%B1%C3%ADa.PNG)

1. **Lista de Contratos:** Esta opción lista todos los contratos con sus respectivos saldos, pero no da detalles de los movimientos.

![Cuentas Corrientes de Compañía - Lista de Contratos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Cuentas%20Corrientes%20de%20Compa%C3%B1%C3%ADa%20-%20Lista%20de%20Contratos.PNG)

2. **Movimientos de Contratos:** Esta opción muestra todos los movimientos de los contratos.

![Cuentas Corrientes de Compañía - Movimientos de Contratos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Cuentas%20Corrientes%20de%20Compa%C3%B1%C3%ADa%20-%20Movimientos%20de%20Contratos.PNG)

3. **Lista de Subcuentas:** Esta opción lista todas las subcuentas con sus respectivos saldos, pero no da detalles de los movimientos.

![Cuentas Corrientes de Compañía - Lista de Subcuentas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Cuentas%20Corrientes%20de%20Compa%C3%B1%C3%ADa%20-%20Lista%20de%20Subcuentas.PNG)

4. **Movimientos de Subcuentas:** Esta vista lista todos los movimientos de las subcuentas.  

![Cuentas Corrientes de Compañía - Movimientos de Subcuentas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Cuentas%20Corrientes%20de%20Compa%C3%B1%C3%ADa%20-%20Movimientos%20de%20Subcuentas.PNG)

<br>

Para realizar un movimiento de cuenta corriente, haga click en el botón **Nuevo**.

Los campos a completar son los siguientes:

* **Descripción:** Introduzca una breve descripción del movimiento.
* **Contrato:** Seleccione el contrato asociado al movimiento (solo contratos de tipo **Disperso** podrán seleccionarse).
* **Tipo:** Seleccione el tipo de movimiento.
  * ***Transferencia de fondos de contrato a subcuenta:*** Indique la subcuenta a la cual se depositará el monto ingresado.

![Cuenta Corriente Movimiento 1](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Flota/Cuenta%20Corriente%20Movimiento%201.PNG)

  * ***Transferencia de fondos de subcuenta a contrato:*** Indique la subcuenta a la cual se le retirará el monto ingresado.

![Cuenta Corriente Movimiento 2](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Flota/Cuenta%20Corriente%20Movimiento%202.PNG)

  * ***Transferencia de fondos de subcuenta a subcuenta:*** Indique la subcuenta a la cuál se le retirará el monto ingresado y también la subcuenta a la cual se le depositará el monto ingresado.

![Cuenta Corriente Movimiento 3](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Flota/Cuenta%20Corriente%20Movimiento%203.PNG)

## Cuotas por Vehículo / Conductor
En esta vista se listan los vehículos/conductores de la Compañía y sus respectivas cuotas. Para facilitar las consultas, hay un panel de filtros en la parte superior

![Cuotas por Vehículo/Conductor](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Flota/Cuotas%20por%20veh%C3%ADculo-conductor.PNG)

## Excepciones
ATIONet separa las transacciones no autorizadas en 2 secciones: **Excepciones** y [Transacciones Rechazadas] (#transacciones-rechazadas). Las excepciones son aquellas transacciones que no pasaron las validaciones duras del sistema o las que se detectan como posibles fraudes.

![Excepciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Excepciones.PNG)

En esta vista, al principio se puede filtrar por el tipo de excepción. Los tipos de excepciones disponibles son los siguientes:

![Excepciones Filtros](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Excepciones%20Filtros.PNG)

## Facturas****

## Identificaciones Solicitadas
En este apartado podrá consultar las identificaciones solicitadas. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Identificaciones Solicitadas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Flota/Identificaciones%20Solicitadas.PNG)

Desde esta sección podrá confirmar la recepción de las solicitudes de identificadores realizadas, para finalizar el proceso de solicitud. Tenga en consideración que las únicas ordenes que puede confirmar, son las que ya fueron marcadas como **Entregada**.
Para cambiar el estado de los identificadores solicitados, haga clic en el botón **Acción en Lote** y seleccione la opción **Confirmar la entrega de identificaciones**.

## Reglas
En ATIONet las reglas se refieren a los límites que pueden ser configurados. Dentro de esta vista se pueden consultar, crear o editar reglas. Existen diferentes tipos de reglas: Cuota, Rango de Fechas, Ubicación, Combustible, Límite por Transacciones, DíasHora, Solicitud, Límite de Transacciones Secas y Límite de Cuotas Secas.

Tenga en cuenta que todas las reglas pueden ser **No Bloqueantes**, lo que significa que ATIONet no rechazará la transacción, aunque se cumplan los parámetros configurados.

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

## Rendimiento por Transacción****

## Rendimiento por Vehículo****

## Transacciones
La vista de transacciones es una de las más importantes en ATIONet. En esta vista puede ver todas las transacciones exitosas.

El panel de filtro tiene todos estos campos disponibles:

![Trasacciones - Filtro](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Filtros.PNG)

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

Una vez que haya filtrado, haga clic en ***Búsqueda*** y se listarán las transacciones que cumplen con el filtro.

![Transacciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones.PNG)

Si quiere ver el detalle de la transacción, presione sobre el **Código de Autorización** y esto le llevará a una vista detallada de la transacción.

![Transacciones Detalles](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Detalles.PNG)

Desde esta sección también puede comenzar el proceso de **Disputa** de transacciones. Para ello debe seleccionar la opción de **Desconocer** bajo la columna de **Opciones**. Esto abrirá una ventana emergente en la cual debe seleccionar el motivo e ingresar un comentario sobre la disputa.

![Disputa de Transacciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Flota/Desconocer%20Transacciones.PNG)

## Transacciones Desconocidas
En esta sección se pueden consultar las transacciones que fueron desconocidas; listadas por código, fecha, motivo, estado, número de transacción, compañía, sitio. También está el comentario de la compañía, del comercio y de la network.

![Transacciones desconocidas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Desconocidas.PNG)

## Transacciones Despachadas
En esta sección puede ver todas las transacciones en las que hubo combustible dispensado.

![Transacciones Despachadas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Despachadas.PNG)
 
## Transacciones ERP****

## Transacciones por Conductor
En esta vista puede ver las transacciones agrupadas por el conductor que las realizó. Los botones de la parte superior izquierda sirven para imprimir la tabla o crear un archivo Excel a partir de la misma, respectivamente.

![Transacciones por Conductor](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20por%20Conductor.PNG)

## Transacciones por Flota
En esta vista puede ver las transacciones agrupadas por la flota que las realizó. Los botones de la parte superior izquierda sirven para imprimir la tabla o crear un archivo Excel a partir de la misma, respectivamente.

![Transacciones por Flota](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20por%20Flota.PNG)

## Transacciones por Vehículo
En esta vista puede ver las transacciones agrupadas por el vehículo que las realizó. Los botones de la parte superior izquierda sirven para imprimir la tabla o crear un archivo Excel a partir de la misma, respectivamente.

![Transacciones por Vehículo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20por%20Veh%C3%ADculo.PNG)

## Transacciones Rechazadas
ATIONet separa las transacciones no autorizadas en 2 secciones: [Excepciones](#excepciones) y **Transacciones Rechazadas**.

Las Transacciones Rechazadas son aquellas que lograron pasar las autenticaciones duras de ATIONet, pero fueron rechazadas por otras validaciones como una regla insatisfecha o una validación de saldo.

![Transacciones Rechazadas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Rechazadas.PNG)

En esta vista, al principio se puede filtrar por el tipo de rechazo. Los tipos de rechazo disponibles son los siguientes:

![Transacciones Rechazadas Filtros](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Rechazadas%20Filtros.PNG)

# Liquidaciones

## Cargos Externos****

## Documentos de Cargo
En esta sección podrá ver todos los conceptos aplicados agrupados por estado de cuenta. Si hace clic en el código, le redirigirá al detalle del mismo.

![Documentos de Cargo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Liquidaciones/Documentos%20de%20Cargo.PNG)

## Documentos de Liquidaciones
En esta sección se pueden ver todos los estados de registro de los documentos de liquidación solicitados. Los estados posibles son: Pendiente, Procesando, Finalizado o Finalizado con errores.

![Documentos de Liquidaciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Liquidaciones/Documentos%20de%20Liquidaciones.PNG)

## Estados de Cuenta
En esta sección podrá ver y descargar los estados de cuenta de su Network. También puede generar los estados de cuenta en .pdf uno a uno, o dentro de la **Acción en Lote** generar un paquete.

![Estados de Cuenta](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Liquidaciones/Estados%20de%20Cuenta.PNG)

## Items Liquidados
En esta sección puede ver los conceptos aplicados para cada estado de cuenta.

![Liquidación](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Liquidaciones/Items%20Liquidados.PNG)

# Bitácora

## Bitácora de Auditoría
En esta sección puede ver una lista de todas las acciones realizadas por todos los usuarios. Hay un panel de filtros en la parte superior para facilitar las consultas.

![Bitácora de Auditoría](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Bitacora/Bitacora%20de%20Auditoria.PNG)
