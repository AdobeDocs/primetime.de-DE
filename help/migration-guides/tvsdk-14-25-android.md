---
title: TVSDK 1.4 bis 2.5 für Android (Java)
description: TVSDK 2.5 bietet im Vergleich zu Version 1.4 mehrere Vorteile in Bezug auf Leistung, Sicherheit, bessere Integrationen und mehr.
contentOwner: vishgupt
products: SG_PRIMETIME
topic-tags: migration
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 0%

---

# TVSDK 1.4 bis 2.5 für Android (Java) {#tvsdk-to-for-android-java}

TVSDK 2.5 bietet im Vergleich zu Version 1.4 mehrere Vorteile in Bezug auf Leistung, Sicherheit, bessere Integrationen und mehr.

TVSDK löst die größten Herausforderungen auf dem Gerät, auf dem es am wichtigsten ist. Android setzt seine weltweite Marktbeherrschung fort, mit über 86% des Marktanteils. Die Migration zu TVSDK unter Android optimiert die Wiedergabeleistung, um die Benutzerinteraktion zu verbessern und die Time-to-Market mit Unterstützung für neue Inhaltsformate zu beschleunigen.

## Vorteile der Migration zu TVSDK v2.5 {#benefits-of-migrating-to-tvsdk-v}

TVSDK 2.5 bietet im Vergleich zu Version 1.4 mehrere Vorteile in Bezug auf Leistung, Sicherheit, bessere Integrationen und mehr. Lesen Sie weiter, um die Vorteile der Migration auf diese neue Version schnell zu erfahren.

Laut einer Benchmarking-Studie von Drittanbietern sorgt v2.5 für eine 5fache Reduzierung der Startzeit und eine 3,8fache Reduzierung der Dropped Frames gegenüber dem Branchendurchschnitt.

| Leistungsmerkmale | Beschreibung |
|--- |--- |
| Sofort-On für VOD und Live | Beim ersten Laden werden die Segmente für die sofortige Wiedergabe für VOD- und Live-lineare Streams beim Kanalwechsel für ein TV-ähnliches Erlebnis vorausgeladen. |
| Verzögertes Laden von Anzeigen | Startet die Wiedergabe, sobald beim Auflösen von Mid-Roll-Anzeigen in einem parallelen Thread eine Pre-Roll- oder Inhaltsbereitstellung verfügbar ist. |
| Persistente Netzwerkverbindungen | Steigerung der Effizienz und Verringerung der Latenz von Netzwerkcode für eine schnellere Wiedergabeleistung. |
| Verbesserte ABR-Logik | Die neue ABR-Logik basiert auf der Pufferlänge, der Änderungsrate der Pufferlänge und der gemessenen Bandbreite. Dadurch wird sichergestellt, dass die ABR bei Bandbreitenschwankungen die richtige Bitrate auswählt und die Anzahl der tatsächlichen Bitratenwechsel optimiert, indem die Geschwindigkeit überwacht wird, mit der sich die Pufferlänge ändert. |
| Teilweise Herunterladen von Segmenten | Startet die Wiedergabe, sobald genügend Frames aus einem Segment verfügbar sind, um Videos auf Clientseite zuverlässig wiederzugeben. |
| Parallele Downloads | TVSDK lädt Audio- und Videosegmente parallel für demutierte Inhalte herunter, um die Wiedergabeleistung zu optimieren. |

Die Wiedergabefunktionen verbessern die Interaktion der Verbraucher, indem sie das Erlebnis von linearen Broadcasts auf digitalem Weg bieten. Außerdem können Sie damit natives DRM wie Widevine für die HD-Wiedergabe nutzen.

| Wiedergabefunktionen | Beschreibung |
|--- |--- |
| MP4-Wiedergabe | MP4-Kurzclips müssen nicht in die Wiedergabe in TVSDK neu transkodiert werden. |
| DASH-VOD-Inhaltswiedergabe | Es werden grundlegende Anwendungsfälle für die DASH-VOD-Wiedergabe unterstützt. |
| Glattes Trickplay mit ABR | Unterstützung für schnelle Vorwärts- und Rückspaltung in HLS mit Keyframes bei niedrigen Raten und I-Frames bei schnelleren Geschwindigkeiten. ABR-Unterstützung für alle unterstützten Frames. |

Die Funktionen sind wichtig, um die Einschränkungen des Studios, wie HD-Wiedergabe über natives DRM, zu erfüllen.

| Funktionen | Beschreibung |
|--- |--- |
| Auflösungsbasierter Output-Schutz | Die Wiedergabe kann auf bestimmte Auflösungen beschränkt werden, die von DRM-Anforderungen zulässig sind. Nur über Primetime DRM verfügbar. |
| Weitgehende Unterstützung | Unterstützt mit DASH-VOD-Streams zur Aktivierung nativer DRM-Anwendungsfälle. |

Dank der Verbesserung der direkten Rechnungsstellung müssen monatlich keine manuellen Berichte für die Rechnungsstellung erstellt werden. VHL 2.0 ermöglicht eine schnellere Markteinführungszeit mit einer Pre-Build-Integration und einer höheren Genauigkeit beim Tracking.

| Funktionen | Beschreibung |
|--- |--- |
| Mottenintegration | Unterstützung für die Anzeigensichtbarkeitsmessung von Moat. |
| VHL 2.0 | Die neueste optimierte Video Heartbeats-Bibliotheksintegration für die automatische Erfassung von Nutzungsdaten für Adobe Analytics. |
| Failover-Unterstützung | Es wurden zusätzliche Strategien implementiert, um die unterbrechungsfreie Wiedergabe trotz eines Fehlers von Host-Servern, Wiedergabelisten und Segmenten fortzusetzen. |
| Direkte Rechnungsintegration | Sendet Abrechnungsmetriken an das Adobe Analytics-Backend, das von Adobe Primetime für vom Kunden verwendete Streams zertifiziert wurde. |

>[!NOTE]
>
>Alle Funktionen von TVSDK v1.4 werden in v2.5 unterstützt, mit Ausnahme der Multi-CDN-Unterstützung.

## Übersicht über den Migrationsprozess {#overview-of-the-migration-process}

Die reibungslose Migration von TVSDK 1.4 zu 2.5 beinhaltet das Ändern in Version 2.5-Bibliotheken, das Neukompilieren und dann die Verwendung dieses Dokuments, um Probleme zu beheben, die auftreten.

TVSDK v1.4-Bibliotheken funktionieren nicht mit v2.5-Bibliotheken und sind nicht gleichzeitig mit diesen vorhanden. Sie müssen v2.5-Bibliotheken mit TVSDK 2.5 verwenden und Ihre Anwendungen und Integrationen migrieren, um auf TVSDK 2.5 zu aktualisieren. In diesem Dokument wird beschrieben, wie und was Sie im Anwendungscode ändern und Fehler während der Neukompilierung beheben können.

Die Datei &quot;psdk.jar&quot;verwendet Bibliotheken von Drittanbietern, um verschiedene Funktionen zu unterstützen. Um das Entfernen der Bibliotheken zu verhindern, fügen Sie Folgendes in die `proguard.cfg` Datei:

```java
# Adobe TVSDK keep classes
-keep class com.adobe.** { *; }
-keep class com.google.android.exoplayer.**
{ *; }
```

Im `build.gradle` -Datei, müssen Sie die kompilierte Direktive einschließen, um die TVSDK-basierten JAR-Dateien einzuschließen. Wenn Ihre App Adobe Video Analytics enthält, müssen Sie die Kompilierungsanweisung für die zusätzlichen JARs einbeziehen, die für die Adobe Video Analytics-Integration in die App erforderlich sind

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
| import com.adobe.ave.drm .DRMAcquireLicenseSettings | import com.adobe.mediacore.drm .DRMAcquireLicenseSettings; | Alle Klassennamen in der TVSDK 2.5-API beginnen mit dem com.adobe.mediacore-Präfix. Das ist nur ein Beispiel. |
| MediaPlayerException, IllegalStateException oder IllegalArgumentException | MediaPlayerException | In 2.5 generieren die APIs nur MediaPlayerException. |
| MediaPlayer.PlayerState (MediaPlayer.Event.PLAYBACK) | MediaPlayerStatus (MediaPlayerEvent.STATUS_CHANGED) | In Version 2.5 wurde MediaPlayer.PlayerState in einen separaten MediaPlayerStatus umbenannt. |
| DefaultMediaPlayer.create (getActivity().getApplicationContext()) | MediaPlayer mediaPlayer = new MediaPlayer(getActivity(). getApplicationContext()); | Die statischen Methoden zum Erstellen von Objekten werden durch öffentliche Konstruktoren ersetzt. |
| MediaPlayer.seekToLocalTime() | MediaPlayer.seekToLocal() | Die MediaPlayer.searchToLocalTime() -Methode heißt jetzt MediaPlayer.searchToLocal() . |
| closedCaptionsTrack.isActive() |  | Nicht verfügbar |
| MetadataNode | Metadaten | In v2.5 ersetzt die Metadatenklasse die Verwendung der Klasse v1.4 MetadataNode . |
| DefaultMetadataKeys | MetadataKeys | Die DefaultMetadataKeys von v1.4 befinden sich in v2.5 enum MetadataKeys. |
| AdvertisingFactory | ContentFactory | AdvertisingFactory von v1.4 wird in v2.5 in ContentFactory umbenannt. |
| PlacementOpportunityDetector | ChancenGenerator | Detektoren werden durch Generatoren ersetzt. |
| mediaPlayer.getView().notifyClick(); | mediaPlayer.notifyClick(); | Die Methode notifyClick() von MediaPlayerView wurde in die MediaPlayer-Klasse verschoben. |
| public ABRControlParameters(ABRPolicy abrPolicy, int nInitialBitRate, int nMinBitRate, int nMaxBitRate) | public ABRControlParameters(int nInitialBitRate, int MinBitRate, int nMaxBitRate, ABRPolicy abrPolicy, int MinTrickPlayBitRate, int nMaxTrickPlayBitRate, int nMaxTrickPlayBandwidthUsage, double dMaxPbit layoutRate) |  |
| playbackInformation.getTimeToFirstFrame() |  | Nicht verfügbar |
|  | playInformation.get PerceivedBandwidth() | TVSDK v2.5 QOSProvider verfügt über eine neue Eigenschaft, mit der die wahrgenommene Bandbreite während einer Streaming-Sitzung ermittelt wird. |

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

Die letzten sechs dieser Klassen sind als Dienstprogrammklassen in der Referenzimplementierung verfügbar.

## Namensänderungen {#namespace-changes}

Die TVSDK 2.5-API konsolidiert Namespaces.

Alle Klassennamen in der TVSDK 2.5-API beginnen mit dem com.adobe.mediacore-Präfix. Einige Klassennamen in der TVSDK 1.4-API beginnen mit com.adobe.ave. Die entsprechenden 2.5-Klassen ändern com.adobe.ave in com.adobe.mediacore. Beachten Sie beispielsweise die Änderungen in den folgenden Codezeilen für 1.4 und 2.5:

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

## Änderungen bei der Ereignisverarbeitung {#changes-in-event-handling}

Übergeben Sie zum Registrieren von Ereignissen in dieser Version den -Handler an `addEventListener`. Die Liste der Ereignisse wurde von Version 1.4 auf Version 2.5 überarbeitet.\
Hier erfahren Sie beispielsweise, wie Sie einen Ereignishandler für `MediaPlayerEvent.STATUS_CHANGED:`

```java
mPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,
new StatusChangeEventListener() {
@Override
public void onStatusChanged(MediaPlayerStatusChangeEvent event) {
//Handle status change event
}
});
```

So wurde das Ereignis in Version 1.4 registriert:

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

Die MediaPlayerEvent -Enumeration enthält alle Ereigniscodes. Die folgenden Ereigniscodes aus 1.4 sind in 2.5 nicht mehr vorhanden:

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

Die folgenden Ereigniscodes sind in Version 2.5 neu:

* `AD_RESOLUTION_COMPLETE`
* `BUFFER_PREPARED`
* `CAPTIONS_UPDATED`
* `MANIFEST_UPDATED`
* `PLAYBACK_RANGE_UPDATED`
* `RESERVATION_REACHED`
* `TIME_CHANGED`
* `TIMED_EVENT`
* `TIMED_METADATA_ADDED_IN_BACKGROUND`

### Umbenannte Ereignisse {#renamed-events}

| Neuer Name | Alter Name |
|--- |--- |
| SEEK_BEGIN | SEEK_STARTED |
| SEEK_END | SEEK_COMPLETED |
| SEEK_POSITION_ADJUSTED | SEEK_ADJUST_COMPLETED |
| PUFFERING_BEGIN | BUFFERING_STARTED |
| BUFFERING_END | BUFFERING_COMPLETED |
| AUDIO_TRACK_UPDATED | AUDIO_TRACK_CHANGED |
| STATUS_CHANGED | STATE_CHANGED |
| TIMED_METADATA_AVAILABLE | TIMED_METADATA_ADDED |
| SIZE_AVAILABLE | SIZE_CHANGED |
| LOAD_INFO | LOAD_INFORMATION_AVAILABLE |

## MediaPlayer-Änderungen {#mediaplayer-changes}

Eine neue Bauart `MediaPlayer` und Änderungen an einigen der Methoden.

**Änderungen an der MediaPlayer-Klasse**

Im Folgenden finden Sie die Änderungen an `MediaPlayer` -Klasse:

* Die `MediaPlayerStatus` enum ersetzt `MediaPlayer.PlayerState`. Beispiel:

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

* Die `MediaPlayer.seekToLocalTime()` -Methode heißt jetzt `MediaPlayer.seekToLocal`. Beispiel:

```java
//TVSDK v1.4
public void seekToLocal(long localPosition) { mediaPlayer.seekToLocalTime(localPosition);
}

//TVSDK v2.5
public void seekToLocal(long localPosition) { mediaPlayer.seekToLocal(localPosition);
}
```

* Die `MediaPlayerView.notifyClick()` -Methode ist jetzt `MediaPlayer.notifyClick()`. Beispiel:

```java
//TVSDK v1.4
public void adClick() { mediaPlayer.getView().notifyClick();
}

//TVSDK v2.5
public void adClick() { mediaPlayer.notifyClick();
}
```

* Das erste `MediaPlayer.MediaPlayer.getNotificationHistory()` -Methode ist nun beendet und nicht ersetzt.
* Das erste `MediaPlayer.replaceCurrentItem()` ist in zwei Methoden unterteilt: `replaceCurrentResource()`, das eine Instanz von `MediaResource`, und `replaceCurrentItem()`, das eine Instanz von `MediaPlayerItem`. Beispiel:

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

Sie können dies verwenden, um zwischen vorinitialisierten MediaPlayer-Instanzen zu wechseln, wie im Falle von Blackouts.

**Konstruktoren ersetzen statische create() -Methoden**

Sie können Konstruktoren in TVSDK v2.5 verwenden, anstatt `create()` -Methoden von TVSDK v1.4. Alle Klassen mit Namen, die mit &quot;Default&quot;beginnen, z. B. `DefaultMediaPlayer`, `DefaultNetworkConfig`, `DefaultContentFactory`, sind in Version 2.5 nicht verfügbar.

In einigen Fällen verwendet die TVSDK v1.4-API das folgende Muster zum Erstellen von Klassen:

1. Definieren einer Benutzeroberfläche (z. B. `MediaPlayer`).
1. Bereitstellung einer Standardklasse (z. B. `DefaultMediaPlayer`).
1. Stellen Sie eine `create()` -Methode für die Standardklasse verwenden, um eine Klasse bereitzustellen, die die -Schnittstelle implementiert.

In TVSDK v2.5 sind solche Schnittstellen konkrete Klassen und Sie erstellen Instanzen dieser Klassen mithilfe der entsprechenden Konstruktoren. Die folgenden Codefragmente veranschaulichen diesen Unterschied:

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

Andere Klassen, die diesem Muster nicht folgen, aber `create()` Zu den Methoden in 1.4 gehören:

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

Einige Klassen (zum Beispiel `ContentFactory`) sind abstrakte Klassen ohne öffentlich verfügbare Standardimplementierung (zum Beispiel `DefaultContentFactory`). In diesen Fällen können Sie eine Standardimplementierung über eine bequeme Funktion bereitstellen, z. B.: `mediaPlayerItemConfig.getDefaultContentFactory()`

**Änderungen bei Untertiteln**

Die folgenden Änderungen betreffen Klassen im Zusammenhang mit der Untertitelung:

* Beim Abrufen von Untertitelspuren, `MediaPlayerItem.getClosedCaptionTracks()` gibt nur aktive Tracks zurück.
* `ClosedCaptionTrack` enthält nicht mehr `isActive()` -Methode.

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

## Werbeinterstellungsänderungen {#advertising-changes}

Es gibt mehrere anzeigenbezogene Änderungen in Version 2.5.

**Änderungen am Werbeverhalten**

Das Standardverhalten der Anzeigenwiedergabe, wenn ein Benutzer eine Suche über einen Anzeigen-Pod hinaus durchführt, ändert sich in Version 2.5 geringfügig. Wenn die Werbeunterbrechung nicht überwacht wird, wird die Anzeige nach einer Suche nach vorne wiedergegeben. Wenn die App die standardmäßige Anzeigenrichtlinie verwendet, wird die Werbeunterbrechung nach Abschluss der Wiedergabe entfernt. Wenn ein Benutzer mit TVSDK v2.5 hinter einem Anzeigen-Pod in der Timeline sucht und die Werbeunterbrechung nicht überwacht wird, wird keine Anzeige wiedergegeben.

In TVSDK v1.4 wird jedoch standardmäßig eine Anzeige wiedergegeben, falls eine Suche rückwärts erfolgt. Wenn Sie beispielsweise zwischen der dritten und vierten Werbeunterbrechung nach hinten suchen, wird TVSDK v1.4 standardmäßig dazu verwendet, die dritte Werbeunterbrechung wiederzugeben.

**Änderung von Anzeigenregeln**

Die Anzeigenregeln werden mithilfe einer JSON-Datei angegeben. Das Format der JSON-Datei bleibt in beiden Versionen des TVSDK unverändert. In TVSDK v2.5 muss die JSON-Datei mit den Anzeigenregeln jedoch an einem Speicherort gehostet werden, auf den über eine HTTP-URL zugegriffen werden kann. Die Anwendung kann eine Instanz von AuditudeSettings verwenden.

```java
//TVSDK v2.5
AuditudeSettings result = new AuditudeSettings(); result.setCRSRulesJsonURL(<http url of AdobeTVSDKConfig.json>);
```

In TVSDK-Version 1.4 wird diese Datei unter dem Ordner &quot;assets&quot;in der Anwendung abgelegt und TVSDK lädt die Datei.

**Umbenennung von Anzeigenwerkzeugen**

`AdvertisingFactory` heißt jetzt `ContentFactory`. Mit `ContentFactory` Sie können benutzerdefinierte Werbe-Workflows erstellen, indem Sie einige ihrer Methoden überschreiben. Verwenden Sie &quot;return null&quot;, um das Standardverhalten beizubehalten, wie im folgenden Beispiel:

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

**Werbeunterbrechungen mit Nulllänge**

TVSDK 2.5 fügt keine Werbeunterbrechungen als Platzhalter ein, wenn der Werbeserver keine Anzeigen zurückgibt.

Die Werbeunterbrechungen mit null Länge können ermittelt werden, indem die Anzahl der Anzeigen, die in der Werbeunterbrechung null sein sollen, mithilfe des onAdBreakStarted -Ereignisses ermittelt wird und die Anwendung diese Werbeunterbrechungen entsprechend handhaben muss.

**Metadatenänderungen**

Die Metadaten-Klasse bietet einen leistungsfähigeren Ersatz für die frühere MetadataNode-Klasse.

* Die Metadatenklasse kann Zeichenfolgen, Byte-Arrays und andere Metadatenobjekte speichern:

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

* Die `MetadataKeys` enum ersetzt `DefaultMetadataKeys`. Nicht alle Schlüssel in `DefaultMetadataKeys` in der neuen Version vorhanden sind.

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

* Advertising-Metadaten werden jetzt durch die `AdvertisingMetadata` -Klasse, eine Unterklasse von Metadaten, und wird jetzt in gespeichert. `MediaPlayerItemConfig` anstelle von `MediaResource`.

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

Metadaten für die Netzwerkkonfiguration, ehemals Mitglied der `MediaResource` -Klasse wird nun durch die `NetworkConfiguration` -Klasse und wird jetzt in gespeichert. `MediaPlayerItemConfig` anstelle von `MediaResource`.

```java
//TVSDK v1.4
MediaResource playerResource = MediaResource.createFromUrl(url, mediaMetadata);
...

//TVSDK v2.5
MediaPlayerItemConfig mediaItemConfig = new MediaPlayerItemConfig(context);

NetworkConfiguration mediaNetworkConfiguration = mediaItemConfig.getNetworkConfiguration();
```

**Änderungen an der TimedMetadata-Analyse**

Die Analyse von `TimedMetadata` hat sich in Version 2.5 in Bezug auf die Datentypen zum Analysieren des ID3-Tags geändert.

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

**Sonstige Änderungen**

Die folgenden zusätzlichen Änderungen sind in Version 2.5 verfügbar:

* Die `notifyClick()` -Methode von `MediaPlayerView` nach `MediaPlayer`.

* `AdPolicySelector` ist eine Schnittstelle, keine Klasse. Implementieren Sie alle zugehörigen Methoden.
* `AdPolicyInfo` enthält jetzt eine Liste von `AdBreakTimelineItem`, nicht `AdBreakPlacement`.

* API-Name von `ContentResolver` abstrakte Klasse geändert wird.
* `PlacementOpportunityDetector` nicht mehr verfügbar ist. Erweitern Sie stattdessen die `OpportunityGenerator` abstrakte Klasse. Die Referenzimplementierung bietet ein Beispiel dafür.

* Die Parameter der `AdBreakPlacement` -Konstruktor sind identisch, aber in einer anderen Reihenfolge. Eine Beispielimplementierung finden Sie in der im Lieferumfang des Produkts enthaltenen Referenz-Player-Implementierung.

## Veränderungen in DRM {#changes-in-drm}

Die meisten Änderungen in dieser Version befinden sich in der DRM-Schicht. Die folgende Tabelle zeigt zusätzliche Änderungen zwischen den Versionen 1.4 und 2.5:

| DRMManager-Methode | Erfolgsrückruf in 1.4 | Fehler-Callback in 1.4 | Listener in 2.5 |
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

Das statische `DRMManager` -Instanz, die in 1.4 nach der Erstellung von mediaplayer verfügbar war, ist jetzt verfügbar, nachdem `onDRMMetadataInfo` Ereignis-Listener wird ausgelöst.

## Adaptive Bitrate (ABR)-bezogene Änderungen {#adaptive-bitrate-abr-related-changes}

**Änderungen in Konstanten**

Viele Konstanten haben den Typ von `String` nach `int`. Beispiel: `MediaResourceType`, `ABRControlParameters`, und `MediaPlayerStatusChangeEvent`.

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

Einige Parameter wurden hinzugefügt, einige wurden umbenannt und andere verschoben. Im Folgenden finden Sie die Konstruktorsignatur in v1.4 und die neue Signatur in 2.5:

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

## Fehlerereignisse und Umgang {#error-events-and-handling}

**Änderungen bei der Fehlerbehandlung**

Die `MediaError` -Klasse durch die `Notification` -Klasse. Der einzige Unterschied zwischen den Klassen `MediaError` und `Notification` ist, dass letztere kein Beschreibungsattribut enthält. Die TVSDK 1.4-Fehlercodes mit den Werten 101xxx, 102xxx,104xxx,106xxx,107xxx,109xxx sind in TVSDK 2.5 nicht vorhanden. Die Wiedergabe-Codes in TVSDK 2.5 finden Sie unter [Nativer Fehler - Werte für die Videowiedergabe](assets/psdk_android_2.5.pdf).

Im Folgenden finden Sie Beispiele für die Fehlerbehandlung in TVSDK 1.4 und 2.5:

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

Alle wiederherstellbaren Fehler werden als Warnhinweise behandelt und mithilfe der Variablen `NotificationEventListener` in TVSDK 2.5. Die Warnungen werden als Benachrichtigungen mit dem `onOperationFailed` Listener im QOS-Handler in TVSDK 1.4, wobei wie in TVSDK 2.5 die Benachrichtigung ein separates Ereignis ist. Die in den Abschnitten 1.4 und 2.5 behandelte Warnung lautet wie folgt:

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

Während TVSDK v1.4 eine Kombination aus Nullen, Fehlerrückgaben und verschiedenen Ausnahmen ( `MediaPlayerException`, `IllegalStateException`, und `IllegalArgumentException`), TVSDK v2.5 `generatesMediaPlayerException` für alle Fehler.

>[!NOTE]
>
>Um Details zu einer MediaPlayerException abzurufen, können Sie `getErrorCode()`.

Nachfolgend finden Sie ein Beispiel für die Änderung:

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

Es gibt geringfügige Änderungen an den QOSProvider-Objekteigenschaften:

* Die `TimeToFirstFrame` ist nicht in TVSDK 2.5 verfügbar.
* TVSDK 2.5 QOSProvider verfügt über eine neue Eigenschaft, mit der die wahrgenommene Bandbreite während einer Streaming-Sitzung ermittelt wird.

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

* Die `QOSEventListener::onOperationFailed()` ist in TVSDK 2.5 nicht mehr vorhanden. Die Warnungen, die früher in diesem Ereignis-Listener angezeigt wurden, werden jetzt im `NotificationEventListener::onNotification()` Ereignis-Listener.

* Die `QOSProvider event listeners onBufferStart()`, `onBufferComplete()`, `onSeekStart()`, `onSeekComplete()`, und `onLoadInfo()` sind einzelne Ereignis-Listener, die mit einer mediaPlayer-Instanz verbunden sind.

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

* Siehe vollständige Hilfedokumentation unter [Adobe Primetime - Lernen und Support](https://helpx.adobe.com/support/primetime.html) Seite.
