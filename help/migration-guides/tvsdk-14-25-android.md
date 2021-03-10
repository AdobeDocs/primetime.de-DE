---
title: TVSDK 1.4 bis 2.5 für Android (Java)
description: TVSDK 2.5 bietet im Vergleich zu Version 1.4 mehrere Vorteile in Bezug auf Leistung, Sicherheit, bessere Integrationen und mehr.
contentOwner: vishgupt
products: SG_PRIMETIME
topic-tags: migration
translation-type: tm+mt
source-git-commit: b33240bf1b42b80389cd95a7ae4d3f85185a2d32
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 0%

---


# TVSDK 1.4 bis 2.5 für Android (Java) {#tvsdk-to-for-android-java}

TVSDK 2.5 bietet im Vergleich zu Version 1.4 mehrere Vorteile in Bezug auf Leistung, Sicherheit, bessere Integrationen und mehr.

TVSDK löst die größten Herausforderungen, auf dem Gerät, das am wichtigsten ist. Android setzt seine globale Dominanz fort, mit über 86% Marktanteil. Durch die Migration zu TVSDK unter Android wird die Wiedergabeleistung optimiert, um die Benutzerinteraktion zu verbessern und die Time-to-Market mit Unterstützung neuer Inhaltsformate zu beschleunigen.

## Vorteile der Migration zu TVSDK v2.5 {#benefits-of-migrating-to-tvsdk-v}

TVSDK 2.5 bietet im Vergleich zu Version 1.4 mehrere Vorteile in Bezug auf Leistung, Sicherheit, bessere Integrationen und mehr. Lesen Sie weiter, um die Vorteile der Migration auf diese neue Version schnell zu erfahren.

Laut einer Benchmarking-Studie eines Drittanbieters bietet Version 2.5 eine 5fache Reduzierung der Startzeit und eine 3,8fache Reduzierung der Dropped Frames im Vergleich zum Branchendurchschnitt.

| Leistungsfunktionen | Beschreibung |
|--- |--- |
| Sofort-On für VOD und Live | Zunächst müssen die Segmente für die sofortige Wiedergabe für VOD- und Live-lineare Streams beim Wechseln des Kanals für ein TV-ähnliches Erlebnis geladen werden. |
| Verzögertes Laden von Werbeanzeigen | Beginn werden abgespielt, sobald Pre-Roll- oder Content-Funktion verfügbar ist, während Mid-Roll-Anzeigen in einem parallelen Thread aufgelöst werden. |
| Persistente Netzwerkverbindungen | Verbessern Sie die Effizienz und verringern Sie die Latenz des Netzwerkcodes, um die Wiedergabeleistung zu beschleunigen. |
| Verbesserte ABR-Logik | Die neue ABR-Logik basiert auf der Pufferlänge, der Änderungsrate der Pufferlänge und der gemessenen Bandbreite. Dadurch wird sichergestellt, dass die ABR die richtige Bitrate wählt, wenn die Bandbreite schwankt, und auch die Anzahl der auftretenden Bitratenwechsel optimiert wird, indem die Rate überwacht wird, mit der sich die Pufferlänge ändert. |
| Teilweiser Segmentdownload | Beginn werden abgespielt, sobald genügend Frames aus einem Segment verfügbar sind, um Videos auf Clientseite zuverlässig wiederzugeben. |
| Parallele Downloads | TVSDK lädt parallel Audio- und Videosegmente herunter, um entmufferten Inhalt zur Optimierung der Wiedergabeleistung zu erhalten. |

Die Wiedergabe-Funktionen verbessern die Interaktion der Verbraucher, indem sie das Erlebnis linearer Übertragungen auf digitalen Medien bereitstellen. Außerdem können Sie damit native DRM-Dateien wie Widevine für die HD-Wiedergabe nutzen.

| Wiedergabe-Funktionen | Beschreibung |
|--- |--- |
| MP4-Wiedergabe | MP4-Kurzclips müssen nicht neu transkodiert werden, um sie in TVSDK wiederzugeben. |
| Wiedergabe von DASH-VOD-Inhalten | Grundlegende Anwendungsfälle für die DASH VOD-Wiedergabe werden unterstützt. |
| Glattes Triplay mit ABR | Unterstützung für schnelle Vorwärts- und Rückspulen in HLS mit Keyframes mit niedrigen Raten und I-Frames mit schnelleren Geschwindigkeiten. ABR-Unterstützung für alle unterstützten Frames. |

Die Funktionen sind wichtig, um die Einschränkungen des Studios, wie die HD-Wiedergabe über natives DRM, zu erfüllen.

| Funktionen | Beschreibung |
|--- |--- |
| Auflösungsbasierter Ausgabeschutz | Die Wiedergabe kann auf bestimmte Auflösungen beschränkt werden, die nach DRM-Anforderungen zulässig sind. Nur über Primetime DRM verfügbar. |
| Weitgehende Unterstützung | Unterstützt mit DASH VOD-Streams, um native DRM-Anwendungsfälle zu aktivieren. |

Die Verbesserung der direkten Rechnungsstellung entfällt mit der Notwendigkeit, monatlich manuelle Berichte zur Rechnungsstellung zu erstellen. VHL 2.0 ermöglicht eine schnellere Markteinführungszeit bei vorab erstellter Integration und einer genaueren Verfolgung.

| Funktionen | Beschreibung |
|--- |--- |
| Mottenintegration | Unterstützung für Anzeigensichtbarkeitsmessung von Moat. |
| VHL 2.0 | Die neueste optimierte Video Heartbeats-Bibliotheksintegration zur automatischen Erfassung von Nutzungsdaten für Adobe Analytics. |
| Failover-Unterstützung | Zusätzliche implementierte Strategien, um die unterbrechungsfreie Wiedergabe trotz Fehlern von Hostservern, Playlist-Dateien und Segmenten fortzusetzen. |
| Integration der direkten Rechnungsstellung | Sendet Rechnungsmetriken an das Adobe Analytics Backend, das von Adobe Primetime für vom Kunden verwendete Streams zertifiziert wurde. |

>[!NOTE]
>
>Alle Funktionen von TVSDK v1.4 werden in Version 2.5 unterstützt, mit Ausnahme der Multi-CDN-Unterstützung.

## Übersicht über den Migrationsprozess {#overview-of-the-migration-process}

Die reibungslose Migration von TVSDK 1.4 auf 2.5 beinhaltet die Änderung auf Version 2.5 Bibliotheken, die Neukompilierung und dann die Verwendung dieses Dokuments, um Probleme zu beheben, die auftreten.

TVSDK v1.4-Bibliotheken funktionieren nicht mit v2.5-Bibliotheken und sind nicht gleichzeitig vorhanden. Sie müssen v2.5-Bibliotheken mit TVSDK 2.5 verwenden und Ihre Anwendungen und Integrationen migrieren, um auf TVSDK 2.5 zu aktualisieren. In diesem Dokument wird beschrieben, wie und was Sie im Anwendungscode ändern und wie Sie Fehler während der Neukompilierung beheben.

Die Datei &quot;psdk.jar&quot;verwendet Bibliotheken von Drittanbietern, um verschiedene Funktionen zu unterstützen. Um das Entfernen der Bibliotheken zu verhindern, fügen Sie Folgendes in die Datei `proguard.cfg` ein:

```java
# Adobe TVSDK keep classes
-keep class com.adobe.** { *; }
-keep class com.google.android.exoplayer.**
{ *; }
```

In der Datei `build.gradle` müssen Sie die Kompilierdirektive einschließen, um die TVSDK-basierten JAR-Dateien einzuschließen. Wenn Ihre App Adobe Video Analytics enthält, müssen Sie die Kompilierungsrichtlinie für die zusätzlichen JARs einschließen, die für die Integration von Adobe Video Analytics in die App erforderlich sind

```java
# Compile Adobe TVSDK jars compile files('libs/psdk-va.jar')
compile files('libs/VideoHeartbeat.jar')
```

Mehrere geringfügige Änderungen werden in diesem Dokument nicht behandelt. Die kleineren API-Änderungen finden Sie unter [TVSDK 2.5 für Android Java API](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.5/index.html). Die entsprechende Referenz zur C++-API enthält detaillierte Beschreibungen. Eine entsprechende Dokumentation zur C++-API finden Sie unter [TVSDK 2.5 für Android C++ API](https://help.adobe.com/en_US/primetime/api/psdk/cpp_2.5/index.html).

In der mit dem TVSDK verteilten Referenzimplementierung werden mehrere Beispiele für die API-Verwendung behandelt.

## API-Änderungen in TVSDK v2.5 {#api-changes-in-tvsdk-v}

Die neuen, veralteten und geänderten APIs werden nachfolgend beschrieben.

| TVSDK v1.4 | TVSDK v2.5 | Beschreibung |
|--- |--- |--- |
| import com.adobe.ave.drm .DRMAcquireLicenseSettings | import com.adobe.mediacore.drm .DRMAcquireLicenseSettings; | Alle Klassennamen in der TVSDK 2.5-API beginnen mit dem Präfix com.adobe.mediacore. Das ist nur ein Beispiel. |
| MediaPlayerException, IllegalStateException oder IllegalArgumentException | MediaPlayerException | In 2.5 generieren die APIs nur MediaPlayerException. |
| MediaPlayer.PlayerState (MediaPlayer.Ereignis.PLAYBACK) | MediaPlayerStatus (MediaPlayerEvent.STATUS_CHANGED) | In Version 2.5 wurde MediaPlayer.PlayerState in eine separate MediaPlayerStatus-Enum umbenannt. |
| DefaultMediaPlayer.create (getActivity().getApplicationContext()) | MediaPlayer mediaPlayer = new MediaPlayer(getActivity(). getApplicationContext(); | Die zum Erstellen von Objekten verwendeten statischen Methoden werden durch öffentliche Konstruktoren ersetzt. |
| MediaPlayer.seekToLocalTime() | MediaPlayer.seekToLocal() | Die MediaPlayer.searchToLocalTime()-Methode heißt jetzt MediaPlayer.ListenToLocal(). |
| closedCaptionsTrack.isActive() |  | Nicht verfügbar |
| MetadataNode | Metadaten | In Version 2.5 ersetzt die Metadata-Klasse die Verwendung der MetadataNode-Klasse der Version 1.4. |
| DefaultMetadataKeys | MetadataKeys | Die DefaultMetadataKeys von Version 1.4 befinden sich in Version 2.5 enum MetadataKeys. |
| AdvertisingFactory | ContentFactory | Die AdvertisingFactory von Version 1.4 wird in Version 2.5 in ContentFactory umbenannt |
| PlacementOpportunityDetector | OpportunityGenerator | Detektoren werden durch Generatoren ersetzt. |
| mediaPlayer.getView().notificationClick(); | mediaPlayer.notificationClick(); | Die Methode notificationClick() von MediaPlayerView wurde in die MediaPlayer-Klasse verschoben. |
| public ABRControlParameters(ABRPopolicy abrPolicy, int nInitialBitRate, int MinBitRate, int nMaxBitRate) | public ABRControlParameters(int nInitialBitRate, int MinBitRate, int nMaxBitRate, ABRPopolicy abrPolicy, int MinTrickPlayBitRate, int nMaxTrickPlayBitRate, int nMaxTrickPlayBandwidthUsage, Dublette dMax PlayoutRate) |  |
| playbackInformation.getTimeToFirstFrame() |  | Nicht verfügbar |
|  | playInformation.get PerceivedBandwidth() | TVSDK v2.5 QOSProvider verfügt über eine neue Eigenschaft, um die wahrgenommene Bandbreite während einer Streaming-Sitzung zu bestimmen. |

### Entfernte Klassen {#removed-classes}

Die folgenden Klassen werden entfernt und haben keine Entsprechungen.

* `TimeRangeCollection`
* `PSDKConfig`
* `BaseLogger`
* `DefaultLogger`
* `Log`
* `Logger`
* `LogFactory`
* `NullLogger`

Die letzten sechs dieser Klassen sind als Dienstprogrammklassen in der Referenz-Implementierung verfügbar.

## Namensraum ändert sich {#namespace-changes}

Die TVSDK 2.5-API konsolidiert Namensraum.

Alle Klassennamen in der TVSDK 2.5-API beginnen mit dem Präfix com.adobe.mediacore. Einige Klassennamen im TVSDK 1.4 API-Beginn mit com.adobe.ave. Die entsprechenden 2.5-Klassen ändern com.adobe.ave in com.adobe.mediacore. Beachten Sie beispielsweise die Änderungen in den folgenden Codezeilen für 1.4 und 2.5:

```java
// TVSDK 1.4
import com.adobe.ave.drm.DRMAcquireLicenseSettings; import com.adobe.ave.drm.DRMLicense;
import com.adobe.ave.drm.DRMManager; import com.adobe.ave.drm.DRMMetadata
```

```java
// TVSDK 2.5
import com.adobe.mediacore.drm.DRMAcquireLicenseSettings; import com.adobe.mediacore.drm.DRMLicense;
import com.adobe.mediacore.drm.DRMManager; import com.adobe.mediacore.drm.DRMMetadata;
```

## Änderungen bei der Handhabung von Ereignissen {#changes-in-event-handling}

Um Ereignis in dieser Version zu registrieren, übergeben Sie den Handler an `addEventListener`. Die Liste von Ereignissen wurde von Version 1.4 auf Version 2.5 überarbeitet.\
So registrieren Sie beispielsweise einen Ereignis-Handler für `MediaPlayerEvent.STATUS_CHANGED:`

```java
mPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,
new StatusChangeEventListener() {
@Override
public void onStatusChanged(MediaPlayerStatusChangeEvent event) {
//Handle status change event
}
});
```

So wurde das Ereignis unter 1.4 registriert:

```java
mPlayer.addEventListener(MediaPlayer.Event.PLAYBACK, new MediaPlayer.PlaybackEventListener() {
@Override
public void onStateChanged(MediaPlayer.PlayerState state,
MediaPlayerNotification notification) {
//Handle status change event
}
// Additional handlers
...
});
```

Die MediaPlayerEvent-Enum enthält alle Ereignis-Codes. Die folgenden Ereignis-Codes aus 1.4 sind in 2.5 nicht mehr vorhanden:

* `ADBREAK_PLACEMENT_COMPLETED`
* `ADBREAK_PLACEMENT_FAILED`
* `ADBREAK_REMOVAL_COMPLETED`
* `AD_BREAK_MANIFEST_LOAD_COMPLETE`
* `AD_MANIFEST_LOAD_COMPLETE`
* `AD_MANIFEST_LOAD_FAILED`
* `AUDIO_TRACK_FAILED`
* `BACKGROUND_MANIFEST_FAILED`
* `BUFFERING_FULL, CUSTOM_AD_EVENT`
* `CONTENT_MARKER`
* `CONTENT_PLACEMENT_COMPLETE`
* `CONTENT_CHANGED`
* `ITEM_REPLACED`
* `ITEM_READY`
* `VIEW_CLICKED`
* `PREPARED`
* `UPDATED`
* `OPPORTUNITY_COMPLETED`
* `OPPORTUNITY_CREATED`
* `OPPORTUNITY_FAILED`
* `PAUSE_AT_PERIOD_END`
* `PLAYBACK_STARTED`
* `PLAYBACK_PAUSED`
* `PLAYBACK_COMPLETED`
* `PLAY_COMPLETE`
* `POST_ROLL_COMPLETE`
* `RESOURCE_LOADED`
* `TIMED_METADATA_SKIPPED`
* `VIDEO_ERROR`
* `VIDEO_STATE_CHANGED`

Die folgenden Ereignis-Codes sind in 2.5 neu:

* `AD_RESOLUTION_COMPLETE`
* `BUFFER_PREPARED`
* `CAPTIONS_UPDATED`
* `MANIFEST_UPDATED`
* `PLAYBACK_RANGE_UPDATED`
* `RESERVATION_REACHED`
* `TIME_CHANGED`
* `TIMED_EVENT`
* `TIMED_METADATA_ADDED_IN_BACKGROUND`

### Umbenannte Ereignis {#renamed-events}

| Neuer Name | Alter Name |
|--- |--- |
| SEEK_BEGIN | SEEK_STARTED |
| SEEK_END | SEEK_COMPLETED |
| SEEK_POSITION_ADJUSTED | SEEK_ADJUST_COMPLETED |
| BUFFERING_BEGIN | BUFFERING_STARTED |
| BUFFERING_END | BUFFERING_COMPLETED |
| AUDIO_TRACK_UPDATED | AUDIO_TRACK_CHANGED |
| STATUS_CHANGED | STATE_CHANGED |
| TIMED_METADATA_AVAILABLE | TIMED_METADATA_ADDED |
| SIZE_AVAILABLE | SIZE_CHANGED |
| LOAD_INFO | LOAD_INFORMATION_AVAILABLE |

## MediaPlayer ändert {#mediaplayer-changes}

Eine neue Methode zum Erstellen von `MediaPlayer` und Änderungen an einigen Methoden.

**Änderungen an der MediaPlayer-Klasse**

Die folgenden Änderungen gelten für die Klasse `MediaPlayer`:

* Das Enum `MediaPlayerStatus` ersetzt `MediaPlayer.PlayerState`. Beispiel:

```java
//TVSDK v1.4
mPlayer. addEventListener(MediaPlayer.Event.PLAYBACK, new MediaPlayer.PlaybackEventListener() {

@Override
public void onStateChanged(MediaPlayer.PlayerState state,MediaPlayerNotification notification) {
//Handle status change event
}
// Additional handlers
...
});

//TVSDK v2.5
mPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED, new StatusChangeEventListener() {
@Override
public void onStatusChanged(MediaPlayerStatusChangeEvent event) {
//Handle status change event
}
//Additional handlers.
...
});
```

* Die `MediaPlayer.seekToLocalTime()`-Methode heißt jetzt `MediaPlayer.seekToLocal`. Beispiel:

```java
//TVSDK v1.4
public void seekToLocal(long localPosition) { mediaPlayer.seekToLocalTime(localPosition);
}

//TVSDK v2.5
public void seekToLocal(long localPosition) { mediaPlayer.seekToLocal(localPosition);
}
```

* Die `MediaPlayerView.notifyClick()`-Methode ist jetzt `MediaPlayer.notifyClick()`. Beispiel:

```java
//TVSDK v1.4
public void adClick() { mediaPlayer.getView().notifyClick();
}

//TVSDK v2.5
public void adClick() { mediaPlayer.notifyClick();
}
```

* Die frühere `MediaPlayer.MediaPlayer.getNotificationHistory()`-Methode ist jetzt weg und nicht ersetzt.
* Das frühere `MediaPlayer.replaceCurrentItem()` wird in zwei Methoden unterteilt: `replaceCurrentResource()`, das eine Instanz von `MediaResource` und `replaceCurrentItem()` übernimmt, die eine Instanz von `MediaPlayerItem` übernimmt. Beispiel:

```java
//TVSDK v1.4
MediaResource playerResource = MediaResource.createFromUrl(url, getAdvertisingMetadata());

mediaPlayer.replaceCurrentItem(playerResource);

//TVSDK v2.5 - replacing a resource
MediaResource playerResource = new MediaResource(url,
MediaResource.Type.HLS, getAdvertisingMetadata());
...
try {
mMediaPlayer.replaceCurrentResource(playerResource, _mediaPlayerItemConfig);
} catch (MediaPlayerException mediaPlayerException) {
// handle exception.
}
// TVSDK 2.5 - replacing an Item
MediaPlayerItemLoader itemLoader = new MediaPlayerItemLoader(context, new MediaPlayerItemLoader.LoaderListener() {

@Override
public void onError(PSDKErrorCode psdkErrorCode, String s) {
...
}
@Override
public void onLoadComplete(MediaPlayerItem mediaPlayerItem) {
...
}
@Override
public void onBufferingBegin() {
...
}
@Override
public void onBufferPrepared() {
...
}
});
MediaResource playerResource = new MediaResource(url,
MediaResource.Type.HLS, getAdvertisingMetadata());

itemLoader.load(playerResource); itemLoader.prepareBuffer();
mediaPlayer.replaceCurrentItem(itemLoader.getItem());
```

Verwenden Sie diese Option, um zwischen vorinitialisierten MediaPlayer-Instanzen zu wechseln, wie im Falle von Blackouts.

**Konstruktoren ersetzen statische create()-Methoden**

Sie können Konstruktoren in TVSDK v2.5 verwenden, anstatt die Methoden `create()` von TVSDK v1.4 zu verwenden. Alle Klassen mit Namen, die mit Default beginnen, wie `DefaultMediaPlayer`, `DefaultNetworkConfig`, `DefaultContentFactory`, sind in Version 2.5 nicht verfügbar.

In einigen Fällen verwendet die TVSDK v1.4-API das folgende Muster zum Erstellen von Klassen:

1. Definieren Sie eine Schnittstelle (z. B. `MediaPlayer`).
1. Geben Sie eine Standardklasse an (z. B. `DefaultMediaPlayer`).
1. Stellen Sie eine `create()`-Methode für die Standardklasse bereit, um eine Klasse bereitzustellen, die die Schnittstelle implementiert.

In TVSDK v2.5 sind solche Schnittstellen konkrete Klassen und Sie erstellen Instanzen dieser Klassen mit den entsprechenden Konstruktoren. Die folgenden Codebeispiele illustrieren diesen Unterschied:

```java
//TVSDK v1.4
// Create a media player
// MediaPlayer is an interface
private MediaPlayer createMediaPlayer() { MediaPlayer mediaPlayer =
DefaultMediaPlayer.create(getActivity().getApplicationContext()); return mediaPlayer;

//TVSDK v2.5
// Create a media player
// MediaPlayer is a class that you instantiate private MediaPlayer createMediaPlayer() {
MediaPlayer mediaPlayer =
new MediaPlayer(getActivity().getApplicationContext()); return mediaPlayer;
}
```

Andere Klassen, die diesem Muster nicht folgen, aber in 1.4 `create()` Methoden verwenden, umfassen:

* MediaResource\
   Diese zuvor verwendete `MediaResource.createFromUrl()`. Verwenden Sie jetzt den Konstruktor, der eine URL, einen Ressourcentyp und Metadaten akzeptiert. Beispiel:

```java
//TVSDK v1.4
MediaResource playerResource = MediaResource.createFromUrl(url, getAdvertisingMetadata());
mediaPlayer.replaceCurrentItem(playerResource);

//TVSDK v2.5
MediaResource playerResource =
new MediaResource(url, MediaResource.Type.HLS, getAdvertisingMetadata());

try { mediaPlayer.replaceCurrentResource(playerResource,_mediaPlayerItemConfig);
} catch (MediaPlayerException mediaPlayerException) {
// handle exception.
}
```

* Anzeige
* AdAsset
* AdBreak

Einige Klassen (z. B. `ContentFactory`) sind abstrakte Klassen ohne öffentlich verfügbare Standardimplementierung (z. B. `DefaultContentFactory`). In diesen Fällen können Sie beispielsweise eine Standardimplementierung über eine einfache Funktion bereitstellen: `mediaPlayerItemConfig.getDefaultContentFactory()`

**Änderungen bei Untertiteln**

Die folgenden Änderungen wirken sich auf Klassen im Zusammenhang mit Untertiteln aus:

* Beim Abrufen von Untertitelspuren gibt `MediaPlayerItem.getClosedCaptionTracks()` nur aktive Spuren zurück.
* `ClosedCaptionTrack` hat keine  `isActive()` Methode mehr.

```java
//TVSDK v1.4
public List<String> getClosedCaptionTracks(String label) {
List<String> closedCaptionsTracksAsStrings = new ArrayList<String>(); MediaPlayerItem currentItem = mediaPlayer.getCurrentItem(); List<ClosedCaptionsTrack> closedCaptionsTracks =
currentItem.getClosedCaptionsTracks(); Iterator<ClosedCaptionsTrack> iterator =
closedCaptionsTracks.iterator();
if (currentItem != null) {
while (iterator.hasNext()) {
ClosedCaptionsTrack closedCaptionsTrack = iterator.next(); String isActive = closedCaptionsTrack.isActive() ? " (" + label
+ ")" : "";
closedCaptionsTracksAsStrings.add(closedCaptionsTrack.getName()
+ " : " + closedCaptionsTrack.getLanguage() + isActive);
}
}
return closedCaptionsTracksAsStrings;
}

//TVSDK v2.5
public List<String> getClosedCaptionTracks(String label) {

MediaPlayerItem currentItem = mediaPlayer.getCurrentItem(); List<ClosedCaptionsTrack> closedCaptionsTracks =
currentItem.getClosedCaptionsTracks();
Iterator<ClosedCaptionsTrack> iterator = closedCaptionsTracks.iterator();

List<String> closedCaptionsTracksAsStrings = new ArrayList<String>(); if (currentItem != null) {
while (iterator.hasNext()) {
ClosedCaptionsTrack closedCaptionsTrack = iterator.next(); closedCaptionsTracksAsStrings.
add(closedCaptionsTrack.getName() + " : ");
}
}
return closedCaptionsTracksAsStrings;
}
// Add snippet and desc for CaptionsUpdatedEventListener mediaPlayer.addEventListener(MediaPlayerEvent.CAPTIONS_UPDATED,
captionsUpdatedEventListener);

private final CaptionsUpdatedEventListener captionsUpdatedEventListener = new CaptionsUpdatedEventListener() {

@Override
public void onCaptionsUpdated(MediaPlayerItemEvent mediaPlayerItemEvent) { getActivity().findViewById(R.id.sbPlayerControlCC).setVisibility(
View.VISIBLE/*Visible*/);
}
};
```

## Änderungen in der Werbung {#advertising-changes}

In Version 2.5 gibt es mehrere Änderungen im Zusammenhang mit Anzeigen.

**Änderungen des Werbeverhaltens**

Das Standardverhalten der Anzeigenwiedergabe, wenn ein Benutzer eine Suche nach einem Anzeigen-Pod durchführt, ändert sich in Version 2.5 geringfügig. Wenn die Werbeunterbrechung nicht beobachtet wird, wird die Anzeige nach einer Suche nach vorne wiedergegeben. Wenn die App die Standard-Anzeigenrichtlinie verwendet, wird die Werbeunterbrechung nach Abschluss der Wiedergabe entfernt. Bei Verwendung von TVSDK v2.5 wird keine Anzeige wiedergegeben, wenn ein Benutzer hinter einem Anzeigen-Pod auf der Zeitleiste sucht und die Werbeunterbrechung nicht überwacht wird.

In TVSDK v1.4 wird jedoch standardmäßig eine Anzeige wiedergegeben, wenn eine Suche rückwärts erfolgt. Wenn Sie beispielsweise zwischen der dritten und vierten Werbeunterbrechung nach hinten suchen, wird für TVSDK v1.4 standardmäßig die dritte Werbeunterbrechung abgespielt.

**Änderung der Anzeigenregeln**

Die Anzeigenregeln werden mithilfe einer JSON-Datei angegeben. Das Format der JSON-Datei bleibt in beiden Versionen des TVSDK gleich. In TVSDK v2.5 muss die JSON-Datei der Anzeigenregeln jedoch an einem Speicherort gehostet werden, auf den über eine HTTP-URL zugegriffen werden kann. Die Anwendung kann eine Instanz von AuditudeSettings verwenden.

```java
//TVSDK v2.5
AuditudeSettings result = new AuditudeSettings(); result.setCRSRulesJsonURL(<http url of AdobeTVSDKConfig.json>);
```

In TVSDK Version 1.4 wird diese Datei unter dem Ordner assets in der Anwendung platziert und TVSDK lädt die Datei.

**Umbenennung von Anzeigenwerksbetrieben**

`AdvertisingFactory` jetzt benannt  `ContentFactory`. Mit `ContentFactory` können Sie benutzerspezifische Workflows erstellen, indem Sie einige der Methoden überschreiben. Verwenden Sie return null, um das Standardverhalten beizubehalten, wie im Folgenden:

```java
//TVSDK v2.5
new ContentFactory() {
@Override
public AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem item) { return new CustomAdPolicySelector();
}
@Override
public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { return null;
}
@Override
public List<ContentResolver> retrieveResolvers(MediaPlayerItem item) { return null;
}
@Override
public List<CustomAdHandler> retrieveCustomAdPlaybackHandlers(MediaPlayerItem item) { return null;
}
};
```

**Werbeunterbrechungen mit null Länge**

TVSDK 2.5 fügt Werbeunterbrechungen von 0 Länge als Platzhalter ein, wenn der Werbeserver keine Anzeigen zurückgibt.

Die Werbeunterbrechungen mit null Länge können ermittelt werden, indem die Anzahl der Anzeigen in der Werbeunterbrechung mit dem onAdBreakStarted-Ereignis auf null gesetzt wird und die Anwendung diese Werbeunterbrechungen entsprechend handhaben muss.

**Änderungen an Metadaten**

Die Metadata-Klasse bietet einen leistungsfähigeren Ersatz für die frühere MetadataNode-Klasse.

* Die Metadata-Klasse kann Zeichenfolgen, Byte-Arrays und andere Metadata-Objekte speichern:

```java
TVSDK v1.4
public AuditudeSettings createAdvertisementSettings() { Metadata advertisingParams = new MetadataNode();
advertisingParams.setValue("platform", Build.VERSION.RELEASE); advertisingParams.setValue("model", Build.MODEL);
AuditudeSettings adSettings = new AuditudeSettings();
// Set ad domain, zone id and media_id
...

// Set the target paramaters adSettings.setTargetingParameters(advertisingParams);

return adSettings;
}
//TVSDK v2.5
public AuditudeSettings createAdvertisementSettings() { Metadata advertisingParams = new Metadata();
advertisingParams.setValue("platform", Build.VERSION.RELEASE); advertisingParams.setValue("model", Build.MODEL);
AuditudeSettings adSettings = new AuditudeSettings();
// Set ad domain, zone id and media_id
...

// Set the target paramaters adSettings.setTargetingInfo(advertisingParams);

return adSettings;
}
```

* Das Enum `MetadataKeys` ersetzt `DefaultMetadataKeys`. Nicht alle Schlüssel in `DefaultMetadataKeys` sind in der neuen Version vorhanden.

```java
//TVSDK v1.4
if (this.mediaPlayer != null && this.mediaPlayer.getCurrentItem() != null) { MetadataNode resourceMetadata =
(MetadataNode) this.mediaPlayer.getCurrentItem().getResource().getMetadata();
VideoAnalyticsMetadata vaMetadata = (VideoAnalyticsMetadata)
resourceMetadata.getNode(DefaultMetadataKeys.
VIDEO_ANALYTICS_METADATA_KEY.getValue());
}

//TVSDK v2.5
if (resourceMetadata.containsKey(VideoAnalyticsMetadata.
VIDEO_ANALYTICS_METADATA_KEY)) {
JSONObject vaMetadataObj =
new JSONObject(resourceMetadata.
getValue(VideoAnalyticsMetadata. VIDEO_ANALYTICS_METADATA_KEY));
vaMetadata = parseVideoAnalyticsMetadata(vaMetadataObj);
}

} catch (JSONException e) { e.printStackTrace();
}
```

* Anzeigenmetadaten werden jetzt durch die Klasse `AdvertisingMetadata`, eine Unterklasse von Metadaten, dargestellt und werden nun in `MediaPlayerItemConfig` und nicht mehr in `MediaResource` gespeichert.

```java
//TVSDK v1.4
MetadataNode mediaMetadata = new MetadataNode();

if (stream.live) { mediaMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY.getValue(),
getAdSettingsForLive());
} else {
mediaMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY.getValue(), getAdSettingsForVod());
}
MediaResource playerResource = MediaResource.createFromUrl(url, mediaMetadata);

//TVSDK v2.5
MediaPlayerItemConfig mediaItemConfig = new MediaPlayerItemConfig(context);

if (stream.live) {
AuditudeSettings adSettings = getAdSettingsForLive(); adSettings.setLivePreroll(true); mediaItemConfig.setAdvertisingMetadata(adSettings);
} else {
// Set the advertising parameters for VOD. mediaItemConfig.setAdvertisingMetadata(getAuditudeSettingsForVod());
}

// Create advertising metadata node Metadata mediaMetadata = new Metadata();

// Asset Url
MediaResource playerResource =
new MediaResource(url, MediaResource.Type.HLS, mediaMetadata);
try {
mediaPlayer.replaceCurrentResource(playerResource, mItemConfig);
} catch (MediaPlayerException mediaPlayerException) {
//handle exception.
}
```

Metadaten zur Netzwerkkonfiguration, ehemals Mitglied der `MediaResource`-Klasse, werden jetzt durch die `NetworkConfiguration`-Klasse dargestellt und werden jetzt in `MediaPlayerItemConfig` anstatt in `MediaResource` gespeichert.

```java
//TVSDK v1.4
MediaResource playerResource = MediaResource.createFromUrl(url, mediaMetadata);
...

//TVSDK v2.5
MediaPlayerItemConfig mediaItemConfig = new MediaPlayerItemConfig(context);

NetworkConfiguration mediaNetworkConfiguration = mediaItemConfig.getNetworkConfiguration();
```

**Änderungen an der TimedMetadata-Analyse**

Die Analyse von `TimedMetadata` hat sich in 2.5 in Bezug auf die Datentypen für die Analyse des ID3-Tags geändert.

```java
//TVSDK v1.4
public void onTimedMetadata(TimedMetadata timedMetadata) { TimedMetadata.Type type = timedMetadata.getType();
if (type.equals(TimedMetadata.Type.ID3)){ PMPDemoApp.logger.i(LOG_TAG + "#onTimedMetadata",
"New ID3 tag detected at time = " + timedMetadata.getTime());
Metadata metadata = timedMetadata.getMetadata(); Set<String> keys = metadata.keySet();
for (String key : keys) {
String value = metadata.getValue(key); PMPDemoApp.logger.i(LOG_TAG + "#onTimedMetadata",
"Key = " + key + " Value = " + value);
}
} else if (_mediaPlayer.getPlaybackRange() != null &&
_mediaPlayer.getPlaybackRange().getDuration() > 0) { displayRanges();
PMPDemoApp.logger.i(LOG_TAG +
"#onTimedMetadata",
"New timed metadata. Name " + timedMetadata.getName() +
", time " + timedMetadata.getTime() + ", id " + timedMetadata.getId() + ", metadata " +
timedMetadata.getMetadata() + ".");
/*if (!_timedMetadataList.contains(timedMetadata)) {
_timedMetadataList.add(timedMetadata);
}*/
/* scte35 */
if (timedMetadata.getName().equalsIgnoreCase("#EXT-OATCLS-SCTE35")) { parseSCTE35Tag(timedMetadata);
}
}
}

//TVSDK v2.5
public void onTimedMetadata(TimedMetadataEvent timedMetadataEvent) { PMPDemoApp.logger.i(LOG_TAG + " inside"," ontimedmetadata"); TimedMetadata timedMetadata = timedMetadataEvent.getTimedMetadata();

TimedMetadata.Type type = timedMetadata.getType(); if (type.equals(TimedMetadata.Type.ID3)) {
PMPDemoApp.logger.i(LOG_TAG +
"#onTimedMetadata",
"New ID3 tag detected at time = " + timedMetadata.getTime());
Metadata metadata = timedMetadata.getMetadata();
if (metadata != null) { PMPDemoApp.logger.i(LOG_TAG +
"::expandID3Metadata", "isEmpty " + metadata.isEmpty());
Set<String> keys = metadata.keySet(); PMPDemoApp.logger.i(LOG_TAG + "::expandID3Metadata",
"No of keys=" + keys.size());
String s;
for (String key : keys) {
byte[] value = metadata.getByteArray(key); s = new String(value);
if (key.equalsIgnoreCase("APIC"))
s = "SUPPRESSING BINARY DATA FOR ATTACHED PICTURE.";
PMPDemoApp.logger.i(LOG_TAG + "::expandID3Metadata",
"Key=" + key + ", Length=" + value.length + ", Value=" + s.trim());
}
}
} else if (_mediaPlayer.getPlaybackRange() != null &&
_mediaPlayer.getPlaybackRange().getDuration() > 0) { displayRanges();
PMPDemoApp.logger.i(LOG_TAG +
"#onTimedMetadata",
"New timed metadata. Name " + timedMetadata.getName() +
", time " + timedMetadata.getTime() + ", id " + timedMetadata.getId() + ", metadata " +
timedMetadata.getMetadata() + ".");
/*if (!_timedMetadataList.contains(timedMetadata)) {
_timedMetadataList.add(timedMetadata);
}*/
/* scte35 */
if (timedMetadata.getName().equalsIgnoreCase("#EXT-OATCLS-SCTE35")) { PMPDemoApp.logger.i(LOG_TAG +
" inside ontimedmetadata"," ext"); parseSCTE35Tag(timedMetadata);
}
}
}
```

**Weitere Änderungen**

Die folgenden zusätzlichen Änderungen sind in Version 2.5 verfügbar:

* Die `notifyClick()`-Methode wurde von `MediaPlayerView` zu `MediaPlayer` verschoben.

* `AdPolicySelector` ist eine Schnittstelle, keine Klasse. Implementieren Sie alle zugehörigen Methoden.
* `AdPolicyInfo` enthält jetzt eine Liste von  `AdBreakTimelineItem`, nicht  `AdBreakPlacement`.

* Der API-Name der abstrakten Klasse `ContentResolver` wird geändert.
* `PlacementOpportunityDetector` nicht mehr verfügbar ist. Erweitern Sie stattdessen die abstrakte Klasse `OpportunityGenerator`. Die Referenz-Implementierung bietet hierfür ein Beispiel.

* Die Parameter des Konstruktors `AdBreakPlacement` sind identisch, jedoch in einer anderen Reihenfolge. Eine Beispielimplementierung finden Sie in der im Lieferumfang des Produkts enthaltenen Referenz-Player-Implementierung.

## Änderungen in DRM {#changes-in-drm}

Die meisten Änderungen in dieser Version befinden sich auf der DRM-Ebene. Die folgende Tabelle zeigt weitere Änderungen zwischen Version 1.4 und Version 2.5:

| DRMManager-Methode | Erfolgsrückruf in 1.4 | Fehler-Rückruf in 1.4 | Listener in 2.5 |
|--- |--- |--- |--- |
| acquisitionLicense | DRMLicenseAcquiredCallback | DRMOperationErrorCallback | DRMAcquireLicenseListener |
| acquisitionPreviewLicense | DRMLicenseAcquiredCallback | DRMOperationErrorCallback | DRMAcquireLicenseListener |
| authentifizieren | DRMAuthenticationCompleteCallback | DRMOperationErrorCallback | DRMAuthenticateListener |
| createMetadataFromBytes | NA | DRMOperationErrorCallback | DRMErrorListener |
| initialize | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| joinLicenseDomain | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| leaveLicenseDomain | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| resetDRM | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| returnLicense | DRMLicenseReturnCompleteCallback | DRMOperationErrorCallback | DRMReturnLicenseListener |
| setAuthenticationToken | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| storeLicenseBytes | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |

```java
//TVSDK 1.4
private final MediaPlayer.DRMEventListener _drmEventListener = new MediaPlayer.DRMEventListener() {

@Override
public void onDRMMetadata(final DRMMetadataInfo drmMetadataInfo) { PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.DRMEventListener#onDRMMetadata",
"DRM metadata available: " + drmMetadataInfo + ".");
if (getSuppressAutoPlayPreference() && drmMetadataInfo != null) {
// if suppress play setting, then the user is a tester who
// wishes to manually intervene between the metadata available
// event and the play event, so launch the metadata interface
// and give it the loaded metadata bytes, but only once
_drmMetadata = drmMetadataInfo.getDRMMetadata();
}
if (drmMetadataInfo == null ||
!DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { PMPDemoApp.logger.i(LOG_TAG + "#onDRMMetadata", "DRM auth is not needed."); return;
}
// Perform DRM auth.
// Possible logic might take into consideration a threshold
// between the current player time and the DRM metadata start
// time. For the time being, we resolve it as soon as we receive
// the DRM metadata.

DRMManager drmManager = _mediaPlayer.getDRMManager(); if (drmManager == null) {
PMPDemoApp.logger.e(LOG_TAG + "#onDRMMetadata", "DRMManager is null."); return;
}
SharedPreferences sharedPreferences =
PreferenceManager.getDefaultSharedPreferences(getActivity()); String authUser =
sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_USERNAME,
getResources().getString(R.string.drmUsername));
String authPass = sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_PASSWORD,
getResources().getString(R.string.drmPassword));
DRMHelper.performDrmAuthentication(drmManager,
drmMetadataInfo.getDRMMetadata(), authUser,
authPass,
new DRMAuthenticationListener() {
@Override
public void onAuthenticationStart() { PMPDemoApp.logger.i(LOG_TAG + "#onAuthenticationStart",
"DRM authentication started for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
@Override
public void onAuthenticationError(long majorCode,
long minorCode, Exception e) {
if (getActivity() == null) { return;
}
PMPDemoApp.logger.e(LOG_TAG +
"#onAuthenticationError",
"DRM authentication failed. " + majorCode + " 0x" + Long.toHexString(minorCode));
_handler.post(new Runnable() {
@Override
public void run() { showToast(getString(R.string.drmAuthenticationError)); getActivity().finish();
}
});
}
@Override
public void onAuthenticationComplete(byte[] authenticationToken) { PMPDemoApp.logger.i(LOG_TAG +
"#onAuthenticationComplete",
"Auth successful for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
});
}
};

//TVSDK 2.5
private final DRMMetadataInfoEventListener drmMetadataInfoEventListener = new DRMMetadataInfoEventListener() {
@Override
public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { final DRMMetadataInfo drmMetadataInfo =
drmMetadataInfoEvent.getDRMMetadataInfo();
PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.DRMEventListener#onDRMMetadata",
"DRM metadata available: " + drmMetadataInfo + ".");
if (getSuppressAutoPlayPreference() && drmMetadataInfo != null) {
// if suppress play setting, then the user is a tester who
// wishes to manually intervene between the metadata
// available event and the play event, so launch the
// metadata interface and give it the loaded metadata
// bytes, but only once
drmMetadata = drmMetadataInfo.getDRMMetadata();
}
if (drmMetadataInfo ==
null || !DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { PMPDemoApp.logger.i(LOG_TAG +
"#onDRMMetadata",
"DRM auth is not needed.");
return;
}
// Perform DRM auth.
// Possible logic might take into consideration a threshold between
// the current player time and the DRM metadata start time. For the
// time being, we resolve it as soon as we receive the DRM metadata.

DRMManager drmManager = _mediaPlayer.getDRMManager(); if (drmManager == null) {
PMPDemoApp.logger.e(LOG_TAG +
"#onDRMMetadata", "DRMManager is null.");
return;
}

SharedPreferences sharedPreferences = PreferenceManager.getDefaultSharedPreferences(getActivity());
String authUser = sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_USERNAME,
getResources().getString(R.string.drmUsername));
String authPass = sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_PASSWORD,
getResources().getString(R.string.drmPassword));
DRMHelper.performDrmAuthentication(drmManager,
drmMetadataInfo.getDRMMetadata(), authUser,
authPass,
new DRMAuthenticationListener() {
@Override
public void onAuthenticationStart() { PMPDemoApp.logger.i(LOG_TAG +
"#onAuthenticationStart",
"DRM authentication started for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
@Override
public void onAuthenticationError(int major,
int minor,
String erroString, String serverErrorURL) {
if (getActivity() == null) { return;
}
PMPDemoApp.logger.e(LOG_TAG +
"#onAuthenticationError",
"DRM authentication failed. " + major +
" 0x" +
Long.toHexString(minor));
_handler.post(new Runnable() {
@Override
public void run() { showToast(getString(R.string.drmAuthenticationError)); getActivity().finish();
}
});
}
@Override
public void onAuthenticationComplete(byte[] authenticationToken) { PMPDemoApp.logger.i(LOG_TAG +
"#onAuthenticationComplete",
"Auth successful for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
});
}
};
```

Die statische `DRMManager`-Instanz, die in 1.4 verfügbar war, nachdem mediaplayer erstellt wurde, ist jetzt verfügbar, nachdem der `onDRMMetadataInfo`-Ereignis-Listener ausgelöst wurde.

## Adaptive Bitrate (ABR)-bezogene Änderungen {#adaptive-bitrate-abr-related-changes}

**Änderungen bei Konstanten**

Viele Konstanten haben den Typ von `String` in `int` geändert. Beispiel: `MediaResourceType`, `ABRControlParameters` und `MediaPlayerStatusChangeEvent`.

```java
//TVSDK v1.4
ABRControlParameters
private void setAbrControlParams() { SharedPreferences sharedPreferences =
PreferenceManager.getDefaultSharedPreferences(getActivity());
if (sharedPreferences.getBoolean(PMPDemoApp.SETTINGS_ABR_CTRL_ENABLED,
PMPDemoApp.DEFAULT_ABR_ENABLED)) {
int initialBitRate = getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_INITIAL_BITRATE, 0);
int minBitRate = getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MIN_BITRATE, 0);
int maxBitRate = getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_BITRATE, PMPDemoApp.DEFAULT_MAX_BIT_RATE);
int mbrPolicyAsInt =
getIntPreference(sharedPreferences, PMPDemoApp.SETTINGS_ABR_POLICY, 0); ABRControlParameters.ABRPolicy abrPolicy = policyFromInt(mbrPolicyAsInt); abrPolicy = abrPolicy != null ?
abrPolicy : ABRControlParameters.ABRPolicy.ABR_MODERATE;
_mediaPlayer.setABRControlParameters(new ABRControlParameters(initialBitRate,
minBitRate, maxBitRate, abrPolicy));
}
}

//TVSDK v2.5
ABRControlParameters
private void setAbrControlParams() { ABRControlParametersBuilder abrBuilder =
new ABRControlParametersBuilder();

if (sharedPreferences.getBoolean(PMPDemoApp.SETTINGS_ABR_CTRL_ENABLED, PMPDemoApp.DEFAULT_ABR_ENABLED)) {

abrBuilder.setInitialBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_INITIAL_BITRATE,
ABRControlParameters.DEFAULT_ABR_INITIAL_BITRATE)); abrBuilder.setMinBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MIN_BITRATE,
ABRControlParameters.DEFAULT_ABR_MIN_BITRATE)); abrBuilder.setMaxBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_BITRATE,
ABRControlParameters.DEFAULT_ABR_MAX_BITRATE)); abrBuilder.setMaxPlayoutRate(getDoublePreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_PLAYOUT_RATE,
ABRControlParameters.DEFAULT_MAX_PLAYOUT_RATE)); abrBuilder.setMinTrickPlayBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MIN_TRICKPLAY_BITRATE,
ABRControlParameters.DEFAULT_ABR_MIN_BITRATE)); abrBuilder.setMaxTrickPlayBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_TRICKPLAY_BITRATE,
ABRControlParameters.DEFAULT_ABR_MAX_BITRATE)); abrBuilder.setMaxTrickPlayBandwidthUsage(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_TRICKPLAY_BANDWIDTH,
ABRControlParameters.DEFAULT_ABR_MAX_BITRATE));

switch (getIntPreference(sharedPreferences, PMPDemoApp.SETTINGS_ABR_POLICY, -1)) {
case 0: abrBuilder.setPolicy(ABRControlParameters.ABRPolicy.ABR_CONSERVATIVE); break;
case 1: abrBuilder.setPolicy(ABRControlParameters.ABRPolicy.ABR_MODERATE); break;
case 2: abrBuilder.setPolicy(ABRControlParameters.ABRPolicy.ABR_AGGRESSIVE); break;
default: abrBuilder.setPolicy(ABRControlParameters.DEFAULT_ABR_POLICY);
}
}
_mediaPlayer.setABRControlParameters(abrBuilder.toABRControlParameters());
}
```

**Änderungen am ABRControlParameters-Konstruktor**

Einige Parameter wurden hinzugefügt, einige umbenannt und andere verschoben. Folgende Konstruktorsignatur ist in Version 1.4 und die neue Signatur in Version 2.5 vorhanden:

```java
//TVSDK v1.4
public ABRControlParameters(ABRPolicy abrPolicy,
int nInitialBitRate, int nMinBitRate,
int nMaxBitRate)

//TVSDK v2.5
public ABRControlParameters(int nInitialBitRate,
int nMinBitRate, int nMaxBitRate,
ABRPolicy abrPolicy,
int nMinTrickPlayBitRate, int nMaxTrickPlayBitRate,
int nMaxTrickPlayBandwidthUsage, double dMaxPlayoutRate)
```

## Fehler-Ereignis und Verarbeitung von {#error-events-and-handling}

**Änderungen bei der Fehlerverarbeitung**

Die `MediaError`-Klasse wurde durch die `Notification`-Klasse ersetzt. Der einzige Unterschied zwischen den Klassen `MediaError` und `Notification` besteht darin, dass letztere kein Beschreibungsattribut enthalten. Die TVSDK 1.4-Fehlercodes mit den Werten 101xxx, 102xxx,104xxx,106xxx,107xxx,109xxx sind in TVSDK 2.5 nicht vorhanden. Die Wiedergabe-Codes in TVSDK 2.5 finden Sie unter [Nativer Fehler- Videowiedergabewerte](assets/psdk_android_2.5.pdf).

Die folgenden Beispiele zeigen die Fehlerbehandlung in TVSDK 1.4 und 2.5:

```java
//TVSDK v1.4
@Override
public void onStateChanged(MediaPlayer.PlayerState state, MediaPlayerNotification notification) {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Player state changed to [" + state
+ "].");

switch (state) {
// Non recoverable state - either reset player and reinitialize
// or release the player and create a new one.
case ERROR: PMPDemoApp.logger.e(LOG_TAG +
"::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Error: " + notification + "."); getActivity().finish();
break;
default:
// do nothing
}
}

//TVSDK v2.5
private final StatusChangeEventListener statusChangeEventListener = new StatusChangeEventListener() {
@Override
public void onStatusChanged(MediaPlayerStatusChangeEvent mediaPlayerStatusChangeEvent)
{
MediaPlayerStatus state = mediaPlayerStatusChangeEvent.getStatus(); PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Player state changed to [" + state
+ "].");
switch (state) {
// Non recoverable state - either reset player and reinitialize
// or release the player and create a new one.
case ERROR:
PMPDemoApp.logger.e(LOG_TAG + "::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Error: ");
printErrorMetadata(mediaPlayerStatusChangeEvent.getMetadata()); showToast("MediaPlayer status ERROR: Look at the logs for details"); getActivity().finish();
break;
default:
// do nothing
}
}
};
```

Alle wiederherstellbaren Fehler werden als Warnungen behandelt und mit dem `NotificationEventListener` in TVSDK 2.5 verarbeitet. Die Warnungen werden als Benachrichtigungen mit dem Listener `onOperationFailed` im QOS-Handler in TVSDK 1.4 angezeigt, wobei, wie in TVSDK 2.5, die Benachrichtigung ein separates Ereignis ist. Die in den Abschnitten 1.4 und 2.5 behandelte Warnung lautet wie folgt:

```java
//TVSDK v1.4
private final MediaPlayer.QOSEventListener _qosEventListener = new MediaPlayer.QOSEventListener()
{
@Override
public void onBufferStart() {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onBufferStart()", "Buffering started.");
}
@Override
public void onBufferComplete() {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onBufferComplete()", "Buffering complete.");
}
@Override
public void onSeekStart() {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onSeekStart()", "Seek starting.");
}
@Override
public void onSeekComplete(long adjustedTime) {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onSeekComplete()", "Seek complete at position: " + adjustedTime + ".");
}
@Override
public void onLoadInfo(LoadInfo loadInfo) {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onLoadInfo()", "Url: " + loadInfo.getUrl() + ", size: "
+ loadInfo.getSize() + " bytes, media duration: " + loadInfo.getMediaDuration() + "ms, download duration: " + loadInfo.getDownloadDuration() + "ms");
}
@Override
public void onOperationFailed(MediaPlayerNotification.Warning warning) {

StringBuffer sb = new StringBuffer("Player operation failed: "); sb.append(warning.getCode()).append(" - ").append(warning.getDescription()); if (warning.getMetadata() != null) {
sb.append("Warning metadata: ").append(warning.getMetadata().toString());
}

MediaPlayerNotification innerNotification = warning.getInnerNotification(); registerFailedAudioTrackIndex(innerNotification); handleFailedSeekEvent(innerNotification);

while (innerNotification != null) { sb.append("Inner notification: ");
sb.append(innerNotification.getCode()).append(" - ").append(innerNotification.getDescription());
Metadata metadata = innerNotification.getMetadata(); if (metadata != null) {
for (String key : metadata.keySet()) { sb.append(" - ").append

//TVSDK v2.5
private final NotificationEventListener notificationEventListener = new NotificationEventListener() {
/**
* An example of dumping the information within a Notification. Here, we don't handle the event in
* any way except to print a log message.
* @param event The NotificationEvent
*/
@Override
public void onNotification(NotificationEvent event) { Notification notification = event.getNotification(); Notification.Type type = notification.getType(); StringBuilder sb = new StringBuilder(); sb.append("[").append(type).append("]");
sb.append(" Player operation failed (").append(notification.getCode()).append(")"); Metadata metadata = notification.getMetadata();
if (metadata != null)
{
for (String key : metadata.keySet())
{
sb.append(", ").append(key).append(" = ").append(metadata.getValue(key));
}
}
Notification inner = notification.getInnerNotification(); if (inner != null) {
sb.append(" :: Inner Notification [").append(inner.getType()).append("](").append(inner.getCode()).append(")");
Metadata innerMetadata = inner.getMetadata(); if (innerMetadata != null) {
for (String iKey : innerMetadata.keySet()) { sb.append(", ").append(iKey).append(" =
").append(innerMetadata.getValue(iKey));
}
}
}
switch(type)
{
case ERROR:
PMPDemoApp.logger.e(LOG_TAG, sb.toString()); break;
case WARNING:
PMPDemoApp.logger.w(LOG_TAG, sb.toString()); break;
default:
PMPDemoApp.logger.i(LOG_TAG, sb.toString()); break;
}
showToast(sb.toString()); PMPDemoApp.logger.d(LOG_TAG, sb.toString());
}
};
```

**Neue Ausnahmen**

Während TVSDK v1.4 eine Kombination aus &quot;nulls&quot;, &quot;error return&quot;und einer Reihe von Ausnahmen ( `MediaPlayerException`, `IllegalStateException` und `IllegalArgumentException`) verwendet hat, gilt TVSDK v2.5 `generatesMediaPlayerException` für alle Fehler.

>[!NOTE]
>
>Um Details zu einer MediaPlayerException abzurufen, können Sie `getErrorCode()` verwenden.

Beispiel für die Änderung:

```java
//TVSDK v1.4
public void setBufferControlParams() { try {
mediaPlayer.setBufferControlParameters(getBufferParamsFromSettings());
} catch (IllegalArgumentException e) { PrimetimeReference.logger.w(LOG_TAG +
"#setBufferControlParams",
"Unable to apply buffering params: " + e.getMessage() + ".");
}
}

//TVSDK v2.5
public void setBufferControlParams() { try {
mediaPlayer.setBufferControlParameters(getBufferParamsFromSettings());
} catch (MediaPlayerException e) { PrimetimeReference.logger.w(LOG_TAG + "#setBufferControlParams", "Unable to apply buffering params: " + e.getMessage() + ".");
}
}
```

## Änderungen an QOS-Parametern {#changes-to-qos-parameters}

An den Eigenschaften des QOSProvider-Objekts wurden geringfügige Änderungen vorgenommen:

* Das `TimeToFirstFrame` ist in TVSDK 2.5 nicht verfügbar.
* TVSDK 2.5 QOSProvider verfügt über eine neue Eigenschaft, um die wahrgenommene Bandbreite während einer Streaming-Sitzung zu bestimmen.

```java
//TVSDK v1.4
public void updateQosInformation(PlaybackInformation playbackInformation) { if (playbackInformation == null) {
return;
}
setQosItem("Frame rate", (int) playbackInformation.getFrameRate() +
" (" + (int) playbackInformation.getDroppedFrameCount() + " dropped)"); setQosItem("Bitrate", (int) playbackInformation.getBitrate()); setQosItem("Buffering time", (long) playbackInformation.getBufferingTime()); setQosItem("Buffer length", (long) playbackInformation.getBufferLength()); setQosItem("Buffer time", (long) playbackInformation.getBufferTime()); setQosItem("Empty buffer count", (int) playbackInformation.getEmptyBufferCount()); setQosItem("Time to load", (int) playbackInformation.getTimeToLoad()); setQosItem("Time to start", (int) playbackInformation.getTimeToStart()); setQosItem("Time to first frame", (int) playbackInformation.getTimeToFirstFrame()); setQosItem("Time to prepare", (int) playbackInformation.getTimeToPrepare()); setQosItem("Last seek time", (int) playbackInformation.getLastSeekTime());
}

//TVSDK v2.5
public void updateQosInformation(PlaybackInformation playbackInformation) { if (playbackInformation == null) {
return;
}
setQosItem("Frame rate", (int) playbackInformation.getFrameRate() +
" (" + (int) playbackInformation.getDroppedFrameCount() + " dropped)"); setQosItem("Bitrate", (int) playbackInformation.getBitRate()); setQosItem("Buffering time", (long) playbackInformation.getBufferingTime()); setQosItem("Buffer length", (long) playbackInformation.getBufferLength()); setQosItem("Buffer time", (long) playbackInformation.getBufferTime()); setQosItem("Empty buffer count", (int) playbackInformation.getEmptyBufferCount()); setQosItem("Time to load", (int) playbackInformation.getTimeToLoad()); setQosItem("Time to start", (int) playbackInformation.getTimeToStart());
setQosItem("Time to prepare", (int) playbackInformation.getTimeToPrepare());
setQosItem("Perceived Bandwidth", (int) playbackInformation.getPerceivedBandwidth());
```

* Das `QOSEventListener::onOperationFailed()` existiert nicht mehr in TVSDK 2.5. Die Warnungen, die früher in diesem Ereignis-Listener angezeigt wurden, werden jetzt im `NotificationEventListener::onNotification()`-Ereignis-Listener angezeigt.

* Die Elemente `QOSProvider event listeners onBufferStart()`, `onBufferComplete()`, `onSeekStart()`, `onSeekComplete()` und `onLoadInfo()` sind individuelle Ereignis-Listener, die an eine mediaPlayer-Instanz gebunden sind.

```java
//TVSDK v1.4
private final MediaPlayer.QOSEventListener _qosEventListener = new MediaPlayer.QOSEventListener() {

@Override
public void onBufferStart() { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferStart()", "Buffering started.");
showBufferingSpinner();
}
@Override
public void onBufferComplete() { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferComplete()", "Buffering complete.");
hideBufferingSpinner();
}
@Override
public void onSeekStart() { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekStart()", "Seek starting.");
inTrickPlayMode = false;
}
@Override
public void onSeekComplete(long adjustedTime) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekComplete()", "Seek complete at position: " +
adjustedTime + ".");
_controlBar.setPosition(adjustedTime);
if (adjustedTime == _mediaPlayer.getPlaybackRange().getEnd() &&
_mediaPlayer.getStatus() == MediaPlayer.PlayerState.COMPLETE) {
// Show the replay button. showReplayButton();
}
if (_mediaPlayer.getStatus() == MediaPlayer.PlayerState.PAUSED) {
// Show the pause icon.
_controlBar.pause();
}
}
@Override
public void onLoadInfo(LoadInfo loadInfo) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onLoadInfo()", "Url: " +
loadInfo.getUrl() + ", size: " + loadInfo.getSize() +
" bytes, media duration: " +
loadInfo.getMediaDuration() + "ms, download duration: " +
loadInfo.getDownloadDuration() + "ms");
 
public void onOperationFailed(MediaPlayerNotification.Warning warning) {

StringBuffer sb = new StringBuffer("Player operation failed: "); sb.append(warning.getCode()).append(" - ").append(warning.getDescription()); if (warning.getMetadata() != null) {
sb.append("Warning metadata: ").append(warning.getMetadata().toString());
}

MediaPlayerNotification innerNotification = warning.getInnerNotification(); registerFailedAudioTrackIndex(innerNotification); handleFailedSeekEvent(innerNotification);

while (innerNotification != null) { sb.append("Inner notification: ");
sb.append(innerNotification.getCode()).append(" - "). append(innerNotification.getDescription());
Metadata metadata = innerNotification.getMetadata(); if (metadata != null) {
for (String key : metadata.keySet()) { sb.append(" - ").append(key).append(": ").
append(metadata.getValue(key));
}
}
innerNotification = innerNotification.getInnerNotification();
}
String errMsg = sb.toString(); PMPDemoApp.logger.w(LOG_TAG +
"::MediaPlayer.QOSEventListener#onOperationFailed()", errMsg);
showToast(errMsg);
}
};

//TVSDK v2.5
mediaPlayer.addEventListener(MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE,
loadInfoEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.BUFFERING_BEGIN,
bufferingBeginEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.BUFFERING_END,
bufferingEndEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.SEEK_BEGIN,
seekBeginEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.SEEK_END,
seekEndEventListener);
// Buffering events.
BufferingBeginEventListener bufferingBeginEventListener = new BufferingBeginEventListener() {
@Override
public void onBufferingBegin(BufferEvent bufferEvent) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferStart()", "Buffering started.");
showBufferingSpinner();
}
};

BufferingEndEventListener bufferingEndEventListener = new BufferingEndEventListener() {
@Override
public void onBufferingEnd(BufferEvent bufferEvent) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferComplete()",
"Buffering complete."); hideBufferingSpinner();
}
};

BufferPreparedEventListener bufferPreparedEventListener = new BufferPreparedEventListener() {
@Override
public void onBufferPrepared() {
}
};
// seek events.
SeekBeginEventListener seekBeginEventListener = new SeekBeginEventListener() {

@Override
public void onSeekBegin(SeekEvent seekEvent) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekStart()", "Seek starting.");
inTrickPlayMode = false;
}
};
SeekEndEventListener seekEndEventListener = new SeekEndEventListener() {
@Override
public void onSeekEnd(SeekEvent seekEvent) {
double adjustedTime = seekEvent.getActualPosition();
PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekComplete()", "Seek complete at position: " + adjustedTime + ".");
_controlBar.setPosition((long) adjustedTime);
if (adjustedTime == _mediaPlayer.getPlaybackRange().getEnd() &&
_mediaPlayer.getStatus() == MediaPlayerStatus.COMPLETE) {
// Show the replay button. showReplayButton();
}
if (_mediaPlayer.getStatus() == MediaPlayerStatus.PAUSED) {
// Show the pause icon.
_controlBar.pause();
}
}
};
/**
* LoadInformationEventListener that intercepts PSDK load info events
*/
private final LoadInformationEventListener loadInfoEventListener = new LoadInformationEventListener() {

@Override
public void onLoadInformation(LoadInformationEvent event) { LoadInformation loadInfo = event.getLoadInfomation(); PMPDemoApp.logger.i(
LOG_TAG + "::LoadInformationEventListener#onLoadInfomation()", "Url: " + loadInfo.getUrl() + ", size: "
+ loadInfo.getSize()
+ " bytes, download duration: "
+ loadInfo.getDownloadDuration() + "ms");
}
};
```

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation auf der Seite [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).