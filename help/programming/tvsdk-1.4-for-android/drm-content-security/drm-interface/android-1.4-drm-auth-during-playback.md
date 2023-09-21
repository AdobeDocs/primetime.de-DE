---
description: Wenn die DRM-Metadaten für ein Video im Medien-Stream enthalten sind, führen Sie während der Wiedergabe eine Authentifizierung durch.
title: DRM-Authentifizierung während der Wiedergabe
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# DRM-Authentifizierung während der Wiedergabe {#drm-authentication-during-playback}

Wenn die DRM-Metadaten für ein Video im Medien-Stream enthalten sind, führen Sie während der Wiedergabe eine Authentifizierung durch.

Betrachten Sie die Funktion zur Lizenzrotation, bei der ein Asset mit mehreren DRM-Lizenzen verschlüsselt ist. Verwenden Sie jedes Mal, wenn neue DRM-Metadaten gefunden werden, `DRMHelper` -Methoden, um zu überprüfen, ob die DRM-Metadaten DRM-Authentifizierung erfordern.

>[!NOTE]
>
>In diesem Tutorial werden domänengebundene Lizenzen nicht behandelt. Überprüfen Sie idealerweise vor dem Start der Wiedergabe, ob Sie es mit einer domänengebundenen Lizenz zu tun haben. Falls ja, führen Sie eine Domänenauthentifizierung durch (falls erforderlich) und treten Sie der Domäne bei.

1. Wenn neue DRM-Metadaten in einem Asset gefunden werden, wird ein Ereignis auf der Anwendungsebene gesendet.

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

1. Verwenden Sie die `DRMMetadata` , um zu überprüfen, ob eine Authentifizierung erforderlich ist. Ist dies nicht der Fall, führen Sie nichts aus. Die Wiedergabe wird ununterbrochen fortgesetzt.
1. Führen Sie andernfalls DRM-Authentifizierung durch. Da dieser Vorgang asynchron ist und in einem anderen Thread verarbeitet wird, hat er keine Auswirkungen auf die Benutzeroberfläche und auch keine Videowiedergabe.
1. Wenn die Authentifizierung fehlschlägt, kann der Benutzer die Wiedergabe des Videos nicht fortsetzen und die Wiedergabe wird beendet. Andernfalls wird die Wiedergabe unterbrechungsfrei fortgesetzt.

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
