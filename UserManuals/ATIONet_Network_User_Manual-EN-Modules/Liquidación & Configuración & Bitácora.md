![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

# Contenido

- [Liquidaciones](#liquidaciones)
	- [Documentos de Cargo](#documentos-de-cargo)
	- [Documentos de Liquidaciones](#documentos-de-liquidaciones)
	- [Estados de Cuenta](#estados-de-cuenta)
	- [Items Liquidados](#items-liquidados)
	- [Procesos de Liquidación](#procesos-de-liquidación)
- [Configuración](#configuración)
	- [Clasificadores de Contratos de Compañía](#clasificadores-de-contratos-de-compañía)
	- [Clasificadores de Sitios](#clasificadores-de-sitios)
	- [Configuraciones de Procesos](#configuraciones-de-procesos)
	- [Motivos de Contingencias](#motivos-de-contingencias)
	- [Red](#red)
	- [Tipos de Documentos Externos](#tipos-de-documentos-externos)
- [Bitacora](#bitacora)
	- [Bitácora de Auditorias](#bitácoras-de-auditorias)
	- [Bitácora de Procesos](#bitácora-de-procesos)


# Liquidaciones

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

## Procesos de Liquidación
En esta sección puede ejecutar manualmente un proceso de facturación o ver el estado de todos los procesos de facturación. Los posibles estados de los procesos son: Pendiente, Confirmado, Error o Confirmado con errores.

![Procesos de Liquidación](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Liquidaciones/Procesos%20de%20Liquidaci%C3%B3n.PNG)

Para ejecutar manualmente un proceso de facturación, haga clic en el botón **Ejecutar proceso**. Esto generará automáticamente un registro del proceso de liquidación. Tenga en cuenta que esto sólo afectará a los contratos que tengan el proceso de facturación configurado como **Manual**.

# Configuración

## Clasificadores de los Contratos de Compañía
En esta sección puede configurar los clasificadores de contratos de compañía personalizados.

![Clasificaciones de contratos de compañía](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Clasificadores%20de%20Contratos%20de%20Compa%C3%B1%C3%ADa.PNG)

## Clasificadores de Sitios
En esta sección puede configurar los clasificadores de sitios personalizados.

![Clasificadores de Sitios](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Clasificadores%20de%20Sitios.PNG)

## Configuración de procesos
En esta sección se visualizan y crean las configuraciones de los procesos de liquidación para que se ejecuten automáticamente.

![Configuración de procesos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Configuraciones%20de%20Procesos.PNG)

Para crear una configuración de proceso, haga clic en el botón **Nuevo**.

![Configuración de Procesos Nueva](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Configuraciones%20de%20Procesos%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Descripción:** Introduzca la descripción del proceso.
* **Tipo:** Seleccione el tipo de proceso (ahora mismo sólo está disponible el de Liquidación).
* **Periodicidad:** Seleccione la periodicidad con la que se ejecuta el proceso.
* **Hora:** Introduzca la hora en la que se ejecuta el proceso.
* **Habilitado:** Marque esta opción para habilitar/deshabilitar el proceso.
* **PDF:** Marque esta opción para habilitar/deshabilitar el proceso para crear un pdf del estado de cuenta cuando se termine de procesar.
* **Email:** Marque esta opción para habilitar/deshabilitar el proceso para enviar el pdf creado de la declaración cuando se termine de procesar.

## Motivos de Contingencias
En esta sección puede configurar los motivos de la creación de contingencias.

![Motivos de Contingencias](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Motivos%20de%20Contingencias.PNG)

## Red
Dentro de esta sección puede personalizar su Network (cambiar el logo, añadir campos personalizados, etc).

1. **Logo**

![Logotipo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Network%20-%20Logo.PNG)

2. **Correos**

![Correos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Network%20-%20Correos.PNG)

3. **Campos Personalizados del Conductor**

![Campos personalizados del conductor](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Network%20-%20Conductores.PNG)

4. **Campos Personalizados de Vehículos**

![Campos personalizados de vehículos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Network%20-%20Veh%C3%ADculos.PNG)

5. **Campos Personalizados de Sitios**

![Campos personalizados de sitios](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Network%20-%20Sitios.PNG)

6. **Campos Personalizados de Compañía**

![Campos personalizados de compañías](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Network%20-%20Compa%C3%B1%C3%ADas.PNG)

7. **Campos Personalizados de Comercio**

![Campos personalizados de comercio](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Network%20-%20Comercios.PNG)

8. **Campos Personalizados de Contratos de Compañía**

![Campos personalizados de contratos de compañía](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Network%20-%20Contratos%20de%20Compa%C3%B1%C3%ADa.PNG)

9. **Paleta de Colores**

![Paleta de colores](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Network%20-%20Paleta%20de%20Colores.PNG)

10. **Otros**

![Otros](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Configuraci%C3%B3n/Network%20-%20Otros.PNG)

## Tipos de Documentos Externos



# Bitácora

## Bitácora de Auditoría
En esta sección puede ver una lista de todas las acciones realizadas por todos los usuarios. Hay un panel de filtros en la parte superior para facilitar las consultas.

![Bitácora de Auditoría](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Bitacora/Bitacora%20de%20Auditoria.PNG)

## Bitácora de Procesos
En esta sección puede ver una lista de todos los procesos ejecutados.

![Bitácora de Procesos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Bitacora/Bitacora%20de%20Procesos.PNG)
