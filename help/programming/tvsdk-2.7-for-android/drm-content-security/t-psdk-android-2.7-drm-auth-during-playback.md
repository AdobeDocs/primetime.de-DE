---
description: Wenn die DRM-Metadaten für ein Video im Medienstream enthalten sind, können Sie während der Wiedergabe eine Authentifizierung durchführen.
seo-description: Wenn die DRM-Metadaten für ein Video im Medienstream enthalten sind, können Sie während der Wiedergabe eine Authentifizierung durchführen.
seo-title: DRM-Authentifizierung während der Wiedergabe
title: DRM-Authentifizierung während der Wiedergabe
uuid: b3ff8edd-a3d4-470e-8899-580eca9fff4a
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# DRM-Authentifizierung während der Wiedergabe {#drm-authentication-during-playback}

Wenn die DRM-Metadaten für ein Video im Medienstream enthalten sind, können Sie während der Wiedergabe eine Authentifizierung durchführen.

Bei der Lizenzrotation wird ein Asset mit mehreren DRM-Lizenzen verschlüsselt. Jedes Mal, wenn neue DRM-Metadaten gefunden werden, werden die `DRMHelper` Methoden verwendet, um zu überprüfen, ob die DRM-Metadaten DRM-Authentifizierung erfordern.

>[!TIP]
>
>Stellen Sie vor dem Starten der Wiedergabe fest, ob Sie mit einer domänengebundenen Lizenz zu tun haben und ob eine Domänenauthentifizierung erforderlich ist. Falls ja, führen Sie die Domänenauthentifizierung durch und schließen Sie sich der Domäne an.

1. Wenn neue DRM-Metadaten in einem Asset gefunden werden, wird ein Ereignis auf der Anwendungsebene ausgelöst.

   ```java
   mediaPlayer.addEventListener(MediaPlayerEvent.DRM_METADATA,  
                                drmMetadataInfoEventListener); 
   
   DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
     new DRMMetadataInfoEventListener() { 
       @Override 
       public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
           ... 
       } 
   };
   ```

1. Mit der `DRMMetadata` können Sie überprüfen, ob eine Authentifizierung erforderlich ist.

   * Wenn keine Authentifizierung erforderlich ist, müssen Sie nichts tun, und die Wiedergabe wird ununterbrochen fortgesetzt.
   * Ist eine Authentifizierung erforderlich, führen Sie die DRM-Authentifizierung durch.

      Da dieser Vorgang asynchron abläuft und in einem anderen Thread verarbeitet wird, hat er keine Auswirkungen auf die Benutzeroberfläche und auch nicht auf die Videowiedergabe.

1. Wenn die Authentifizierung fehlschlägt, kann der Benutzer das Video nicht weiter anzeigen und die Wiedergabe wird beendet.

<!--<a id="example_939B95F831A245869F9248E2767F260C"></a>-->

Beispiel:

```java
DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
  new DRMMetadataInfoEventListener() { 
    @Override 
    public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
        final DRMMetadataInfo drmMetadataInfo =  
          drmMetadataInfoEvent.getDRMMetadataInfo(); 
 
        if (drmMetadataInfo == null ||  
          !DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { 
            return; 
        } 
 
        // Perform DRM auth. 
        // Possible logic might take into consideration a threshold between the  
        // current player time and the DRM metadata start time. For the time being,  
        // we resolve it as soon as we receive the DRM metadata. 
 
        DRMManager drmManager = _mediaPlayer.getDRMManager(); 
        if (drmManager == null) { 
            return; 
        } 
 
        SharedPreferences sharedPreferences =  
          PreferenceManager.getDefaultSharedPreferences(getActivity()); 
        String authUser = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_USERNAME,  
          getResources().getString(R.string.drmUsername)); 
        String authPass = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_PASSWORD,  
          getResources().getString(R.string.drmPassword)); 
 
        DRMHelper.performDrmAuthentication(drmManager, drmMetadataInfo.getDRMMetadata(),  
          authUser, authPass, new DRMAuthenticationListener() { 
 
            @Override 
            public void onAuthenticationStart() { 
                ... 
            } 
 
            @Override 
            public void onAuthenticationError(int major,  
                                              int minor,  
                                              String erroString,  
                                              String serverErrorURL) { 
                if (getActivity() == null) { 
                    return; 
                } 
                _handler.post(new Runnable() { 
                    @Override 
                    public void run() { 
                        showToast(getString(R.string.drmAuthenticationError)); 
                        getActivity().finish(); 
                    } 
                }); 
            } 
 
            @Override 
            public void onAuthenticationComplete(byte[] authenticationToken) { 
            } 
 
        }); 
    } 
}; 
```

