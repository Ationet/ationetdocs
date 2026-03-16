


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

IMAGE

Beneath the battery is a small button into which you must insert a paperclip or another object of similar size.
By holding this button down for 3 seconds, you will enter the terminal’s operator menu, from which you can access the supervisor menu.

IMAGE

Now you must select the ***"Supervisor"*** option, for which you will be asked for a password; the default password is **1668311**

IMAGE

Next, select the options **"Device"** > **"Load Update Package"**.

IMAGE
IMAGE

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

IMAGE

Now you must select the ***"Supervisor"*** option, for which you will be asked for a password; the default password is **1668311**

IMAGE

Next, tap the three dots in the top-left corner of the screen and select the ***“Android Settings”*** option.

IMAGE

Within this menu, select the ***“System”*** options and go to ***“Recovery Option”***.

IMAGE
IMAGE

Once there, make the following selection: ***“Factory data reset” > “Reset” > “Erase everything”***

IMAGE

Once this is complete, to install the new version, you must repeat the steps outlined in the [Installation](#Installation) section.


# Configuration

In this section, we will outline the necessary configuration to start using the T650p terminal

>  [!NOTE]
> *The only information detailed in this section is the MINIMUM information required to operate the terminal*

1. Start by going to the ***"Maintenance"*** section in the bottom right-hand corner of the screen

IMAGE

2. Next, enter the supervisor password, which by default is ***Ationet@1*** (If you are unable to log in with this password, please contact support@atioinc.com)

IMAGE

3. Next, go to the ***"Settings"*** menu

IMAGE

4. Once in this menu, go to the ***"Ationet"*** section

IMAGE

5. Finally, we need to configure the following settings:

* **"Native URL"**: This is the URL that points to one of the following two environments:

    - https://native-beta.ationet.com/ (BETA)

    - https://native.ationet.com/ (PROD)

* **Terminal Identification**: In this section, you must configure the terminal code corresponding to the portal

    - **Terminal code:** "The first 3 characters of the subscription code" + "Terminal-specific code"

IMAGE

6. Once this configuration is complete, you must **save** and **exit**.

IMAGE

7. Finally, you must go to the ***"Product/SKU Configuration"*** section and configure the products you will be using.

IMAGE

8. Here, select "Add new Product/SKU" and enter the following information:

* **Product/SKU Code**: Enter the Product/SKU code corresponding to the one on the fleet portal
  
* **Product/SKU Name**: Enter a reference name for the Product/SKU
  
* **Product/SKU Price**: Enter the desired price for the Product/SKU

IMAGE

"Once you have entered this information, click **Save** and you will have completed the main configuration of the T650p terminal"








