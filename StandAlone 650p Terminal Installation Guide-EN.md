![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)


|**Document Information**|.|
|--- |--- |
|**File:**|ATIONet-StandAlone_650p_Terminal_Installation_Guide-EN.md|
|**Document Version:**|1.0|
|**Publication Date:**|17 March 2026|
|**Author:**|ATIONet LLC|


# Contents

- [Introduction](#Introduction)
- [Required hardware](#Required-hardware)
- [Required software](#Required-software)
- [Downloading Prerequisites and Application](#Downloading-Prerequisites-and-Application)
- [Installation](#Installation)
- [Update](#Update)
- [Configuration](#Configuration) 

# Introduction

In this manual, we will provide a brief explanation of how to install and update the StandAlone T650p terminals. 
Installation must be carried out by downloading the files from a computer to the terminal’s internal memory. To do this, we will use a USB stick and a female-to-male USB Type-C cable

# Required hardware

- Verifone T650p terminal
- USB [FEMALE] to Type-C [MALE] cable IMAGE
- USB flash drive
- Computer

# Downloading Prerequisites and Application

Download the files required for installation from [here](https://downloads.ationet.com). The files to download are:

- OTA Secure
- SetSponsor
- SDI
- T650p Terminal Version

# Installation

First, you must download the files listed above **(OTA Secure, SetSponsor, SDI and the T650p Terminal Version)** onto a USB stick, then use the USB (FEMALE) to Type-C (MALE) cable to transfer them to the terminal.
Once this step is complete, open the back of the terminal where you will see the battery. 

![Parte de Atras de la terminal](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Parte%20de%20Atras%20de%20la%20terminal.jpg)

Beneath the battery is a small button into which you must insert a paperclip or another object of similar size.
By holding this button down for 3 seconds, you will enter the terminal’s operator menu, from which you can access the supervisor menu.

![Menu de Supervisor](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor.PNG)

Now you must select the ***"Supervisor"*** option, for which you will be asked for a password; the default password is **1668311**

![Menu de Supervisor (Password)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor%20(Password).PNG)

Next, select the options **"Device"** > **"Load Update Package"**.

![Menu de Supervisor (Devices)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor%20(Devices).PNG)
![Menu de Supervisor (Load Update Package)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor%20(Load%20Update%20Package).PNG)

On this screen, tap the three-line icon to select the **"Choose Files"** option, where you must then select **"Internal Storage"** (as you have already transferred the installation files to the device’s internal storage).
In this section, you can view the various prerequisites, which must be installed in the following order:

***OTA Secure > SetSponsor > SDI > APK (Latest version for the 650p device)***

>  [!NOTE]
> ***Once the first file has been uploaded, the device will restart, so the installation process must be repeated for each file to be uploaded***

After completing these steps, a screen will appear displaying ***“Checking for updates”***. 
To proceed from this screen, you must press the four corners of the screen in the following order:

* **Top left corner** 
* **Top right corner** 
* **Bottom right corner**
* **Bottom left corner**


## Update

To update the T650p terminal, you will need to perform a factory reset on the terminal.
To do this, open the back of the device to reveal the battery. 
Underneath the battery, there is a small button which you must press using a paperclip or another object of similar size.
By holding this button down for 3 seconds, you will enter the terminal’s operator menu, from which you can access the supervisor menu.

![Parte de Atras de la terminal](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Parte%20de%20Atras%20de%20la%20terminal.jpg)

Now you must select the ***"Supervisor"*** option, for which you will be asked for a password; the default password is **1668311**

![Menu de Supervisor](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor.PNG)

Next, tap the three dots in the top-left corner of the screen and select the ***“Android Settings”*** option.

![Menu de Supervisor (Android Settings)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor%20(Android%20Settings).PNG)

Within this menu, select the ***“System”*** options and go to ***“Recovery Option”***.

![Menu de Supervisor (System)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor%20(System).PNG)
![Menu de Supervisor (Reset options)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor%20(Reset%20options).PNG)

Once there, make the following selection: ***“Factory data reset” > “Reset” > “Erase everything”***

![Menu de Supervisor (Reset de fabrica)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Menu%20de%20Supervisor%20(Reset%20de%20fabrica).PNG)

Once this is complete, to install the new version, you must repeat the steps outlined in the [Installation](#Installation) section.


# Configuration

In this section, we will outline the necessary configuration to start using the T650p terminal

>  [!NOTE]
> *The only information detailed in this section is the MINIMUM information required to operate the terminal*

1. Start by going to the ***"Maintenance"*** section in the bottom right-hand corner of the screen

![Config (Manteinance)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Manteinance).PNG)

2. Next, enter the supervisor password, which by default is ***Ationet@1*** (If you are unable to log in with this password, please contact support@atioinc.com)

![Config (Password)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Password).PNG)

3. Next, go to the ***"Settings"*** menu

![Config (Settings)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Settings).PNG)

4. Once in this menu, go to the ***"Ationet"*** section

![Config (Ationet)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Ationet).PNG)

5. Finally, we need to configure the following settings:

* **"Native URL"**: This is the URL that points to one of the following two environments:

    - https://native-beta.ationet.com/ (BETA)

    - https://native.ationet.com/ (PROD)

* **Terminal Identification**: In this section, you must configure the terminal code corresponding to the portal

    - **Terminal code:** "The first 3 characters of the subscription code" + "Terminal-specific code"

![Config (Ationet - Terminal de ejemplo)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Ationet%20-%20Terminal%20de%20ejemplo).PNG)

6. Once this configuration is complete, you must **save** and **exit**.

![Config (Ationet - Save)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Ationet%20-%20Save).PNG)

7. Finally, you must go to the ***"Product/SKU Configuration"*** section and configure the products you will be using.

![Config (Products)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Products).PNG)

8. Here, select "Add new Product/SKU" and enter the following information:

* **Product/SKU Code**: Enter the Product/SKU code corresponding to the one on the fleet portal
  
* **Product/SKU Name**: Enter a reference name for the Product/SKU
  
* **Product/SKU Price**: Enter the desired price for the Product/SKU

![Config (Products - New)](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Verifone%20T650p/Config%20(Products%20-%20New).PNG)

"Once you have entered this information, click **Save** and you will have completed the main configuration of the T650p terminal"



[Back to top](#contents) 	:arrow_up:




