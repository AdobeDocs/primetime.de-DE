---
description: 'null'
seo-description: 'null'
seo-title: Konfigurieren der Lizenzserverdatenbank
title: Konfigurieren der Lizenzserverdatenbank
uuid: 6d34e849-1616-46bd-ad18-4f98e6c45af7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Konfigurieren der Lizenzserverdatenbank{#configure-the-license-server-database}

So konfigurieren Sie die Beispieldatenbank, indem Sie das Schema einrichten und die Datenbank mit Beispieldaten füllen:

1. Öffnen Sie die MySQL-Befehlszeile.

   **Windows -** Klicken Sie auf **[!UICONTROL Window's Start Menu]** > **[!UICONTROL MySQL]** > **[!UICONTROL MySQL Server 5.1]** > **[!UICONTROL MySQL Command Line Client]**

   **Unter Linux, etc.** - Typ `MySQL`.

1. Führen Sie das folgende SQL-Skript aus:

   mysql> source &quot; `"[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\createsampledb.sql" dbscript\createsampledb.sql`&quot;

   Dieses Skript fügt das Benutzerkonto hinzu `dbuser`, stellt eine Verbindung über eine Webanwendung her und erstellt ein Datenbankkonto.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass am Ende des Skripts kein Semikolon ( `;`) steht.

1. Bearbeiten Sie das `PopulateSampleDB.sql` Skript, das Beispieldaten in den Tabellen ausfüllt, um Daten für Ihre Tests einzuschließen.

   Dieses Skript befindet sich im `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\ dbscript\` Ordner.
1. Führen Sie das [!DNL PopulateSampleDB] Skript aus, um die Daten wie in Schritt 2 auszufüllen.

   >[!NOTE] {class=&quot;- topic/note &quot;
   >
   >Beim ersten Ausführen des [!DNL CreateSampleDB.sql] Skripts tritt der folgende Fehler auf:

   Sie können diesen Fehler ignorieren. Es tritt nur beim ersten Ausführen dieses Skripts ein.

Sie müssen die Datenbankverbindung-Zusammenführung (DBCP) konfigurieren, die den Jakarta-Commons-Datenbankverbindungspool verwendet. Eine JNDI-Datenquelle-TestDB ist so konfiguriert, dass sie diese Verbindungspools des Anwendungsservers nutzen kann. Um die Datenbankverbindung so zu ändern, dass sie auf einen MySQL-Server verweist, der sich nicht auf localhost befindet, ändern Sie eine der folgenden Dateien:

* Die [!DNL META-INF\context.xml] Datei, die den Speicherort, den Benutzernamen und das Kennwort der Datenbank des Lizenzservers angibt, die sich in der [!DNL flashaccess.war] Datei befindet.

* Die `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl\WebContent/META-INF\context.xml` Datei.

und erstellen Sie die WAR-Datei mithilfe der aktualisierten Dateien neu.

Um diese Parameter zu ändern, bearbeiten Sie die [!DNL context.xml] Datei im Ordner und verwenden Sie das [!DNL WebContent] Ant-Skript, um die WAR-Datei neu zu erstellen. Um die Datenbank anzupassen, ändern Sie die JNDI-Datenquelleneinstellungen in dieser Datei.

Wenn Sie das Projekt &quot;Referenzimplementierung&quot;in Eclipse debuggen, fügen Sie es Ihrer run/debug-Konfiguration `$CATALINA_HOME\lib\tomcat-dbcp.jar` hinzu.

>[!NOTE]
>
>Wenn Sie die [!DNL flashaccess.war] Datei auf einem eigenständigen Tomcat 6.0-Server ausführen, ist dieser Schritt nicht erforderlich.

