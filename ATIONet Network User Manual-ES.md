![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|**Información del Documento**|.|
|--- |--- |
|**Archivo:**|ATIONet_Network_User_Manual-ES.md|
|**Versión Doc:**|2.0|
|**Fecha Liberación:**|22, Jun 2021|
|**Autor:**|ATIONet LLC|


|**Bitácora de Cambios**|||
|--- |--- |--- |
|**Ver.**|**Fecha**|**Resumen de Cambios**|
|1.0|02/Ago/2017|- Versión Inicial
|2.0|22/Jun/2021|- Actualización de Manual

# Contenido

- [Overview](#overview)
- [Definitions](#definitions)
  - [Contract](#contract) 
  - [Sub-account](#sub-account)
  - [Company](#company)
  - [Identification](#identification)
  - [Site](#site)
	- [Vehicle](#vehicle)
	- [Driver](#driver)
	- [Offline module](#offline-module)
  - [Terminal](#terminal)
- [My Preferences](#my-preferences) 
- [Navigation Menu](#navigation-menu)
  - [Tablero](#tablero)
   - [Estado General](#estado-general)
   - [Unidades/Mes](#unidadesmes)
   - [Transacciones del Día](#transacciones-del-día)
   - [Lista de Pre-Autorizaciones Pendientes](#lista-de-pre-autorizaciones-pendientes)
   - [Transacciones Marcadas en el Mes Actual](#transacciones-marcadas-en-el-mes-actual)
   - [Contratos sin Actividad](#contratos-sin-actividad)
   - [Transacciones Recientes](#transacciones-recientes)
   - [Listado de Contratos con Bajo Saldo](#listado-de-contratos-con-bajo-saldo)
   - [Actualizaciones de Identificadores del Último Mes](#actualizaciones-de-identificadores-del-último-mes)
   - [Estado de Terminales](#estado-de-terminales)
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
  - [Flotas](#flotas)
	  - [Alertas de Fraude](#alertas-de-fraude)
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
  	- [Familias de Conceptos](#familias-de-conceptos)
  	- [Identificadores Solicitados](#identificadores-solicitados)
  	- [Programas](#programas)
  	- [Reglas](#reglas)
  	- [Sobregiro](#sobregiro)
  	- [Transacciones](#transacciones)
  	- [Transacciones Desconocidas](#transacciones-desconocidas)
  	- [Transacciones Despachadas](#transacciones-despachadas)
  	- [Transacciones por Conductor](#transacciones-por-conductor)
  	- [Transacciones por Flota](#transacciones-por-flota)
  	- [Transacciones por Sitio](#transacciones-por-sitio)
  	- [Transacciones por Vehículo](#transacciones-por-vehículo)
  	- [Transacciones por Rechazadas](#transacciones-rechazadas)
  	- [Transacciones Sin Control](#transacciones-sin-control)

# Resumen

ATIONet is based on the premise that online communications between sites and the web portal are possible, however, it provides solid contingency procedures in the event of a communication error.

The ATIONet platform is a fleet management service with an innovative and unique market offer. Cloud processing, 100% web-based, multi-user access, data availability and sharing, instant updates, security, automatic back-up and paperwork reduction.

ATIONet is a web portal for fleet service companies that allows the processing of transactions from any point of sale application through a simple and reliable interface. 

ATIONet can be installed at any service station with one or multiple fleet service programs. The web portal allows fleet managers full access to their vehicle information.

ATIONet makes it possible for the fleet manager to operate, monitor, change and edit fleet information in real time.


# Definitions

## Contract 

The contract is the relationship that exists between the network and the client, in which it is guided, for example, if it will be of amount or volume, the price at which the fuel is going to be sold, in which sites it can load, among others.

## Sub-account 

Each time an identification is associated with a vehicle or driver, a sub-account is created. The sub-account is definitely who is going to have a current account, the sub-account is going to be able to receive deposits of money or product. The rules also impact the sub-account.

The sub-accounts are hierarchically dependent on the contract.

## Company

In ATIONet the company refers to the entity that owns the fleet. It is the one that manages the vehicles, drivers and fleet rules.

## Identification

The identification is the physical means used by ATIONet to identify a vehicle or driver. ATIONet supports various types of identifications, such as card, TAG, chip, ATIONet card, manual entry, barcode and iButton. When an identification is associated to a Vehicle or Driver, a sub-account is created.

## Site 

The Site represents the service station. A site is assigned a terminal/controller and may also have associated Location rules.

## Vehicle 

The vehicles can be associated or grouped by a fleet, they can have associated rules and at the moment of being related with an identification a sub-account is created. They may also have an associated driver.

## Driver 

The driver in ATIONet is the person who is identified as a chauffeur. If this driver is assigned an identification, a sub-account is created. Drivers may also have associated rules.

## Offline module 

ATIONet's offline module is automatically activated when the service station has no Internet connection and the authorizations cannot be processed online. At this point the offline module comes into play. For the terminal/controller it is completely transparent. When the offline module recovers the connectivity it sends all the information processed locally and also downloads any updates. As long as there is connectivity, the offline module is continuously downloading ATIONet updates (balances, identifications, rules, etc).

## Terminal

The terminal (or controller) is the representation of the dispenser controller, which needs to be parameterized in a particular way according to the type of terminal. The terminals handled by ATIONet are ATIO-NanoCPI, ATIO-Standalone, ATIO-CG, VF-Sapphire, VF-Commander, VF-Ruby, ControlGas, among others. 

# Navigation Menu

ATIONet has a quick access menu located on the left side of the website. From this menu you can access different options. The menu is divided into 9 sections. (Dashboard, Favorites, Reports, Administration, Fleets, Billing, Notifications, Configuration and Logbook).

# My Preferences
Inside this section each user can customize their portal preferences.

1. **Default Role:** Select the default role when loggin in.

![Default Role](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Default%20Role.PNG)

2. **Profile Picture:** Change the profile picture of your user.

![Profile Picture](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Profile%20Picture.PNG)

3. **Change Password:** Change the password for your user.

![Change Password](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Change%20Password.PNG)

To edit your password, click the ***change password*** link.

![Change Password New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Change%20Password%20New.PNG)

4. **Widgets Configuration:** Select which widgets to show on your dashboard.

![Widget Configuration](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Widget%20Configuration.PNG)
