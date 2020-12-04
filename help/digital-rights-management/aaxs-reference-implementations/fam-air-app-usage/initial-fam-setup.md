---
description: 'null'
seo-description: 'null'
seo-title: Einrichten von Flash Access Manager
title: Einrichten von Flash Access Manager
uuid: e9041f7c-b098-4121-88bf-ff3e6369e01b
translation-type: tm+mt
source-git-commit: 4f196bbd079edeb1a423afee6b4b7e249d380f40
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---


# Einrichten des Flash Access-Managers beim Öffnen {#initial-flash-access-manager-setup}

Gehen Sie wie folgt vor, um Flash Access Manager einzurichten:

1. Stellen Sie den Packager-Server bereit. Dieser Server sollte nur Benutzern innerhalb Ihrer Firewall zur Verfügung stehen (stellen Sie diese Software nicht auf einem öffentlich zugänglichen Computer bereit). Weitere Informationen zum Bereitstellen des Servers finden Sie unter [Bereitstellen des Lizenzservers und des Pakets für überwachte Ordner](../../aaxs-reference-implementations/deploying-license-server-and-wfp/deploying-license-server-wfp-overview.md).

   * Kopieren Sie [!DNL flashaccess-packager.war] in den Webappordner von Tomcat.
   * Kopieren Sie [!DNL flashaccess-refimpl-packager.properties] aus den Ressourcen an einen Speicherort im Klassenpfad.
   * Beginn des Servers. Es werden einige Fehler aufgrund von Problemen in der Eigenschaftendatei angezeigt. wird erwartet, da die Eigenschaften noch nicht ausgefüllt wurden.

1. Installieren Sie die AIR-Flash Access-Manager-Anwendung, indem Sie die [!DNL .air]-Datei starten (AIR 1.5 oder höher erforderlich).
1. Starten Sie die AIR-Flash Access-Manager-Anwendung.

   Wenn Ihr Server an einem anderen Ort als `https://localhost:8080*` ausgeführt wird, treten Fehler auf, die darauf hinweisen, dass die Anwendung keine Verbindung zum Server herstellen kann. Schließen Sie das Fehlerdialogfeld und geben Sie auf der Registerkarte &quot;Voreinstellungen&quot;die richtige URL für die Packager Server-URL ein. Wenn der Server unter der angegebenen URL ausgeführt wird und sich die Eigenschaftendatei im Klassenpfad befindet, werden im Anzeigebereich &quot;Voreinstellungen&quot;die Werte in der Eigenschaftendatei angezeigt. Nachdem Sie die URL des Packager-Servers festgelegt haben, speichert die AIR-Anwendung diese Einstellung und Sie müssen sie beim nächsten Start der Anwendung nicht mehr eingeben.
1. Füllen Sie die Werte auf der Registerkarte Voreinstellungen aus und klicken Sie auf **[!UICONTROL Save]**.
1. Wenn Sie die überwachten Ordner verwenden möchten, müssen Sie den Server neu starten, um die Fehler, die Sie in Schritt 3 gesehen haben, zu beheben. Wenn die Voreinstellungen korrekt konfiguriert sind, sollten beim Starten keine Fehler auftreten.

