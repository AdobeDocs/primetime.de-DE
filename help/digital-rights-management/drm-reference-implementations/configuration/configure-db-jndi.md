---
description: 'null'
seo-description: 'null'
seo-title: Konfigurieren der Lizenzserverdatenbank
title: Konfigurieren der Lizenzserverdatenbank
uuid: 6d34e849-1616-46bd-ad18-4f98e6c45af7
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---


# Konfigurieren der Lizenzserverdatenbank{#configure-the-license-server-database}

So konfigurieren Sie die Beispieldatenbank, indem Sie das Schema einrichten und die Datenbank mit Beispieldaten füllen:

1. Öffnen Sie die MySQL-Befehlszeile.

   **Windows -** Klicken Sie auf   **[!UICONTROL Window's Start Menu]** >  **[!UICONTROL MySQL]** >  **[!UICONTROL MySQL Server 5.1]** >  **[!UICONTROL MySQL Command Line Client]**

   **Unter Linux, etc.** - Typ  `MySQL`.

1. Führen Sie das folgende SQL-Skript aus:

   mysql> source &quot;`"[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\createsampledb.sql" dbscript\createsampledb.sql`&quot;

   Dieses Skript fügt das Benutzerkonto `dbuser` hinzu, stellt eine Verbindung über eine Webanwendung her und erstellt ein Schema.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass am Ende des Skripts kein Semikolon ( `;`) steht.

1. Bearbeiten Sie das Skript `PopulateSampleDB.sql`, das Beispieldaten in den Tabellen füllt, um Daten für Ihre Tests einzuschließen.

   Dieses Skript befindet sich im Ordner `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\ dbscript\`.
1. Führen Sie das Skript [!DNL PopulateSampleDB] aus, um die Daten wie in Schritt 2 auszufüllen.

   >[!NOTE]
   >
   >Beim ersten Ausführen des Skripts [!DNL CreateSampleDB.sql] tritt der folgende Fehler auf:

   Sie können diesen Fehler ignorieren. Es tritt nur beim ersten Ausführen dieses Skripts ein.

Sie müssen die Datenbankverbindung-Zusammenführung (DBCP) konfigurieren, die den Jakarta-Commons-Datenbankverbindungspool verwendet. Eine JNDI-Datenquelle-TestDB ist so konfiguriert, dass sie diese Verbindungspools des Anwendungsservers nutzen kann. Um die Datenbankverbindung so zu ändern, dass sie auf einen MySQL-Server verweist, der sich nicht auf localhost befindet, ändern Sie eine der folgenden Dateien:

* Die Datei [!DNL META-INF\context.xml], die den Speicherort, den Benutzernamen und das Kennwort der Datenbank des Lizenzservers in der Datei [!DNL flashaccess.war] angibt.

* Die Datei `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl\WebContent/META-INF\context.xml`.

und erstellen Sie die WAR-Datei mithilfe der aktualisierten Dateien neu.

Um einen dieser Parameter zu ändern, bearbeiten Sie die Datei [!DNL context.xml] im Ordner [!DNL WebContent] und verwenden Sie das Ant-Skript, um die WAR-Datei neu zu erstellen. Um die Datenbank anzupassen, ändern Sie die JNDI-Datenquelleneinstellungen in dieser Datei.

Wenn Sie das Projekt &quot;Referenzimplementierung&quot;in Eclipse debuggen, fügen Sie `$CATALINA_HOME\lib\tomcat-dbcp.jar` Ihrer run/debug-Konfiguration hinzu.

>[!NOTE]
>
>Wenn Sie die Datei [!DNL flashaccess.war] auf einem eigenständigen Tomcat 6.0-Server ausführen, ist dieser Schritt nicht erforderlich.

