---
description: Sie können die Funktionen des Primetime-Digital Rights Managements (DRM) verwenden, um einen sicheren Zugriff auf Ihre Videoinhalte zu ermöglichen. Alternativ dazu können Sie auch DRM-Lösungen von Drittanbietern als Alternative zur integrierten Primetime-DRM-Lösung der Adobe verwenden.
seo-description: Sie können die Funktionen des Primetime-Digital Rights Managements (DRM) verwenden, um einen sicheren Zugriff auf Ihre Videoinhalte zu ermöglichen. Alternativ dazu können Sie auch DRM-Lösungen von Drittanbietern als Alternative zur integrierten Primetime-DRM-Lösung der Adobe verwenden.
seo-title: Übersicht über die Primetime-DRM-Oberfläche
title: Übersicht über die Primetime-DRM-Oberfläche
uuid: 71479464-8356-4732-9774-da9f6084e6ad
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# Übersicht {#primetime-drm-interface-overview}

Sie können die Funktionen des Primetime-Digital Rights Managements (DRM) verwenden, um einen sicheren Zugriff auf Ihre Videoinhalte zu ermöglichen. Alternativ dazu können Sie auch DRM-Lösungen von Drittanbietern als Alternative zur integrierten Primetime-DRM-Lösung der Adobe verwenden.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Wenden Sie sich an Ihren Kundenbetreuer, um aktuelle Informationen zur Verfügbarkeit von DRM-Lösungen von Drittanbietern zu erhalten.

Das wichtigste clientseitige Element des DRM-Systems (Primetime Digital Rights Management) ist der DRM Manager. Die im Android-SDK enthaltene Beispielanwendung enthält eine `DRMHelper`-Klasse, die zeigt, wie bestimmte DRM-Vorgänge leichter implementiert werden können.

Primetime DRM bietet einen skalierbaren, effizienten Arbeitsablauf zur Implementierung des Inhaltsschutzes in TVSDK-Anwendungen. Sie schützen und verwalten die Rechte an Ihren Videoinhalten, indem Sie eine Lizenz für jede digitale Mediendatei erstellen.

Siehe DRM-Beispielplayer-Code im TVSDK-Paket.

Dies sind die wichtigsten API-Elemente für die Arbeit mit DRM:

* Ein Verweis im Medienplayer auf das DRM-Manager-Objekt, das das DRM-Subsystem implementiert:

   ```java
   MediaPlayer.getDRMManager();
   ```

   >[!TIP]
   >
   >Diese API gibt ein gültiges `DRMManager`-Objekt erst zurück, nachdem das `MediaPlayerEvent.DRM_METADATA` ausgelöst wurde. Wenn Sie `getDRMManager()` aufrufen, bevor dieses Ereignis ausgelöst wird, wird möglicherweise NULL zurückgegeben.

* Die `DRMHelper` Helper-Klasse, die bei der Implementierung von DRM-Workflows nützlich ist.

   Sie können `DRMHelper` in `ReferencePlayer` sehen.

* Eine `DRMHelper`-Metadaten-Lademethode, die DRM-Metadaten lädt, wenn sie sich in einer separaten URL vom Medium befinden.

   ```java
   public static void loadDRMMetadata(final DRMManager drmManager,  
      final String drmMetadataUrl,  
      final DRMLoadMetadataListener loadMetadataListener);
   ```

* Eine `DRMHelper`-Methode zur Überprüfung der DRM-Metadaten, um festzustellen, ob eine Authentifizierung erforderlich ist.

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

<!--<a id="section_899BD9061D484E1BBA46E84617C36867"></a>-->

Zusätzliche relevante API-Elemente:

* [com.adobe.ave.drm.DRMManager](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMManager.html)
* [com.adobe.ave.drm.DRMMetdata](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMMetadata.html)
* [com.adobe.ave.drm.DRMPopolicy](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMPolicy.html)
* [com.adobe.ave.drm.DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMAuthenticationMethod.html)
* [com.adobe.ave.drm.DRMAuthenticationCompleteCallback](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMAuthenticationCompleteCallback.html)
* [com.adobe.ave.drm.DRMOperationErrorCallback](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMOperationErrorCallback.html)
* com.adobe.mediacore.drm.DRMAuthenticateListener

<!-- 
Comment Type: draft
(https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/drm/DRMAuthenticateListener.html)

-->
<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Weitere Informationen zu DRM finden Sie in der [Adobe Primetime DRM-Dokumentation](https://helpx.adobe.com/primetime/user-guide.html).
