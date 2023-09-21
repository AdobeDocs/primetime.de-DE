---
title: Bestimmen, ob der Lizenzserver für Referenzimplementierung ordnungsgemäß ausgeführt wird
description: Bestimmen, ob der Lizenzserver für Referenzimplementierung ordnungsgemäß ausgeführt wird
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Bestimmen, ob der Lizenzserver für Referenzimplementierung ordnungsgemäß ausgeführt wird {#determining-if-reference-implementation-license-server-runs-properly}

Es gibt mehrere Möglichkeiten, festzustellen, ob Ihr Referenz-Implementierungs-Lizenzserver ordnungsgemäß gestartet wurde. Sie können die [!DNL catalina.log] -Protokolle reichen möglicherweise nicht aus, da der Lizenzserver seine eigenen Protokolldateien protokolliert. Führen Sie die folgenden Schritte aus, um sicherzustellen, dass Ihre Referenzimplementierung ordnungsgemäß gestartet wurde.

* Überprüfen Sie Ihre [!DNL AdobeFlashAccess.log] -Datei. Hier schreibt die Referenzimplementierung Protokollinformationen. Der Speicherort dieser Protokolldatei wird durch Ihre [!DNL log4j.xml] und können geändert werden, um auf einen beliebigen Ort zu verweisen. Standardmäßig wird die Protokolldatei in das Arbeitsverzeichnis kopiert, in das Sie catalina ausführen.

* Gehen Sie zur folgenden URL: [!DNL https:// flashaccess/license/v4]*Ihr Server:Server-Anschluss*. Sie sollten den Text &quot;Lizenzserver ist richtig eingerichtet&quot;sehen.

Eine weitere Möglichkeit, zu testen, ob Ihr Server ordnungsgemäß ausgeführt wird, besteht darin, ein Segment des Testinhalts zu verpacken, einen Beispiel-Videoplayer einzurichten und anschließend abzuspielen.

Im folgenden Verfahren wird dieser Vorgang beschrieben:

1. Navigieren Sie zu [!DNL \Reference Implementation\Command Line Tools] Ordner.

   Siehe [Installieren der Befehlszeilen-Tools](../drm-reference-implementations/command-line-tools/install-command-line-tools.md) Informationen zur Installation der Befehlszeilen-Tools.

1. Geben Sie den folgenden Befehl ein, um eine einfache anonyme DRM-Richtlinie zu erstellen:

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Siehe [Befehlszeilenverwendung](../drm-reference-implementations/command-line-tools/configure-command-line-tools/policy-manager/policy-manager-command-line-usage.md) Informationen zum Erstellen von DRM-Richtlinien mit dem DRM Policy Manager.

1. Legen Sie die `encrypt.license.serverurl` -Eigenschaft in der [!DNL flashaccesstools.properties] -Datei an die URL des Lizenzservers.

   Beispiel: [!DNL https:// localhost:8080/]. Die [!DNL flashaccesstools.properties] befindet sich im [!DNL \Reference Implementation\Command Line Tools] Ordner.

1. Geben Sie den folgenden Befehl ein, um ein Segment des Inhalts zu verpacken:

```
       java -jar libs\AdobePackager.jar  
       <i class="+ topic ph hi-d="" i "="">
         test_input_FLV  
        <i class="+ topic ph hi-d="" i "="">
       output_file  
               -p policy_test.pol 
       </i class="+ topic> 
       </i class="+ topic>
```

1. Kopieren Sie die beiden generierten Dateien in die [!DNL webapps\ROOT\Content] auf dem Tomcat-Server.
1. Navigieren Sie zu [!DNL Reference Implementation\Sample Video Players\Desktop\Flash Player\Release] und kopieren Sie den Inhalt in den [!DNL webapps\ROOT\SVP\] auf dem Tomcat-Server.

1. Installieren Sie Flash Player Version 10.1 oder höher.
1. Öffnen Sie einen Webbrowser und navigieren Sie zur folgenden URL: [!DNL        https:// localhost:8080/SVP/player.html]

1. Gehen Sie zur folgenden URL und klicken Sie auf **[!UICONTROL Play]**: [!DNL https:// localhost:8080/Content/] *`your_encrypted_FLV`*.

1. Wenn die Wiedergabe des Videos fehlschlägt, überprüfen Sie, ob im Protokollfenster des Beispiel-Video-Players Fehlercodes angezeigt oder zum [!DNL AdobeFlashAccess.log] -Datei.

   Sie können jetzt nach dem Speicherort der [!DNL AdobeFlashAccess.log] Protokolldatei in der Datei log4j.xml speichern und dann ändern. Standardmäßig wird die Protokolldatei in das Arbeitsverzeichnis kopiert, in das Sie die Katalina ausführen.
