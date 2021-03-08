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

Download the files needed for the installation from here. The files to download are:

- StandAlone Application for the V240m Terminal
- Operative System
- Library
- Remove MAC
- Library Camera
- Mx Downloader

# Date/Time &amp; WiFi configuration

With the terminal turned on, enter the Supervisor menu by pressing the **1+5+9** keys simultaneously. This way you&#39;ll see the following menu:

![](RackMultipart20210308-4-sbevb0_html_a17f57682edf9bd3.png)

Selecting the **supervisor** option will prompt for a password. The default supervisor password is **166831**. From this menu go to **Administration - Date/Time** and update the date and time of the terminal.

![](RackMultipart20210308-4-sbevb0_html_865639e4b434fb68.png)

Once the date and time are set, go to **Administration - Communications - WiFi - WiFi Scan** and turn on the WiFi so that it can scan for available networks.

![](RackMultipart20210308-4-sbevb0_html_61697734628955f5.png)

Once the scan is complete, select the network to use from the list of available networks.

![](RackMultipart20210308-4-sbevb0_html_844703c56decab5d.png)

Return to the **WiFi Menu** using the arrows in the upper left corner and enter to **WiFi Configuration**.

![](RackMultipart20210308-4-sbevb0_html_cf70d0f645d2278d.png)

Input the network&#39;s password in the **PSK** field and press **Enter** (green key).

![](RackMultipart20210308-4-sbevb0_html_3f3a6f993ae902f9.png)

Go back to the **WiFi**** menu **and select the option** WiFi Interface IPv4**.

![](RackMultipart20210308-4-sbevb0_html_c44ebe27423c1f46.png)

From here configure the options: **Mode=&quot;DHCP&quot;** , **AutoStart=&quot;Once&quot;** and then click on the red connection icon.

![](RackMultipart20210308-4-sbevb0_html_27f0dfd451afb48e.png)

Once successfully connected to the network, the connection icon located in the upper right section of the screen will be displayed in green and will indicate the IP assigned to the terminal in the **IP address** field.

![](RackMultipart20210308-4-sbevb0_html_c0bea99206d1978c.png)

IMPORTANT: In case you have a previous version installed, return to the initial menu and enter the Remove user bundle option and select Remove all (DO NOT select Remove Users option).

Once this configuration is complete, we can proceed to install the pre-requisites and StandAlone application on the terminal.

# Installation

First, we will set the terminal in download mode to be able to receive the installation files. For that we must enter from the supervisor menu to **Update - Netloader - wlan0**.

![](RackMultipart20210308-4-sbevb0_html_82f8f56b7bf156b5.png)

Then, from a PC within the same network as the terminal, open the **MxDownloader** application. Go to the **Network** tab and fill in the fields:

- _ **File to send:** _ Select the file to install.
- _ **Destination IP:** _ Input the V240m terminal&#39;s IP address
- _ **Download Type:** _ Select the option **Full**.
- _ **Post-Download:** _ Select the option **Run App**.

![](RackMultipart20210308-4-sbevb0_html_4c7ca121f0f15e53.png)

Once all the corresponding fields have been completed, click on **Send** , which will send the file to the terminal and it will be installed automatically. After the installation the terminal will proceed to restart (otherwise force restart manually).

This procedure must be repeated for each file specifically in the following order:

- Operative System
- Library
- Remove MAC
- Camera Library
- V240m StandAlone Terminal Application

IMPORTANT: If the V240m terminal doesn&#39;t have a camera on top of it, then the **Camera Library** prerequisite shouldn&#39;t be installed.

# Configuration

Once everything is installed we will proceed to configure the terminal. When the application starts, click the configuration symbol in the upper right corner.

![](RackMultipart20210308-4-sbevb0_html_948d2615370d01a0.png)

NOTE: In case you have not been able to click on **configuration** icon in time, you can access it from **Maintenance - Configuration - Parameters** within the application itself.

Once here the terminal will prompt for a password (enter the default password **123456** ).

From here you&#39;ll have the 3 configuration sections: **Terminal** , **Sites** and **Ationet**.

![](RackMultipart20210308-4-sbevb0_html_9ffd7e3de2a0aeb8.png)

## Terminal

The parameters to be configured in this section are as follows:

- _ **Language:** _ SPA for Spanish - ENG for English)
- _ **Password:** _ Initial supervisor password of the application. Once modified, the field is invalidated even if it is modified or is not the same as the one configured.
- _ **iButton:** _ 0 Disabled - 1 Enabled (iButton Reader)
- _ **Bar code:** _ 0 Disabled - 1 Enabled (Scanner)
- _ **Chip card:** _ 0 Disabled - 1 Enabled (Chip Reader)
- _ **NFC card:** _ 0 Disabled - 1 Enabled (RFID)
- _ **MSR card:** _ 0 Disabled - 1 Enabled (Card Reader)
- _ **Receipt number:** _ 1
- _ **Ping:** _ 3
- _ **Ping threshold:** _ 3
- _ **SSL:** _ 1

**NFC Parameters**

- _ **CTLS:** _ 1
- _ **EMV debug:** _ 0
- _ **VAS:** _ 0
- _ **WI-FI:** _ ON – _ **GSM:** _ OFF

**GSM Parameters**

- _ **APN:** _ APN provider

**WI-FI Parameters**

  - _ **DHCP:** _ 1
  - _ **IP:** _ 0.0.0.0
  - _ **Subnetmask:** _ 0.0.0.0
  - _ **Gateway:** _ 0.0.0.0
  - _ **DNS1:** _ 0.0.0.0
  - _ **DNS2:** _ 0.0.0.0
  - _ **NETWORK NAME:** _ WiFi Network exact name (SSID)
  - _ **NETWORK PASSWORD:** _ WiFi password

## Sites

The parameters to be configured in this section are as follows:

_ **Site code:** _ Site code

_ **Site address:** _ Site address

_ **Site name:** _ Site name

_ **Site cuit:** _ Site Tax ID

_ **Main header:** _ Main header

_ **Secondary header:** _ Secondary header

_ **Main footer:** _ Main footer

_ **Secondary footer:** _ Secondary footer

## Ationet

The parameters to be configured in this section are as follows:

_ **Sale in money:** _ Allows you to make sales either in amount or volume (0 Disabled for volume sales - 1 Enabled for amount sales)

_ **Default prompt:** _ Request for extra parameters (0 Disabled – 1 Enabled)

_ **Attendant Id:** _ Request Attendant ID (0 Disabled – 1 Enabled)

_ **Driver ID:** __Prompting parameter_ (0 Disabled – 1 Enabled)

_ **Vehicle ID:** __Prompting parameter_ (0 Disabled – 1 Enabled)

_ **Odometer:** __Prompting parameter_ (0 Disabled – 1 Enabled)

_ **Engine hours:** __Prompting parameter_ (0 Disabled – 1 Enabled)

_ **Trailer:** __Prompting parameter_ (0 Disabled – 1 Enabled)

_ **Miscellaneous:** __Prompting parameter_ (0 Disabled – 1 Enabled)

_ **Truck unit:** __Prompting parameter_ (0 Disabled – 1 Enabled)

_ **Secondary track:** __Prompting parameter_ (0 Disabled – 1 Enabled)

_ **Primary pin:** __Prompting parameter_ (0 Disabled – 1 Enabled)

_ **Secondary pin:** __Prompting parameter_ (0 Disabled – 1 Enabled)

_ **Native URL:** _ ATIONet&#39;s address for Beta or Production environment

_ **Maintenance URL:** _ ATIONet&#39;s address for Beta or Production environment

_ **User name:** _ LoyaltyAPI user configured in ATIONet

_ **Password:** _ LoyaltyAPI user&#39;s password configured in ATIONet

_ **Terminal ID:** _ Terminal ID configured in ATIONet

_ **Local agent:** _ 0

_ **Local agent IP:** _ 0.0.0.0
