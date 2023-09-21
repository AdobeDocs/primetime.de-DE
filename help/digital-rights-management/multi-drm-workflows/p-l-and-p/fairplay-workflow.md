---
description: Die DRM-Workflows beinhalten die Verpackung Ihres Inhalts, Lizenzierung des Inhalts und Wiedergabe des geschützten Inhalts über Ihre eigene Videoanwendung. Der Arbeitsablauf ist im Allgemeinen für jede DRM-Lösung ähnlich, allerdings bestehen einige Unterschiede in den Details.
title: Multi-DRM Workflow für FairPlay
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1470'
ht-degree: 0%

---

# Multi-DRM Workflow für FairPlay {#multi-drm-workflow-for-fairplay}

Die DRM-Workflows beinhalten die Verpackung Ihres Inhalts, Lizenzierung des Inhalts und Wiedergabe des geschützten Inhalts über Ihre eigene Videoanwendung. Der Arbeitsablauf ist im Allgemeinen für jede DRM-Lösung ähnlich, allerdings bestehen einige Unterschiede in den Details.

Dieser Multi-DRM-Workflow führt Sie durch Einrichtung, Verpackung, Lizenzierung und Wiedergabe von HLS-Inhalten, die mit Apple FairPlay geschützt sind. Dieser Workflow enthält auch optionale Anweisungen zur Implementierung der Offline-Wiedergabe und der Lizenzrotation.

## Aktivieren des ExpressPlay-Dienstes für FairPlay {#enable-expressplay-service-for-fairplay}

Die FairPlay DRM-Lösung von Apple erfordert einige Einstellungen, wenn Sie sie mit den ExpressPlay DRM-Diensten verwenden. Dazu gehört das Abrufen von Anmeldedaten von Apple und das Hochladen dieser Anmeldedaten in ExpressPlay.

Führen Sie diese Schritte aus, um den ExpressPlay-Dienst für den FairPlay-Inhaltsschutz zu aktivieren.

1. Erhalten Sie Anmeldeinformationen von Apple.

   Diese Anmeldeinformationen werden jedem Dienstleister eindeutig bereitgestellt. Sie müssen sie anfordern, indem Sie das folgende Formular ausfüllen: [https://developer.apple.com/contact/fps/](https://developer.apple.com/contact/fps/).

   >[!NOTE]
   >
   >Auswählen **[!UICONTROL Content Provider]** für die Primäre Rolle.

   Sobald Ihre Anfrage genehmigt wurde, sendet Ihnen Apple eine *FairPlay Streaming-Implementierungspaket*.
1. Generieren Sie eine Certificate Signing Request.

   Sie können [!DNL openssl] , um Ihr Schlüsselpaar aus öffentlichem/privatem Schlüssel und Ihre zertifikatsignierte Anforderung (CSR) zu generieren.

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
      >Die Anweisungen für diesen Schritt finden Sie in Ihrer *FairPlay Streaming-Implementierungspaket*, aber sind hier für Ihre Bequemlichkeit. Wenn Sie Probleme mit diesem Teil des Prozesses haben, lesen Sie die Anweisungen unter *FairPlayCertificateCreation.pdf* (in Ihrem Bereitstellungspaket).

1. Laden Sie Ihre CSR über das Apple-Entwicklerportal hoch.
   1. Der Team Agent für Ihr Entwicklungsteam muss sich bei [!DNL developer.apple.com/account].
   1. Klicken Sie auf **[!UICONTROL Certificates, Identifiers & Profiles]** und wählen Sie dann die **[!UICONTROL iOS, tvOS, watchOS]** links oben auf der Seite und klicken Sie auf **[!UICONTROL Certificates->Production]** auf der linken Seite der Seite.
   1. Klicken Sie auf **[!UICONTROL +]** rechts oben auf der Seite, um ein neues Zertifikat anzufordern. Wählen Sie die **[!UICONTROL FairPlay Streaming Certificate]** Option unter **[!UICONTROL Production]**.

      Die *IOS-Zertifikat hinzufügen* wird geöffnet.
   1. Im *IOS-Zertifikat hinzufügen*, laden Sie die CSR-Datei hoch, die Sie in Schritt 2.b generiert haben, und klicken Sie auf **[!UICONTROL Generate]**.

      Ihr Anwendungs-Geheimschlüssel (ASK) wird im selben Dialogfeld angezeigt.
   1. Schreiben Sie Ihre ASK auf und speichern Sie sie an einem sicheren Ort.
   1. Schlüssel in Ihrem ASK zum Abschließen der Zertifikatgenerierung und klicken Sie auf **[!UICONTROL Continue]**.
   1. Nachdem Sie überprüft haben, ob Sie Ihre ASK gespeichert haben, klicken Sie auf **[!UICONTROL Generate]** , um fortzufahren.

      >[!NOTE]
      >
      >Es ist wichtig, dass Sie eine Kopie Ihres ASK speichern und sicher speichern. *Wenn Ihr ASK kompromittiert ist, können Sie Ihre Inhalte nicht mehr mit FairPlay Streaming schützen.* Nur eine (1) ASK wird Ihrem Team zugewiesen. Der Wert wird nicht erneut bereitgestellt und kann nicht zu einem späteren Zeitpunkt abgerufen werden.

   1. Laden Sie Ihr FPS-Zertifikat herunter.

      Stellen Sie sicher, dass Sie eine Sicherungskopie Ihres privaten Schlüssels (aus Schritt 2.a) und Ihres öffentlichen Schlüssels (das in diesem Schritt heruntergeladene FPS-Zertifikat) an einem sicheren Ort speichern.
1. Richten Sie Ihr ExpressPlay-Konto mit Ihren FairPlay-Anmeldedaten ein.
   1. Angenommen, der in Schritt 3.h heruntergeladene Zertifikatname lautet [!DNL fairplay.cer].
   1. Öffnen Sie die [!DNL fairplay.cer] -Datei mit dem Apple Keychain Access-Dienstprogramm.
   1. Filtern Sie Ihre vielen Zertifikate durch Eingabe von &quot; `fairplay`&quot; in das Suchfeld oben rechts.
   1. Identifizieren Sie das FairPlay-Zertifikat Ihres Unternehmens.

      Ihr Firmenname sollte mit dem von Apple ausgestellten Zertifikat verknüpft sein.
   1. Erweitern Sie das Zertifikat, indem Sie den Pfeil Erweitern auswählen und mit der rechten Maustaste auf Ihren privaten Schlüssel klicken.
   1. Auswählen **[!UICONTROL Export "Your Company Name"]** und speichern Sie die [!DNL .p12] -Datei.

      Sie werden aufgefordert, ein Kennwort zum Schutz dieser Datei zuzuweisen. Notieren Sie sich dieses Kennwort, da Sie es mit Ihrem Anmeldepaket senden müssen.
   1. Melden Sie sich bei Ihrem Konto an bei [www.expressplay.com](https://www.expressplay.com).
   1. Klicks **[!UICONTROL DRM SERVICES]** oben links und wählen Sie dann die **[!UICONTROL FairPlay]** Registerkarte.
   1. Laden Sie Ihre FairPlay-Anmeldedaten in Ihr ExpressPlay-Konto hoch.

      1. Erstellen Sie eine Textdatei, die den Wert Ihres ASK enthält (diese sollte 32 Zeichen lang sein, z. B.: `1234567890abcdef1234567890abcdef`) und wählen Sie diese Datei für den Upload aus.
      1. Wählen Sie die PKCS12-Datei aus Schritt 4.f. zum Hochladen aus.
      1. Geben Sie das PKCS12-Dateikennwort aus Schritt 4.f ein.
      1. Klicken Sie auf die Schaltfläche Hochladen .

Jetzt können Sie iOS-Anwendungen oder HTML5-Seiten mit FairPlay-Inhaltsschutz zusammen mit Ihrem [!DNL fairplay.cer] Zertifikat mit dem ExpressPlay-Dienst für FairPlay.

<!--<a id="fig_sjr_2pn_sv"></a>-->

![](assets/multi_drm_expressplay_drm_services_web.png)

### Verpacken Sie Ihren Inhalt für FairPlay {#package-your-content-for-fairplay}

Um Ihre Inhalte zu verpacken, können Sie entweder Adobe Offline Packager oder andere Tools wie den Bento4 Packager von ExpressPlay verwenden.

Packager bereiten das Video für die Wiedergabe vor (z. B. Fragmentieren der Originaldatei und Einfügen in ein Manifest) und schützen das Video mit der ausgewählten DRM-Lösung (in diesem Fall FairPlay):

* [Adobe Offline Packager für FairPlay DRM](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=21)
* [ExpressPlay-Packager - Bento4 für HLS](https://www.bento4.com/developers/hls/)

<!--<a id="fig_jbn_fw5_xw"></a>-->

![](assets/pkg_lic_play_hls_web.png)

1. Verpacken Sie den Inhalt.

   Im Folgenden finden Sie ein Verpackungsbeispiel mit Adobe Offline Packager. Der Packager verwendet eine Konfigurationsdatei (z. B. [!DNL fairplay.xml]), was ungefähr so aussieht:

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

   * `in_path` - Dieser Eintrag verweist auf den Speicherort des Quellvideos auf Ihrem lokalen Verpackungsgerät.
   * `out_type` - Dieser Eintrag beschreibt den Typ der gepackten Ausgabe, in diesem Fall HLS für FairPlay.
   * `out_path` - Der Speicherort auf dem lokalen Computer, an den die Ausgabe ausgeführt werden soll.
   * `drm_sys` - Die DRM-Lösung, für die Sie die Verpackung verwenden. Dies ist `FAIRPLAY` in diesem Fall.
   * `frag_dur` - Fragmentdauer in Sekunden.
   * `target_dur` - Die Zieldauer für die HLS-Ausgabe.
   * `key_file_path` - Dies ist der Speicherort der Lizenzdatei auf Ihrem Verpackungscomputer, die als Content Encryption Key (CEK) dient. Es handelt sich um eine Base-64-kodierte 16-Byte-Hex-Zeichenfolge.
   * `iv_file_path` - Dies ist der Speicherort der Datei IV auf Ihrem Verpackungsgerät.
   * `key_url` - Der URI-Parameter der `EXT-X-KEY` -Tag [!DNL .m3u8] -Datei.
   * `content_id` - Standardwert.

   Wie im Abschnitt [Packager-Dokumentation](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=7), &quot;Als Best Practice empfiehlt es sich, eine Konfigurationsdatei zu erstellen, die die allgemeinen Optionen enthält, die Sie zum Generieren der Ausgaben verwenden möchten. Erstellen Sie dann die Ausgabe, indem Sie bestimmte Optionen als Befehlszeilenargument angeben.&quot;

   ```
   java -jar OfflinePackager.jar -in_path sample.mp4 -out_type hls 
   -out_path out_file_path -drm -drm_sys FAIRPLAY -key_file_path "creds/fairplay.bin" 
   -key_url "user_provided_value"
   ```

   Die generierte M3U8-Datei verfügt über eine `EXT-X-KEY` -Attribut, das wie folgt angezeigt wird:

   ```
   #EXT-X-KEY:METHOD=SAMPLE-AES,URI="user_provided_value",​
   KEYFORMAT="com.apple.streamingkeydelivery",KEYFORMATVERSIONS="1" 
   ```

### Festlegen von Richtlinien für FairPlay {#setting-policies-for-fairplay}

Sie können mithilfe eines Berechtigungsservers Richtlinien für FairPlay-geschützte Inhalte festlegen. Sie können einen eigenen Berechtigungsserver einrichten oder einen von der Adobe bereitgestellten Beispiel-Berechtigungsserver verwenden.

Adobe bietet einen Beispiel-ExpressPlay-Entitlement-Server (SEES), der die Vorgehensweise anzeigt *zeitbasiert* und *Gerätebindung* Berechtigung. Dieser Beispiel-Berechtigungsserver basiert auf den ExpressPlay-Diensten.

[Referenz-Server: Beispiel für ExpressPlay Entitlement Server (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

* [Referenz-Dienst: Zeitbasierte Berechtigung](../../multi-drm-workflows/feature-topics/sees-reference-server-time-entitlement.md)
* [Referenz-Dienst: Berechtigung zum Binden von Geräten](../../multi-drm-workflows/feature-topics/sees-reference-server-binding-entitlement.md)

## Lizenzierung und Wiedergabe für FairPlay {#licensing-and-playback-for-fairplay}

Die Lizenzierung und Wiedergabe von FairPlay-geschützten Inhalten erfordert den Austausch von URL-Schemas zwischen dem in der Videomanifestdatei verwendeten Schema (skd:) und dem in ExpressPlay-Token-Anfragen verwendeten Schema (https:).

Anweisungen zur Implementierung der Lizenzierung und Wiedergabe von einem iOS TVSDK-Client finden Sie hier: [Aktivieren von Apple FairPlay in TVSDK-Anwendungen](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md). Sie können optional auch die Offline-Wiedergabe und Lizenzrotation für FairPlay implementieren.

## HLS Offline mit FairPlay {#section_047A05D1E3B64883858BC601CFC8F759}

Sie können es Benutzern ermöglichen, FairPlay-geschützte Inhalte abzuspielen, wenn die Lizenzierung nicht abgerufen werden kann, da der Player aus dem Internet isoliert ist (z. B. in einem Flugzeug).

Laden Sie vor Beginn dieser Aufgabe das Apple-Dokument herunter und lesen Sie es **&quot;Offline-Wiedergabe mit FairPlay Streaming und HTTP Live Streaming&quot;**. Lesen Sie das Handbuch, um zu erfahren, wie Sie Transport Stream (TS)-Segmente herunterladen und auf Ihrem lokalen Computer speichern können.

Implementieren der Offline-Wiedergabe für FairPlay mit diesem Workflow:

1. Laden Sie das HLS TS-Segment herunter.
1. Fordern Sie eine dauerhafte Mietlizenz vom FairPlay-Server an (siehe **&quot;FairPlay Persistent Rental Policy&quot;**).
1. Speichern Sie die `persistentContentKey`.
1. FairPlay-Inhalt offline abspielen.

>[!NOTE]
>
>FairPlay Streaming auf dem Client startet die Entschlüsselung nicht, wenn der beibehaltene Inhaltsschlüssel abgelaufen ist. Das Benutzererlebnis wird jedoch fortgesetzt, wenn der Inhaltsschlüssel während der Wiedergabe abläuft.
>
>Siehe [Arbeiten mit HTTP Live Streaming](https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/MediaPlaybackGuide/Contents/Resources/en.lproj/HTTPLiveStreaming/HTTPLiveStreaming.html#//apple_ref/doc/uid/TP40016757-CH11-SW3) für weitere Details.

### FairPlay-Lizenzrotation {#section_D32AA08C61474B4F876AC2A5F18CB879}

Die Lizenzrotation ist ein Schema, das das Lizenzhacken von Inhalten verhindert, die lange wiedergegeben werden.

In einem M3U8-Manifest wird jedes Schlüssel-Tag bis zum nächsten Schlüssel-Tag oder bis zum Ende der Datei auf die folgenden TS-Segmente angewendet.

Gehen Sie wie folgt vor, um eine Lizenzrotation hinzuzufügen:

* Fügen Sie während der Lizenzrotation ein neues FairPlay-Schlüssel-Tag ein.

  Es kann eine beliebige Anzahl von Schlüssel-Tags hinzugefügt werden.

  Achten Sie bei linearen Inhalten darauf, das neueste Schlüsseltag im M3U8-Fenster beizubehalten. iOS fordert den nächsten M3U8 an, wenn zwei TS-Segmente noch abgespielt werden müssen (etwa 20 Sekunden). Wenn das neue M3U8 neue Schlüssel-Tags enthält, werden alle wichtigen Anforderungen sofort ausgeführt. Die vorherigen vorhandenen Schlüssel werden nicht erneut angefordert. iOS wartet, bis alle wichtigen Anforderungen abgeschlossen sind, bevor die Wiedergabe gestartet wird.

  Bei VOD-Inhalten mit Lizenzrotation erfolgen alle Schlüsselanforderungen zu Beginn der Wiedergabe.

  Im Folgenden finden Sie ein Beispiel für M3U8 mit Schlüsselrotation:

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
