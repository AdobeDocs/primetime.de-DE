---
title: Bestimmen, ob der Lizenzserver für Referenzimplementierung ordnungsgemäß ausgeführt wird
description: Bestimmen, ob der Lizenzserver für Referenzimplementierung ordnungsgemäß ausgeführt wird
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Bestimmen, ob der Lizenzserver für Referenzimplementierung ordnungsgemäß ausgeführt wird {#determining-if-reference-implementation-license-server-is-running-properly}

Es gibt mehrere Möglichkeiten, festzustellen, ob Ihr Server ordnungsgemäß gestartet wurde. Anzeigen der [!DNL catalina.log] -Protokolle reichen möglicherweise nicht aus, da der Lizenzserver seine eigenen Protokolldateien protokolliert. Führen Sie die folgenden Schritte aus, um sicherzustellen, dass Ihre Referenzimplementierung ordnungsgemäß gestartet wurde.

* Überprüfen Sie Ihre [!DNL AdobeFlashAccess.log] -Datei. Hier schreibt die Referenzimplementierung Protokollinformationen. Der Speicherort dieser Protokolldatei wird durch Ihre [!DNL log4j.xml] und können geändert werden, um auf einen beliebigen Ort zu verweisen. Standardmäßig wird die Protokolldatei in das Arbeitsverzeichnis ausgegeben, in dem Sie catalina ausgeführt haben.

* Navigieren Sie zur folgenden URL: `https:///flashaccess/license/v4<your server:server port>`. Sie sollten den Text &quot;Lizenzserver ist richtig eingerichtet&quot;sehen.

Eine andere Möglichkeit, zu testen, ob Ihr Server ordnungsgemäß ausgeführt wird, besteht darin, einen Teil des Testinhalts zu verpacken, einen Beispiel-Videoplayer einzurichten und abzuspielen. Im folgenden Verfahren wird dieser Vorgang beschrieben:

1. Navigieren Sie zum [!DNL \Reference Implementation\Command Line Tools] Ordner. Informationen zum Installieren der Befehlszeilen-Tools finden Sie unter [Installieren der Befehlszeilen-Tools](../aaxs-reference-implementations/command-line-tools/aaxs-ref-impl-command-line-overview.md#installing-the-command-line-tools).

1. Erstellen Sie mit dem folgenden Befehl eine einfache anonyme Richtlinie:

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Weitere Informationen zum Erstellen von Richtlinien mit dem Policy Manager finden Sie unter [Befehlszeilenverwendung](../aaxs-reference-implementations/command-line-tools/policy-manager/command-line-usage.md).

1. Legen Sie die `encrypt.license.serverurl` -Eigenschaft in der [!DNL flashaccesstools.properties] Datei an die URL des Lizenzservers (z. B. `https:// localhost:8080/`). Die [!DNL flashaccesstools.properties] befindet sich unter der [!DNL \Reference Implementation\Command Line Tools] Ordner.

1. Komprimieren Sie ein Inhaltselement mit dem folgenden Befehl:

   ```java
       java -jar libs\AdobePackager.jar  
   <i class="+ topic ph hi-d="" i "="">
   test_input_FLV  
   <i class="+ topic ph hi-d="" i "="">
   output_file  
               -p policy_test.pol 
   </i class="+ topic> 
   </i class="+ topic>
   ```

1. Kopieren Sie die beiden generierten Dateien in den Tomcat [!DNL webapps\ROOT\Content] Ordner.
1. Navigieren Sie zu `Reference Implementation\Sample Video Players\Desktop\Flash Player\Release` und kopieren Sie den Inhalt in den Tomcat `webapps\ROOT\SVP\` Ordner.
1. Installieren Sie Flash Player 10.1 oder höher.
1. Öffnen Sie den Webbrowser und navigieren Sie zur folgenden URL:

   `https:// localhost:8080/SVP/player.html`
1. Navigieren Sie zur folgenden URL und klicken Sie auf die Schaltfläche Abspielen :

   `https:// localhost:8080/Content/<your_encrypted_FLV>`
1. Wenn die Wiedergabe des Videos fehlschlägt, überprüfen Sie, ob im Protokollbereich des Beispiel-Video-Players oder im `AdobeFlashAccess.log` -Datei. Der Speicherort der `AdobeFlashAccess.log` Die Protokolldatei wird durch Ihre Datei log4j.xml angegeben und kann geändert werden, um auf einen beliebigen Speicherort zu verweisen. Standardmäßig wird die Protokolldatei in das Arbeitsverzeichnis geschrieben, in dem Sie catalina ausgeführt haben.
