---
description: Der Primetime-Player unterstützt die Primetime DRM-Integration als benutzerdefinierte DRM-Workflows. Das bedeutet, dass Ihre Anwendung die DRM-Authentifizierungs-Workflows implementieren muss, bevor der Stream wiedergegeben wird.
title: DRM-Inhaltsschutz
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# DRM-Inhaltsschutz {#drm-content-protection}

Der Primetime-Player unterstützt die Primetime DRM-Integration als benutzerdefinierte DRM-Workflows. Das bedeutet, dass Ihre Anwendung die DRM-Authentifizierungs-Workflows implementieren muss, bevor der Stream wiedergegeben wird.

Um dies zu aktivieren, stellt TVSDK Ihnen den DRM-Manager zur Authentifizierung zur Verfügung. Die Referenzimplementierung bietet ein Beispiel für die folgenden Workflows:

* Laden und Wiedergeben von HLS-Streams mit dem Inhaltsschutz Access, optimiert für niedrige Fehlerquoten und schnelles Starten.
* Laden und Wiedergeben von HLS-Streams mit AES128-Inhaltsschutz.
* Laden und Wiedergeben von HLS-Streams mit PHLS-Inhaltsschutz, optimiert für niedrige Fehlerquoten und schnelles Starten.

Alle DRM-geschützten Inhalte werden automatisch von den DRM-Bibliotheken verarbeitet, die in das TVSDK integriert sind. Sie können jedoch die Fehlerbehandlung, die Optimierung der Geräteindividualisierung und die Lizenzakquise mithilfe von TVSDK-API-Callbacks verfügbar machen.

## Hinzufügen des Inhaltsschutzes zum Player {#section_F1FC4322C35C4FE8A3B47FDC0A74221B}

Sie können dem Player Inhaltsschutz hinzufügen, indem Sie einen Wiedergabemanager erstellen oder die Managers-Factory verwenden.

So erstellen Sie einen Inhaltsschutz-Manager:

* Initialisieren Sie das DRM-System.

  Das folgende Codebeispiel zeigt, wie die `loadDRMServices` im Antrag `onCreate()` -Funktion, um sicherzustellen, dass jede für das DRM-System erforderliche Initialisierung vor dem Start der Wiedergabe gestartet wird.

  ```java
  @Override 
   public void onCreate() { 
       super.onCreate();  
       DrmManager.loadDRMServices(getApplicationContext()); 
   }
  ```

* Laden Sie die DRM-Lizenzen vorab.

  Das folgende Codebeispiel zeigt das Laden der `VideoItems` wenn das Laden der Inhaltsliste abgeschlossen ist. Dadurch werden die DRM-Lizenzen vom Lizenzserver erworben und lokal zwischengespeichert, sodass der Inhalt beim Start der Wiedergabe mit minimaler Verzögerung geladen wird.

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
  >Sie können in der Benutzeroberfläche &quot;Einstellungen&quot;Precache DRM-Lizenzen auf EIN setzen, um DRM-Lizenzen beim Laden von Inhalten zwischenzuspeichern. Es empfiehlt sich jedoch, ein bestimmtes Element im Voraus zu laden, anstatt alle Lizenzen im Katalog voranzustellen.
  >
  >![](assets/precache-drm-licenses.jpg)

* Verwendung `ManagerFactory` Um die DRM-Fehlerbehandlung zu implementieren, stellen Sie sicher, dass die folgende Codezeile im [!DNL PlayerFragment.java] Datei:

  ```java
  drmManager = ManagerFactory.getDrmManager(config, mediaPlayer);
  ```

**Verwandte API-Dokumentation**

* [Klasse DrmManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.html)
* [DrmManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.DrmManagerEventListener.html)
