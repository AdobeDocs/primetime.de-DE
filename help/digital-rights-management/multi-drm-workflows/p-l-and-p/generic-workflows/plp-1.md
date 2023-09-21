---
description: Sie können Adobe Offline Packager verwenden, um Inhalte für beliebige DRM-Lösungen vorzubereiten, die von Primetime Cloud DRM unterstützt werden, powered by ExpressPlay.
title: Primetime Packager/Cloud DRM/TVSDK
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Primetime Packager/Cloud DRM/TVSDK {#primetime-packager-cloud-drm-tvsdk}

Sie können Adobe Offline Packager verwenden, um Inhalte für beliebige DRM-Lösungen vorzubereiten, die von Primetime Cloud DRM unterstützt werden, powered by ExpressPlay.

Bei diesen Anweisungen wird davon ausgegangen, dass Sie bereits ein ExpressPlay-Administratorkonto eingerichtet haben: [Primetime DRM Cloud-Schnellstart](../../../multi-drm-workflows/quick-start/quick-overview.md).
1. Wählen Sie die Infrastruktur aus, die zum Verpacken Ihres Inhalts verwendet werden soll. Primetime Packager unterstützt sowohl die Befehlszeilen- als auch die konfigurationsbasierte Verpackung von Inhalten für die Verwendung mit den FairPlay-, Widevine- und PlayReady-DRMs. Die folgenden Formate und Verschlüsselungen werden derzeit in TVSDK unterstützt (weitere werden in der Pipeline bereitgestellt):

   * DASH (CENC) / PlayReady, Widevine - für HTML 5
   * HLS/FairPlay, Zugriff - für iOS

1. Wählen Sie ein Key Management System (KMS):

   * Verwenden Sie das ExpressPlay-KMS ( [ExpressPlay-Schlüsselspeicher](https://www.expressplay.com/developer/key-storage/)); dieses System verwaltet Ihre Inhaltsschlüssel über die RESTful-API von ExpressPlay.

     oder ...

   * Richten Sie Ihr eigenes KMS ein. Erstellen Sie eine Datenbank mit Inhaltsschlüsseln, die nach Inhalts-ID ausgewählt werden können.

     In beiden Fällen verwaltet das KMS eine Bereitstellung von Inhaltsschlüsseln, wobei jeder Schlüssel über eine zugehörige Inhalts-ID verfügt.

1. Verpacken Sie den Inhalt. Mit Primetime Packager können Sie Inhalte für eine bestimmte DRM-Lösung oder für mehrere DRM-Lösungen verpacken.

   Die folgenden Beispielbefehle zeigen einige Beispiele für das Verpacken von Inhalten für verschiedene DRM-Lösungen:

   * [Widevine mit Primetime Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=19) (erzeugt MPD-Datei):

     ```
     java -jar OfflinePackager.jar \ 
       -in_path [ 
       <your_content.mp4>] \ 
       -out_type dash \ 
       -out_path [ 
       <your_out_file_path>] \ 
       -drm \ 
       -drm_sys WIDEVINE \ 
       -key_file_path "creds/widevine_key.bin" \ 
       -widevine_key_id [ 
       <some_keyID>] \ 
       -widevine_content_id [ 
       <some_content-ID] \ 
       -widevine_header provider:intertrust#content_id:2a
     ```

   * [FairPlay mit Primetime Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=20) (Generiert eine M3U8-Datei):

     ```
     java -jar OfflinePackager.jar  
       -in_path [ 
       <your_content.mp4>]  
       -out_type hls  
       -out_path [ 
       <your_out_file_path>]  
       -drm  
       -drm_sys FAIRPLAY  
       -key_file_path "creds/fairplay_key.bin"  
       -key_url "user_provided_value"
     ```

     >[!NOTE]
     >
     >Die `key_url` -Wert wird wie in der Datei M3U8 kopiert.

1. Erstellen Sie einen &quot;Storefront-Server&quot;.

       Der Storefront-Server muss die folgenden Vorgänge durchführen:
   
   1. Kundenauswahl von Inhalten. Diese Implementierung muss einen -Endpunkt enthalten, an den Clients ein Inhalts-Token für eine bestimmte Inhalts-ID anfordern können.
   1. Kundenberechtigungen
   1. Lizenztoken-Anfragen (ExpressPlay) vom Client ( [ExpressPlay-Lizenztoken-Anfrage/Antwort-Referenz](../../../multi-drm-workflows/license-token-req-resp-ref/license-req-resp-overview.md))

1. Erstellen Sie Ihren Client.

       Der Client sollte einen Aufruf an Ihren Storefront-Server einschließen. Adobe empfiehlt, dass der Client die Storefront aufruft, nachdem der Benutzer einen bestimmten Inhalt ausgewählt und der Benutzer authentifiziert wurde. Übergeben Sie dann das von ExpressPlay zurückgegebene Token an Ihren Player, um es für Lizenzanfragen zu verwenden. Hier finden Sie eine Einführung in die Implementierung der DRM-Komponente Ihrer Player:
   
   * [Browser TVSDK für HTML 5](https://help.adobe.com/en_US/primetime/psdk/browser_tvsdk/index.html#PSDKs-reference-DRM_interface_overview)
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. Mit dem vorhandenen Lizenz-Token kann der Client jetzt die Anfrage-URL vom Token ableiten, die Lizenzanforderung an ExpressPlay senden und dann den ausgewählten Inhalt für den Benutzer wiedergeben.
