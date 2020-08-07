---
seo-title: Setting up the database and configuring the JNDI datasource
title: Setting up the database and configuring the JNDI datasource
uuid: 1326523f-c053-4169-a934-1b2d3907b1f4
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# Setting up the database and configuring the JNDI datasource {#setting-up-the-database-and-configuring-the-jndi-datasource}

The reference implementation license server requires a database to support the following features:

* User authentication
* Usage model demo business rules
* Metadata conversion
* Domain support

Anonymous license acquisition does not require a database to be running.

>[!NOTE]
>
>The instructions in this section are for the Microsoft Windows platform. For other operating systems, see the documentation for your operating system or see the MySQL documentation.

To run the license server, you will need to install and configure MySQL 5.1.34:

1. Run the MySQL installer (found in the Third Party\MySQL\Installer\5.1 folder on the DVD).
1. Überprüfen Sie am Ende des Installationsvorgangs den Konfigurationsassistenten **[!UICONTROL Configure MySQL Server Now]** auf Beginn. Verwenden Sie die Standardeinstellungen oder wählen Sie spezifische Einstellungen für Ihre Testzwecke aus, mit der Ausnahme, dass Sie im 5. Bildschirm die maximal zulässige Anzahl von Verbindungen auswählen **[!UICONTROL Online Transaction Processing (OLTP)]** oder **[!UICONTROL Manual Setting]** und eingeben müssen.

1. Notieren Sie sich das Stammkennwort.
1. Wenn Sie MySQL neu installieren müssen, führen Sie die folgenden Schritte aus, um Probleme beim anschließenden Starten des Servers zu vermeiden:

   * Löschen Sie das *Systemlaufwerk des Ordners:* [!DNL \Documents and Settings\All Users\Application Data\MySQL].

   * Löschen Sie den alten MySQL-Installationsordner: Beispiel: *Systemlaufwerk:* [!DNL \Program Files\MySQL\MySQL Server 5.1].

Als Nächstes müssen Sie den MySQL JDBC-Treiber 5.1.7 installieren. Kopieren Sie dazu [!DNL mysql-connector-java-5.1.7-bin.jar] (im [!DNL Third Party\MySQL\Installer\5.1] Ordner auf der DVD) in den Ordner &quot;Tomcat Server lib&quot;: [!DNL ...\Tomcat6.0\lib].

>[!NOTE]
>
>MySQL JDBC Driver 5.1.7 funktioniert mit Tomcat 6.0. Ältere Versionen von Tomcat werden nicht unterstützt.

Richten Sie die Beispieldatenbank ein, indem Sie das Schema einrichten und die Datenbank mit Musterdaten füllen. Führen Sie dazu die folgenden Schritte aus:

1. Gehen Sie zu **[!UICONTROL Window's Start Menu]** > **[!UICONTROL MySQL]** > **[!UICONTROL MySQL Server 5.1]** > **[!UICONTROL MySQL Command Line Client]** .
1. Nachdem Sie das Kennwort eingegeben haben, führen Sie das folgende SQL-Schema aus, um das Benutzerkonto zum Herstellen einer Verbindung über eine Webanwendung hinzuzufügen, und erstellen Sie das Datenbankskript (stellen Sie sicher, dass am Ende kein &quot;;&quot;steht). `dbuser` Drücken Sie einfach die Eingabetaste.)

   ```
       mysql> source “Reference Implementation\Server\dbscript\createsampledb.sql”
   ```

1. Bearbeiten Sie das Skript, das Beispieldaten in den Tabellen ausfüllt, um Daten zu Testzwecken einzuschließen: [!DNL Reference Implementation\Server\dbscript\PopulateSampleDB.sql].
1. Führen Sie dieses Skript aus, um die Daten wie in Schritt 2 auszufüllen.

>[!NOTE]
>
>Wenn Sie das [!DNL CreateSampleDB.sql] Skript zum ersten Mal ausführen, erhalten Sie den folgenden Fehler:

*FEHLER 1396 (HY000): Operation DROP USER fehlgeschlagen für &#39;dbuser&#39;@&#39;localhost&#39; Abfrage OK, 0 Zeilen betroffen (0,00 Sek.).*

Sie können diesen Fehler ignorieren. Dies geschieht nur, wenn Sie dieses Skript zum ersten Mal ausführen.

An dieser Stelle müssen Sie Datenbankverbindung-Pooling (DBCP) konfigurieren. DBCP verwendet den Jakarta-Commons Database Connection Pool. Eine JNDI-Datenquelle-TestDB ist so konfiguriert, dass sie diese Verbindungspools des Anwendungsservers nutzen kann. Um die Datenbankverbindung so zu ändern, dass sie auf einen MySQL-Server verweist, der sich nicht auf localhost befindet, ändern Sie die [!DNL META-INF\context.xml] Datei (die den Speicherort, den Benutzernamen und das Kennwort der Datenbank des Lizenzservers angibt) in [!DNL flashaccess.war]oder ändern [!DNL \Reference Implementation\Server\refimpl\WebContent\META-INF\context.xml] und erstellen Sie die WAR-Datei mithilfe der aktualisierten Dateien neu. Um einen dieser Parameter zu ändern, bearbeiten Sie den [!DNL context.xml] Ordner im WebContent-Ordner und verwenden Sie das Ant-Skript, um die WAR-Datei neu zu erstellen. Um die Datenbank anzupassen, ändern Sie die JNDI-Datenquelleneinstellungen in dieser Datei.

Wenn Sie das Projekt &quot;Referenzimplementierung&quot;in Eclipse debuggen, müssen Sie der Konfiguration `$CATALINA_HOME\lib\tomcat-dbcp.jar` &quot;Ausführen/Debuggen&quot;hinzufügen. Dieser Schritt ist nicht erforderlich, wenn Sie die [!DNL flashaccess.war] Datei auf einem eigenständigen Tomcat 6.0-Server ausführen.
