---
description: Das DRM-Workflows umfasst das Verpacken Ihrer Inhalte, die Bereitstellung von Lizenzen für die Inhalte und die Wiedergabe der geschützten Inhalte aus Ihrer eigenen Videoanwendung. Der Arbeitsablauf ist im Allgemeinen für jede DRM-Lösung ähnlich, jedoch mit einigen Unterschieden in den Details.
seo-description: Das DRM-Workflows umfasst das Verpacken Ihrer Inhalte, die Bereitstellung von Lizenzen für die Inhalte und die Wiedergabe der geschützten Inhalte aus Ihrer eigenen Videoanwendung. Der Arbeitsablauf ist im Allgemeinen für jede DRM-Lösung ähnlich, jedoch mit einigen Unterschieden in den Details.
seo-title: Multi-DRM Workflow für FairPlay
title: Multi-DRM Workflow für FairPlay
uuid: cd940a70-400c-435e-8322-55bd624164e1
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 0%

---


# Multi-DRM Workflow für FairPlay {#multi-drm-workflow-for-fairplay}

Das DRM-Workflows umfasst das Verpacken Ihrer Inhalte, die Bereitstellung von Lizenzen für die Inhalte und die Wiedergabe der geschützten Inhalte aus Ihrer eigenen Videoanwendung. Der Arbeitsablauf ist im Allgemeinen für jede DRM-Lösung ähnlich, jedoch mit einigen Unterschieden in den Details.

Dieser Multi-DRM-Arbeitsablauf führt Sie durch Einrichtung, Verpackung, Lizenzierung und Wiedergabe von HLS-Inhalten, die mit Apple FairPlay geschützt sind. Dieser Arbeitsablauf enthält auch optionale Anweisungen zur Implementierung der Offline-Wiedergabe und Lizenzrotation.

## ExpressPlay-Dienst für FairPlay aktivieren {#enable-expressplay-service-for-fairplay}

Die FairPlay DRM-Lösung von Apple erfordert ein gewisses Setup, wenn Sie sie mit den ExpressPlay DRM-Diensten verwenden. Hierzu müssen Sie Anmeldeinformationen von Apple abrufen und in ExpressPlay hochladen.

Führen Sie die folgenden Schritte aus, um den ExpressPlay-Dienst für den Schutz von FairPlay-Inhalten zu aktivieren.

1. Erhalten Sie Anmeldeinformationen von Apple.

   Diese Anmeldeinformationen werden jedem Dienstleister eindeutig bereitgestellt. Sie müssen sie anfordern, indem Sie das folgende Formular ausfüllen: [https://developer.apple.com/contact/fps/](https://developer.apple.com/contact/fps/).

   >[!NOTE]
   >
   >Wählen Sie **[!UICONTROL Content Provider]** &quot;Primär Rolle&quot;.

   Nachdem Ihre Anforderung genehmigt wurde, sendet Apple Ihnen ein *FairPlay Streaming-Bereitstellungspaket*.
1. Generate a Certificate Signing Request.

   Sie können Ihr öffentliches/privates Schlüsselpaar und Ihre mit Zertifikat signierte Anforderung (CSR) [!DNL openssl] generieren.

   1. Generieren Sie Ihr Schlüsselpaar.

      ```
      openssl genrsa -aes256 -out privatekey.pem 1024 
      ```

   1. Erstellen Sie Ihre CSR.

      ```
      openssl req -new -sha1 -key privatekey.pem -out certreq.csr  
        -subj "/CN=SubjectName /OU=OrganizationalUnit /O=Organization /C=US"
      ```

      >[!NOTE]
      >
      >Die Anweisungen für diesen Schritt finden Sie in Ihrem *FairPlay Streaming-Bereitstellungspaket*, aber Sie finden sie hier. Wenn Sie Probleme mit diesem Teil des Prozesses haben, lesen Sie die Anweisungen in *FairPlayCertificateCreation.pdf* (in Ihrem Bereitstellungspaket).

1. Laden Sie Ihr CSR über das Apple Developer Portal hoch.
   1. The Team Agent for your development team must log into [!DNL developer.apple.com/account].
   1. Klicken Sie auf **[!UICONTROL Certificates, Identifiers & Profiles]**, wählen Sie das **[!UICONTROL iOS, tvOS, watchOS]** Dropdown-Menü oben links auf der Seite und klicken Sie dann auf **[!UICONTROL Certificates->Production]** links auf der Seite.
   1. Klicken Sie auf die **[!UICONTROL +]** Schaltfläche oben rechts auf der Seite, um ein neues Zertifikat anzufordern. Wählen Sie die **[!UICONTROL FairPlay Streaming Certificate]** Option unter **[!UICONTROL Production]**.

      Das Dialogfeld *Hinzufügen iOS-Zertifikat* wird geöffnet.
   1. In the *Add iOS Certificate*, upload the CSR file you generated in Step 2.b., and click **[!UICONTROL Generate]**.

      Ihr Anwendungs-Geheimcode-Key (ASK) wird im selben Dialogfeld angezeigt.
   1. Write down your ASK, and store it in a safe location.
   1. Key in your ASK to complete certificate generation and click **[!UICONTROL Continue]**.
   1. After you verify that you have saved your ASK, click **[!UICONTROL Generate]** to continue.

      >[!NOTE]
      >
      >It is important that you save a copy of your ASK and store it securely. *If your ASK is compromised, you will no longer be able to protect your content with FairPlay Streaming.* Only one (1) ASK is allocated to your team. The value will not be provided again and you cannot retrieve it at a later time.

   1. Download your FPS Certificate.

      Be sure to save a backup copy of your private key (from Step 2.a.) and your public key (the FPS Certificate you downloaded in this step) in a safe place.
1. Set up your ExpressPlay account with your FairPlay credentials.
   1. Let&#39;s say the certificate name you downloaded in Step 3.h. is [!DNL fairplay.cer].
   1. Öffnen Sie die [!DNL fairplay.cer] Datei mit dem Apple Keychain Access-Dienstprogramm.
   1. Filter your many certificates by entering &quot; `fairplay`&quot; in the search field located up on the top right.
   1. Identifizieren Sie das FairPlay-Zertifikat Ihrer Firma.

      Ihr Firmen-Name sollte mit dem von Apple ausgestellten Zertifikat verknüpft sein.
   1. Erweitern Sie das Zertifikat, indem Sie den Pfeil erweitern und mit der rechten Maustaste auf den privaten Schlüssel klicken.
   1. Wählen Sie **[!UICONTROL Export "Your Company Name"]** die [!DNL .p12] Datei aus und speichern Sie sie.

      Sie werden gebeten, ein Kennwort zuzuweisen, um diese Datei zu sichern. Notieren Sie sich dieses Kennwort, da Sie es mit Ihrem Anmeldepaket senden müssen.
   1. Melden Sie sich bei Ihrem Konto unter [www.expressplay.com](https://www.expressplay.com)an.
   1. Klicken Sie **[!UICONTROL DRM SERVICES]** oben links und wählen Sie dann die **[!UICONTROL FairPlay]** Registerkarte aus.
   1. Laden Sie Ihre FairPlay-Anmeldedaten in Ihr ExpressPlay-Konto hoch.

      1. Erstellen Sie eine Textdatei, die den Wert Ihres ASK enthält (diese sollte 32 Zeichen umfassen, z. B.: `1234567890abcdef1234567890abcdef`) und wählen Sie diese Datei zum Hochladen aus.
      1. Wählen Sie die PKCS12-Datei aus Schritt 4.f. zum Hochladen.
      1. Geben Sie in Schritt 4.f das Kennwort für die PKCS12-Datei ein.
      1. Klicken Sie auf die Schaltfläche &quot;Hochladen&quot;.

Jetzt können Sie iOS-Anwendungen oder HTML5-Seiten mit FairPlay-Inhaltsschutz zusammen mit Ihrem [!DNL fairplay.cer] Zertifikat mit dem ExpressPlay-Dienst für FairPlay erstellen.

<!--<a id="fig_sjr_2pn_sv"></a>-->

![](assets/multi_drm_expressplay_drm_services_web.png)

### Verpacken Sie Ihre Inhalte für FairPlay {#package-your-content-for-fairplay}

Zum Verpacken von Inhalten können Sie entweder Adobe Offline Packager oder andere Tools wie z. B. den Bento4 Packager von ExpressPlay verwenden.

Packager bereiten das Video für die Wiedergabe vor (z. B. Fragmentieren der Originaldatei und Einfügen in ein Manifest) und schützen das Video mit der ausgewählten DRM-Lösung (in diesem Fall FairPlay):

* [Adobe Offline Packager for FairPlay DRM](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=21)
* [ExpressPlay Packager - Bento4 für HLS](https://www.bento4.com/developers/hls/)

<!--<a id="fig_jbn_fw5_xw"></a>-->

![](assets/pkg_lic_play_hls_web.png)

1. Verpacken Sie Ihren Inhalt.

   Im Folgenden finden Sie ein Verpackungsbeispiel mit Adobe Offline Packager. Der Packager verwendet eine Konfigurationsdatei (z. B. [!DNL fairplay.xml]), die wie folgt aussieht:

   ```
   <config>
   <in_path>mp4_file_path</in_path>
   <out_type>hls</out_type>
   <out_path>out_file_path</out_path>
   <drm/>
   <drm_sys>FAIRPLAY</drm_sys>
   <frag_dur>4</frag_dur>
   <target_dur>6</target_dur>
   <key_file_path>creds/fairplay.bin</key_file_path>
   <iv_file_path>creds/iv.bin</iv_file_path>
   <key_url>user_provided_value</key_url>
   <content_id>_default_</content_id>
   </config>
   ```

   * `in_path` - Dieser Eintrag verweist auf die Position des Quellvideos auf Ihrem lokalen Verpackungscomputer.
   * `out_type` - Dieser Eintrag beschreibt den Typ der verpackten Ausgabe, in diesem Fall HLS für FairPlay.
   * `out_path` - Der Speicherort auf dem lokalen Computer, auf den die Ausgabe gesendet werden soll.
   * `drm_sys` - Die DRM-Lösung, für die Sie verpacken. This is `FAIRPLAY` in this case.
   * `frag_dur` - Fragmentdauer in Sekunden.
   * `target_dur` - Die Dauer der Zielgruppe für die HLS-Ausgabe.
   * `key_file_path` - Dies ist der Speicherort der Lizenzdatei auf Ihrem Verpackungscomputer, der als Content Encryption Key (CEK) dient. Es handelt sich um eine Base-64-kodierte 16-Byte-Hex-Zeichenfolge.
   * `iv_file_path` - This is the location of the IV file on your packaging machine.
   * `key_url` - The URI parameter of the `EXT-X-KEY` tag of the [!DNL .m3u8] file.
   * `content_id` - Default value.

   As stated in the [Packager documentation](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=7), &quot;As a best practice, create a configuration file that contains the common options that you want to use for generating the outputs. Then, create the output by providing specific options as a command-line argument.&quot;

   ```
   java -jar OfflinePackager.jar -in_path sample.mp4 -out_type hls 
   -out_path out_file_path -drm -drm_sys FAIRPLAY -key_file_path "creds/fairplay.bin" 
   -key_url "user_provided_value"
   ```

   The generated M3U8 file has an `EXT-X-KEY` attribute that appears as follows:

   ```
   #EXT-X-KEY:METHOD=SAMPLE-AES,URI="user_provided_value",​
   KEYFORMAT="com.apple.streamingkeydelivery",KEYFORMATVERSIONS="1" 
   ```

### Setting policies for FairPlay {#setting-policies-for-fairplay}

You can set polices for FairPlay-protected content by using an entitlement server. You can set up your own, or make use of an Adobe-provided sample entitlement server.

Adobe provides a Sample ExpressPlay Entitlement Server (SEES) that shows how to do *time-based* and *device-binding* entitlement. This sample entitlement server is built on top of ExpressPlay services.

[Reference Server: Sample ExpressPlay Entitlement Server (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

* [Reference Service: Time-based Entitlement](../../multi-drm-workflows/feature-topics/sees-reference-server-time-entitlement.md)
* [Reference Service: Device-Binding Entitlement](../../multi-drm-workflows/feature-topics/sees-reference-server-binding-entitlement.md)

## Lizenzierung und Wiedergabe von FairPlay {#licensing-and-playback-for-fairplay}

Die Lizenzierung und Wiedergabe von FairPlay-geschützten Inhalten erfordert den Austausch von URL-Schemata zwischen dem in der Videomanifestdatei verwendeten Schema (skd:) und dem Schema, das in ExpressPlay-Token-Anforderungen verwendet wird (https:).

Anweisungen zum Implementieren der Lizenzierung und Wiedergabe von einem iOS TVSDK-Client finden Sie hier: [Aktivieren Sie Apple FairPlay in TVSDK-Anwendungen](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md). Sie können auch optional die Offline-Wiedergabe und Lizenzrotation für FairPlay implementieren.

## HLS Offline mit FairPlay {#section_047A05D1E3B64883858BC601CFC8F759}

You may want to make it possible for users to play FairPlay-protected content when its licensing is not retrievable because the player is isolated from the web (such as on an airplane).

Bevor Sie mit dieser Aufgabe beginnen, laden Sie das Apple-Dokument **&quot;Offline Play-back with FairPlay Streaming and HTTP Live Streaming&quot;** herunter und lesen Sie es. Read the guide to learn how to download Transport Stream (TS) segments and save them to your local machine.

Implement offline play for FairPlay with this workflow:

1. Download the HLS TS segment.
1. Request Persistent Rental license from the FairPlay server (see **&quot;FairPlay Persistent Rental Policy&quot;**).
1. Save the `persistentContentKey`.
1. Play the FairPlay content offline.

>[!NOTE]
>
>FairPlay Streaming on the client does not start decryption if the persisted content key has expired. However, it will continue the user experience if the content key expires during playback.
>
>See [Working with HTTP Live Streaming](https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/MediaPlaybackGuide/Contents/Resources/en.lproj/HTTPLiveStreaming/HTTPLiveStreaming.html#//apple_ref/doc/uid/TP40016757-CH11-SW3) document for more details.

### FairPlay license rotation {#section_D32AA08C61474B4F876AC2A5F18CB879}

License rotation is a scheme for preventing license hacking of content that plays for a long time.

In an M3U8 manifest, each key tag will apply to the following TS segments until the next key tag, or until the end of the file.

To add license rotation, do the following:

* Insert a new FairPlay key tag during license rotation time.

   Any number of key tags can be added.

   For linear contents, make sure to maintain the most recent key tag in the M3U8 window. iOS will request the next M3U8 when there are about two TS segments left to be played (around 20 seconds). If the new M3U8 contains new key tags, all of the key requests will happen immediately. The previous existing keys will not be requested again. iOS will wait for all of the key requests to finish before playback will start.

   For VOD contents with license rotation, all of the key requests will happen at the beginning of playback.

   Following is a sample M3U8 with key rotation:

   ```
   #EXTM3U
   #EXT-X-TARGETDURATION:10
   #EXT-X-VERSION:5
   #EXT-X-MEDIA-SEQUENCE:0
   #EXT-X-PLAYLIST-TYPE:VOD
   #EXT-X-KEY:METHOD=SAMPLE-AES,URI="skd://one?cek=1dc2cc71d913f4f74eca0c4632
   212b25&iv=e21f0f72b6363ff6143737cb1e9ca8d7",KEYFORMAT="com.apple.streaming
   keydelivery",KEYFORMATVERSIONS="1"
   #EXTINF:10,
   fileSequence0.ts
   #EXTINF:10,
   fileSequence1.ts
   #EXTINF:10,
   fileSequence2.ts
   #EXTINF:10,
   fileSequence3.ts
   #EXTINF:10,
   fileSequence4.ts
   #EXTINF:10,
   fileSequence5.ts
   #EXTINF:10,
   fileSequence6.ts
   #EXTINF:10,
   fileSequence7.ts
   #EXTINF:10,
   #EXT-X-KEY:METHOD=SAMPLE-AES,URI="skd://two?cek=f6efc698b96cf8f4fa46d5237d
   337c77&iv=18401077091784bcda8079acf978dc95",KEYFORMAT="com.apple.streaming
   keydelivery",KEYFORMATVERSIONS="1"
   #EXTINF:10,
   fileSequence8.ts
   #EXTINF:10,
   ```
