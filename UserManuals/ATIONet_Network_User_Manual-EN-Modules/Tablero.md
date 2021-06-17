![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

# Contenido

- [Tablero](#tablero)
	- [Estado General](#estado-general)
	- [Unidades/Mes](#unidades-/-mes)
	- [Transacciones del Día](#transacciones-del-día)
	- [Lista de Pre-Autorizaciones Pendientes](#lista-de-pre---autorizaciones-pendientes)
	- [Transacciones Marcadas en el Mes Actual](#transacciones-marcadas-en-el-mes-actual)
	- [Contratos sin Actividad](#contratos-sin-actividad)
	- [Transacciones Recientes](#transacciones-recientes)
	- [Listado de Contratos con Bajo Saldo](#listado-de-contratos-con-bajo-saldo)
	- [Actualizaciones de Identificadores del Último Mes](#actualizaciones-de-identificadores-del-último-mes)
	- [Estado de Terminales](#estado-de-terminales)


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
5. 5. **Suspendido:** El número de identificaciones que han pasado al estado **Suspendido**.

![Actualizaciones de identificadores del último mes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Actualizaciones%20de%20Identificadores.PNG)

## Estado de Terminales

Todos los terminales que están conectados de forma nativa a ATIONet envían un mensaje regular indicando que están activos. Si el terminal informó del estado en las últimas 5 horas, el terminal se mostrará con el icono verde, si no informó en las últimas 5 horas el icono será rojo.
La columna **Edad** muestra el número de minutos transcurridos desde la última vez que se informó del terminal. 

![Estado del terminal](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Estado%20Terminales.PNG)
