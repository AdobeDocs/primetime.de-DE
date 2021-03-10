---
description: Der Primetime-Player unterstützt die Primetime DRM-Integration als benutzerdefinierte DRM-Workflows. Das bedeutet, dass Ihre Anwendung die DRM-Workflows implementieren muss, bevor der Stream wiedergegeben wird.
title: DRM-Inhaltsschutz
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---


# DRM-Inhaltsschutz {#drm-content-protection}

Der Primetime-Player unterstützt die Primetime DRM-Integration als benutzerdefinierte DRM-Workflows. Das bedeutet, dass Ihre Anwendung die DRM-Workflows implementieren muss, bevor der Stream wiedergegeben wird.

Um dies zu aktivieren, stellt TVSDK Ihnen den DRM-Manager zur Authentifizierung zur Verfügung. Die Referenzimplementierung bietet ein Beispiel für folgende Workflows:

* So laden und wiedergeben Sie HLS-Streams mit Inhaltsschutz von Access, optimiert für niedrige Fehlerquoten und schnellen Beginn.
* So laden und wiedergeben Sie HLS-Streams mit AES128-Inhaltsschutz.
* So laden und wiedergeben Sie HLS-Streams mit PHLS-Inhaltsschutz, optimiert für niedrige Fehlerquoten und schnellen Beginn.

Alle DRM-geschützten Inhalte werden automatisch von den DRM-Bibliotheken verarbeitet, die in das TVSDK integriert sind. Sie können jedoch die Fehlerverarbeitung, die Optimierung der Geräteindividualisierung und die Lizenzerfassung mithilfe von TVSDK API-Rückrufen bereitstellen.

## hinzufügen Inhaltsschutz für den Player {#section_F1FC4322C35C4FE8A3B47FDC0A74221B}

Sie können dem Player Inhaltsschutz hinzufügen, indem Sie einen Play-back-Manager erstellen oder die Manager-Factory verwenden.

So erstellen Sie einen Content Protection Manager:

* Initialisieren Sie das DRM-System.

   Im folgenden Codebeispiel wird gezeigt, wie `loadDRMServices` in der Funktion `onCreate()` aufgerufen wird, um sicherzustellen, dass eine für das DRM-System erforderliche Initialisierung vor dem Starten der Wiedergabe gestartet wird.

   ```java
   @Override 
    public void onCreate() { 
        super.onCreate();  
        DrmManager.loadDRMServices(getApplicationContext()); 
    }
   ```

* Laden Sie die DRM-Lizenzen im Voraus.

   Das folgende Codebeispiel zeigt, wie Sie das `VideoItems` laden, wenn die Liste für den Inhalt fertig geladen wurde. Dies führt dazu, dass die DRM-Lizenzen vom Lizenzserver erworben und lokal zwischengespeichert werden, sodass die Inhalte bei Wiedergabe-Beginn mit minimaler Verzögerung geladen werden.

   ```java
   DrmManager.preLoadDrmLicenses(item.getUrl(),  
     new MediaPlayerItemLoader.LoaderListener() { 
   
       @Override 
       public void onLoadComplete(MediaPlayerItem item) { 
           Player.logger.w(LOG_TAG + "::DRMPreload#onLoadComplete", item.getResource().getUrl()); 
       } 
   
       @Override 
       public void onError(MediaErrorCode errorCode, String s) { 
           Player.logger.e(LOG_TAG + "::DRMPreload#onError", s); 
       } 
   } 
   ```

   >[!NOTE]
   >
   >Sie können in der Benutzeroberfläche &quot;Einstellungen&quot;Precache DRM-Lizenzen auf ON setzen, um DRM-Lizenzen beim Laden von Inhalten zu aktualisieren. Es empfiehlt sich jedoch, einen bestimmten Artikel im Voraus zu laden, anstatt alle Lizenzen im Katalog zu aktualisieren.
   >
   >![](assets/precache-drm-licenses.jpg)

* Um `ManagerFactory` zur Implementierung der DRM-Fehlerbearbeitung zu verwenden, stellen Sie sicher, dass die folgende Codezeile in der Datei [!DNL PlayerFragment.java] enthalten ist:

   ```java
   drmManager = ManagerFactory.getDrmManager(config, mediaPlayer);
   ```

**Verwandte API-Dokumentation**

* [Klasse DRMManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.html)
* [DrmManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.DrmManagerEventListener.html)