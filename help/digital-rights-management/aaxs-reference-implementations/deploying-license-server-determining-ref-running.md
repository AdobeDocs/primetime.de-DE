---
description: 'null'
seo-description: 'null'
seo-title: Bestimmen, ob der Referenz-Implementierungslizenzserver ordnungsgemäß ausgeführt wird
title: Bestimmen, ob der Referenz-Implementierungslizenzserver ordnungsgemäß ausgeführt wird
uuid: 84d32c94-7594-464e-a883-5338b52de2bf
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Bestimmen, ob der Referenz-Implementierungslizenzserver ordnungsgemäß ausgeführt wird {#determining-if-reference-implementation-license-server-is-running-properly}

Es gibt mehrere Möglichkeiten, um festzustellen, ob Ihr Server korrekt gestartet wurde. Die Anzeige der [!DNL catalina.log] Protokolle ist möglicherweise nicht ausreichend, da der Lizenzserver sich bei seinen eigenen Protokolldateien anmeldet. Führen Sie die folgenden Schritte aus, um sicherzustellen, dass Ihre Referenzimplementierung ordnungsgemäß gestartet wurde.

* Überprüfen Sie Ihre [!DNL AdobeFlashAccess.log] Datei. Hier schreibt die Referenzimplementierung Protokollinformationen. Der Speicherort dieser Protokolldatei wird durch Ihre [!DNL log4j.xml] Datei angegeben und kann so geändert werden, dass er auf einen beliebigen Speicherort verweist. Standardmäßig wird die Protokolldatei in das Arbeitsverzeichnis ausgegeben, in dem Sie catalina ausgeführt haben.

* Navigieren Sie zur folgenden URL: `https:///flashaccess/license/v4<your server:server port>`. Sie sollten den Text &quot;License Server ist korrekt eingerichtet&quot;sehen.

Eine andere Möglichkeit, zu testen, ob Ihr Server ordnungsgemäß ausgeführt wird, besteht darin, ein Testinhalt zu verpacken, einen Beispiel-Videoplayer einzurichten und abzuspielen. Im folgenden Verfahren wird dieser Vorgang beschrieben:

1. Navigieren Sie zum [!DNL \Reference Implementation\Command Line Tools] Ordner. Informationen zum Installieren der Befehlszeilenwerkzeuge finden Sie unter [Installieren der Befehlszeilenwerkzeuge](../aaxs-reference-implementations/command-line-tools/aaxs-ref-impl-command-line-overview.md#installing-the-command-line-tools).

1. Erstellen Sie eine einfache anonyme Richtlinie mit dem folgenden Befehl:

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Weitere Informationen zum Erstellen von Richtlinien mit dem Policy Manager finden Sie unter [Befehlszeilenverwendung](../aaxs-reference-implementations/command-line-tools/policy-manager/command-line-usage.md).

1. Legen Sie die `encrypt.license.serverurl` Eigenschaft in der [!DNL flashaccesstools.properties] Datei auf die URL des Lizenzservers fest (z. B. `https:// localhost:8080/`). Die [!DNL flashaccesstools.properties] Datei befindet sich im [!DNL \Reference Implementation\Command Line Tools] Ordner.

1. Komprimieren Sie Inhalte mit dem folgenden Befehl:

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

1. Kopieren Sie die 2 generierten Dateien in den Tomcat- [!DNL webapps\ROOT\Content] Ordner.
1. Navigieren Sie zum Tomcat- `Reference Implementation\Sample Video Players\Desktop\Flash Player\Release` Ordner `webapps\ROOT\SVP\` und kopieren Sie ihn.
1. Installieren Sie Flash Player 10.1 oder höher.
1. Öffnen Sie den Webbrowser und navigieren Sie zur folgenden URL:

   `https:// localhost:8080/SVP/player.html`
1. Navigieren Sie zur folgenden URL und klicken Sie dann auf die Schaltfläche Abspielen:

   `https:// localhost:8080/Content/<your_encrypted_FLV>`
1. Wenn das Video nicht abgespielt werden kann, prüfen Sie, ob Fehlercodes im Protokollbereich des Beispiel-Video-Players oder in der `AdobeFlashAccess.log` Datei geschrieben wurden. Der Speicherort der `AdobeFlashAccess.log` Protokolldatei wird durch Ihre Datei &quot;log4j.xml&quot;angegeben und kann so geändert werden, dass sie auf einen beliebigen Speicherort verweist. Standardmäßig wird die Protokolldatei in das Arbeitsverzeichnis geschrieben, in dem Sie catalina ausgeführt haben.
