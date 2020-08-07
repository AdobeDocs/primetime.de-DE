---
description: 'null'
seo-description: 'null'
seo-title: Set up the license server database
title: Set up the license server database
uuid: aa6185f2-8e9d-4b65-971a-b7534d910580
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# Set up the license server database{#set-up-the-license-server-database}

The reference implementation license server requires a database to support the following:

* User authentication
* Usage model demo business rules
* Metadata conversion
* Domain support

Anonymous license acquisition does not require that the database be running.

>[!NOTE]
>
>Dieses Verfahren gilt nur für Microsoft Windows. For other operating systems, see the documentation for your operating system or see the MySQL documentation.

To run the license server, you need to install and configure MySQL:

1. Wechseln Sie auf der DVD zum [!DNL Third Party\MySQL\Installer\5.1] Ordner und Beginn Sie das Programm für die Installation.
1. Compete the MySQL installation.
1. Wählen Sie **[!UICONTROL Configure MySQL Server Now]** die Option zum Beginn des Konfigurationsassistenten.
1. Verwenden Sie bis zum fünften Bildschirm die Standardeinstellungen oder wählen Sie bestimmte Einstellungen für Ihren Test aus.
1. On the fifth screen, select **[!UICONTROL Online Transaction Processing (OLTP)]** or **[!UICONTROL Manual Setting]** and enter the maximum number of allowed connections.
1. Notieren Sie sich das Stammkennwort.
1. Führen Sie die folgenden Schritte aus, um MySQL neu zu installieren, wenn Sie den Server später erneut installieren müssen:
   1. Löschen Sie das *Systemlaufwerk:* Ordner.

      This folder is located in [!DNL \Documents and Settings\All Users\Application Data\MySQL].
   1. Delete the old MySQL install folder.

      For example, *system drive:*, which is located in [!DNL \Program Files\MySQL\MySQL Server 5.1].
1. To install MySQL JDBC Driver 5.1.7, copy the [!DNL mysql-connector-java-5.1.7-bin.jar] file in the [!DNL Third Party\MySQL\Installer\5.1] folder on the DVD to the [!DNL ...\Tomcat6.0\lib] directory on the Tomcat Server.

   >[!NOTE]
   >
   >MySQL JDBC Driver 5.1.7 works with Tomcat 6.0. Older versions of Tomcat are no longer supported.

