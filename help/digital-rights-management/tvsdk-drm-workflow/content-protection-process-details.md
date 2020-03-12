---
seo-title: Details zum Lizenzerwerb
title: Details zum Lizenzerwerb
uuid: 4825c49e-fa6f-4c98-9d21-a2743930ca2e
translation-type: tm+mt
source-git-commit: 3fdef12b717bb6f70ca27d9278de61d709f8349c

---


# Details zum Lizenzerwerb {#license-acquisition-process-details}

Dieser Vorgang stellt eine detaillierte Ansicht des Primetime DRM-Arbeitsablaufs mit geschützten Inhalten auf API-Ebene dar:

1. Laden Sie mithilfe eines `URLLoader` Objekts die Bytes der Metadatendatei des geschützten Inhalts.

   Legen Sie dieses Objekt auf eine Variable wie `metadata_bytes`z. B. Alle von Primetime DRM verwalteten Inhalte verfügen über Primetime DRM-Metadaten. Wenn der Inhalt gepackt wird, können diese Metadaten als separate Metadatendatei ( [!DNL .metadata]) neben dem Inhalt gespeichert werden. Alternativ können die Metadaten Base64-kodiert und in den Hauptteil der Videomanifestdatei eingefügt werden. Weitere Informationen finden Sie unter [Verpacken von Mediendateien](../protecting-content/packaging-media-overview/packaging-media-files.md).
   1. Entfernen Sie bei Bedarf den Ausrufezeichen `!` aus dem Beginn der Zeichenfolge.
   1. Dekodieren Sie bei Bedarf für HLS- oder HDS-Inhalte die enthaltenen Metadaten in der Base64-kodierten Zeichenfolge in Binärdaten, bevor Sie sie weiterleiten.
1. Erstellen Sie eine `DRMContentData` Instanz.

   Fügen Sie diesen Code in einen try-catch-Block ein:

   ```
   new DRMContentData(metadata_bytes)
   ```

   wobei `metadata_bytes` das in Schritt 1 abgerufene `URLLoader` Objekt ist.

   [iOS: DRMMetadata](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_metadata.html)

   [Android: DRMMetadata](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/index.html)

1. Erstellen Sie Listener, die auf das Objekt warten `DRMStatusEvent` und `DRMErrorEvent` vom `DRMManager` Objekt gesendet werden.

   ```
   DRMManager.addEventListener(DRMStatusEvent.DRM_STATUS, onDRMStatus); 
   DRMManager.addEventListener(DRMErrorEvent.DRM_ERROR, onDRMError);
   ```

   Überprüfen Sie im `DRMStatusEvent` Listener, ob die Lizenz gültig ist (nicht null). Nehmen Sie im `DRMErrorEvent` Listener die Hand `DRMErrorEvents`. Siehe *Verwenden der Klasse* DRMStatusEvent und *Verwenden der Klasse* DRMErrorEvent in diesem Handbuch.

1. Laden Sie die Lizenz, die zum Abspielen des Inhalts erforderlich ist.
Laden Sie zunächst eine lokal gespeicherte Lizenz, um den Inhalt wiederzugeben:

   ```
   DRMManager.loadvoucher(drmContentData, LoadVoucherSetting.LOCAL_ONLY)
   ```

   [Android: DRMManager.acquisitionLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquireLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMAcquireLicenseSettings,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))

   [iOS: acquisitionLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a52accb5ed5b49d6e5d91277d78279f1b)

   Nach dem Laden wird das `DRMManager` Objekt ausgelöst `DRMStatusEvent.DRM_Status`.

1. Überprüfen Sie das `DRMVoucher` Objekt.


   Wenn das `DRMVoucher` Objekt nicht null ist, ist die Lizenz gültig. Gehen Sie zu Schritt 9.

   [Android: DRMLicenseAcquiredCallback](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMLicenseAcquiredCallback.html)

   [iOS: DRMLicenseAcquired](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#afe5a9e3a003f312ee268d9b00927fa6d)
1. Überprüfen Sie die Authentifizierungsmethode, die von der Richtlinie für diesen Inhalt benötigt wird.

   Verwenden Sie die `DRMContentData.authenticationMethod` Eigenschaft.
   1. Wenn die Authentifizierungsmethode `ANONYMOUS`ist, fahren Sie mit Schritt 9 fort. 

      [Android: DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/index.html?com/adobe/ave/drm/DRMLicenseAcquiredCallback.html)

      [iOS: DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#a2003f29af93898b52a4123c2dd92c457)
   1. Ist die Authentifizierungsmethode `USERNAME_AND_PASSWORD`aktiviert, muss Ihre Anwendung einen Mechanismus bereitstellen, mit dem der Benutzer Anmeldeinformationen eingeben kann.

      Übergeben Sie die Anmeldeinformationen des Benutzers an den Lizenzserver, um den Benutzer zu authentifizieren:

      ```
      DRMManager.authenticate( metadata.serverURL, metadata.domain, username, password)
      ```

      Der `DRMManager` Dispatch löst einen `DRMAuthenticationErrorEvent` Fehler bei der Authentifizierung aus oder einen `DRMAuthenticationCompleteEvent` Fehler bei der Authentifizierung. Erstellen Sie Listener für diese Ereignis.

      [Android: authentication()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#authenticate(com.adobe.ave.drm.DRMMetadata,%20java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMAuthenticationCompleteCallback))

      [iOS: authentifizieren:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a169c1441f196a834094a8e0f5ecb4aca)

      >[!NOTE]
      >
      >Adobe empfiehlt die Verwendung eines sichereren Mechanismus zur Bereitstellung von Anmeldeinformationen. Weitere Informationen finden Sie unter KeyGenParameterSpec [](https://developer.android.com/reference/android/security/keystore/KeyGenParameterSpec.html).

   1. Ist die Authentifizierungsmethode `UNKNOWN`aktiviert, müssen Sie eine benutzerdefinierte Authentifizierungsmethode verwenden.

      In diesem Fall hat der Content Provider eine Out-of-Band-Authentifizierung ohne Verwendung der Primetime-APIs vereinbart. Das benutzerdefinierte Authentifizierungsverfahren muss ein Authentifizierungstoken erzeugen, das an die `DRMManager.setAuthenticationToken()` Methode übergeben werden kann.

      [Android: setAuthenticationToken()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#setAuthenticationToken(com.adobe.ave.drm.DRMMetadata,%20java.lang.String,%20byte[],%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))

      [iOS: setAuthenticationToken:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a17884b5d9bcc5b0b39503f61140f9b09)

      >[!NOTE]
      >
      >Alternativ `.setAuthenticationToken()` können unabhängig von der Authentifizierungsmethode benutzerdefinierte Daten vom Client an den Lizenzserver gesendet werden. Dies ist eine Überlastung der API, da dieser Mechanismus die einzige Möglichkeit ist, dynamische benutzerdefinierte Daten vom Client zum Zeitpunkt der Lizenzerfassung an den Lizenzserver zu senden. Diese Methode des benutzerdefinierten Datenverkehrs wird in verschiedenen Forenbeiträgen in den [Primetime DRM (Adobe Access) Foren ausführlich diskutiert ](https://forums.adobe.com/community/adobe_access).

1. Wenn die Authentifizierung fehlschlägt, muss Ihre Anwendung zu Schritt 6 zurückkehren.

   Vergewissern Sie sich, dass Ihre Anwendung über einen Mechanismus verfügt, mit dem wiederholte Authentifizierungsfehler behandelt und begrenzt werden können. Nach drei Versuchen zeigen Sie dem Benutzer beispielsweise eine Meldung an, dass die Authentifizierung fehlgeschlagen ist und der Inhalt nicht wiedergegeben werden kann.
1. Um das gespeicherte Token zu verwenden, anstatt den Benutzer zur Eingabe von Anmeldeinformationen aufzufordern, legen Sie das Token mit der `DRMManager.setAuthenticationToken()` Methode fest.

   Laden Sie dann die Lizenz vom Lizenzserver herunter und spielen Sie Inhalte wie in Schritt 6 beschrieben ab.
   1. **Optional:** Bei erfolgreicher Authentifizierung können Sie das Authentifizierungstoken erfassen, bei dem es sich um ein im Arbeitsspeicher zwischengespeichertes Bytearray handelt.

      Rufen Sie dieses Token mit der `DRMAuthenticationCompleteEvent.token` Eigenschaft ab. Sie können das Authentifizierungstoken speichern und verwenden, damit der Benutzer nicht wiederholt Anmeldeinformationen für diesen Inhalt eingeben muss. Der Lizenzserver legt den gültigen Zeitraum des Authentifizierungstokens fest.

      [Android: OperationComplete()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMOperationCompleteCallback.html)

      [iOS: DRMOperationComplete](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#a5f2392ec6661b51bf7b0df71cd514731)
1. Wenn die Authentifizierung erfolgreich ist, laden Sie die Lizenz vom Lizenzserver herunter:

   ```
   DRMManager.loadvoucher( 
      drmContentData, 
      LoadVoucherSetting.FORCE_REFRESH)
   ```

   Nach dem Laden wird das `DRMManager` Objekt ausgelöst `DRMStatusEvent.DRM_STATUS`. Suchen Sie nach diesem Ereignis, und wenn es gesendet wird, können Sie den Inhalt abspielen.  Wiedergabe des Videos durch Erstellen eines Primetime-Objekts und anschließendes Aufrufen der zugehörigen `play()` Methode:

   ```
   stream = new Primetime(connection); 
   stream.addEventListener(DRMStatusEvent.DRM _STATUS, drmStatusHandler); 
   stream.addEventListener(DRMErrorEvent.DRM_ERROR, drmErrorHandler); 
   stream.addEventListener(NetStatusEvent.NET_STATUS, netStatusHandler); 
   stream.client = new CustomClient(); 
   video.attachPrimetime(stream); 
   stream.play(videoURL);
   ```

   [Android: acquisitionLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquireLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMAcquireLicenseSettings,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))

   [iOS: acquisitionLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a52accb5ed5b49d6e5d91277d78279f1b)