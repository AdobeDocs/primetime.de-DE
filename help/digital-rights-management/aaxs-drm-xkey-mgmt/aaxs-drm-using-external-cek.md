---
description: Verwenden Sie die externe CEK-Funktion, um Lizenzen mit Ihrem vorhandenen CKMS zu aktualisieren und zu verpacken.
title: Verwenden externer CEK-Lizenzen für Vend- und Package-Lizenzen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Verwenden externer CEK-Lizenzen für Vend- und Package-Lizenzen{#using-external-cek-to-vend-and-package-licenses}

Verwenden Sie die externe CEK-Funktion, um Lizenzen mit Ihrem vorhandenen CKMS zu aktualisieren und zu verpacken.

## EncryptContentWithExternalKey.java

Dies ist ein Befehlszeilen-Tool, mit dem ein Video mit AAXS verschlüsselt und Metadaten erstellt werden, die *not* enthalten das CEK (geschützt mit dem öffentlichen Zertifikat eines AXS-Lizenzservers). Stattdessen bettet das Tool eine CEK-ID in die Metadaten des Videos ein.

Während der Lizenzakquise beobachtet der AXS-Lizenzserver eine Markierung in den Metadaten, die angibt, dass dieser Inhalt durch ein externes CEK geschützt wurde. Der Lizenzserver extrahiert die CEK-ID aus den Metadaten und fragt dann ein sicheres Repository/CKMS ab, um das entsprechende CEK abzurufen.

## Verpackungs-Workflow

1. Stellen Sie sicher, dass Sie Java 1.6.0_24 oder höher verwenden.
1. So sehen Sie die Verwendung des Tools: `java -jar AdobePackager_ExternalCEK.jar`
1. So verpacken Sie Inhalte:

   ```
   java -jar AdobePackager_ExternalCEK.jar sample.flv encrypted.flv abc abcdef0123456789 
       policy.pol https://path-to-your-server:8090 <license-server-public-cert.pem> 
       <license-server-private-key.pfx> <private-key-password>
   ```

>[!NOTE]
>
>* Der Java-Quellcode kann mithilfe der enthaltenen ANT erstellt werden `build-samples.xml`
>* Das Flash Access-SDK ( `adobe-flashaccess-sdk.jar`) muss sich im Klassenpfad befinden
>

## Server-Workflow

1. Richten Sie die Referenzimplementierung ein.
1. Falls vorhanden, bereinigen Sie frühere Implementierungen für die Referenzimplementierung:

   1. `delete <tomcat>\work\Catalina\*.*`
   1. `delete <tomcat>\conf\Catalina\*.*`
   1. `delete <tomcat>\logs\*.*`

1. Stellen Sie sicher, dass eine [!DNL CEKDepot.properties] -Datei neben [!DNL flashaccess-refimpl.properties]

1. Lizenzanfrage von einem Adobe Primetime-Player starten
1. Beobachten Sie Ref Impl-Protokolle für etwas Ähnliches:

   ```
   DEBUG [com.adobe.flashaccess.refimpl.web.RefImplLicenseReqHandler.REQUESTS] 
     Used CEK ID:{abc} to retrieve CEK: {abcdef0123456789} from depot
   ```

   1. Möglicherweise müssen Sie Ihre [!DNL log4j.xml] Einstellungen zum Anmelden bei einem `DEBUG` level ( `INFO` ist standardmäßig festgelegt)

## Bekannte Probleme

Keines
