---
title: Lizenzserver-Datenbank konfigurieren
description: Lizenzserver-Datenbank konfigurieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Lizenzserver-Datenbank konfigurieren{#configure-the-license-server-database}

So konfigurieren Sie die Beispieldatenbank, indem Sie das Datenbankschema einrichten und die Datenbank mit Beispieldaten ausfüllen:

1. Öffnen Sie die MySQL-Befehlszeile.

   **Unter Windows:** Klicks  **[!UICONTROL Window's Start Menu]** > **[!UICONTROL MySQL]** > **[!UICONTROL MySQL Server 5.1]** > **[!UICONTROL MySQL Command Line Client]**

   **Unter Linux usw.** - Typ `MySQL`.

1. Führen Sie das folgende SQL-Skript aus:

   mysql> source &quot; `"[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\createsampledb.sql" dbscript\createsampledb.sql`&quot;

   Dieses Skript fügt das Benutzerkonto hinzu `dbuser`, stellt eine Verbindung über eine Webanwendung her und erstellt ein Datenbankschema.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass kein Semikolon ( `;`) am Ende des Skripts.

1. Bearbeiten Sie die `PopulateSampleDB.sql` -Skript, das Beispieldaten in die Tabellen füllt, um Daten für Ihre Tests einzuschließen.

   Dieses Skript befindet sich im `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\ dbscript\` Ordner.
1. Führen Sie die [!DNL PopulateSampleDB] -Skript, um die Daten wie in Schritt 2 zu füllen.

   >[!NOTE]
   >
   >Beim ersten Ausführen der [!DNL CreateSampleDB.sql] Skript der folgende Fehler auftritt:

   Sie können diesen Fehler ignorieren. Es tritt nur auf, wenn Sie dieses Skript zum ersten Mal ausführen.

Sie müssen das Datenbankverbindungspool (DBCP) konfigurieren, das den Jakarta-Commons Database Connection Pool verwendet. Eine JNDI-Datenquellen-TestDB ist so konfiguriert, dass sie dieses Verbindungspooling für den Anwendungsserver nutzen kann. Um die Datenbankverbindung so zu ändern, dass sie auf einen MySQL-Server verweist, der sich nicht auf localhost befindet, ändern Sie eine der folgenden Dateien:

* Die [!DNL META-INF\context.xml] -Datei, die den Speicherort, den Benutzernamen und das Kennwort der Datenbank des Lizenzservers angibt, die sich in der [!DNL flashaccess.war] -Datei.

* Die `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl\WebContent/META-INF\context.xml` -Datei.

und erstellen Sie die WAR-Datei mithilfe der aktualisierten Dateien neu.

Um einen dieser Parameter zu ändern, bearbeiten Sie die [!DNL context.xml] in der Datei [!DNL WebContent] und verwenden Sie das Ant-Skript, um die WAR-Datei neu zu erstellen. Um die Datenbank anzupassen, ändern Sie die JNDI-Datenquelleneinstellungen in dieser Datei.

Wenn Sie das Projekt &quot;Referenzimplementierung&quot;in Eclipse debuggen, fügen Sie `$CATALINA_HOME\lib\tomcat-dbcp.jar` auf Ihre Ausführungs-/Debugging-Konfiguration.

>[!NOTE]
>
>Wenn Sie die [!DNL flashaccess.war] -Datei auf einem eigenständigen Tomcat 6.0-Server speichern, ist dieser Schritt nicht erforderlich.
