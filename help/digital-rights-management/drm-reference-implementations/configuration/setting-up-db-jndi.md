---
title: Einrichten der Lizenzserver-Datenbank
description: Einrichten der Lizenzserver-Datenbank
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Einrichten der Lizenzserver-Datenbank{#set-up-the-license-server-database}

Der Referenz-Implementierungslizenzserver benötigt eine Datenbank, um Folgendes zu unterstützen:

* Benutzerauthentifizierung
* Geschäftsregeln der Demovorlage für Nutzungsmodelle
* Metadatenkonvertierung
* Domänenunterstützung

Für die anonyme Lizenzakquise muss die Datenbank nicht ausgeführt werden.

>[!NOTE]
>
>Dieses Verfahren gilt nur für Microsoft Windows. Weitere Betriebssysteme finden Sie in der Dokumentation für Ihr Betriebssystem oder in der MySQL-Dokumentation.

Um den Lizenzserver auszuführen, müssen Sie MySQL installieren und konfigurieren:

1. Wechseln Sie auf der DVD zum [!DNL Third Party\MySQL\Installer\5.1] und starten Sie das Installationsprogramm.
1. Schließen Sie die MySQL-Installation ab.
1. Auswählen **[!UICONTROL Configure MySQL Server Now]** um den Konfigurationsassistenten zu starten.
1. Verwenden Sie bis zum fünften Bildschirm die Standardeinstellungen oder wählen Sie bestimmte Einstellungen für Ihre Tests aus.
1. Wählen Sie im fünften Bildschirm die Option **[!UICONTROL Online Transaction Processing (OLTP)]** oder **[!UICONTROL Manual Setting]** und geben Sie die maximal zulässige Anzahl von Verbindungen an.
1. Notieren Sie sich das Stammkennwort.
1. Führen Sie die folgenden Schritte aus, um MySQL neu zu installieren, wenn Sie den Server später starten müssen:
   1. Löschen Sie die *Systemlaufwerk:* Ordner.

      Dieser Ordner befindet sich unter [!DNL \Documents and Settings\All Users\Application Data\MySQL].
   1. Löschen Sie den alten MySQL-Installationsordner.

      Beispiel: *Systemlaufwerk:*, das sich in [!DNL \Program Files\MySQL\MySQL Server 5.1].
1. Kopieren Sie zum Installieren des MySQL JDBC-Treibers 5.1.7 den [!DNL mysql-connector-java-5.1.7-bin.jar] in der Datei [!DNL Third Party\MySQL\Installer\5.1] Ordner auf der DVD auf der [!DNL ...\Tomcat6.0\lib] auf dem Tomcat-Server.

   >[!NOTE]
   >
   >MySQL JDBC Driver 5.1.7 funktioniert mit Tomcat 6.0. Ältere Versionen von Tomcat werden nicht mehr unterstützt.
