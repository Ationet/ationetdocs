![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|**Información del Documento**|.|
|--- |--- |
|**Archivo:**|ATIONet-Local_Agent_Product_Description-ES.md|
|**Versión del Doc.:**|1.0|
|**Fecha de Publicación:**|02, Julio 2021|
|**Autor:**|ATIONet LLC|


|**Registro de Cambios**|||
|--- |--- |--- |
|**Ver.**|**Fecha**|**Resumen de Cambios**|
|1.0|02/Jul/2021|- Versión Inicial



# Contenido

- [Información General](#información-general)
- [Procesamiento de Transacciones](#procesamiento-de-transacciones)
- [Reconexión a ATIONet](#reconexión-a-ationet)
- [Reglas y Validaciones](#reglas-y-validaciones) 



# **Información General**

Local Agent es un producto que nos permite configurar en un equipo dentro de una estación, un ambiente para continuar operando, aunque presentemos problemas de conectividad en la estación y no contemos en ese momento conexión con ATIONet.

El producto cuenta con la lógica de autorización implementada en ATIONet, para el despacho de combustibles. A su vez, el mismo en su última versión permite ser utilizado con protocolo Nativo y con protocolo Payware.

En el caso de contar con conectividad, será Ationet el encargado de procesar la autorización y proveer la respuesta necesaria para el despacho. En caso de perder conectividad, el LocalAgent cumplirá con tal fin, de manera transparente en el proceso, procesando la transacción y guardando la información pertinente de manera local, para ser enviada a Ationet al momento de recuperar la conexión.

# **Procesamiento de Transacciones**

A continuación, se adjunta un gráfico explicativo del flujo que realiza LocalAgent a la hora de determinar de qué manera será procesada la transacción:

![Procesamiento de Transacciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Local%20Agent/Procesamiento%20Transacciones.png)

1. La trama llega desde la terminal/controladora al LocalAgent.
2. Se valida la conexión a Ationet
    a. En caso de que haya conexión: LocalAgent envía la trama y es procesada por ATIONet, quien se encarga de generar la respuesta de la operatoria.
    b. En caso de que no haya conexión: LocalAgent se encarga de determinar si es factible procesar la trama de manera offline, caso afirmativo el Motor de Procesamiento Offline se encargará de realizar el procesamiento de la misma, generando la respuesta de la operatoria.
3. La respuesta generada es enviada a la controladora que generó la petición.

# **Reconexión a ATIONet**

Al momento de recuperar conexión con ATIONet, el LocalAgent realiza dos procesos:

1. Descarga las novedades que se hayan generado para poder continuar operando offline con la información más actualizada posible.
2. Sube a ATIONet las transacciones que hayan sido procesadas de manera Offline.

A continuación, se adjunta un gráfico explicativo del flujo que realiza LocalAgent a la hora de recuperar la conexión:

![Reconexión a ATIONet](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Local%20Agent/Reconexi%C3%B3n%20ATIONet.png)

1. El LocalAgent ejecuta un proceso que evalúa el estado de conexión con ATIONet
  1. Si continúa sin conexión, mantiene su status Offline y continúa operando de esta manera.
  2. Si detecta que posee conexión nuevamente:
    1. Solicita las novedades que hayan podido surgir durante el período que se encuentra offline.
    2. Descarga las novedades de ATIONet y aplica esas novedades.
    3. Evalúa si hay transacciones procesadas offline durante el período que estuvo sin conexión. Caso afirmativo, envía las novedades a ATIONet.

# **Reglas y Validaciones**

El producto contempla la aplicación de ciertas reglas del mismo modo que el host cloud de ATIONet, pero no contempla el 100% de las mismas, el motivo es que al ser un autorizador local no se puede replicar la misma cantidad de información que se tiene al nivel del host en el LocalAgent, ya que esto afectaría la cantidad de datos administrados de forma local con el correspondiente impacto de requerimiento de servidor, y la cantidad de tráfico que sería necesario considerar entre el servidor local y el host de ATIONet.

Se debe tener en cuenta que todas las reglas que se mencionan en el presente documento son reglas que se aplican a subcuentas, el LocalAgent baja toda la configuración de reglas a nivel de subcuenta y no de vehículo o conductor, para de esta manera simplificar el volumen de información que debe ser sincronizada. Esto implica que toda regla configurada a una flota, vehículo o conductor que no tenga asociada una subcuenta, no va a poder aplicarse.

A continuación, se detallan las reglas que son aplicadas en el LocalAgent:

- ***DateTime:*** Valida que la transacción sea hecha entre las fechas establecidas. Podría haber más de una regla de este tipo y rechazaría con que solo una le impida, a pesar de que haya otra que sí le permita. La lógica actual descarga los valores de la regla como enteros y convierte la fecha de validación a uno para luego compararlos.
- ***Location:*** Valida que la transacción sea hecha por cualquiera de las terminales permitidas. Al no existir el concepto de sitio en LocalAgent, la regla obtiene todas las terminales que pertenezcan a los sitios de la regla.
- ***Fuel:*** Valida que la transacción haya sido realizada con alguno de los combustibles configurados.
- ***TransactionsLimit:*** Limita los máximos de la transacción en volumen o monto.
- ***DaysTime:*** Valida que la transacción sea hecha entre los horarios y los días establecidos. Todavía tiene el formato viejo, que limita los mismos horarios sin importar el día.
- ***Quota:***
  - **Diaria/Semanal/Mensuales/Quincenal:** Se utiliza el valor de la regla cargado en ATIONet, repartido equitativamente entre las unidades de la periodicidad. Ejemplo, 10 pesos repartidos entre 5 días, resultan en una regla de 2 pesos por día.
  - **Días / Horas:** Se aplica la regla de días / horas para habilitar el despacho de combustible.
  - **Actuales y próximos:** Se descarga el valor resultante del cálculo mencionado en el punto anterior, y se coloca como actual y próximo. Al valor actual se le resta lo consumido durante el periodo designado. En caso de permanecer offline el tiempo suficiente para cumplir con los tiempos de la cuota, se comenzará a utilizar el valor próximo.
  - **Anuales:** Las cuotas anuales en realidad se consideran como cuotas mensuales repartidas equitativamente entre los 12 meses.
  - **Globales:** Offline existe el concepto de cuota global (sin periodicidad) que se valida siempre primero antes de las otras cuotas. Actualmente en ATIONet no hay manera de cargar una cuota sin periodicidad, por lo cual este concepto queda deprecado.
- ***Prompting:***
  - VehiclePIN, DriverPIN, DriverId, VehicleId, Miscellaneous, Odometer, EngineHours, TruckUnitNumber, TrailerNumber.
  - Se valida variación de Odómetro, pero no de Horas de Motor.
***Validaciones:***
- **Active:** Identifications.
- **Enabled:** Vehicle &amp; Driver.
- **ExpirationDate:** Identifications &amp; CompanyContracts.
- **SiteValidation:**  Sólo permite despachar de los sitios indicados por el contrato.
- **FuelValidation:** Si el contrato es de productos, solo permite despachar de los que estén configurados.
- **Driver/Vehicle Relationships:** Solo permite despachar a los Drivers o Vehicles que hayan identificado a un Vehicle o Driver relacionado, respectivamente. No se permite relacionar dos entidades iguales.
- **CodeValidation:** Según lo indicado en la terminal, se utilizará el DriverId o VehicleId como validación de código.
- **SecondaryTrack:** Según lo indicado en la terminal, se utilizará el DriverId o VehicleId como Track Secondario.
- **VehicleClass:**  Solo permite despachar los combustibles indicados en la clase del vehículo. También lo utiliza como sugerencia si es posible.
- **FastTrack:** Permite la utilización de FastTrack y lleva registro de su saldo.
- **PriceChange:** Si la terminal lo permite, se realiza el cambio de precio según lo que diga el contrato. Son válidos los precios por Site. **NO SE APLICAN DESCUENTOS.**
- **BalanceMode:** Respeta la distribución de saldos de los contratos y programas.
- **ProductAndMoney:** Permite la autorización por múltiple especie y sus limitantes según lo indique el modo de autorización de la terminal.
- **OfflineLimits:** Permite la limitación de valores de forma porcentual. Siempre aplican a lo último antes de responder la autorización.
