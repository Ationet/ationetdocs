![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|**Document Information**|.|
|--- |--- |
|**File:**|ATIONet-Local_Agent_Installation_Guide-EN.md|
|**Doc Version:**|1.0|
|**Release Date:**|12, March 2021|
|**Author:**|ATIONet LLC|


|**Change Log**|||
|--- |--- |--- |
|**Ver.**|**Date**|**Change Summary**|
|1.0|12/Mar/2021|- Initial version
|2.0|04/Sep/2025|- New version 2.6.0000 included


# Contents

- [Required Tools](#required-tools)
- [Required Hardware & Sofware](#required-hardware--software)
- [Installation Steps](#installation-steps)
- [How to prepare the install.config file](#how-to-prepare-the-installconfig-file)
- [Installation of version 2.6.0000 or higher](#instalacion-version-2.6.0000)
- [Update to version 2.6.0000 or higher](#actualizacion-version-2.6.0000)
- [Log Review](#log-review)
- [Statistics](#statistics)

# **Required Tools**

- Flashdrive
- Keyboard
- Mouse
- Monitor

# **Required Hardware & Software**

- Operative System: Windows 10
- Processor: Intel(R) Celeron(R) CPU N3550 @ 1.10GHz
- Memory RAM: 8.00 GB
- Storage: 60.00 GB

# **Installation Steps**

For the installation of the service there are certain prerequisites. The prerequisites needed to install Local Agent are as follows:

- .Net Framework 4.5
- Sql Express 2008 - Atio Custom Instance
- Windows Installer 3.1
- Windows Installer 4.5

Each program can be downloaded directly from the official Microsoft website, however in our [Download Center](https://downloads.ationet.com) we can get these requirements together with the local agent installer, which installs all the programs automatically, without needing to install one by one

From the Download Center you can locate the following files for download:

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Local%20Agent/ATIONet%20Download%20Center%20Site.png)

Once the file package is downloaded, you'll see the following executables:

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Local%20Agent/File%20Folder.PNG)

The **Setup.exe** executable is responsible for running all the installers with the prerequisites. It is important that the prerequisite files are in the same folder as the **Setup.exe** executable and unzipped.

The program will check if it has everything installed, and if not, the installation program will take care of adding all the prerequisites that are needed. Once it is time to install the Local Agent you'll see the following image:

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Local%20Agent/Installer%20Assistant.PNG)

We'll click on next, after that it'll ask us the location where to install the service data, in this case we will use the default one.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Local%20Agent/Installation%20Folder.PNG)

We'll click next once more and the Local Agent will ask for confirmation again. Once confirmed, the installer will reach 75% of the installation and at this point it will open a pop-up window asking for a file, this is the **install.config**.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Local%20Agent/Install.Config%20Selection.PNG)

```NOTE: Before selecting the "install.config" you'll need to prepare it for your site.```

Once the file is located and selected, the Local Agent installation will continue.

When the installation is finished, click on **Finish** to complete the installation.

# **How to prepare the install.config file**

The **install.config** is a text file that can be edited/created with notepad. The data to be included in the file are as follows:

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Local%20Agent/Install.Config.png)

Here follows a brief description of each parameter:

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Local%20Agent/Install.Config%20Configuration.PNG)

For our equipment to be able to connect to the Ationet portal, we will have to modify the **Subscriber_Code**. To find out which is the one of our site, we must enter the ATIONet portal, go to the **Administration - Terminals / Controllers** section.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Local%20Agent/Terminals-Controllers.PNG)

Once we are in this section we must copy the first three characters found in the Code section and place them in **Subscriber_Code**.


# **Installation Version 2.6.0000**

To install LocalAgent version 2.6.0000 or higher, you must make a change to the Install.config file in order to incorporate the “Terminal_Code” variable.

<img width="975" height="187" alt="image" src="https://github.com/user-attachments/assets/f24f5fe1-f15a-4128-a8c3-6b158cbf6baa" />


This value must correspond to a terminal belonging to the network being installed in LocalAgent.
Currently, it is not a requirement for the terminal to be registered with Ationet.
The install.config file must be modified by adding the key with the required value so that the installation can be carried out.

# **Update Version 2.6.0000**

To perform this update, you must first use the LAConfig tool. This tool allows you to make changes to the LocalAgent Configuration table.

To do this, we must run LAConfig with the argument “terminalcode=VALUE”, where the value of the variable “value” corresponds to the new terminal code that we want to assign to that LocalAgent. The terminal being configured must belong to the Network for which LocalAgent was installed. 

Once this step has been completed, and we have the TerminalCode value in the Configuration table, which we can validate by running LAConfig with the “current” parameter, we are ready to update to version 2.6.0000 or higher.

To do this, we follow the normal update steps, downloading the new LocalAgent and running the update wizard, as with any other version. 


# **Log Review**

Once the installation is finished we proceed to check the logs to see if it completed the corresponding data download for the offline base.

The logs are normally located inside the following folder:

**C:\Program Files (x86)\ATIONet\ATIONet Local Agent\logs**

# **Statistics**

The following information shared is in a test environment. These are the Local Agent upload timeouts when going from OFFLINE to ONLINE mode.

![](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Local%20Agent/Statistics.PNG)
