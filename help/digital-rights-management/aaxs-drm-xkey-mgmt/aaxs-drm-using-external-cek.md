---
description: Verwenden Sie die externe CEK-Funktion, um Lizenzen mit Ihrem vorhandenen CKMS anzuzeigen und zu verpacken.
seo-description: Verwenden Sie die externe CEK-Funktion, um Lizenzen mit Ihrem vorhandenen CKMS anzuzeigen und zu verpacken.
seo-title: Verwenden von externen CEK-Lizenzen für Vend- und Paketlizenzen
title: Verwenden von externen CEK-Lizenzen für Vend- und Paketlizenzen
uuid: 1bfd8c6c-4ae9-47de-8247-085b5360127d
translation-type: tm+mt
source-git-commit: fe9493d610bc6fb97d30351c707b73cda92c67a0
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---


# Verwenden von External CEK to Vend- und Paketlizenzen{#using-external-cek-to-vend-and-package-licenses}

Verwenden Sie die externe CEK-Funktion, um Lizenzen mit Ihrem vorhandenen CKMS anzuzeigen und zu verpacken.

## EncryptContentWithExternalKey.java

Dies ist ein Befehlszeilenwerkzeug, das ein Video mit AAXS verschlüsselt und Metadaten erstellt, die *nicht* den CEK enthalten (geschützt mit dem öffentlichen Zertifikat eines AAXS-Lizenzservers). Stattdessen bettet das Tool eine CEK-ID in die Metadaten des Videos ein.

Während der Lizenzerwerb beobachtet der AAXS-Lizenzserver ein Flag in den Metadaten, das erkennt, dass dieser Inhalt mit einem externen CEK geschützt wurde. Der Lizenzserver extrahiert die CEK-ID aus den Metadaten und dann ein sicheres Repository/CKMS, um den entsprechenden CEK abzurufen.

## Arbeitsablauf für Verpackungen

1. Stellen Sie sicher, dass Sie Java 1.6.0_24 oder höher verwenden.
1. So zeigen Sie die Verwendung des Tools an: `java -jar AdobePackager_ExternalCEK.jar`
1. So verpacken Sie Inhalte:

   ```
   java -jar AdobePackager_ExternalCEK.jar sample.flv encrypted.flv abc abcdef0123456789 
       policy.pol https://path-to-your-server:8090 <license-server-public-cert.pem> 
       <license-server-private-key.pfx> <private-key-password>
   ```

>[!NOTE]
>
>* Der Java-Quellcode kann mit dem enthaltenen ANT `build-samples.xml` erstellt werden
>* Das Flash Access-SDK ( `adobe-flashaccess-sdk.jar`) muss sich im Klassenpfad befinden

>



## Server-Workflow

1. Richten Sie die Referenzimplementierung ein.
1. Bereinigen Sie ggf. frühere Implementierungen für die Referenzimplementierung:

   1. `delete <tomcat>\work\Catalina\*.*`
   1. `delete <tomcat>\conf\Catalina\*.*`
   1. `delete <tomcat>\logs\*.*`

1. Überprüfen Sie, ob neben Ihrer [!DNL flashaccess-refimpl.properties]-Datei eine [!DNL CEKDepot.properties]-Datei vorhanden ist.

1. Lizenzanfragen von einem Adobe Primetime Player starten
1. Beobachten Sie die Ref Impl-Protokolle für etwas Ähnliches:

   ```
   DEBUG [com.adobe.flashaccess.refimpl.web.RefImplLicenseReqHandler.REQUESTS] 
     Used CEK ID:{abc} to retrieve CEK: {abcdef0123456789} from depot
   ```

   1. Möglicherweise müssen Sie Ihre [!DNL log4j.xml]-Einstellungen ändern, um sich auf einer `DEBUG`-Ebene anzumelden ( `INFO` ist standardmäßig eingestellt)

## Bekannte Probleme

Keines
