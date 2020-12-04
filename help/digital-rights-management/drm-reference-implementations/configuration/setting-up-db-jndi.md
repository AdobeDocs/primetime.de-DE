---
description: 'null'
seo-description: 'null'
seo-title: Einrichten der Lizenzserver-Datenbank
title: Einrichten der Lizenzserver-Datenbank
uuid: aa6185f2-8e9d-4b65-971a-b7534d910580
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# Einrichten der Lizenzserverdatenbank{#set-up-the-license-server-database}

Der Referenz-Implementierungslizenzserver benötigt eine Datenbank, um Folgendes zu unterstützen:

* Benutzerauthentifizierung
* Demogeschäftsregeln zum Gebrauchsmodell
* Metadaten-Konvertierung
* Domänenunterstützung

Für die anonyme Lizenzerfassung ist es nicht erforderlich, dass die Datenbank ausgeführt wird.

>[!NOTE]
>
>Dieses Verfahren gilt nur für Microsoft Windows. Andere Betriebssysteme finden Sie in der Dokumentation zu Ihrem Betriebssystem oder in der MySQL-Dokumentation.

Zum Ausführen des Lizenzservers müssen Sie MySQL installieren und konfigurieren:

1. Wechseln Sie auf der DVD zum Ordner [!DNL Third Party\MySQL\Installer\5.1] und Beginn Sie das Programm Installation.
1. Schließen Sie die MySQL-Installation ab.
1. Wählen Sie **[!UICONTROL Configure MySQL Server Now]** aus, um den Konfigurationsassistenten Beginn.
1. Verwenden Sie bis zum fünften Bildschirm die Standardeinstellungen oder wählen Sie bestimmte Einstellungen für Ihren Test aus.
1. Wählen Sie im fünften Bildschirm **[!UICONTROL Online Transaction Processing (OLTP)]** oder **[!UICONTROL Manual Setting]** und geben Sie die maximale Anzahl der zulässigen Verbindungen ein.
1. Notieren Sie sich das Stammkennwort.
1. Führen Sie die folgenden Schritte aus, um MySQL neu zu installieren, wenn Sie den Server später erneut installieren müssen:
   1. Löschen Sie den Ordner *Systemlaufwerk:*.

      Dieser Ordner befindet sich in [!DNL \Documents and Settings\All Users\Application Data\MySQL].
   1. Löschen Sie den alten MySQL-Installationsordner.

      Beispiel: *Systemlaufwerk:*, das sich in [!DNL \Program Files\MySQL\MySQL Server 5.1] befindet.
1. Um den MySQL JDBC-Treiber 5.1.7 zu installieren, kopieren Sie die Datei [!DNL mysql-connector-java-5.1.7-bin.jar] im Ordner [!DNL Third Party\MySQL\Installer\5.1] auf der DVD in den Ordner [!DNL ...\Tomcat6.0\lib] auf dem Tomcat-Server.

   >[!NOTE]
   >
   >MySQL JDBC Driver 5.1.7 funktioniert mit Tomcat 6.0. Ältere Versionen von Tomcat werden nicht mehr unterstützt.

