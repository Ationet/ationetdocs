![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|**Información del Documento**|.|
|--- |--- |
|**Archivo:**|StandAlone_v240m_Terminal_ES.md|
|**Versión del Doc.:**|1.0|
|**Fecha de Publicación:**|28, Noviembre 2024|
|**Autor:**|ATIONet LLC|

</br>

|**Registro de Cambios**|||
|--- |--- |--- |
|**Ver.**|**Fecha**|**Resumen de Cambios**|
|1.0|28/Nov/2024|- Versión Inicial

# StandAlone Verifone V240m
 

## Inicio
En la pestaña principal se puede encontrar botones con distintas funcionalidades. Estos son: 

  - Pre-Authorization
  - Confirmation
  - Clear Pending Pre-Authorizations
  - Sale
  - Balance Enquiry
  - Loyalty
  - Maintenance
  - Pagos QR

 -![Home](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_Home.jpg)

### Pre-autorización
Al seleccionar esta opción se le pedirá que presente un identificador. El identificador podrá ser cualquier método como pasar una tarjeta, scanear un QR, escribir manualmente el track de identificador, etc.

Una vez se le proporciono un identificador, se deberá seleccionar el combustible entre uno de los disponible. 

En caso de que el parámetro “Default prompt” ubicado en mantenimiento -> configuración -> Parámetros -> ATIONET este activo, entonces también se le pedirá que ingrese otro tipo de información como PIN, Odómetro, etc. 

Luego, dependiendo de reglas establecidas es posible que se haga un “re-prompteo” obligando a enviar información necesaria faltante. Cuando se envié toda esa información y dependiendo de las reglas establecidas, saldo del contrato, etc. Entonces la pre-autorización será autorizada o no En caso de que sea rechazada, se le mostrara en la pantalla el motivo.

Por último, se imprimirá el ticket correspondiente y le dará la opción de imprimir un segundo ticket para el cliente.

 -![Pre-Auth](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_preauth.jpg)


 

### Confirmación
Al seleccionar esta opción se le pedirá que presente un identificador. El identificador deberá de ser el mismo del usado previamente al realizar la pre-autorización.

Una vez se le proporciono el identificador, se deberá indicar el monto de la transacción (el mismo deberá de ser menor o igual a la cantidad autorizada en el pre).

 En caso de que sea rechazada, se le mostrara en la pantalla el motivo.

Luego se imprimirá el ticket correspondiente y le dará la opción de imprimir un segundo ticket para el cliente.


 -![completion](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_Completion.jpg)


### Borrar Pre-Autorizaciones Pendientes
Al seleccionar esta opción se le pedirá que presente un identificador. 

En caso de que dicho identificador tenga alguna pre-autorización aun pendiente, entonces se realizara un completion con monto 0 para eliminar la pre-autorización.  Luego se imprimirá el ticket correspondiente y le dará la opción de imprimir un segundo ticket para el cliente.

En caso de que no haya pre-autorizaciones para dicho identificador, entonces se mostrara un mensaje que indica esto.

 -![Clear-Pending-Pre](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_Clear-Pending-Pre.jpg)
 

### Venta
Al seleccionar esta opción se le pedirá que presente un identificador. El identificador podrá ser cualquier método como pasar una tarjeta, scanear un QR, escribir manualmente el track de identificador, etc.

Una vez se le proporciono un identificador, se deberá seleccionar el combustible entre uno de los disponibles y un monto o volumen. 

En caso de que el parámetro “Default prompt” ubicado en mantenimiento -> configuración -> Parámetros -> ATIONET este activo, entonces también se le pedirá que ingrese otro tipo de información como PIN, Odómetro, etc. 

Luego, dependiendo de reglas establecidas es posible que se haga un “re-prompteo” obligando a enviar información necesaria faltante. Cuando se envié toda esa información y dependiendo de las reglas establecidas, saldo del contrato, etc. Entonces la venta será autorizada o no. En caso de que sea rechazada, se le mostrara en la pantalla el motivo.

Por último, se imprimirá el ticket correspondiente y le dará la opción de imprimir un segundo ticket para el cliente.

 -![Sale](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/Sale.jpg)

 

### Consulta de Saldo
Al seleccionar esta opción se le pedirá que presente un identificador. El identificador podrá ser cualquier método como pasar una tarjeta, scanear un QR, escribir manualmente el track de identificador, etc.

Una vez se le proporciono un identificador, se deberá seleccionar el combustible entre uno de los disponibles y Luego se imprimirá un ticket en donde se muestra el saldo restante para esta subcuenta del combustible seleccionado.

-![Balance-Inquiry](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_Balance-Inquiry.jpg)


### Pagos QR
(Solo disponible si se configura el parámetro “Mobile Menú” en 1) 
 
## Loyalty

También conocido como Fidelidad, en esta pestaña se puede encontrar botones con distintas funcionalidades de este módulo.
-	Acumulación
-	Devolución de acumulación
-	Consulta de saldo
-	Intercambio de regalos
-	Redención de puntos

 -![Loyalty](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_Loyalty.jpg)


### Acumulación 
Desde aquí se puede realizar una acumulación de puntos. Se pide que se escanee un identificador y posteriormente se ingrese un monto. Esto hará que según las reglas de puntos configuradas en ATIONET se le agregara la cantidad de puntos correspondiente al usuario.

-![Acumulation](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_Acumulation.png)

### Devolución de acumulación
Desde aquí se puede hacer la devolución de una acumulación al ingresar el código de autorización de esta. Esto resultara en que se quiten los puntos acumulados en dicha transacción al usuario.

### Consulta de saldo
Aquí podrá consultar cuantos puntos tiene acumulado un usuario al escanear un identificador.

-![Balance-Inquiry-Loyalty](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_Balance-Inquiry-Loyalty.jpg)


### Canje de regalos
Al seleccionar esta opción, saldrá el escáner de QRs, donde se tendrá que escanear el QR asociado al canje del regalo que el usuario desea obtener. 

-![Gift-Exchane](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_GIft-Exchange.jpg)


### Redención de puntos
Desde aquí se puede hacer un canje de puntos por un SKU disponible en el sitio.



## Mantenimiento
En esta pestaña podrá encontrar botones con distintas funcionalidades las cuales requieren ingresar el código del supervisor. Estas son: 
-	Batch Close
-	Print Last Receipt
-	Reverse Transaction
-	Recharge Subaccount
-	Active Giftcard
-	Recharge Consumer Card
-	Reversal Consumer Card
-	Subaccount recharge
-	Pin Change
-	Configuration

 -![Mainteance](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_Maintenance.jpg)

 
### Cierre de lote
Desde aquí se puede imprimir un ticket con la cantidad de transacciones y el monto total de las mismas realizadas desde el ultimo cierre de lote.

 -![Batch Close](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_Batch-Close.jpg)


### Imprimir ultimo comprobante
Desde aquí podrá imprimir nuevamente el ultimo ticket impreso.

### Anular Transacción
También conocido como void transaction.
Desde aquí se podrá cancelar una transacción  realizada recientemente al proporcionarle el código de autorización de la misma. Esto hará que se le devuelva el saldo a la subcuenta.

 -![Void](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_Void.jpg)

### Recargar Subcuenta
Esta funcionalidad solo estará disponible si se encuentra el parámetro “Subaccount Recharge” activo.
Desde aquí se le puede entregar saldo a una subcuenta (Vehículo o Conductor) que tenga un contrato con dispersión, es decir que permita que cada subcuenta tenga saldo propio.

### Activar Giftcard
Con esta funcionalidad se podrá activar tarjetas de giftcard para que puedan ser utilizadas.

### Recargas Consumer Card
(solo disponible si se encuentra el flag de consumer card activado en parámetros)

### Reversa Consumer Card
(solo disponible si se encuentra el flag de consumer card activado en parámetros)

### Cambio de PIN
Desde aquí se le pedirá que pase un identificador por medio de cualquier método, posteriormente se le pedirá el PIN del identificador actual y un PIN nuevo. En caso de que se el pin actual sea correcto, que el PIN Nuevo sea distinto al anterior y que coincidan las dos veces que se escribe el PIN nuevo, entonces sea actualizara la información.

## Configuración
Al abrir esta ventana le saldrá las siguientes opciones en las cuales se le pedirá que ingrese la contraseña de supervisor para poder proceder con ellas:
-	Supervisor Password
-	Fuels
-	APP Information
-	Parameters
-	Factory reset
-	Sent Log
-	Diagnosis

 -![Configuration](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_Configuration.jpg)

 
### Clave de Supervisor
Desde este botón, luego de ingresar la contraseña del supervisor, se puede ingresar una nueva contraseña para modificarla.

### Combustible
Desde aquí se podrá ver los combustibles disponibles y editar el precio por unidad de cada uno. Para poder agregar mas combustibles, editar el código y nombre de los ya creados o eliminarlos, es necesario activar el flag “Configurable products” en Parámetros -> ATIONET


 -![Fuel1](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_Fuel1.jpg)   ![Fuel2](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_Fuel2.jpg)




### Información de la APP
Desde aquí podrá ver e imprimir algunos los parámetros configurados e información del software:
-	Site code
-	Site Name
-	Address site
-	Native URL
-	Maintanance URL
-	Mobile URL
-	Controller Type
-	Controller IP
-	Controller Port
-	Controller Pay Type
-	SSL
-	Serial Number
-	Version
-	Terminal IP
-	Gateway
-	Terminal ID

### Formatear de Fabrica
Con esta función podrá resetear toda la configuración del software. Esto llevara a su valor predeterminado a todos los parámetros, combustibles, configuración, etc.

### Enviar Log


### Diagnostico
Podrá testear si distintas funcionalidades funcionan correctamente. Estas son:
-	Lector de banda magnética
-	Lector NFC
-	Lector Chip
-	Conexión
-	Ping
-	Sistema operativo
-	Escaner
-	Teclado
-	Impresora
 


## Parámetros
Desde aquí tendremos las 3 secciones de configuración: Terminal, Sites y Ationet.

 -![parameters](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/standAloneTerminal/v240m_Paramters.png)
 
**Terminal**<br />
Los parámetros para configurar en esta sección son los siguientes:
-	Language: Idioma (SPA español - ENG inglés) 
-	Password: Contraseña inicial de supervisor de la aplicación. Una vez modificado por aplicación, el campo queda invalidado por más que se modifique o no sea el mismo configurado.
-	iButton: 0 Deshabilitado - 1 Habilitado (Lector de iButton)
-	Bar code: 0 Deshabilitado - 1 Habilitado (Scanner) 
-	Chip card: 0 Deshabilitado - 1 Habilitado (Lector de Chip) 
-	NFC card: 0 Deshabilitado - 1 Habilitado (RFID) 
-	MSR card: 0 Deshabilitado - 1 Habilitado (Lector de Tarjetas) </sub>
-	Ping: 3 <sub> (recomendamos no modificar) </sub> 
-	Ping threshold: 3 <sub> (recomendamos no modificar) </sub>
-	SSL: Envío de información segura <sub> (recomendamos dejar en 1) </sub>

**Parámetros para NFC**<br />
-	CTLS: 1 <sub> (recomendamos no modificar) </sub>
-	EMV debug: 0 <sub> (recomendamos no modificar) </sub>
-	VAS: 0<sub>  (recomendamos no modificar) </sub>
-	WI-FI - GSM <sub> (No se pueden tener ambos a la vez) </sub>
  
**Parámetros para GSM**<br />
-	APN: APN del proveedor
  
**Parámetros para WI-FI**<br />
-	DHCP: 0 Deshabilitado - 1 Habilitado (IP dinámica en caso de poner en 0 hay que configurar los parámetros de IP manualmente)  </sub> 
-	IP: 0.0.0.0
-	Subnetmask: 0.0.0.0
-	Gateway: 0.0.0.0
-	DNS1: 0.0.0.0
-	DNS2: 0.0.0.0
-	NETWORK Name: Nombre de la red WiFi 
-	NETWORK Password: Contraseña de la red WiFi

**Parametros de Log**<br />
-	Log Enable: 0 deshabilitado - 1 habilitado 
-	Log verbocity: Numero entre 0 y 7 que implica la cantidad de información que habrá en cada log. Un número mayor implica más información.
-	Log size (KB): El tamaño máximo de cada log

**Sites**<br />
Los parámetros para configurar en esta sección son los siguientes:
-	Site code: Código del sitio
-	Site address: Dirección del sitio
-	Site name: Nombre del sitio
-	Site cuit: ID Tributario del sitio
-	Main header: Texto de cabecera primario
-	Secondary header: Texto de cabecera secundario
-	Main footer: Texto de pie de página primario
-	Secondary footer: Texto de pie de página secundario

**ATIONET**<br />
Los parámetros para configurar en esta sección son los siguientes:
-	Sale in money: Si es 0 las transacciones utilizaran el volumen y si 1 se utilizara el monto.
-	Configurable Products: En 0 solo se pueden ver los combustibles configurados y en 1 se podrá crear, editar y eliminar combustibles.
-	Subaccount recharge: Si es 1 entonces estará disponible la función de “recarga de la subcuenta” en Mantenimiento.
-	Consumer Card: 1 si se utilizara Consumer Card y 0 si no.
-	Default prompt: Si es 1 se le podrá añadir distintas solicitudes que la terminal pedirá previamente a hacer una pre-autorización o venta.
-	Attendant Id: Si es 1 se le pedirá un identificador al encargado previo a realizar una pre-autorización, completion y venta.
-	Driver ID: 0 deshabilitado - 1 habilitado <sub>  (Parámetro de solicitud) </sub>
-	Vehicle ID: 0 deshabilitado - 1 habilitado <sub>  (Parámetro de solicitud) </sub>
-	Odometer: 0 deshabilitado - 1 habilitado <sub>  (Parámetro de solicitud) </sub>
-	Engine hours: 0 deshabilitado - 1 habilitado <sub>  (Parámetro de solicitud) </sub>
-	Trailer: 0 deshabilitado - 1 habilitado <sub>  (Parámetro de solicitud) </sub>
-	Miscellaneous: 0 deshabilitado - 1 habilitado <sub>  (Parámetro de solicitud) </sub>
-	Truck unit: 0 deshabilitado - 1 habilitado <sub>  (Parámetro de solicitud) </sub>
-	Secondary track: 0 deshabilitado - 1 habilitado <sub>  (Parámetro de solicitud) </sub>
-	Primary pin: 0 deshabilitado - 1 habilitado <sub>  (Parámetro de solicitud) </sub>
-	Secondary pin: 0 deshabilitado - 1 habilitado <sub>  (Parámetro de solicitud) </sub>
-	Print Driver ID: 0 deshabilitado - 1 habilitado <sub> (Información a imprimir en el ticket) </sub>
-	Print Vehicle ID: 0 deshabilitado - 1 habilitado <sub> (Información a imprimir en el ticket) </sub>
-	Print Company Name: 0 deshabilitado - 1 habilitado <sub> (Información a imprimir en el ticket) </sub>
-	Print Primary Track: 0 deshabilitado - 1 habilitado <sub> (Información a imprimir en el ticket) </sub>
-	Print Secondary Track: 0 deshabilitado - 1 habilitado <sub> (Información a imprimir en el ticket) </sub>
-	Print Modifiers: 0 deshabilitado - 1 habilitado <sub> (Información a imprimir en el ticket) </sub>
-	Native URL: Dirección de ATIONet ambiente Beta o Producción (native.ationet.com para Producción / native-beta.ationet.com para Beta)
-	Maintenance URL: Dirección de terminal manager ambiente Beta o Producción 
-	Mobile URL: Dirección de mobile para ambiente beta o producción.
-	Keep Alive Time: La cantidad de minutos que tarda en enviar a terminal manager un nuevo keep alive.
-	User name: Usuario de fidelidad configurado en ATIONet. Debe pertenecer a un usuario con rol LoyaltyAPI.
-	Password: Contraseña del usuario de fidelidad configurado en ATIONet. Debe pertenecer a un usuario con rol LoyaltyAPI.
-	Mobile User Name: Usuario de Mobile
-	Mobile Password: Contraseña del usuario de mobile
-	Mobile Menu: Si es 1 se la opción de “Pagos QR” estara disponible.
-	Terminal ID: ID de terminal configurado en ATIONet
-	Local agent: 0 deshabilitado - 1 habilitado
-	Local agent IP:  Dirección de IP del Local Agent
-	Local agent Port: 33173 <sub> (recomendamos no modificar) </sub> 
-	Controller Type: FUSION
-	Controller Port: El puerto de la controladora
-	Controller Pay Type: Tipo de pago de la controladora
-	Loyalty POS Code:
