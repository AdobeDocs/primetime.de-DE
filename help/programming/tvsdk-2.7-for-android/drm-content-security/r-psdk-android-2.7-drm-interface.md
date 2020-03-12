---
description: Das wichtigste clientseitige Element der Primetime DRM-Lösung ist der DRM-Manager. Die im Android SDK enthaltene Beispielanwendung enthält auch eine DRMHelper-Klasse, mit der bestimmte DRM-Vorgänge leichter implementiert werden können.
seo-description: Das wichtigste clientseitige Element der Primetime DRM-Lösung ist der DRM-Manager. Die im Android SDK enthaltene Beispielanwendung enthält auch eine DRMHelper-Klasse, mit der bestimmte DRM-Vorgänge leichter implementiert werden können.
seo-title: Übersicht über die Primetime-DRM-Oberfläche
title: Übersicht über die Primetime-DRM-Oberfläche
uuid: d77a98c8-c1f5-4fe3-8d0b-3d21e288f228
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Übersicht über die Primetime-DRM-Oberfläche {#primetime-drm-interface-overview}

Das wichtigste clientseitige Element der Primetime DRM-Lösung ist der DRM-Manager. Die im Android SDK enthaltene Beispielanwendung enthält auch eine DRMHelper-Klasse, mit der bestimmte DRM-Vorgänge leichter implementiert werden können.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRM bietet einen skalierbaren, effizienten Arbeitsablauf zur Implementierung des Inhaltsschutzes in TVSDK-Anwendungen. Sie schützen und verwalten die Rechte an Ihren Videoinhalten, indem Sie eine Lizenz für jede digitale Mediendatei erstellen.

Weitere Informationen finden Sie im DRM-Beispielplayer-Code, der im TVSDK-Paket enthalten ist.

Im Folgenden finden Sie die wichtigsten API-Elemente für die Arbeit mit DRM:

* Ein Verweis im Medienplayer auf das DRM-Manager-Objekt, das das DRM-Subsystem implementiert:

   ```java
   MediaPlayer.getDRMManager();
   ```

   >[!TIP]
   >
   >Diese API gibt ein gültiges `DRMManager` Objekt erst zurück, nachdem der `MediaPlayerEvent.DRM_METADATA` ausgelöst wurde. Wenn Sie `getDRMManager()` vor dem Auslösen dieses Ereignisses anrufen, wird möglicherweise NULL zurückgegeben.

* Die `DRMHelper` Helper-Klasse, die bei der Implementierung von DRM-Workflows nützlich ist.
* Eine `DRMHelper` Metadaten-Lader-Methode, die DRM-Metadaten lädt, wenn sie sich in einer separaten URL vom Medium befinden.

   ```java
   public static void loadDRMMetadata(final DRMManager drmManager,  
      final String drmMetadataUrl,  
      final DRMLoadMetadataListener loadMetadataListener);
   ```

* Eine `DRMHelper` Methode zum Überprüfen der DRM-Metadaten und zum Bestimmen, ob eine Authentifizierung erforderlich ist.

   ```java
   /** 
   * Return whether authentication is needed for the provided 
   * DRMMetadata. 
   * 
   * @param drmMetadata 
   * The desired DRMMetadata on which to check whether auth is needed. 
   * @return whether authentication is required for the provided metadata 
   */ 
   public static boolean isAuthNeeded(DRMMetadata drmMetadata);
   ```

* `DRMHelper` zur Durchführung der Authentifizierung.

   ```java
   /** 
   * Helper method to perform DRM authentication. 
   * 
   * @param drmManager 
   * the DRMManager, used to perform the authentication. 
   * @param drmMetadata 
   * the DRMMetadata, containing the DRM specific information. 
   * @param authenticationListener 
   * the listener, on which the user can be notified about the 
   * authentication process status. 
   * @param authUser 
   * the DRM username provider by the user. 
   * @param authPass 
   * the DRM password provided by the user. 
   */ 
   public static void performDrmAuthentication(final DRMManager drmManager,  
   final DRMMetadata drmMetadata,  
   final String authUser,  
   final String authPass,  
   final DRMAuthenticationListener authenticationListener);
   ```

* Ereignis, die Ihre Anwendung über verschiedene DRM-Aktivitäten und -Status informieren.

<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Weitere Informationen zu DRM finden Sie in der [DRM-Dokumentation](https://helpx.adobe.com/primetime/user-guide.html).
