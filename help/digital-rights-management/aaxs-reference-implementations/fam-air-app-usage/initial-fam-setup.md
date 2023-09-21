---
title: Einrichten des anfänglichen Flash Access Managers
description: Einrichten des anfänglichen Flash Access Managers
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Einrichten des anfänglichen Flash Access Managers {#initial-flash-access-manager-setup}

Gehen Sie wie folgt vor, um Flash Access Manager einzurichten:

1. Stellen Sie den Paketserver bereit. Dieser Server sollte nur für Benutzer in Ihrer Firewall verfügbar sein (stellen Sie diese Software nicht auf einem öffentlich zugänglichen Computer bereit). Weitere Informationen zur Bereitstellung des Servers finden Sie unter [Bereitstellen des Lizenzservers und des überwachten Ordner-Packagers](../../aaxs-reference-implementations/deploying-license-server-and-wfp/deploying-license-server-wfp-overview.md).

   * Kopieren [!DNL flashaccess-packager.war] in den Ordner webapps von Tomcat.
   * Kopieren [!DNL flashaccess-refimpl-packager.properties] von Ressourcen an einen Speicherort im Klassenpfad.
   * Starten Sie den Server. Es werden einige Fehler aufgrund von Problemen in der Eigenschaftendatei angezeigt. Dies ist zu erwarten, da die Eigenschaften noch nicht ausgefüllt wurden.

1. Installieren Sie die Flash Access Manager AIR-Anwendung, indem Sie die [!DNL .air] -Datei (erfordert AIR 1.5 oder höher).
1. Starten Sie die Flash Access Manager AIR-Anwendung.

   Wenn Ihr Server an einer anderen Stelle als `https://localhost:8080*`angezeigt, werden Fehler angezeigt, die darauf hinweisen, dass die Anwendung keine Verbindung zum Server herstellen kann. Schließen Sie das Fehlerdialogfeld und geben Sie auf der Registerkarte &quot;Voreinstellungen&quot;die richtige URL für die Paketserver-URL ein. Wenn der Server unter der angegebenen URL ausgeführt wird und sich die Eigenschaftendatei im Klassenpfad befindet, wird der Bildschirm &quot;Voreinstellungen&quot;mit den Werten in der Eigenschaftendatei gefüllt. Nachdem Sie die Paketserver-URL festgelegt haben, speichert die AIR-Anwendung diese Einstellung und Sie müssen sie nicht beim nächsten Start der Anwendung eingeben.
1. Füllen Sie die Werte auf der Registerkarte Voreinstellungen aus und klicken Sie auf **[!UICONTROL Save]**.
1. Wenn Sie die überwachten Ordner verwenden möchten, müssen Sie den Server neu starten, um die in Schritt 3 aufgetretenen Fehler zu beheben. Wenn die Voreinstellungen ordnungsgemäß konfiguriert sind, sollten beim Start keine Fehler auftreten.
