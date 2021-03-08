![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|Document Information|.|
|--- |--- |
|File:|ATIONet-Installation_Guide_StandAlone_V240m_Terminal.md|
|Doc Version:|1.0|
|Release Date:|08, March 2021|
|Author:|ATIO International LLC|


|Change Log|||
|--- |--- |--- |
|Ver.|Date|Change Summary|
|1.0|08/Mar/2021|- Initial version

## Contents

- [Introduction](#Introduction)
- [Hardware required](#Hardware-required)
- [Software required](#Software-required)
- [Pre-requisites and application download](#Pre-requisites-and-application-download)
- [Date/Time and WiFi configuration](#datetime--wifi-configuration)
- [Installation](#Installation)
- [Configuration](#Configuration)
    - [Terminal](#Terminal)
    - [Sites](#Sites)
    - [Ationet](#Ationet)

# Introduction

In this manual we&#39;ll proceed to explain how to update the StandAlone V240m terminals. The installation can be done via WiFi or with the programming cable + USB flashdrive.

# Hardware required

- Terminal V240m
- WiFi/Card SIM connectivity
- V240m programming cable (optional)
- 8GB USB flashdrive (optional)

# Software required

- V240m pre-requisites
- Mx Downloader 2.9.0

# Pre-requisites and application download

Download the files needed for the installation from [here](https://github.com/Ationet/ationetdownloads/blob/master/README.md). The files to download are:

- StandAlone Application for the V240m Terminal
- Operative System
- Library
- Remove MAC
- Library Camera
- Mx Downloader

# Date/Time &amp; WiFi configuration

With the terminal turned on, enter the Supervisor menu by pressing the **1+5+9** keys simultaneously. This way you&#39;ll see the following menu:

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/Supervisor%20Menu.png)

Selecting the **supervisor** option will prompt for a password. The default supervisor password is **166831**. From this menu go to **Administration - Date/Time** and update the date and time of the terminal.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/Date%20and%20Time.png)

Once the date and time are set, go to **Administration - Communications - WiFi - WiFi Scan** and turn on the WiFi so that it can scan for available networks.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/WiFi%20Scan.png)

Once the scan is complete, select the network to use from the list of available networks.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/WiFi%20List.png)

Return to the **WiFi Menu** using the arrows in the upper left corner and enter to **WiFi Configuration**.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/WiFi%20Menu%20-%20Configuration.png)

Input the network&#39;s password in the **PSK** field and press **Enter** (green key).

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/WiFi%20Configuration.png)

Go back to the **WiFi** menu and select the option **WiFi Interface IPv4**.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/WiFi%20Menu%20-%20IPv4.png)

From here configure the options: **Mode=&quot;DHCP&quot;**, **AutoStart=&quot;Once&quot;** and then click on the red connection icon.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/WiFi%20IPv4.png)

Once successfully connected to the network, the connection icon located in the upper right section of the screen will be displayed in green and will indicate the IP assigned to the terminal in the **IP address** field.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/WiFi%20Connected.png)

```IMPORTANT: In case you have a previous version installed, return to the initial menu and enter the "Remove user bundle" option and select "Remove all" (DO NOT select "Remove Users" option).```

Once this configuration is complete, we can proceed to install the pre-requisites and StandAlone application on the terminal.

# Installation

First, we will set the terminal in download mode to be able to receive the installation files. For that we must enter from the supervisor menu to **Update - Netloader - wlan0**.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/Waiting%20for%20Download.png)

Then, from a PC within the same network as the terminal, open the **MxDownloader** application. Go to the **Network** tab and fill in the fields:

- **File to send:** Select the file to install.
- **Destination IP:** Input the V240m terminal&#39;s IP address
- **Download Type:** Select the option **Full**.
- **Post-Download:** Select the option **Run App**.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/Mx%20Downloader.png)

Once all the corresponding fields have been completed, click on **Send** , which will send the file to the terminal and it will be installed automatically. After the installation the terminal will proceed to restart (otherwise force restart manually).

This procedure must be repeated for each file specifically in the following order:

- Operative System
- Library
- Remove MAC
- Camera Library
- V240m StandAlone Terminal Application

```IMPORTANT: If the V240m terminal doesn't have a camera on top of it, then the "Camera Library" prerequisite shouldn't be installed.```

# Configuration

Once everything is installed we will proceed to configure the terminal. When the application starts, click the configuration symbol in the upper right corner.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/Application%20Configuration.png)

```NOTE: In case you have not been able to click on "configuration" icon in time, you can access it from "Maintenance - Configuration - Parameters" within the application itself.```

Once here the terminal will prompt for a password (enter the default password **123456**).

From here you&#39;ll have the 3 configuration sections: **Terminal**, **Sites** and **Ationet**.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/StandAlone%20V240m/Parameters.png)

## Terminal

The parameters to be configured in this section are as follows:

- **Language:** SPA for Spanish - ENG for English
- **Password:** Initial supervisor password of the application. Once modified, the field is invalidated even if it is modified or is not the same as the one configured
- **iButton:** 0 Disabled - 1 Enabled (iButton Reader)
- **Bar code:** 0 Disabled - 1 Enabled (Scanner)
- **Chip card:** 0 Disabled - 1 Enabled (Chip Reader)
- **NFC card:** 0 Disabled - 1 Enabled (RFID)
- **MSR card:** 0 Disabled - 1 Enabled (Magnetic Stripe Card Reader)
- **Receipt number:** 1 (suggested not to change)
- **Ping:** 3 (adviced not to change)
- **Ping threshold:** 3 (adviced not to change)
- **SSL:** 1 (adviced not to change)

**NFC Parameters**

- **CTLS:** 1 (adviced not to change)
- **EMV debug:** 0 (adviced not to change)
- **VAS:** 0 (adviced not to change)
- **WI-FI:** ON – **GSM:** OFF (adviced not to change)

**GSM Parameters**

- **APN:** APN provider (adviced not to change)

**WI-FI Parameters**

  - **DHCP:** 1 (adviced not to change)
  - **IP:** 0.0.0.0
  - **Subnetmask:** 0.0.0.0
  - **Gateway:** 0.0.0.0
  - **DNS1:** 0.0.0.0
  - **DNS2:** 0.0.0.0
  - **NETWORK NAME:** WiFi Network exact name (SSID)
  - **NETWORK PASSWORD:** WiFi password

## Sites

The parameters to be configured in this section are as follows:

**Site code:** *Site code*

**Site address:** *Site address*

**Site name:** *Site name*

**Site cuit:** *Site Tax ID*

**Main header:** *Main header*

**Secondary header:** *Secondary header*

**Main footer:** *Main footer*

**Secondary footer:** *Secondary footer*

## Ationet

The parameters to be configured in this section are as follows:

**Sale in money:** 0 Disabled - 1 Enabled *(Allows you to make sales either in amount or volume)*

**Default prompt:** 0 Disabled - 1 Enabled *(Request for extra parameters)*

**Attendant Id:** 0 Disabled - 1 Enabled *(Request Attendant ID)*

**Driver ID:** 0 Disabled - 1 Enabled *(Prompting parameter)*

**Vehicle ID:** 0 Disabled - 1 Enabled *(Prompting parameter)*

**Odometer:** 0 Disabled - 1 Enabled *(Prompting parameter)*

**Engine hours:** 0 Disabled - 1 Enabled *(Prompting parameter)*

**Trailer:** 0 Disabled - 1 Enabled *(Prompting parameter)*

**Miscellaneous:** 0 Disabled - 1 Enabled *(Prompting parameter)*

**Truck unit:** 0 Disabled - 1 Enabled *(Prompting parameter)*

**Secondary track:** 0 Disabled - 1 Enabled *(Prompting parameter)*

**Primary pin:** 0 Disabled - 1 Enabled *(Prompting parameter)*

**Secondary pin:** 0 Disabled - 1 Enabled *(Prompting parameter)*

**Native URL:** *ATIONet&#39;s address for Beta or Production environment* (```native.ationet.com``` for Production / ```native-beta.ationet.com``` for Beta)

**Maintenance URL:** *ATIONet&#39;s address for Beta or Production environment* (```native.ationet.com``` for Production / ```native-beta.ationet.com``` for Beta)

**User name:** *LoyaltyAPI user configured in ATIONet*

**Password:** *LoyaltyAPI user&#39;s password configured in ATIONet*

**Terminal ID:** *Terminal ID configured in ATIONet*

**Local agent:** 0 Disabled - 1 Enabled

**Local agent IP:** 0.0.0.0 *(Local Agent IP address)*
