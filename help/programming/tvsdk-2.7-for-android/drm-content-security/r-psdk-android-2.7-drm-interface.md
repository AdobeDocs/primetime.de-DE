---
description: Das wichtigste clientseitige Element der Primetime DRM-Lösung ist der DRM-Manager. Die im Android-SDK enthaltene Beispielanwendung enthält auch eine DRMHelper-Klasse, mit der bestimmte DRM-Vorgänge leichter implementiert werden können.
title: Übersicht über die Primetime-DRM-Oberfläche
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Übersicht über die Primetime-DRM-Oberfläche {#primetime-drm-interface-overview}

Das wichtigste clientseitige Element der Primetime DRM-Lösung ist der DRM-Manager. Die im Android-SDK enthaltene Beispielanwendung enthält auch eine DRMHelper-Klasse, mit der bestimmte DRM-Vorgänge leichter implementiert werden können.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRM bietet einen skalierbaren, effizienten Workflow zur Implementierung des Inhaltsschutzes in TVSDK-Anwendungen. Sie schützen und verwalten die Rechte an Ihren Videoinhalten, indem Sie für jede digitale Mediendatei eine Lizenz erstellen.

Weitere Informationen finden Sie im DRM-Beispiel-Player-Code, der im TVSDK-Paket enthalten ist.

Im Folgenden finden Sie die wichtigsten API-Elemente für die Arbeit mit DRM:

* Ein Verweis im Medienplayer auf das DRM-Manager-Objekt, das das DRM-Subsystem implementiert:

  ```java
  MediaPlayer.getDRMManager();
  ```

  >[!TIP]
  >
  >Diese API gibt eine gültige `DRMManager` -Objekt nur nach dem `MediaPlayerEvent.DRM_METADATA` ausgelöst wird. Wenn Sie `getDRMManager()` bevor dieses Ereignis ausgelöst wird, wird möglicherweise NULL zurückgegeben.

* Die `DRMHelper` Helper-Klasse, die bei der Implementierung von DRM-Workflows nützlich ist.
* A `DRMHelper` Metadaten-Lademethode, die DRM-Metadaten lädt, wenn sie sich in einer anderen URL als dem Medium befinden.

  ```java
  public static void loadDRMMetadata(final DRMManager drmManager,  
     final String drmMetadataUrl,  
     final DRMLoadMetadataListener loadMetadataListener);
  ```

* A `DRMHelper` -Methode, um die DRM-Metadaten zu überprüfen und festzustellen, ob eine Authentifizierung erforderlich ist.

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

* `DRMHelper` -Methode, um eine Authentifizierung durchzuführen.

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

* Ereignisse, die Ihre Anwendung über verschiedene DRM-Aktivitäten und -Status informieren.

<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Weitere Informationen zu DRM finden Sie im [DRM-Dokumentation](https://helpx.adobe.com/primetime/user-guide.html).
