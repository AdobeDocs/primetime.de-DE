---
description: 'null'
seo-description: 'null'
seo-title: Bestimmen, ob der Referenz-Implementierungslizenzserver ordnungsgemäß ausgeführt wird
title: Bestimmen, ob der Referenz-Implementierungslizenzserver ordnungsgemäß ausgeführt wird
uuid: afd82d6d-a11c-48ff-b48c-8f81d4b406a0
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Bestimmen, ob der Referenz-Implementierungslizenzserver ordnungsgemäß ausgeführt wird {#determining-if-reference-implementation-license-server-runs-properly}

Es gibt mehrere Möglichkeiten, um festzustellen, ob Ihr Referenz-Implementierungslizenzserver korrekt gestartet wurde. Sie können die Ansicht der [!DNL catalina.log] Protokolle möglicherweise nicht ausreicht, da der Lizenzserver sich bei seinen eigenen Protokolldateien anmeldet. Führen Sie die folgenden Schritte aus, um sicherzustellen, dass Ihre Referenzimplementierung ordnungsgemäß gestartet wurde.

* Überprüfen Sie Ihre [!DNL AdobeFlashAccess.log] Datei. Hier schreibt die Referenzimplementierung Protokollinformationen. Der Speicherort dieser Protokolldatei wird durch Ihre [!DNL log4j.xml] Datei angegeben und kann so geändert werden, dass er auf einen beliebigen Speicherort verweist. Standardmäßig wird die Protokolldatei in den Arbeitsordner kopiert, in dem Sie catalina ausführen.

* Gehen Sie zur folgenden URL: [!DNL https:// flashaccess/license/v4]*Ihr Server:Server-Anschluss *. Sie sollten den Text &quot;License Server ist korrekt eingerichtet&quot;sehen.

Eine andere Möglichkeit, zu testen, ob Ihr Server ordnungsgemäß ausgeführt wird, besteht darin, ein Segment des Testinhalts zu verpacken, einen Beispiel-Videoplayer einzurichten und es dann abzuspielen.

Im folgenden Verfahren wird dieser Vorgang beschrieben:

1. Wechseln Sie zum [!DNL \Reference Implementation\Command Line Tools] Ordner.

   Informationen zum Installieren der Befehlszeilenwerkzeuge finden Sie unter [Installieren der Befehlszeilenwerkzeuge](../drm-reference-implementations/command-line-tools/install-command-line-tools.md) .

1. Geben Sie den folgenden Befehl ein, um eine einfache anonyme DRM-Richtlinie zu erstellen:

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Informationen zum Erstellen von DRM-Richtlinien mit dem DRM Policy Manager finden Sie unter [Befehlszeilenverwendung](../drm-reference-implementations/command-line-tools/configure-command-line-tools/policy-manager/policy-manager-command-line-usage.md) .

1. Legen Sie die `encrypt.license.serverurl` Eigenschaft in der [!DNL flashaccesstools.properties] Datei auf die URL des Lizenzservers fest.

   Beispiel, [!DNL https:// localhost:8080/]. Die [!DNL flashaccesstools.properties] Datei befindet sich im [!DNL \Reference Implementation\Command Line Tools] Ordner.

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

1. Kopieren Sie die beiden generierten Dateien in den [!DNL webapps\ROOT\Content] Ordner auf dem Tomcat-Server.
1. Wechseln Sie zum [!DNL Reference Implementation\Sample Video Players\Desktop\Flash Player\Release] Ordner und kopieren Sie den Inhalt in den Ordner [!DNL webapps\ROOT\SVP\] auf dem Tomcat-Server.

1. Installieren Sie Flash Player Version 10.1 oder höher.
1. Öffnen Sie einen Webbrowser und gehen Sie zur folgenden URL: [!DNL        https:// localhost:8080/SVP/player.html]

1. Gehen Sie zur folgenden URL und klicken Sie dann auf **[!UICONTROL Play]**: [!DNL https:// localhost:8080/Content/]*`your_encrypted_FLV`*.

1. Wenn das Video nicht abgespielt werden kann, überprüfen Sie, ob Fehlercodes im Protokollbereich des Beispiel-Video-Players angezeigt oder der [!DNL AdobeFlashAccess.log] Datei hinzugefügt werden.

   Sie können jetzt in der Datei &quot;log4j.xml&quot;nach dem Speicherort der [!DNL AdobeFlashAccess.log] Protokolldatei suchen und diese dann ändern. Standardmäßig wird die Protokolldatei in den Arbeitsordner kopiert, in dem Sie catalina ausführen.

