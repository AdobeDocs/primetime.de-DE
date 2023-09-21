---
description: Sie können die Funktionen des Primetime Digital Rights Management (DRM)-Systems verwenden, um sicheren Zugriff auf Ihre Videoinhalte zu ermöglichen. Alternativ können Sie DRM-Lösungen von Drittanbietern als Alternative zur integrierten Primetime DRM-Lösung von Adobe verwenden.
title: Übersicht über die Primetime-DRM-Oberfläche
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Übersicht {#primetime-drm-interface-overview}

Sie können die Funktionen des Primetime Digital Rights Management (DRM)-Systems verwenden, um sicheren Zugriff auf Ihre Videoinhalte zu ermöglichen. Alternativ können Sie DRM-Lösungen von Drittanbietern als Alternative zur integrierten Primetime DRM-Lösung von Adobe verwenden.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Wenden Sie sich an Ihren Adobe-Kundenbetreuer, um aktuelle Informationen über die Verfügbarkeit von DRM-Lösungen von Drittanbietern zu erhalten.

Das Client-seitige Schlüsselelement des Digital Rights Management (DRM)-Systems von Primetime ist der DRM Manager. Die im Android-SDK enthaltene Beispielanwendung enthält eine `DRMHelper` -Klasse, die zeigt, wie bestimmte DRM-Vorgänge einfacher implementiert werden können.

Primetime DRM bietet einen skalierbaren, effizienten Workflow zur Implementierung des Inhaltsschutzes in TVSDK-Anwendungen. Sie schützen und verwalten die Rechte an Ihren Videoinhalten, indem Sie für jede digitale Mediendatei eine Lizenz erstellen.

Siehe DRM-Beispiel-Player-Code, der im TVSDK-Paket enthalten ist.

Dies sind die wichtigsten API-Elemente für die Arbeit mit DRM:

* Ein Verweis im Medienplayer auf das DRM-Manager-Objekt, das das DRM-Subsystem implementiert:

  ```java
  MediaPlayer.getDRMManager();
  ```

  >[!TIP]
  >
  >Diese API gibt eine gültige `DRMManager` -Objekt nur nach dem `MediaPlayerEvent.DRM_METADATA` ausgelöst wird. Wenn Sie `getDRMManager()` bevor dieses Ereignis ausgelöst wird, wird möglicherweise NULL zurückgegeben.

* Die `DRMHelper` Helper-Klasse, die bei der Implementierung von DRM-Workflows nützlich ist.

  Sie können `DRMHelper` in `ReferencePlayer`.

* A `DRMHelper` Metadaten-Lademethode, die DRM-Metadaten lädt, wenn sie sich in einer anderen URL als dem Medium befinden.

  ```java
  public static void loadDRMMetadata(final DRMManager drmManager,  
     final String drmMetadataUrl,  
     final DRMLoadMetadataListener loadMetadataListener);
  ```

* A `DRMHelper` -Methode zum Überprüfen der DRM-Metadaten, um festzustellen, ob eine Authentifizierung erforderlich ist.

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

<!--<a id="section_899BD9061D484E1BBA46E84617C36867"></a>-->

Zusätzliche relevante API-Elemente:

* [com.adobe.ave.drm.DRMManager](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMManager.html)
* [com.adobe.ave.drm.DRMMetdata](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMMetadata.html)
* [com.adobe.ave.drm.DRMPolicy](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMPolicy.html)
* [com.adobe.ave.drm.DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMAuthenticationMethod.html)
* [com.adobe.ave.drm.DRMAuthenticationCompleteCallback](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMAuthenticationCompleteCallback.html)
* [com.adobe.ave.drm.DRMOperationErrorCallback](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMOperationErrorCallback.html)
* com.adobe.mediacore.drm.DRMAuthenticateListener

<!-- 
Comment Type: draft
(https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/drm/DRMAuthenticateListener.html)

-->
<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Weitere Informationen zu DRM finden Sie im [Adobe Primetime DRM-Dokumentation](https://helpx.adobe.com/primetime/user-guide.html).
