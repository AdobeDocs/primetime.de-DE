---
title: Einrichten der Datenbank und Konfigurieren der JNDI-Datenquelle
description: Einrichten der Datenbank und Konfigurieren der JNDI-Datenquelle
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Einrichten der Datenbank und Konfigurieren der JNDI-Datenquelle {#setting-up-the-database-and-configuring-the-jndi-datasource}

Der Referenz-Implementierungslizenzserver benötigt eine Datenbank, um die folgenden Funktionen zu unterstützen:

* Benutzerauthentifizierung
* Geschäftsregeln der Demovorlage für Nutzungsmodelle
* Metadatenkonvertierung
* Domänenunterstützung

Für die anonyme Lizenzakquise ist keine Datenbank erforderlich.

>[!NOTE]
>
>Die Anweisungen in diesem Abschnitt richten sich an die Microsoft Windows-Plattform. Weitere Betriebssysteme finden Sie in der Dokumentation für Ihr Betriebssystem oder in der MySQL-Dokumentation.

Um den Lizenzserver auszuführen, müssen Sie MySQL 5.1.34 installieren und konfigurieren:

1. Führen Sie das MySQL-Installationsprogramm aus (befindet sich im Ordner &quot;Dritte Party\MySQL\Installer\5.1&quot;auf der DVD).
1. Überprüfen Sie nach Abschluss des Installationsvorgangs die **[!UICONTROL Configure MySQL Server Now]** um den Konfigurationsassistenten zu starten. Verwenden Sie die Standardeinstellungen oder wählen Sie bestimmte Einstellungen für Ihre Testzwecke aus, mit der Ausnahme, dass Sie auf dem 5. Bildschirm **[!UICONTROL Online Transaction Processing (OLTP)]** oder **[!UICONTROL Manual Setting]** und geben Sie die maximal zulässige Anzahl von Verbindungen an.

1. Notieren Sie sich das Root-Kennwort.
1. Wenn Sie MySQL neu installieren müssen, führen Sie die folgenden Schritte aus, um Probleme beim anschließenden Starten des Servers zu vermeiden:

   * Ordner löschen *Systemlaufwerk:* [!DNL \Documents and Settings\All Users\Application Data\MySQL].

   * Löschen Sie den alten MySQL-Installationsordner, beispielsweise: *Systemlaufwerk:* [!DNL \Program Files\MySQL\MySQL Server 5.1].

Als Nächstes müssen Sie den MySQL JDBC-Treiber 5.1.7 installieren. Kopieren Sie dazu [!DNL mysql-connector-java-5.1.7-bin.jar] (gefunden in der [!DNL Third Party\MySQL\Installer\5.1] -Ordner auf der DVD) in den Ordner &quot;Tomcat Server lib&quot;: [!DNL ...\Tomcat6.0\lib].

>[!NOTE]
>
>MySQL JDBC Driver 5.1.7 funktioniert mit Tomcat 6.0. Ältere Versionen von Tomcat werden nicht unterstützt.

Richten Sie die Beispieldatenbank ein, indem Sie das Datenbankschema einrichten und die Datenbank mit Beispieldaten füllen. Führen Sie dazu die folgenden Schritte aus:

1. Navigieren Sie zu  **[!UICONTROL Window's Start Menu]** > **[!UICONTROL MySQL]** > **[!UICONTROL MySQL Server 5.1]** > **[!UICONTROL MySQL Command Line Client]** .
1. Führen Sie nach Eingabe des Kennworts das folgende SQL-Skript aus, um das Benutzerkonto hinzuzufügen `dbuser` zum Herstellen einer Verbindung über eine Webanwendung und zum Erstellen eines Datenbankschemas (stellen Sie sicher, dass am Ende kein &quot;;&quot;steht. Drücken Sie einfach die Eingabetaste.)

   ```
       mysql> source “Reference Implementation\Server\dbscript\createsampledb.sql”
   ```

1. Bearbeiten Sie das Skript, das Beispieldaten in die Tabellen füllt, um Daten für Ihre Testzwecke einzuschließen: [!DNL Reference Implementation\Server\dbscript\PopulateSampleDB.sql].
1. Führen Sie dieses Skript aus, um die Daten wie in Schritt 2 angegeben auszufüllen.

>[!NOTE]
>
>Beim ersten Ausführen der [!DNL CreateSampleDB.sql] Skript erhalten Sie den folgenden Fehler:

*FEHLER 1396 (HY000): Operation DROP USER failed for &#39;dbuser&#39;@&#39;localhost&#39; Query OK, 0 Zeilen betroffen (0,00 Sek.).*

Sie können diesen Fehler ignorieren. Dies geschieht nur beim ersten Ausführen dieses Skripts.

An dieser Stelle müssen Sie das Datenbankverbindungs-Pooling (DBCP) konfigurieren. DBCP verwendet den Jakarta-Commons Database Connection Pool. Eine JNDI-Datenquellen-TestDB ist so konfiguriert, dass sie dieses Verbindungspooling für den Anwendungsserver nutzen kann. Um die Datenbankverbindung so zu ändern, dass sie auf einen MySQL-Server verweist, der sich nicht auf localhost befindet, ändern Sie die [!DNL META-INF\context.xml] -Datei (die den Speicherort, den Benutzernamen und das Kennwort der Datenbank des Lizenzservers angibt) in [!DNL flashaccess.war]oder ändern [!DNL \Reference Implementation\Server\refimpl\WebContent\META-INF\context.xml] und erstellen Sie die WAR-Datei mithilfe der aktualisierten Dateien neu. Um einen dieser Parameter zu ändern, bearbeiten Sie die [!DNL context.xml] im Ordner WebContent gespeichert sind und das Ant-Skript verwenden, um die WAR-Datei neu zu erstellen. Um die Datenbank anzupassen, ändern Sie die JNDI-Datenquelleneinstellungen in dieser Datei.

Wenn Sie das Projekt &quot;Referenzimplementierung&quot;in Eclipse debuggen, müssen Sie `$CATALINA_HOME\lib\tomcat-dbcp.jar` auf Ihre Ausführungs-/Debugging-Konfiguration. Dieser Schritt ist nicht erforderlich, wenn Sie die [!DNL flashaccess.war] Datei auf einem eigenständigen Tomcat 6.0-Server.
