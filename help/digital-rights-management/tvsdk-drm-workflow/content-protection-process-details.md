---
title: Details zum Lizenzakquise-Prozess
description: Details zum Lizenzakquise-Prozess
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 0%

---

# Details zum Lizenzakquise-Prozess {#license-acquisition-process-details}

Dieser Prozess zeigt eine detaillierte Ansicht des Primetime DRM-geschützten Inhalts-Workflows auf API-Ebene:

1. Verwenden eines `URLLoader` -Objekt, laden Sie die Bytes der Metadatendatei des geschützten Inhalts.

   Legen Sie dieses Objekt auf eine Variable fest, z. B. `metadata_bytes`. Alle von Primetime DRM verwalteten Inhalte verfügen über Primetime DRM-Metadaten. Wenn der Inhalt gepackt wird, können diese Metadaten als separate Metadatendatei gespeichert werden ( [!DNL .metadata]) neben dem Inhalt. Alternativ können die Metadaten Base64-kodiert und in den Hauptteil der Videomanifestdatei eingefügt werden. Weitere Informationen finden Sie unter [Verpacken von Mediendateien](../protecting-content/packaging-media-overview/packaging-media-files.md).
   1. Entfernen Sie bei Bedarf den Ausrufezeichen `!` vom Anfang der Zeichenfolge aus.
   1. Dekodieren Sie bei Bedarf für HLS- oder HDS-Inhalte die in der Base64-kodierten Zeichenfolge enthaltenen Metadaten in Binärdaten, bevor Sie sie übergeben.
1. Erstellen Sie eine `DRMContentData` -Instanz.

   Fügen Sie diesen Code in einen try-catch-Block ein:

   ```
   new DRMContentData(metadata_bytes)
   ```

   where `metadata_bytes` ist die `URLLoader` -Objekt, das in Schritt 1 abgerufen wurde.

   [iOS: DRMMetadata](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_metadata.html)

   [Android: DRMMetadata](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/index.html)

1. Erstellen Sie Listener, die auf die `DRMStatusEvent` und `DRMErrorEvent` von der `DRMManager` -Objekt.

   ```
   DRMManager.addEventListener(DRMStatusEvent.DRM_STATUS, onDRMStatus); 
   DRMManager.addEventListener(DRMErrorEvent.DRM_ERROR, onDRMError);
   ```

   Im `DRMStatusEvent` Listener, überprüfen Sie, ob die Lizenz gültig ist (nicht null). Im `DRMErrorEvent` Listener, Handle `DRMErrorEvents`. Siehe *Verwenden der DRMStatusEvent-Klasse* und *Verwenden der DRMErrorEvent-Klasse* in diesem Handbuch.

1. Laden Sie die Lizenz, die zum Abspielen des Inhalts erforderlich ist.
Versuchen Sie zunächst, eine lokal gespeicherte Lizenz zu laden, um den Inhalt wiederzugeben:

   ```
   DRMManager.loadvoucher(drmContentData, LoadVoucherSetting.LOCAL_ONLY)
   ```

   [Android: DRMManager.acquisitionLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquireLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMAcquireLicenseSettings,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))

   [iOS: acquisitionLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a52accb5ed5b49d6e5d91277d78279f1b)

   Nach Abschluss des Ladevorgangs wird die `DRMManager` Objektdispatches `DRMStatusEvent.DRM_Status`.

1. Überprüfen Sie die `DRMVoucher` -Objekt.


   Wenn die Variable `DRMVoucher` -Objekt nicht null ist, ist die Lizenz gültig. Gehen Sie zu Schritt 9.

   [Android: DRMLicenseAcquiredCallback](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMLicenseAcquiredCallback.html)

   [iOS: DRMLicenseAcquired](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#afe5a9e3a003f312ee268d9b00927fa6d)
1. Überprüfen Sie die Authentifizierungsmethode, die von der Richtlinie für diesen Inhalt benötigt wird.

   Verwenden Sie die `DRMContentData.authenticationMethod` -Eigenschaft.
   1. Wenn die Authentifizierungsmethode `ANONYMOUS`, gehen Sie zu Schritt 9. 

      [Android: DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/index.html?com/adobe/ave/drm/DRMLicenseAcquiredCallback.html)

      [iOS: DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#a2003f29af93898b52a4123c2dd92c457)
   1. Wenn die Authentifizierungsmethode `USERNAME_AND_PASSWORD`muss Ihre Anwendung einen Mechanismus bereitstellen, mit dem der Benutzer Anmeldeinformationen eingeben kann.

      Übergeben Sie die Anmeldeinformationen des Benutzers an den Lizenzserver, um den Benutzer zu authentifizieren:

      ```
      DRMManager.authenticate( metadata.serverURL, metadata.domain, username, password)
      ```

      Die `DRMManager` sendet einen `DRMAuthenticationErrorEvent` wenn die Authentifizierung fehlschlägt, oder eine `DRMAuthenticationCompleteEvent` wenn die Authentifizierung erfolgreich ist. Erstellen Sie Listener für diese Ereignisse.

      [Android: authenticate()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#authenticate(com.adobe.ave.drm.DRMMetadata,%20java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMAuthenticationCompleteCallback))

      [iOS: authenticate:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a169c1441f196a834094a8e0f5ecb4aca)

      >[!NOTE]
      >
      >Adobe empfiehlt die Verwendung eines sichereren Mechanismus zur Bereitstellung von Anmeldeinformationen. Weitere Informationen finden Sie unter [KeyGenParameterSpec](https://developer.android.com/reference/android/security/keystore/KeyGenParameterSpec.html).

   1. Wenn die Authentifizierungsmethode `UNKNOWN`müssen Sie eine benutzerdefinierte Authentifizierungsmethode verwenden.

      In diesem Fall hat der Inhalts-Provider festgelegt, dass die Authentifizierung Out-of-Band-erfolgt, ohne die Primetime-APIs zu verwenden. Das benutzerdefinierte Authentifizierungsverfahren muss ein Authentifizierungstoken erzeugen, das an die `DRMManager.setAuthenticationToken()` -Methode.

      [Android: setAuthenticationToken()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#setAuthenticationToken(com.adobe.ave.drm.DRMMetadata,%20java.lang.String,%20byte[],%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))

      [iOS: setAuthenticationToken:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a17884b5d9bcc5b0b39503f61140f9b09)

      >[!NOTE]
      >
      >Alternativ können Sie unabhängig von der Authentifizierungsmethode `.setAuthenticationToken()` kann verwendet werden, um benutzerdefinierte Daten vom Client an den Lizenzserver zu senden. Dies ist eine Überlastung der API, da dieser Mechanismus die einzige Möglichkeit ist, dynamische benutzerdefinierte Daten vom Client zum Zeitpunkt der Lizenzakquise an den Lizenzserver zu senden. Diese Methode des benutzerdefinierten Datenverkehrs wird in verschiedenen Forumsbeiträgen im Abschnitt [Primetime-DRM-Foren (Adobe-Zugriff)](https://forums.adobe.com/community/adobe_access).

1. Wenn die Authentifizierung fehlschlägt, muss Ihre Anwendung zu Schritt 6 zurückkehren.

   Stellen Sie sicher, dass Ihre Anwendung über einen Mechanismus zum Verarbeiten und Eingrenzen wiederholter Authentifizierungsfehler verfügt. Beispielsweise wird dem Benutzer nach drei Versuchen eine Meldung angezeigt, die angibt, dass die Authentifizierung fehlgeschlagen ist und der Inhalt nicht wiedergegeben werden kann.
1. Um das gespeicherte Token zu verwenden, anstatt den Benutzer zur Eingabe der Anmeldeinformationen aufzufordern, setzen Sie das Token mit dem `DRMManager.setAuthenticationToken()` -Methode.

   Anschließend laden Sie die Lizenz vom Lizenzserver herunter und geben Inhalte wie in Schritt 6 beschrieben wieder.
   1. **Optional:** Wenn die Authentifizierung erfolgreich ist, können Sie das Authentifizierungstoken erfassen, bei dem es sich um ein im Speicher zwischengespeichertes Byte-Array handelt.

      Rufen Sie dieses Token mit dem `DRMAuthenticationCompleteEvent.token` -Eigenschaft. Sie können das Authentifizierungstoken speichern und verwenden, damit der Benutzer die Anmeldeinformationen für diesen Inhalt nicht wiederholt eingeben muss. Der Lizenzserver legt den gültigen Zeitraum des Authentifizierungstokens fest.

      [Android: OperationComplete()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMOperationCompleteCallback.html)

      [iOS: DRMOperationComplete](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#a5f2392ec6661b51bf7b0df71cd514731)
1. Wenn die Authentifizierung erfolgreich ist, laden Sie die Lizenz vom Lizenzserver herunter:

   ```
   DRMManager.loadvoucher( 
      drmContentData, 
      LoadVoucherSetting.FORCE_REFRESH)
   ```

   Nach Abschluss des Ladevorgangs wird die `DRMManager` Objektdispatches `DRMStatusEvent.DRM_STATUS`. Suchen Sie nach diesem Ereignis. Wenn es gesendet wird, können Sie den Inhalt abspielen.  Wiedergabe des Videos durch Erstellen eines Primetime-Objekts und anschließendes Aufrufen der zugehörigen `play()` -Methode:

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
