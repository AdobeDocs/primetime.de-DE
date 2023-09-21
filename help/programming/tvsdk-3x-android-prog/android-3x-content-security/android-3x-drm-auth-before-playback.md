---
description: Wenn die DRM-Metadaten für ein Video vom Medien-Stream getrennt sind, sollten Sie sich authentifizieren, bevor Sie mit der Wiedergabe beginnen.
title: DRM-Authentifizierung vor der Wiedergabe
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# DRM-Authentifizierung vor der Wiedergabe {#drm-authentication-before-playback}

Wenn die DRM-Metadaten für ein Video vom Medien-Stream getrennt sind, sollten Sie sich authentifizieren, bevor Sie mit der Wiedergabe beginnen.

Ein Video-Asset kann über eine verknüpfte DRM-Metadatendatei verfügen, z. B.:

* `"url": "https://www.domain.com/asset.m3u8"`
* `"drmMetadata": "https://www.domain.com/asset.metadata"`

In diesem Beispiel können Sie `DRMHelper` -Methoden, um den Inhalt der DRM-Metadatendatei herunterzuladen, sie zu analysieren und zu überprüfen, ob die DRM-Authentifizierung erforderlich ist.

1. Verwendung `loadDRMMetadata` , um den Metadaten-URL-Inhalt zu laden und die heruntergeladenen Bytes in eine `DRMMetadata`.

   >[!TIP]
   >
   >Diese Methode ist asynchron und erstellt einen eigenen Thread.

   ```java
   public static void loadDRMMetadata( 
       final DRMManager drmManager, 
       final String drmMetadataUrl,  
       final DRMLoadMetadataListener loadMetadataListener); 
   ```

   Beispiel:

   ```java
   DRMHelper.loadDRMMetadata(drmManager,  
                                      metadataURL,  
                                      new DRMLoadMetadataListener());
   ```

1. Informieren Sie den Benutzer darüber, dass dieser Vorgang asynchron ist. Es empfiehlt sich, den Benutzer darauf aufmerksam zu machen.

   Wenn Benutzer nicht wissen, dass der Vorgang asynchron ist, fragen sie sich möglicherweise, warum die Wiedergabe noch nicht gestartet wurde. Sie können beispielsweise ein Rotationsrad anzeigen, während die DRM-Metadaten heruntergeladen und geparst werden.

1. Implementieren Sie die Rückrufe im `DRMLoadMetadataListener`.

   Die `loadDRMMetadata` ruft diese Ereignishandler auf.

   ```java
   public interface DRMLoadMetadataListener { 
   
       public void onLoadMetadataUrlStart(); 
   
       /** 
       * @param authNeeded 
       * whether DRM authentication is needed. 
       * @param drmMetadata 
       * the parsed DRMMetadata obtained.    */ 
       public void onLoadMetadataUrlComplete(boolean authNeeded, DRMMetadata drmMetadata); 
       public void onLoadMetadataUrlError(); 
   } 
   ```

   Im Folgenden finden Sie weitere Details zu den Handlern:

   * `onLoadMetadataUrlStart` erkennt, wann das Laden der Metadaten-URL begonnen hat.
   * `onLoadMetadataUrlComplete` erkennt, wann das Laden der Metadaten-URL abgeschlossen ist.
   * `onLoadMetadataUrlError` gibt an, dass die Metadaten nicht geladen werden konnten.

1. Nachdem das Laden abgeschlossen ist, überprüfen Sie die `DRMMetadata` -Objekt, um zu bestimmen, ob DRM-Authentifizierung erforderlich ist.

   ```java
   public static boolean isAuthNeeded(DRMMetadata drmMetadata);
   ```

   Beispiel:

   ```java
   @Override 
   public void onLoadMetadataUrlComplete(boolean authNeeded, DRMMetadata drmMetadata) {  
       Log.i(LOG_TAG + "#onLoadMetadataUrlComplete",  
             "Loaded metadata URL contents. Auth needed:" + authNeeded + "."); 
       if (!authNeeded) { 
           // Auth is not required. Start player activity.     
           showLoadingSpinner(false);     
           startPlayerActivity(ASSET_URL); 
           return; 
       } 
   } 
   ```

1. Führen Sie eine der folgenden Aufgaben aus:

   * Wenn keine Authentifizierung erforderlich ist, starten Sie die Wiedergabe.
   * Wenn eine Authentifizierung erforderlich ist, schließen Sie die Authentifizierung durch Erwerb der Lizenz ab.

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
     */ 
     public static void performDrmAuthentication( 
          final DRMManager drmManager,  
          final DRMMetadata drmMetadata, 
          final String authUser,  
          final String authPass,  
          final DRMAuthenticationListener authenticationListener);
     ```

     In diesem Beispiel werden der Name und das Kennwort des Benutzers aus Gründen der Einfachheit explizit codiert:

     ```java
     DRMHelper.performDrmAuthentication(drmManager,  
                                        drmMetadata,  
                                        DRM_USERNAME,  
                                        DRM_PASSWORD, new DRMAuthenticationListener() { 
         @Override 
         public void onAuthenticationStart() { 
             Log.i(LOG_TAG + "#onAuthenticationStart", "DRM authentication started."); 
             // Spinner is already showing. 
         } 
         @Override 
         public void onAuthenticationError(int major,  
                                           int minor,  
                                           String errorString,  
                                           String serverErrorURL) { 
             Log.e(LOG_TAG +  
                   "#onAuthenticationError",  
                   "DRM authentication failed. " +  
                   major + " 0x" + Long.toHexString(minor)); 
             showToast(getString(R.string.drmAuthenticationError));   
             showLoadingSpinner(false); 
         } 
         @Override 
         public void onAuthenticationComplete(byte[] authenticationToken) { 
             Log.i(LOG_TAG +  
                   "#onAuthenticationComplete", "Auth successful. Launching content."); 
             showLoadingSpinner(false); 
             startPlayerActivity(ASSET_URL); 
         } 
     }); 
     ```

1. Verwenden Sie einen Ereignis-Listener, um den Authentifizierungsstatus zu überprüfen.

   Dieser Prozess erfordert Netzwerkkommunikation, also handelt es sich auch um einen asynchronen Vorgang.

   ```java
   public interface DRMAuthenticationListener { 
       /** 
       * Called to indicate that DRM authentication has started. 
       */ 
       public void onAuthenticationStart(); 
       /** 
       * Called to indicate that DRM authentication has been successful. 
       * 
       * @param authenticationToken 
       * the obtained token, which can be stored locally. 
       */ 
       public void onAuthenticationComplete(byte[] authenticationToken); 
       /** 
       * Called to indicate that an error occurred while performing the DRM 
       * authentication. 
       * 
       * @param major 
       * the major code. 
       * @param minorC 
       * the minor code. 
       * @param errorString 
       * the exception thrown. 
       * @param serverErrorURL 
       * the URL of the server  
       * on which the error occurred 
       */ 
       public void onAuthenticationError(int major,  
                                         int minor,  
                                         String errorString,  
                                         String serverErrorURL); 
   } 
   ```

1. Wenn die Authentifizierung erfolgreich ist, starten Sie die Wiedergabe.
1. Wenn die Authentifizierung nicht erfolgreich ist, benachrichtigen Sie den Benutzer und starten Sie die Wiedergabe nicht.

   Ihre Anwendung muss etwaige Authentifizierungsfehler beheben. Wenn die Authentifizierung vor der Wiedergabe nicht erfolgreich durchgeführt werden konnte, wird TVSDK in einen Fehlerstatus versetzt und die Wiedergabe wird beendet. Ihre Anwendung muss das Problem beheben, den Player zurücksetzen und die Ressource neu laden.
