---
description: Wenn die DRM-Metadaten für ein Video im Medien-Stream enthalten sind, können Sie während der Wiedergabe eine Authentifizierung durchführen.
title: DRM-Authentifizierung während der Wiedergabe
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# DRM-Authentifizierung während der Wiedergabe {#drm-authentication-during-playback}

Wenn die DRM-Metadaten für ein Video im Medien-Stream enthalten sind, können Sie während der Wiedergabe eine Authentifizierung durchführen.

Mit der Lizenzrotation wird ein Asset mit mehreren DRM-Lizenzen verschlüsselt. Jedes Mal, wenn neue DRM-Metadaten gefunden werden, wird die `DRMHelper` -Methoden werden verwendet, um zu überprüfen, ob die DRM-Metadaten DRM-Authentifizierung erfordern.

>[!TIP]
>
>Ermitteln Sie vor dem Start der Wiedergabe, ob Sie es mit einer domänengebundenen Lizenz zu tun haben und ob eine Domänenauthentifizierung erforderlich ist. Wenn ja, schließen Sie die Domänenauthentifizierung ab und treten Sie der Domäne bei.

1. Wenn neue DRM-Metadaten in einem Asset gefunden werden, wird ein Ereignis auf der Anwendungsebene gesendet.

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

1. Verwenden Sie die `DRMMetadata` , um zu überprüfen, ob eine Authentifizierung erforderlich ist.

   * Wenn keine Authentifizierung erforderlich ist, müssen Sie nichts unternehmen und die Wiedergabe wird unterbrechungsfrei fortgesetzt.
   * Wenn eine Authentifizierung erforderlich ist, führen Sie die DRM-Authentifizierung durch.

     Da dieser Vorgang asynchron ist und in einem anderen Thread verarbeitet wird, hat er keine Auswirkungen auf die Benutzeroberfläche und auch keine Videowiedergabe.

1. Wenn die Authentifizierung fehlschlägt, kann der Benutzer die Wiedergabe des Videos nicht fortsetzen und die Wiedergabe wird beendet.

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
