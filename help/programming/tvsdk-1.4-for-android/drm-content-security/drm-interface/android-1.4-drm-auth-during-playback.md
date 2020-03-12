---
description: Wenn die DRM-Metadaten für ein Video im Medienstream enthalten sind, führen Sie bei der Wiedergabe eine Authentifizierung durch.
seo-description: Wenn die DRM-Metadaten für ein Video im Medienstream enthalten sind, führen Sie bei der Wiedergabe eine Authentifizierung durch.
seo-title: DRM-Authentifizierung während der Wiedergabe
title: DRM-Authentifizierung während der Wiedergabe
uuid: a1a63e3e-be34-49e1-96c4-ae266003b3d1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# DRM-Authentifizierung während der Wiedergabe {#drm-authentication-during-playback}

Wenn die DRM-Metadaten für ein Video im Medienstream enthalten sind, führen Sie bei der Wiedergabe eine Authentifizierung durch.

Betrachten Sie die Funktion zum Drehen von Lizenzen, bei der ein Asset mit mehreren DRM-Lizenzen verschlüsselt ist. Verwenden Sie bei jeder Erkennung neuer DRM-Metadaten `DRMHelper` Methoden, um zu überprüfen, ob die DRM-Metadaten DRM-Authentifizierung erfordern.

>[!NOTE]
>
>Dieses Lernprogramm behandelt keine domänengebundenen Lizenzen. Überprüfen Sie im Idealfall, ob Sie eine domänengebundene Lizenz haben, bevor Sie die Wiedergabe starten. Falls ja, führen Sie eine Domänenauthentifizierung durch (falls erforderlich) und treten Sie der Domäne bei.

1. Wenn neue DRM-Metadaten in einem Asset gefunden werden, wird ein Ereignis auf der Anwendungsebene ausgelöst.

   ```java
   mediaPlayer.addEventListener(MediaPlayerEvent.DRM_METADATA,  
                                drmMetadataInfoEventListener); 
   
   DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
     new DRMMetadataInfoEventListener() { 
           @Override 
           public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
           } 
   };
   ```

1. Mit der `DRMMetadata` können Sie überprüfen, ob eine Authentifizierung erforderlich ist. Wenn nicht, nichts tun; Die Wiedergabe wird ununterbrochen fortgesetzt.
1. Andernfalls führen Sie die DRM-Authentifizierung durch. Da dieser Vorgang asynchron abläuft und in einem anderen Thread verarbeitet wird, hat er keine Auswirkungen auf die Benutzeroberfläche und auch nicht auf die Videowiedergabe.
1. Wenn die Authentifizierung fehlschlägt, kann der Benutzer das Video nicht weiter anzeigen und die Wiedergabe wird beendet. Andernfalls wird die Wiedergabe ununterbrochen fortgesetzt.

```java
DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
  new DRMMetadataInfoEventListener() { 
    @Override 
    public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
        final DRMMetadataInfo drmMetadataInfo = drmMetadataInfoEvent.getDRMMetadataInfo(); 
 
        if (drmMetadataInfo == null || !DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { 
            return; 
        } 
 
        // Perform DRM auth. 
        // Possible logic might take into consideration a threshold between the current player time and the 
        // DRM metadata start time. For the time being, we resolve it as soon as we receive the DRM metadata. 
 
        DRMManager drmManager = _mediaPlayer.getDRMManager(); 
        if (drmManager == null) { 
            return; 
        } 
 
        SharedPreferences sharedPreferences = PreferenceManager.getDefaultSharedPreferences(getActivity()); 
        String authUser = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_USERNAME,  
          getResources().getString(R.string.drmUsername)); 
          String authPass = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_PASSWORD,  
          getResources().getString(R.string.drmPassword)); 
 
        DRMHelper.performDrmAuthentication(drmManager, drmMetadataInfo.getDRMMetadata(),  
          authUser, authPass, new DRMAuthenticationListener() { 
 
            @Override 
            public void onAuthenticationStart() { 
            } 
 
            @Override 
            public void onAuthenticationError(int major, int minor, String erroString, String serverErrorURL) { 
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
