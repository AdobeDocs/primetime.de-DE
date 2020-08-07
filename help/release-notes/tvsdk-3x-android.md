---
title: TVSDK 3.12 for Android Release Notes
seo-title: TVSDK 3.12 for Android Release Notes
description: TVSDK 3.12 for Android Release Notes describe what is new or changed, the resolved and known issues and the device issues in TVSDK Android 3.12
seo-description: TVSDK 3.12 for Android Release Notes describe what is new or changed, the resolved and known issues and the device issues in TVSDK Android 3.12
uuid: 685d46f5-5a02-4741-af5c-91e91babd6f7
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: 3a27379f-3cef-4ea3-bcae-21382dc1e9fd
translation-type: tm+mt
source-git-commit: e467153067bb10107054a5d4166b1d9c2ac646ab
workflow-type: tm+mt
source-wordcount: '5418'
ht-degree: 0%

---


# TVSDK 3.12 for Android Release Notes {#tvsdk-for-android-release-notes}

TVSDK 3.12 for Android Release Notes describe what is new or changed, the resolved and known issues and the device issues in TVSDK Android 3.12.

Der Android-Referenzplayer ist im Verzeichnis samples/ Ihrer Distribution im Lieferumfang von Android TVSDK enthalten. In der zugehörigen Datei README.md wird beschrieben, wie Sie den Referenz-Player erstellen.

>[!NOTE]
>
>Um den Referenz-Player erfolgreich zu erstellen, wie in README.md beschrieben, das mit der Version verteilt wird, führen Sie folgende Schritte durch:
>
>1. VideoHeartbeat.jar von [https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) herunterladen (VideoHeartbeat-Bibliothek für Android v2.0.0)
>1. Extrahieren Sie VideoHeartbeat.jar in den Ordner libs/.


TVSDK für Android bietet viele Leistungsverbesserungen im Vergleich zu früheren Versionen. Es bietet ein hochwertiges Anzeigeerlebnis und umfasst alle Funktionen von Version 1.4, mit Ausnahme von Multi-CDN-Unterstützung.

Die umfassenden Funktionen, die unterstützt und nicht unterstützt werden, finden Sie im Abschnitt [Funktionsmatrix](#feature-matrix) der Versionshinweise.

## Android TVSDK 3.12

Die Gradle Version der Primetime Reference-Anwendung wird jetzt auf Version 5.6.4 aktualisiert.

Um die Referenz-App mit Android Studio einzurichten und auszuführen, befolgen Sie die Anweisungen in der ReadMe-Datei, die mit TVSDK zip verfügbar ist unter `TVSDK_Android_x.x.x.x/samples/PrimetimeReference/src/README.md`.

Die wichtigsten in der aktuellen Version behobenen Kundenprobleme werden im Abschnitt [gelöste Probleme](#resolved-issues) beschrieben.

### Neue Funktionen und Verbesserungen in früheren Versionen

**Android TVSDK 3.11**

* **Protection System specific Header (PSSH) Box Abrufen zulässig** - TVSDK ermöglicht das Abrufen des Schutzsystem-spezifischen Header Box, das mit der aktuell geladenen Medienressource verknüpft ist. Neue API `getPSSH()` hinzugefügt `com.adobe.mediacore.drm.DRMManager`.

Weitere Informationen finden Sie unter [Widevine DRM](../programming/tvsdk-3x-android-prog/android-3x-content-security/android-3x-drm-widevine.md).

**Android TVSDK 3.10**

Die Veröffentlichung konzentrierte sich auf die Behebung der wichtigsten Kundenprobleme, wie im Abschnitt [gelöste Probleme](#resolved-issues) beschrieben.

**Android TVSDK 3.9**

* **Secure Versand over HTTPS** - Android TVSDK 3.9 bietet die Funktion zum sicheren Versand über HTTPS, um Inhalte mit beispielloser Skalierbarkeit und Performance sicher bereitzustellen.

   Um sicheren Versand über HTTPS zu aktivieren, wurde in der `NetworkConfiguration` Klasse eine neue API eingeführt.

   `public void setForceHTTPS (boolean value)`

   `public boolean getIsForceHTTPS()`

**Android TVSDK 3.8**

* **Pre-Roll-Unterstützung mit Teil-Werbeunterbrechung** - Mit dieser Verbesserung unterstützt TVSDK 3.8 Pre-Roll-Anzeigen mit Teil-Ad-Break-Funktion (PABI).

Die Pre-Roll-Anzeige wird, sofern verfügbar, abgespielt und dann vom Live-Point aus wiedergegeben, der dem Erlebnis des Live-Fernsehens nachbildet.

**Android TVSDK 3.7**

* Bei Widevine-Testinhalten wird eine neue API `setMediaDrmCallback` in der DRMManager-Klasse bereitgestellt, um die Standardimplementierung der MediaDRMCallback-Schnittstelle zu überschreiben.

   `public static void setMediaDrmCallback(MediaDrmCallback callback)`

* Der AppCrash-Fehler wurde behoben, der dafür gesorgt hatte, dass `MediaPlayerEvent.ITEM_UPDATED` die C++-Ebene (64 Bit Android) nicht verarbeitet wurde.

**Android TVSDK 3.6**

* **Verbessern Sie Ihre Apps für die 64-Bit-Anforderung** - Die native Bibliothek `(libAVEAndroid.so)` wird jetzt aktualisiert und in zwei Versionen zur Verfügung gestellt. Der Speicherort der vorhandenen nativen Armeabi-Bibliothek (32 Bit) wurde geändert `/framework/Player to /framework/Player/armeabi` und eine zusätzliche arm64-v8a-Bibliothek (64 Bit) wurde in `/framework/Player/arm64-v8a.`

**Version 3.5**

* **Just In Time Ad Resolution** - TVSDK 3.5 entfernt die Unterstützung der abgespielten Anzeigen aus der Zeitschiene.

* **Unterstützung für die Offline-Wiedergabe** aktiviert - Bei der Offline-Wiedergabe können Benutzer Videoinhalte jetzt auf ihre Geräte herunterladen und anzeigen, wenn keine Verbindung besteht. For detailed information, refer to &quot;[Offline Playback with Android](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_3.5.pdf).&quot;

**Version 3.4**

* TVSDK now supports CMAF streams playback for CBC encrypted and plain streams.

**Version 3.3**

* **API changes**

   * A new API is added to `NetworkConfiguration::setNumOfTimesManifestRetryBeforeError(n)*` to handle network errors and timeouts.
      * where (n) is the number of retries.

**Version 3.2**

* **Parallel Ad Resolution and Manifest download support**

   * TVSDK 3.2 supports the simultaneous resolution, instead of the sequential resolution for all the Ad requests and Ad breaks except for VMAP.

   * All the ad manifests in an ad break are downloaded simultaneously.

* **Unterstützung für Anzeigenauflösung und Manifestdownload-Timeout aktiviert.**

   * Users can now set the timeout value for overall ad resolution and manifest downloads.  In the case of VMAP, the timeout value applies for individual ad breaks as all the ad breaks are resolved sequentially.

* **Introduced new APIs in AdvertisingMetadata Class:**

   * `void setAdResolutionTimeout(int adResolutionTimeout)`

   * `int getAdResolutionTimeout()`

   * `void setAdManifestTimeout(int adManifestTimeout)`

   * `int getAdManifestTimeout()`

* **Removed below APIs from AdvertisingMetadata Class:**

   * `void setAdRequestTimeout(int adRequestTimeout)`

   * `int getAdRequestTimeout()`

* **Wiedergabe von Streams mit AC3/EAC3-Audio-Codec aktiviert**

   * `void alwaysUseAC3OnSupportedDevices(boolean val)` in `MediaPlayer` Klasse

* **TVSDK unterstützt die Wiedergabe von CMAF- und Nur-Streams für verschlüsselte Widevine CTR.**

* **Die Wiedergabe von 4K HEVC-Streams wird jetzt unterstützt.**

* **Parallele Anzeigenaufrufanforderungen** - TVSDK ruft jetzt parallel 20 Anzeigenaufrufanforderungen ab.

**Version 3.0**

* **TVSDK 3.0 unterstützt HEVC-Streams (High Efficiency Video Coding).**

* **Just in Time - Durch das Beheben von Anzeigen, die näher an Anzeigenmarken** liegen, wird jetzt jede Werbeunterbrechung unabhängig voneinander gelöst. Zuvor war die Anzeigenauflösung ein zweistufiger Ansatz: Pre-Roll-Aufnahmen wurden vor dem Beginn der Wiedergabe aufgelöst und alle Mid-/Post-Roll-Slots nach dem Start der Wiedergabe kombiniert. Mit dieser erweiterten Funktion wird jeder Werbeunterbrechung nun zu einem bestimmten Zeitpunkt vor dem Anzeigen-Cue-Point aufgelöst.

>[!NOTE]
>
>Die verzögerte Anzeigenauflösung wurde jetzt standardmäßig deaktiviert und muss explizit aktiviert werden.

Eine neue API wird hinzugefügt, `AdvertisingMetadata::setDelayAdLoadingTolerance` um die Toleranz für verzögertes Laden der Anzeige im Zusammenhang mit diesen Advertising Metadata abzurufen.\
Die Suche ist jetzt unmittelbar nach der Vorbereitung zulässig, wenn Sie nach Werbeunterbrechungen suchen, wird eine sofortige Auflösung vor Abschluss der Suche erzielt.\
Signalisierungsmodi `SERVER_MAP` und - `MANIFEST_CUES` funktionen werden unterstützt.

Weitere Informationen finden Sie unter [TVSDK 3.0 für Android-Programmierhandbuch](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/c-lazy-ad-resolving/c-lazy-ad-resolving.md) zu API- und Ereignis-Änderungen.

* **Auf`targetSdkVersion`neueste Version aktualisiert**

Aktualisierung `targetSdkVersion` von 19 auf 27 für reibungslose Funktionsweise.

* **Placement.Type getPlacementType() ist jetzt eine Methode auf der Schnittstelle TimelineMarker**

   Diese Methode gibt einen Platzierungstyp von Placement.Type.PRE_ROLL, Placement.Type.MID_ROLL oder Placement.Type.POST_ROLL zurück. Wenn eine Werbeunterbrechung ungelöst ist, gibt die getDuration()-Methode auf der TimelineMarker-Schnittstelle 0 zurück.

**Version 2.5.6.**

* **TVSDK 2.5 unterstützt Android P.**

* **Hintergrundaudio aktivieren**

   Um die Audiowiedergabe zu aktivieren, wenn die App von vorne in den Hintergrund wechselt, sollte die App die MediaPlayer- `enableAudioPlaybackInBackground` API mit true als Argument aufrufen, wenn sich der Player im VORBEREITTEN Status befindet.

* **alwaysUseAudioOutputLatency(boolean val) in der MediaPlayer-Klasse**

Verwenden Sie bei Festlegung die Ausgabedatenz in der Berechnung des Audio-Zeitstempels.
Boolesche Parameter val - True verwendet die Latenz der Audioausgabe bei der Berechnung des Audiozeitstempels.

* **Optimiert, um die beste Wiedergabe zu erzielen, selbst wenn die Bandbreite plötzlich abfällt**

TVSDK bricht jetzt bei Bedarf den Download des aktuellen Segments ab und wechselt dynamisch zur entsprechenden Darstellung. Dies geschieht durch einen nahtlosen Wechsel zwischen den Bitraten ohne Unterbrechungen.

**Version 2.5.5**

* **Einfügen einer partiellen Werbeunterbrechung**

   TV-like experience of joining in the middle of an ad without firing the tracking for the partially watched ad.\
   Example: User joins in the middle (at 40 seconds) of a 90-second ad break consisting of three 30-second ads. This is 10 seconds into the second ad in the break.

   * The second ad plays for the remaining duration (20 sec) followed by the third ad.

   * Ad trackers for the partial ad played (second ad) are not fired. The trackers for only the third ad are fired.

* **Secure Ad Loading over HTTPS**

   Adobe Primetime provides an option to request first call to primetime ad server and CRS over https.

* **AdSystem and Creative Id added to CRS requests**

   Now including `AdSystem` and `CreativeId` as new parameters in the 1401 and 1403 requests.

* **API setEncodeUrlForTracking in NetworkConfiguration class removed** as the unsafe characters in a URL should be encoded.

**Version 2.5.4**

Android TVSDK v2.5.4 offers the following updates and API changes:

* Changes in default value for `WebViewDebbuging`

   `WebViewDebbuging` value is set to `Fals`e by default. Rufen Sie dazu `setWebContentsDebuggingEnabled(true)` in der Anwendung auf.

* **Aktualisierung der OpenSSL- und Curl-Version**

   Aktualisierung von libcurl auf v7.57.0 und OpenSSL auf v1.0.2k.

* Zugriff auf App-Ebene für VAST-Antwortobjekt

   Es wurde eine neue API eingeführt, `NetworkAdInfo::getVastXml()` die den Zugriff auf das VAST-Antwortobjekt auf die Anwendung ermöglicht.

**Version 2.5.3**

Android TVSDK v2.5.3 Angebot die folgenden Updates und API-Änderungen.

* Alle TVSDK-Kunden, die CRS verwenden, sollten ihre Apps mit TVSDK 2.5.3.85 oder höher auf Android aktualisieren. Dies ist eine Ablage, die die vorhandene App-Implementierung ersetzt. Überprüfen Sie nach dem TVSDK-Upgrade die kreativen URL-Anforderungen von CRS in einem Proxy-Tool (z. B.: Charles) und bestätigen Sie, dass der Hostname und die Version im Pfad sich wie in der Beispiel-URL-Struktur unten widerspiegeln.

   `https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784 bf3586d.m3u8`

* Benutzeragent von TVSDK anpassbar: haben wir einige neue APIs hinzugefügt, um die Benutzeragenten anzupassen.

   * `setCustomUserAgent(String value)`
   * `getCustomUserAgent()`

* Freigeben von Cookies zwischen Android-Anwendung und TVSDK: Android TVSDK unterstützt jetzt den Zugriff auf Cookies zwischen der JAVA-Ebene (gespeichert im CookieStore der Android-Anwendung) und der C++ TVSDK-Ebene. Jetzt ist es möglich, Cookies in der nativen C++-Ebene einzustellen und/oder zu ändern, da sie dem Java Cookie Store ausgesetzt werden.

* API-Änderungen:

   * Ein neues Ereignis `CookiesUpdatedEvent` wird hinzugefügt. Er wird vom Medienplayer ausgelöst, wenn sein Cookie aktualisiert wird.

   * Es wird eine neue API hinzugefügt, `NetworkConfiguration::set/ getCustomUserAgent()` um benutzerdefinierte Benutzeragenten zu verwenden.

   * A new API is added to `NetworkConfiguration::set/ getEncodedUrlForTracking` to force Encoding of Unsafe characters.

   * A new API is added to `NetworkConfiguration::getNetworkDownVerificationUrl()` to set a network verification URL in case of a failover.

   * A new property is added to `TextFormat::treatSpaceAsAlphaNum` which define whether to treat space as alphanumeric while displaying captions.

* Changes in `SizeAvailableEvent`. Previously, `getHeight()` and `getWidth()` methods of `SizeAvailableEvent` in 2.5.2 used to return Frame height and frame width, which was returned by media format. Now it returns output height and output width respectively returned by decoder.

* Changes in Buffering behavior: Buffering behavior is changed. Its left up to App developer on what they want to do in case of buffer empty. 2.5.3 uses play buffer size at buffer empty situation.

**Version 2.5.2**

Android TVSDK v2.5.2 offers important bug fixes and a few API changes.

**Version 2.5.1**

The important new features released in Android 2.5.1.

* **Performance Improvements -** The new TVSDK 2.5.1 architecture brings a number of performance improvements. Based on statistics from a third party benchmarking study, the new architecture provides a 5x reduction in startup time and 3.8x fewer dropped frames compared to the industry average:

* **Instant on for VOD and live -** When you enable instant on, the TVSDK initializes and buffers media before playback starts. Because you can launch multiple MediaPlayerItemLoader instances simultaneously in the background, you can buffer multiple streams. When a user changes the channel, and the stream has buffered properly, playback on the new channel starts immediately. TVSDK 2.5.1 unterstützt auch Instant On für **Live** Streams. Die Live-Streams werden erneut gepuffert, wenn das Live-Fenster verschoben wird.

* **Improved ABR logic -** The new ABR logic is based on buffer length, rate of change of buffer length, and measured bandwidth. Dadurch wird sichergestellt, dass die ABR die richtige Bitrate wählt, wenn die Bandbreite schwankt, und auch die Anzahl der auftretenden Bitratenwechsel optimiert wird, indem die Rate überwacht wird, mit der sich die Pufferlänge ändert.

* **Partial Segment Download / Sub-segmentation -** TVSDK further reduces the size of each fragment, in order to start playback as soon as possible. Das zugehörige Fragment muss alle zwei Sekunden über einen Schlüsselrahmen verfügen.

* **Lazy ad resolution -** TVSDK doesn&#39;t wait for resolution of non-preroll ads before starting playback, thus decreasing the startup time. APIs like seek and trick-play are still not allowed until all ads are resolved. This is applicable to VOD streams used with CSAI. Operations like seek and fast forward are not permitted till the ad resolution is completed. For live streams this feature cannot be enabled for ad resolution during a live event.

* **Persistent network connections -** This feature allows TVSDK to create and store an internal list of persistent network connections. These connections are reused for multiple requests, rather than opening a new connection for each network request and then destroying it afterwards. This increases efficiency and decreases latency in the networking code resulting in faster playback performance.
When TVSDK opens a connection it asks the server for a *keep-alive* connection. Some servers may not support this type of connection, in which case TVSDK will fall back to making a connection for each request again. Also, while persistent connections will be on by default, TVSDK now has a configuration option so that apps can turn persistent connections off if desired.

* **Parallel download -** Downloading video and audio in parallel rather than in series reduces startup delays. Diese Funktion ermöglicht die Wiedergabe von HLS Live- und VOD-Dateien, optimiert die verfügbare Bandbreitennutzung von einem Server, verringert die Wahrscheinlichkeit, in Puffersituationen zu gelangen, und minimiert die Verzögerung zwischen Download und Wiedergabe.

* **Parallel ad downloads -** TVSDK prefetches ads in parallel to the content playback before hitting the ad breaks thus enabling seamless playback of ads and content.

* **Playback**

* **MP4 Content Playback -** MP4 short clips do not need to be re-transcoded to play back within TVSDK.

   >[!NOTE]
   >
   >ABR switching, trick play, ad insertion, late audio binding, and sub-segmentation are not supported for MP4 playback.

* **Trick play with adaptive bit rate (ABR) -** This feature allows TVSDK to switch between iFrame streams while in trick play mode. You can use non-iFrame profiles to do trick play at lower speeds.

* **Glättere Trick-Wiedergabe -** Diese Verbesserungen verbessern die Benutzerfreundlichkeit:

   * Adaptive bit-rate and frame rate selection during trick play, based on bandwidth and buffer profile

   * Use of the main stream instead of the IDR stream to get up to 30 fps fast playback.

* **Content Protection**

   * **Resolution-based output protection -** This feature ties playback restrictions to specific resolutions, providing finer grained DRM controls.

* **Workflow Support**

   * **Direct Billing Integration -** This sends billing metrics to the Adobe Analytics backend, which is certified by Adobe Primetime for streams used by the customer.

   TVSDK automatically collects metrics, abiding by the customer sales contract to generate periodic usage reports required for billing purposes. On every stream start event, TVSDK uses the Adobe Analytics data insertion API to send billing metrics such as content type, ad insertion enabled flags, and drm enabled flags - based on the duration of the billable stream - to the Adobe Analytics Primetime owned report suite. This does not interfere with or get included in the customer&#39;s own Adobe Analytics report suites or server calls. On request, this billing usage report is sent to customers periodically. This is the first phase of the billing feature supporting usage billing only. It can be configured based on the sales contract using the APIs described in the documentation. This feature is enabled by default. To turn this feature off, refer to the reference player sample.

   * **Improved Failover Support -** Additional strategies implemented to continue uninterrupted playback, despite failures of host servers, playlist files, and segments.


* **Advertising**

   * **Moat Integration -** Support for ad viewability measurement from Moat.

   * **Companion banners -** Companion banners are displayed alongside a linear ad and often continue to be displayed on the view after the ad ends. These banners can be of type html (an HTML snippet) or type iframe (a URL to an iframe page).

* **Analytics**

   * **VHL 2.0 -** This is the latest optimized Video Heartbeats Library (VHL) integration for automatic collection of usage data for Adobe Analytics. The complexity of the APIs has been decreased to to ease the implementation. Download the VHL library [v2.0.0 for Android](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) and extract the JAR file in the libs folder.

* **SizeAvaliableEventListener**

   * `getHeight()` and `getWidth()` methods of `SizeAvailableEvent` will now return output in height and width respectively. Display aspect ratio can be calculated as follows:

      ```java
      SizeAvailableEvent e;
      DAR = e.getWidth()/ e.getHeight();
      ```

      Storage Aspect Ratio in terms of Sar width and Sar height can also be used to calculate Frame width and Frame height:

      ```java
      SAR = e.getSarWidth()/e.getSarHeight();
      frameHeight = e.getHeight();
      frameWidth = e.getWidth()/SAR;
      ```

* **Cookies**

   * Android TVSDK now supports access to JAVA cookies stored in CookieStore of the Android Application. A Callback API (onCookiesUpdated) is provided to record whenever a new Cookie comes as part of **Set-Cookie** Response header. These cookies are available as a List of HttpCookie(s) used for a different URI/domain by setting these cookie values on that particular URI/domain using CookieStore. Similarly the cookie values in TVSDK are updated using CookieStore add API.

## Feature matrix {#feature-matrix}

TVSDK for Android supports a number of features that you can implement to add functionality to your video applications.

In the feature tables below, a &#39;Y&#39; indicates that the feature is supported in the current release.

| Feature | Content type | HLS |
|---|---|---|
| General playback (Play, Pause, Seek) | VOD + Live | Y |
| FER - General playback (Play, Pause, Seek) | FER VOD | Y |
| Seek when an ad is playing | VOD + Live | Not supported |
| HEVC Playback | VOD + Live | Nur fMP4-Container |
| AC3 and EAC3 | VOD + Live | Nicht unterstützt |
| MP3 | VOD | Not supported |
| MP4 Content Playback | VOD | Y |
| Adaptive Bit Rate Switching Logic | VOD + Live | Y |
| Audio Only Playback | VOD + Live | Y |
| Multi CDN Support | VOD + Live | Not supported |
| Playback of ads with audio-only media | VOD + Live | Not supported |
| Closed Captions - 608/708 | VOD + Live | Y |
| Closed Captions - WebVTT | VOD + Live | Y |
| Manifest Failover | VOD + Live | Y |
| Advanced Failover | VOD + Live | Y |
| QoS and player notifications | VOD + Live | Y |
| Support for cookie headers | VOD + Live | Y |
| Support for custom HTTP headers | VOD + Live | Y (allow listing required) |
| Set buffer control parameters | VOD + Live | Y |
| Set adaptive bit-rate controls | VOD + Live | Y |
| Custom Manifest Tags | VOD + Live | Y |
| Late Audio Binding | VOD + Live | Y |
| 302 Redirect | VOD + Live | Y |
| Playback with Offset | VOD + Live | Y |
| Trick Play | VOD + Live | Y |
| Langsame Bewegung bei Trick Play | VOD + Live | Not supported |
| Smooth Trick Play (with ABR) | VOD + Live | Y |
| ID3 Parsing | VOD + Live | Y |
| Werbeunterbrechung | VOD + Live | Not supported |
| Instant On | VOD + Live | Nicht unterstützt |
| Discontinuity marker support | VOD + Live | Y |
| 302 Redirect Stickiness | VOD + Live | Y |

| Feature | Content type | HLS |
|---|---|---|
| General playback, ads enabled | VOD + Live | Y |
| FER content with ads enabled | VOD | Y |
| Default Ad Behaviors | VOD + Live | Y |
| VAST 2.0/3.0 | VOD + Live | Y |
| VMAP 1.0 | VOD + Live | Y |
| MP4 Ads | VOD + Live | Y (from CRS) |
| Trick Play with Ads Enabled | VOD + Live | Y |
| Ad only | VOD | Y |
| Targeting Parameters | VOD + Live | Y |
| Custom Parameters | VOD + Live | Y |
| Custom Ad Behaviors | VOD + Live | Y |
| Custom Ad Tags | Live | Y |
| Custom Ad Resolvers | VOD + Live | Y |
| Freewheel Custom Ad Resolver | VOD | Y |
| C3 | VOD + Live | Not supported |
| Lazy Ad Resolve | VOD | Y |
| Discontinuity marker support - SSAI | VOD + Live | Y |
| Companion Ads, Banner Ads, and Clickable Ads | VOD + Live | Y |
| VPAID 2.0 | VOD + Live | Y (JS) |
| Vorzeitiger Anzeigenausstieg | Live | Y |
| Rules-based Creative Prioritization | VOD + Live | Y |
| CRS Rules | VOD + Live | Y |
| JSON Ad Resolver | VOD + Live | Not supported |
| Moat Integration | VOD + Live | Y |
| Partial Ad Break Insertion | Live | Y |

| Feature | Content type | HLS |
|---|---|---|
| AES Encryption | VOD + Live | Y |
| Sample AES Encryption | VOD + Live | Y |
| Tokenisierte Streams | VOD + Live | Y |
| Widevine DRM | VOD + Live | fMP4 container only |
| Primetime DRM | VOD + Live | Y |
| External Playback (RBOP) | VOD + Live | Primetime DRM only |
| Lizenzdrehung | VOD + Live | Nur Primetime-DRM |
| Schlüsseldrehung | VOD + Live | Nur Primetime-DRM |

| Funktion | Inhaltstyp | HLS |
|---|---|---|
| Adobe Analytics VHL-Integration | VOD + Live | Y |
| Rechnungsstellung | VOD + Live | Y |

## Resolved issues {#resolved-issues}

Where resolution is associated with a reported issue, a Zendesk reference is displayed, for example ZD#xxxxx.

**Android TVSDK 3.12**

This section provides a summary of the issue resolved in TVSDK 3.12 Android release.

* ZD#40584 - Primetime Reference app does not build with latest gradle version.

### Resolved issues in the previous releases

**Android TVSDK 3.11**

* ZD#41252 - Korean characters in WebVTT broken after Android 7.1.

**Android TVSDK 3.10**

* ZD#40340 - Application crashes with &quot;App Not Responding&quot; error on attempting playback after block listing all the TS (TypeScript) files.

**Android TVSDK 3.8**

* No new issues added.

**Android TVSDK 3.7**

* No new issues added.

**Android TVSDK 3.6**

* No new issues added.

**Version 3.5**

* ZD#37503 - JSON responses for the CRS rules are cached to avoid the duplicate requests.

**Version 3.4**

* ZD#37996 - Fixed an issue about choppy playback issue for linear and VOD CMAF HEVC streams.
* ZD#37706 - Fixed an issue about garbled captions.
* ZD#37622 - Fixed an issue about fatal URISyntaxErrors for  specific ads.
* ZD#36938 - Fixed an issue about bitrate switching down to the middle bitrate and then picking up to the highest bitrate after exiting out of trick plays.

**Version 3.3**

* ZD#37394 - CMAF asset fast forward causes artifacts after the speed changes.
   * Fixed an issue which occurs with a profile change during trick play.
* ZD#37396 - Ad tracking events are missing for some mid-rolls and post-rolls.
   * Fixed a specific case around ad tracking events.
* ZD#37491 - HTTP status code with error meta is not present.
   * Worked on propagating network errors higher in the stack.
* ZD#37808 - Allow list New Custom Header.
   * SSAI_TAG-Unterstützung als Teil dieser Korrektur hinzugefügt.
* ZD#37622 - URISyntax-Fehler von bestimmten Anzeigen-Pods.
   * Es wurde ein Problem mit dem Absturz der Stream-Wiedergabe behoben, der auftrat, wenn eine benutzerdefinierte Android-App mit einer nicht kodierten % bereitgestellt wurde
* ZD#37631 - Master manifest retry mechanism for Android TVSDK.
   * Added new API in the network configuration for handling this enhancement. If this API is not used, then manifest is not retried. Wenn es verwendet wird, wird manifest erneut versucht, um Netzwerkfehler und Timeouts zu verarbeiten.

**Version 3.2**

* ZD#37493- Tracking-Beacons für die Live-Wiedergabe werden nicht zeitweise für die erste Anzeige in der Sequenz ausgelöst.
* ZD#36985- Tracking beacons are not sent for empty ad breaks in VMAP response.
* ZD#37134 - TVSDK gibt gelegentlich die falsche ID für die VMAP-Antwort aus.

**Version 3.0**

* ZD#33740 - TVSDK gibt unmittelbar nach dem Erstellen eines MediaPlayer-Objekts und dem Aufrufen von replaceCurrentResource() eine nicht benötigte Warnung aus

   * Improved the earlier fix by calling restore only when player is in suspended state

* ZD#36442 - Every new playback disconnects remote debugging session making it impossible to debug.

   * Debug not possible by default on web view as debugging is not enabled by default. App should enable debugging if required by calling setWebContentsDebuggingEnabled(true) on object returned from MediaPlayer.getCustomAdView().

* ZD#33688 - Support for Just In Time ad resolving

   * Ad breaks are resolved at a specified interval prior to the position of the ad break.

* ZD#36441 - Duration of live window keeps increasing beyond 5 minutes causing multiple issues.

   * Fixed an issue where virtualStartTime was getting added twice while calculating virtual live point resulting in this issue.

**Android TVSDK 2.5.6**

* ZD #34992 - Language is empty in Closed Caption.

   * Fixed a case where TVSDK was not parsing #EXT-X-MEDIA:TYPE=CLOSED-CAPTIONS from main manifest to get the caption track details.

* ZD #35078 - Android P validation.

   * TVSDK 2..5.6 has been validated with latest Android P beta build(s). No issues found due to the new Android OS.

* ZD #34149 - Player continues to requests manifests even if error is encountered.

   * Fixed the case where TVSDK was making repetitive calls even when all the profiles were down (404 error).

* ZD #31533 - Playing audio on Android after the app is sent to background.

   * Added `enableAudioPlaybackInBackground` API of MediaPlayer which should be called with &#39;True&#39; as argument (when player is in PREPARED state) to enable playback of audio when app is in background.

**Android TVSDK 2.5.5**

* ZD #21647 - Android TVSDK notifies 640x368 when actual video size is 640x360.

   * Due to variable m_nOutputHeight (inside AndroidMCVideoDecoder) getting updated with frame height instead of actual output height. Made relevant changes in function getVideoFrame to calculate m_nOutputHeight correctly.

* ZD #26614 - Urgent --- 3rd party ad serving / programmatic --- failure to serve impressions.

   * Enhanced the earlier fix by handling the case in XML parsing where issue was reproducible when &quot;space&quot; is before the &quot;equal&quot; sign like &lt;VAST version =&quot;2.0&quot;>

* ZD #29296 - Android: Add AdSystem and Creative id to CRS requests.

   * Now including &#39;AdSystem&#39; and &#39;CreativeId&#39; as new parameters in the 1401 and 1403 requests.

* ZD #33062 - TVSDK crashes on the occurrence of pipe character in VAST response under CDATA node

   * API setEncodeUrlForTracking in NetworkConfiguration class removed as the unsafe characters in a URL to be encoded

* ZD #33063 - CRS file selection logic was broken - TVSDK was not sending CRS request for webm format but sending it for 3gpp files instead.

   * Fixed the logic now. On using media files with webm and 3gpp format, CRS request to be sent for webm. Bei Verwendung beider Mediendateien im 3gpp-Format muss die CRS-Anforderung für die höchste Bitrate-3-gpp-Datei gesendet werden.

* ZD #33125 - Android app crashes with specific DoubleClick tag within the VMAP.

   * Fixed the scenario to avoid the crash.

* ZD #32256 - License Rotation &amp; Key Rotation Issue - Adobe Access

   * Fixed the segments initialization with the DRM metadata for SampleAES content. Works fine with AES128 content.

* ZD #33619 - Fast-forwarding a growing playlist content stuck in buffering state near live point.

   * Handled the case when crossing the live point in trick play mode

* ZD #34151 - TimedMetadata objects out of order.

   * Two TimedMetadata events were appearing in random order if they belonged to same time in the timeline. Maintained their original order in manifest.

* ZD #34189 - Issue when seeking to beginning of ad break.

   * The issue was with SSAI ads which are stitched using discontinuity. And the cause was a behavior when we seek to the begining of such ads, we search for a keyframe and we don&#39;t find it. The reason was the ad&#39;s min audio timestamp being before min video timestamp. Hence, we end up searching for a key frame at a wrong fragmentDump data. Fixed now.

* ZD #34528 - Video resolution not upgrading beyond 640x360 on FireTV 3rd gen dongle.

   * Enhanced the fix to include latest firmware updates

* ZD #34793 - TVSDK 2.5.x used to crash with custom content resolver in some cases when VideoEngine was assuming that the auditudeSettings are available and they were not.

   * The crash was happening due to a function call on a Null shared pointer (auditudeSettings). Added a conditional check within VideoEngineTimeline::placeToSourceTimeline() to make sure auditudeSettings are available before calling anything on that object.

* ZD #32584 - Not able to access complete information present in the &lt;Extensions> node of a VAST response.

   * Fixed the issue around XML parsing and now NetworkAdInfo provides the complete information present in the &lt;Extensions> node

* ZD #35086 - Not getting complete extension data from player in case of specific VMAP responses.

   * Das Problem war spezifisch für die Erweiterung XML, da die XML-Analyse nicht funktionierte, wenn die Erweiterung XML Dubletten-Anführungszeichen im Attributwert enthielt. Fixed the issue.

**Android TVSDK 2.5.4**

* ZenDesk#33659 - Wiedergabesitzung zur Aktivierung des Remotedebuggens von Webansicht.

WebViewDebbuging is set to False by default. Um das Debugging zu aktivieren, legen Sie mithilfe von setWebContentsDebuggingEnabled(true) als true über die Anwendung fest.

* ZenDesk#33011 - Ad timeline is not resolved in case of a failed CRS request.

   When a CRS request to an ad fails, the timeline gets resolved and the remaining ads are played.

* ZenDesk#34528 - Video resolution does not upgrade beyond 640x360 on FireTV third-generation dongle.

   Video resolution switches up as bit rate switches.

* ZenDesk#33192 - AudioTrack has null name when track is retrieved via AudioUpdatedEventListener::onAudioUpdated.

   In a few scenarios on FireTV Stick, onAudioUpdate event was getting fired when there was no actual audio update. This is fixed now.

**Android TVSDK 2.5.3**

* Zendesk#32216 - TimedMetadata custom tag subscription is not working.

   We are returning ID3 data as a byte array(to support APIC or generic data) to client whereas in 1.4 return string. Byte array does not handle null terminated character itself, therefore, it was showing special character to the client. This issue is fixed now.
* Zendesk#32670 - Player Not Failing Over to Redundant Playlist

   Dies funktioniert jetzt einwandfrei und setNetworkDownVerificationUrl funktioniert erwartungsgemäß.
* Zendesk#32369 - Closed caption shows different color garbage or artifact.

   Issue with CC glitches has been fixed in latest build
* Zendesk#25590 - Enhance: TVSDK cookie store ( C++ to JAVA )

   Android TVSDK now supports accessing of cookies between JAVA layer (stored in CookieStore of the Android Application) and the C++ TVSDK layer.
* Zendesk#32252 - TVSDK_Android_2.5.2.12 does not seem to have the fix for PTPLAY-20269

   This issue has been fixed and integerated to 2.5.2 branch.
* Zendesk#31806 - Auditude sticks in PREPARING

   Player was stuck in Preparing state because response xml had a empty tag. Now issue is fixed.
* Zendesk#31727 - TVSDK 2.5 closed caption characters are dropped or misspelled.

   Issue is fixed and we are not dropping/misspelling any character.
* Zendesk#31485 - DrmManager in 2.5

   There was some issue in Creating DrmManager via new DrmManager(Context context). Implemented DRMService class which would provide DRMManager.
* Zendesk#32794- 1080P resolution stream not playing on Android

   we have changed SizeAvailableEvent and Previously, getHeight() and getWidth() methods of SizeAvailableEvent in 2.5 used to return Frame height and frame width, which was returned by media format. It now returns output height and output width respectively returned by decoder.
* Zendesk #19359 Flash Player crashes due to the position of #EXT-X-FAXS-CM attribute in set-level manifest.

   The #EXT-X-FAXS-CM tag must always appear at the top playlist before individual bitrate or segments appear in playlist.

**Android TVSDK 2.5.2**

* Zendesk#17305 Artifacts in closed captions with non-opaque background.

   setTreatSpaceAsAlphaNum property in TextFormat is exposed. By default, the property is False. Set the property as True in a client to resolve the dark space issue.

* Zendesk#25097 CC display has visual artifacts with CC settings.

   setTreatSpaceAsAlphaNum property in TextFormat is exposed. By default, the property is False. Set the property as True in a client to resolve the dark space issue.

* Zendesk #31620 User agent string going out of TVSDK player is truncated.

   The User agent string will no more be truncated after 128 characters.

   Adobe Primetime version string is added to the system user agent.

* Zendesk #30809 Fehlendes SEEK_END-Ereignis verhindert, dass die App zu einem Wiedergabestatus wechselt.
* Zendesk #30415 Closed Caption&#39;s &#39;Cyan&#39; color is now a darker hue of blue (turquoise), compared to the previous Primetime TVSDK releases.

   The color is changed from DarkCyan to Cyan.

* Zendesk #30727 VOD ads are not being downloaded/resolved.

   In VMAP XML if there is an empty VAST tag without an explicit closing tag (‘&lt;/VAST>&#39;) and without a newline character after it, then the VMAP XML is not parsed properly and ads may not play.

**Android TVSDK 2.5.1**

* Device-specific (Samsung Galaxy Tab 4) crash; VOD DRM LBA with Auditude and click on ads.
* VHL - Incorrect heartbeat calls are sent when starting content from an offset.
* When VPAID ads are played, the VHL heartbeat calls for event:type:play ad are missing.
* After going into COMPLETE status, the player goes back to the PLAYING status with SKIP adBreakPolicy for post-roll ads.
* Cookies are not being attached to outgoing ad callbacks.
* Ads cue points are not visible.
* HLS with separate EAC3 SAP track won&#39;t load.
* Player crashes as TVSDK receives a Screen On intent after the Media Player is restored.

## Known issues and limitations {#known-issues-and-limitations}

**Android TVSDK 3.11**

* No new limitations added.

### Known issues and limitations in the previous releases

**Android TVSDK 3.10**

* No new limitations added.

**Android TVSDK 3.8**

* No new limitations added.

**Android TVSDK 3.7**

* No new limitations added.

**Android TVSDK 3.6**

* No new limitations added.

**Android TVSDK 3.5**

* No new limitation added.

**Android TVSDK 3.4**

* ID3, Closed Captions, Late Binding Audio support has not been verified for the CMAF (CBC) stream.
* On some devices, a low reproducibility issue exists due to which video distortion can appear on the top during trick play on CMAF streams.

**Android TVSDK 3.3**

* clcp:c608 captions are not supported for CMAF stream playback.

**Android TVSDK 3.2**

* TVSDK 3.2 does not support CMAF Sample AES and AES128 streams playback.
* HEVC CMAF streams do not include support for closed captions playback.
* Green coloration appears for WV Encrypted streams when seeking is performed around the non-encrypted segment.
* CMAF-Streams unterstützen keine ID3-Ereignis.
* HLS-Streams unterstützen kein TTML-Untertitelformat.

**Android TVSDK 3.0**

* HEVC support has following limitations in this release

   * DRM not supported
   * CC (CEA 608/708) support not verified
   * 4K support is not yet present
   * ID3 tags support not verified

* For ad progress events, the timeline bar may not reflect 100% accurate ad playback time. As a workaround, one can use `adcompleteevent` to know the ad playback completion and update UI for various purposes like update the timeline bar, removing ad related UI, etc.
* Vast ad calls returned from VMAP do not honor the Just-In-Time lookahead position.

**Android TVSDK 2.5.6**

* Mehrere VMAP-Werbeunterbrechungen gleichzeitig werden nicht unterstützt.

**Android TVSDK 2.5.3**

Diese Version hat folgende Probleme:

* Bei der Live-Videowiedergabe treten möglicherweise Probleme mit der Audio-/Video-Synchronisierung auf Geräten mit niedrigem Ende oder bei schlechten Netzwerkbedingungen auf.
* Bei FER-Streams können VirtualTime und localTime unterschiedlich sein. Auch FER mit Versatz funktioniert nicht.
* Die Wiedergabe wird möglicherweise gestoppt, wenn der Inhalt von &quot;Spätbindung - Audio&quot;gesucht wird.
* Gelegentlich werden WebVTT-Beschriftungen für LIVE-Inhalte möglicherweise nicht mehr synchron.
* Nach einer Werbeunterbrechung kann immer wieder eine schnelle Wiedergabe einiger Frames auftreten.
* Manchmal wird der Fehler &quot;303&quot;für &quot;Tripple Wrapper Ad Breaks&quot;ausgegeben, auch wenn Anzeigen wiedergegeben werden.

**Android TVSDK 2.5.2**

Diese Version hat folgende Probleme:

* Bei der Live-Videowiedergabe treten möglicherweise Probleme mit der Audio-/Video-Synchronisierung auf Geräten mit niedrigem Status auf.
* Die Wiedergabe kann manchmal anhalten, wenn der Benutzer bis zum Ende des VOD-Mediums sucht.
* Bei FER-Streams können VirtualTime und localTime unterschiedlich sein. FER mit Versatz funktioniert ebenfalls nicht.

**Android TVSDK 2.5.1**

Diese Version von TVSDK hat folgende Probleme:

* Bei der Live-Videowiedergabe treten möglicherweise Probleme mit der Audio-/Video-Synchronisierung auf Geräten mit niedrigem Videostatus auf.
* For FER streams, virtualTime and localTime may differ. Also, FER with offset does not work.
* In VMAP XML, if there is an empty VAST tag without an explicit closing tag (&lt;/VAST>), and without a newline after it, then the VMAP XML is not parsed properly and ads may not play.
* VPAID post-roll are not supported.

## Helpful resources {#helpful-resources}

* [System Requirements](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-android-prog/introduction/android-3x-requirements.html)
* [TVSDK 3.10 for Android Programmer&#39;s Guide](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-android-prog/introduction/android-3x-overview-prod-audience-guide.html)
* [TVSDK Android Javadoc for API Reference](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.5/index.html)
* [TVSDK Android C++ API Document](https://help.adobe.com/en_US/primetime/api/psdk/cpp_3.5/namespaces.html) - Each Java class has a corresponding C++ class, and the C++ documentation contains more explanatory material than the Javadocs, so refer the C++ documentation for a deeper understanding of the Java API.
* [TVSDK 1.4 to 2.5 for Android (Java) Migration Guide](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-25-android.html)
* For handling screen on/off scenarios, see the `Application_Changes_for_Screen_On_Off.pdf` file included in the build.
* See complete help documentation at [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html) page.
