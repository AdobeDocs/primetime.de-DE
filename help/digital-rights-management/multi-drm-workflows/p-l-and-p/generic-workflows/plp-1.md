---
description: Sie können den Offline Packager von Adobe verwenden, um Inhalte für alle DRM-Lösungen vorzubereiten, die von Primetime Cloud DRM unterstützt werden, powered by ExpressPlay.
seo-description: Sie können den Offline Packager von Adobe verwenden, um Inhalte für alle DRM-Lösungen vorzubereiten, die von Primetime Cloud DRM unterstützt werden, powered by ExpressPlay.
seo-title: Primetime Packager / Cloud DRM / TVSDK
title: Primetime Packager / Cloud DRM / TVSDK
uuid: e54a0e4d-c8ea-46d4-b1b0-bed8a680f8f5
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# Primetime Packager / Cloud DRM / TVSDK {#primetime-packager-cloud-drm-tvsdk}

Sie können den Offline Packager von Adobe verwenden, um Inhalte für alle DRM-Lösungen vorzubereiten, die von Primetime Cloud DRM unterstützt werden, powered by ExpressPlay.

Diese Anleitung setzt voraus, dass Sie bereits ein ExpressPlay-Admin-Konto eingerichtet haben: [Primetime DRM Cloud Quick-Beginn](../../../multi-drm-workflows/quick-start/quick-overview.md).
1. Wählen Sie die Infrastruktur, die zum Verpacken Ihrer Inhalte verwendet werden soll. Primetime Packager unterstützt sowohl die Befehlszeilenverpackung als auch die Konfigurationsbasierte Verpackung von Inhalten für die Verwendung mit den DRMs FairPlay, Widevine und PlayReady. Die folgenden Formate und Verschlüsselungen werden derzeit in TVSDK unterstützt (weitere sind in Vorbereitung):

   * DASH (CENC) / PlayReady, Widevine - Für HTML5
   * HLS/FairPlay, Zugriff - für iOS

1. Wählen Sie ein Key Management System (KMS):

   * Verwenden Sie das ExpressPlay-KMS ( [ExpressPlay-Key-Datenspeicherung](https://www.expressplay.com/developer/key-storage/)); Dieses System verwaltet Ihre Inhaltsschlüssel über die RESTful-API von ExpressPlay.

      oder...

   * Richten Sie Ihr eigenes KMS ein. Erstellen Sie eine Datenbank mit Inhaltsschlüsseln, die nach Inhalts-ID ausgewählt werden kann.

      In beiden Fällen verwaltet das KMS eine Bereitstellung von Inhaltsschlüsseln, wobei jeder Schlüssel über eine entsprechende Content-ID verfügt.

1. Verpacken Sie Ihren Inhalt. Mit Primetime Packager können Sie Inhalte für eine bestimmte DRM-Lösung oder für mehrere DRM-Lösungen verpacken.

   Die folgenden Beispielbefehle zeigen einige Beispiele für das Verpacken von Inhalten für verschiedene DRM-Lösungen:

   * [Mit Primetime Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=19)  (erzeugt MPD-Datei) schließen:

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
      >Der Wert `key_url` wird wie in der Datei M3U8 kopiert.

1. Erstellen Sie einen &quot;Schaufensterserver&quot;.

       Der StoreFront-Server muss die folgenden Vorgänge ausführen:
   
   1. Kundenauswahl von Inhalten. Diese Implementierung muss einen Endpunkt enthalten, an dem Kunden ein Content-Token für eine bestimmte Inhalts-ID anfordern können.
   1. Kundenberechtigungen
   1. Lizenztoken-Anfragen (ExpressPlay) vom Client ( [ExpressPlay-Lizenztoken-Anfrage/Antwortreferenz](../../../multi-drm-workflows/license-token-req-resp-ref/license-req-resp-overview.md))

1. Erstellen Sie Ihren Client.

       Der Client sollte einen Aufruf an Ihren Store-Server einschließen. Adobe empfiehlt, dass der Client den Store aufruft, nachdem der Benutzer Inhalte ausgewählt hat und nachdem der Benutzer authentifiziert wurde. Übergeben Sie dann das von ExpressPlay zurückgegebene Token an Ihren Player, um es für Lizenzanforderungen zu verwenden. Die Einführung zur Implementierung der DRM-Komponente Ihrer Player finden Sie hier:
   
   * [Browser TVSDK für HTML5](https://help.adobe.com/en_US/primetime/psdk/browser_tvsdk/index.html#PSDKs-reference-DRM_interface_overview)
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. Wenn das Lizenz-Token vorhanden ist, kann der Client jetzt die Anforderungs-URL vom Token ableiten, die Lizenzanforderung an ExpressPlay stellen und dann den ausgewählten Inhalt für den Benutzer abspielen.
