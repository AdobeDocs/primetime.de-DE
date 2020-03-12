---
description: Das DRM-Workflows umfasst das Verpacken Ihrer Inhalte, die Bereitstellung von Lizenzen für die Inhalte und die Wiedergabe der geschützten Inhalte aus Ihrer eigenen Videoanwendung. Der Arbeitsablauf ist im Allgemeinen für jede DRM-Lösung ähnlich, jedoch mit einigen Unterschieden in den Details.
seo-description: Das DRM-Workflows umfasst das Verpacken Ihrer Inhalte, die Bereitstellung von Lizenzen für die Inhalte und die Wiedergabe der geschützten Inhalte aus Ihrer eigenen Videoanwendung. Der Arbeitsablauf ist im Allgemeinen für jede DRM-Lösung ähnlich, jedoch mit einigen Unterschieden in den Details.
seo-title: Multi-DRM Workflow für FairPlay
title: Multi-DRM Workflow für FairPlay
uuid: cd940a70-400c-435e-8322-55bd624164e1
translation-type: tm+mt
source-git-commit: 29149594c4b41956a091ef27093304e74ff15f2f

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
   >Wählen Sie **[!UICONTROL Content Provider]** &quot;Primäre Rolle&quot;.

   Nachdem Ihre Anforderung genehmigt wurde, sendet Apple Ihnen ein *FairPlay Streaming-Bereitstellungspaket*.
1. Erstellen einer Zertifikatsignaturanforderung.

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
   1. Der Team Agent für Ihr Entwicklungsteam muss sich anmelden [!DNL developer.apple.com/account].
   1. Klicken Sie auf **[!UICONTROL Certificates, Identifiers & Profiles]**, wählen Sie das **[!UICONTROL iOS, tvOS, watchOS]** Dropdown-Menü oben links auf der Seite und klicken Sie dann auf **[!UICONTROL Certificates->Production]** links auf der Seite.
   1. Klicken Sie auf die **[!UICONTROL +]** Schaltfläche oben rechts auf der Seite, um ein neues Zertifikat anzufordern. Wählen Sie die **[!UICONTROL FairPlay Streaming Certificate]** Option unter **[!UICONTROL Production]**.

      Das Dialogfeld *Hinzufügen iOS-Zertifikat* wird geöffnet.
   1. Laden Sie im *Hinzufügen iOS-Zertifikat* die CSR-Datei hoch, die Sie in Schritt 2.b erstellt haben, und klicken Sie auf **[!UICONTROL Generate]**.

      Ihr Anwendungs-Geheimcode-Key (ASK) wird im selben Dialogfeld angezeigt.
   1. Notieren Sie sich Ihren ASK und speichern Sie ihn an einem sicheren Ort.
   1. Schlüssel in Ihrem ASK, um die Zertifikatgenerierung abzuschließen und klicken Sie auf **[!UICONTROL Continue]**.
   1. Nachdem Sie sich vergewissert haben, dass Sie Ihr ASK gespeichert haben, klicken Sie auf **[!UICONTROL Generate]** , um fortzufahren.

      >[!NOTE] {important=&quot;high&quot;}
      >
      >Es ist wichtig, dass Sie eine Kopie Ihres ASK speichern und sicher speichern. *Wenn Ihr ASK beeinträchtigt wird, können Sie Ihre Inhalte nicht mehr mit FairPlay Streaming schützen.* Nur ein ASK (1) wird Ihrem Team zugeordnet. Der Wert wird nicht erneut bereitgestellt und kann nicht zu einem späteren Zeitpunkt abgerufen werden.

   1. Laden Sie das FPS-Zertifikat herunter.

      Stellen Sie sicher, dass Sie eine Sicherungskopie Ihres privaten Schlüssels (ab Schritt 2.a) und Ihres öffentlichen Schlüssels (das FPS-Zertifikat, das Sie in diesem Schritt heruntergeladen haben) an einem sicheren Ort speichern.
1. Richten Sie Ihr ExpressPlay-Konto mit Ihren FairPlay-Anmeldedaten ein.
   1. Nehmen wir an, der Zertifikatsname, den Sie in Schritt 3.h heruntergeladen haben. el [!DNL fairplay.cer].
   1. Öffnen Sie die [!DNL fairplay.cer] Datei mit dem Apple Keychain Access-Dienstprogramm.
   1. Filtern Sie Ihre vielen Zertifikate, indem Sie in das Suchfeld oben rechts &quot; `fairplay`&quot;eingeben.
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

Zum Verpacken Ihrer Inhalte können Sie entweder Adobe Offline Packager oder andere Werkzeuge wie den Bento4 Packager von ExpressPlay verwenden.

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
   * `drm_sys` - Die DRM-Lösung, für die Sie verpacken. Das ist `FAIRPLAY` in diesem Fall.
   * `frag_dur` - Fragmentdauer in Sekunden.
   * `target_dur` - Die Dauer der Zielgruppe für die HLS-Ausgabe.
   * `key_file_path` - Dies ist der Speicherort der Lizenzdatei auf Ihrem Verpackungscomputer, der als Content Encryption Key (CEK) dient. Es handelt sich um eine Base-64-kodierte 16-Byte-Hex-Zeichenfolge.
   * `iv_file_path` - Dies ist der Speicherort der Datei IV auf Ihrem Verpackungsgerät.
   * `key_url` - Der URI-Parameter des `EXT-X-KEY` Tags der [!DNL .m3u8] Datei.
   * `content_id` - Standardwert.
   Wie in der [Packager-Dokumentation](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=7)beschrieben, sollten Sie eine Konfigurationsdatei mit den allgemeinen Optionen erstellen, die Sie zum Generieren der Ausgaben verwenden möchten. Erstellen Sie dann die Ausgabe, indem Sie bestimmte Optionen als Befehlszeilenargument angeben.&quot;

   ```
   java -jar OfflinePackager.jar -in_path sample.mp4 -out_type hls 
   -out_path out_file_path -drm -drm_sys FAIRPLAY -key_file_path "creds/fairplay.bin" 
   -key_url "user_provided_value"
   ```

   Die generierte M3U8-Datei verfügt über ein `EXT-X-KEY` Attribut, das wie folgt angezeigt wird:

   ```
   #EXT-X-KEY:METHOD=SAMPLE-AES,URI="user_provided_value",​
   KEYFORMAT="com.apple.streamingkeydelivery",KEYFORMATVERSIONS="1" 
   ```

### Richtlinien für FairPlay festlegen {#setting-policies-for-fairplay}

Sie können Richtlinien für FairPlay-geschützte Inhalte mithilfe eines Berechtigungsservers festlegen. Sie können einen eigenen Berechtigungsserver einrichten oder einen von Adobe bereitgestellten Beispielberechtigungsserver verwenden.

Adobe stellt einen Beispielserver für ExpressPlay-Berechtigungen (SEES) bereit, der zeigt, wie *zeitbasierte* und *gerätegebundene* Berechtigungen ausgeführt werden. Dieser Beispielberechtigungsserver basiert auf den ExpressPlay-Diensten.

[Referenz-Server: Beispiel für einen ExpressPlay-Berechtigungsserver (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

* [Referenz-Dienst: Zeitbasierte Berechtigung](../../multi-drm-workflows/feature-topics/sees-reference-server-time-entitlement.md)
* [Referenz-Dienst: Berechtigung für Gerätebindung](../../multi-drm-workflows/feature-topics/sees-reference-server-binding-entitlement.md)

## Lizenzierung und Wiedergabe von FairPlay {#licensing-and-playback-for-fairplay}

Die Lizenzierung und Wiedergabe von FairPlay-geschützten Inhalten erfordert den Austausch von URL-Schemata zwischen dem in der Videomanifestdatei verwendeten Schema (skd:) und dem Schema, das in ExpressPlay-Token-Anforderungen verwendet wird (https:).

Anweisungen zum Implementieren der Lizenzierung und Wiedergabe von einem iOS TVSDK-Client finden Sie hier: Apple FairPlay in TVSDK-Anwendungen [aktivieren](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md). Sie können auch optional die Offline-Wiedergabe und Lizenzrotation für FairPlay implementieren.

## HLS Offline mit FairPlay {#section_047A05D1E3B64883858BC601CFC8F759}

Sie können es Benutzern ermöglichen, FairPlay-geschützte Inhalte abzuspielen, wenn die Lizenzierung nicht abgerufen werden kann, da der Player aus dem Internet isoliert ist (z. B. auf einem Flugzeug).

Bevor Sie mit dieser Aufgabe beginnen, laden Sie das Apple-Dokument **&quot;Offline Play-back with FairPlay Streaming and HTTP Live Streaming&quot;** herunter und lesen Sie es. Lesen Sie das Handbuch, um zu erfahren, wie Sie Transport Stream (TS)-Segmente herunterladen und auf Ihrem lokalen Computer speichern können.

Implementieren Sie die Offline-Wiedergabe für FairPlay mit diesem Workflow:

1. Laden Sie das Segment HLS TS herunter.
1. Fordern Sie eine dauerhafte Mietlizenz vom FairPlay-Server an (siehe **&quot;FairPlay Persistent Rental Policy&quot;**).
1. Speichern Sie die `persistentContentKey`.
1. Wiedergabe des FairPlay-Inhalts offline.

>[!NOTE]
>
>FairPlay Streaming auf dem Client führt keine Entschlüsselung des Beginns durch, wenn der beibehaltene Inhaltsschlüssel abgelaufen ist. Das Benutzererlebnis wird jedoch fortgesetzt, wenn der Inhaltsschlüssel während der Wiedergabe abläuft.
>
>Weitere Informationen finden Sie unter [Arbeiten mit dem HTTP Live Streaming](https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/MediaPlaybackGuide/Contents/Resources/en.lproj/HTTPLiveStreaming/HTTPLiveStreaming.html#//apple_ref/doc/uid/TP40016757-CH11-SW3) -Dokument.

### FairPlay-Lizenzrotation {#section_D32AA08C61474B4F876AC2A5F18CB879}

Die Lizenzrotation ist ein Schema, mit dem verhindert werden soll, dass Inhalte, die lange Zeit wiedergegeben werden, in Lizenzen gehackt werden.

In einem M3U8-Manifest gilt jedes Schlüssel-Tag bis zum nächsten Schlüssel-Tag oder bis zum Ende der Datei für die folgenden TS-Segmente.

Gehen Sie wie folgt vor, um die Lizenzrotation hinzuzufügen:

* Fügen Sie während der Lizenzdrehung ein neues FairPlay-Key-Tag ein.

   Es können beliebig viele wichtige Tags hinzugefügt werden.

   Achten Sie bei linearen Inhalten darauf, das neueste Schlüssel-Tag im Fenster M3U8 beizubehalten. iOS fordert die nächste M3U8 an, wenn zwei TS-Segmente noch abgespielt werden müssen (etwa 20 Sekunden). Wenn das neue M3U8 neue Schlüssel-Tags enthält, werden alle wichtigen Anforderungen sofort ausgeführt. Die vorherigen vorhandenen Schlüssel werden nicht erneut angefordert. iOS wartet, bis alle wichtigen Anforderungen abgeschlossen sind, bevor die Wiedergabe Beginn wird.

   Bei VOD-Inhalten mit Lizenzrotation erfolgen alle wichtigen Anforderungen am Anfang der Wiedergabe.

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
