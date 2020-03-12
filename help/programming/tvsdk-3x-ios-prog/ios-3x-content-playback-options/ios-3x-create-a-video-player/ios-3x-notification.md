---
description: Der Player kann auf eine Reihe von Ereignissen hören, die den Status des Players angeben.
seo-description: Der Player kann auf eine Reihe von Ereignissen hören, die den Status des Players angeben.
seo-title: Benachrichtigungen einrichten
title: Benachrichtigungen einrichten
uuid: b178b2eb-da40-456b-997a-46ae18d635fa
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Benachrichtigungen einrichten {#set-up-notifications}

Der Player kann auf eine Reihe von Ereignissen hören, die den Status des Players angeben.

Wenn dies eine Eigenschaft des Client-Players `PTMediaPlayer` ist, stellt `self.player` das folgende Beispiel die `PTMediaPlayer` Instanz dar. Im folgenden Beispiel wird die in den PTMediaPlayer-Setupanweisungen dargestellte `addObservers` Methode implementiert und enthält die meisten Benachrichtigungen:

```
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerStatusChange:)  
      name:PTMediaPlayerStatusNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
      name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerTimeChange:)  
      name:PTMediaPlayerTimeChangeNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerItemPlayStarted:)  
      name:PTMediaPlayerPlayStartedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerItemPlayCompleted:)  
      name:PTMediaPlayerPlayCompletedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerItemTimelineChanged:)  
      name:PTMediaPlayerTimelineChangedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
      name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdBreakStarted:)  
      name:PTMediaPlayerAdBreakStartedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdBreakCompleted:)  
      name:PTMediaPlayerAdBreakCompletedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdPlayStarted:)  
      name:PTMediaPlayerAdStartedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdPlayProgress:)  
      name:PTMediaPlayerAdProgressNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdPlayCompleted:)  
      name:PTMediaPlayerAdCompletedNotification object:self.player]; 
```

## iOS-Benachrichtigungen {#section_65D9B2DBF5574313BD3218AB02242BBB}

`ThePTMediaPlayerNotifications` -Klasse die Benachrichtigungen Liste, die das TVSDK an Ihren Player sendet.

<table frame="all" colsep="1" rowsep="1" id="table_ios_notifications"> 
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Benachrichtigung</b> </td> 
   <td colname="2"> <b>Bedeutung</b> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdBreakCompletedNotification </span> </td> 
   <td colname="2"> Eine Werbeunterbrechung endete. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdBreakStartedNotification </span> </td> 
   <td colname="2"> Eine Werbeunterbrechung begann. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdClickNotification </span> </td> 
   <td colname="2"> Ein Benutzer klickte auf eine Banneranzeige. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdCompletedNotification </span> </td> 
   <td colname="2"> Eine einzelne Anzeige endete. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdProgressNotification </span> </td> 
   <td colname="2"> eine Anzeige fortgeführt wird; wird während der Wiedergabe einer Anzeige ständig abgesetzt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdStartedNotification </span> </td> 
   <td colname="2"> Eine einzelne Anzeige begann. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTBackgroundManifestErrorNotification </span> </td> 
   <td colname="2"> Das Herunterladen des Hintergrundmanifests ist fehlgeschlagen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerBufferingCompletedNotification </span> </td> 
   <td colname="2"> Die Pufferung ist abgeschlossen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerBufferingStartedNotification </span> </td> 
   <td colname="2"> Der Medienplayer wechselt in den Status "Pufferung". </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTAudioTrackChangeCompleted </span> </td> 
   <td colname="2"> Eine Änderung der Audiospur des derzeit wiedergegebenen Mediums ist abgeschlossen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTAudioTrackChangeStarted </span> </td> 
   <td colname="2"> Eine Änderung der Audiospur des derzeit wiedergegebenen Mediums wird eingeleitet. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerItemChangedNotification </span> </td> 
   <td colname="2"> Ein anderes <span class="codeph"> PTMediaPlayerItem </span> des <span class="codeph"> PTMediaPlayer </span> wurde eingestellt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerItemDRMMetadataChanged </span> </td> 
   <td colname="2"> Die DRM-Metadaten wurden geändert. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerMediaSelectionOptionsAvailableNotification </span> </td> 
   <td colname="2"> Es gibt neue Untertitel und alternative Audiospuren ( <span class="codeph"> PTMediaSelectionOption </span>). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerNewNotificationEntryAddedNotification </span> </td> 
   <td colname="2"> Eine neue <span class="codeph"> PTNotification </span> wurde dem <span class="codeph"> PTNotificationHistoryItem </span> des aktuellen <span class="codeph"> </span>PTMediaPlayerItem hinzugefügt, das heißt, wenn ein Benachrichtigungs-Ereignis zum Benachrichtigungsverlauf hinzugefügt wird. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerPlayCompletedNotification </span> </td> 
   <td colname="2"> Medienwiedergabe endete. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerSeekCompletedNotification </span> </td> 
   <td colname="2"> Die Suche ist abgeschlossen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerSeekErrorNotification </span> </td> 
   <td colname="2"> Der aktuelle Suchvorgang ist fehlgeschlagen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerSeekStartedNotification </span> </td> 
   <td colname="2"> Die Suche fängt an. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerPlayStartedNotification </span> </td> 
   <td colname="2"> Die Wiedergabe wurde gestartet. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerStatusNotification </span> </td> 
   <td colname="2"> Der Player-Status wurde geändert. Mögliche Statuswerte sind: 
    <ul id="ul_DDBE8CAD5D5A46D2AAA6B98F0754A881"> 
     <li id="li_48F9AD580BCB4BB8A5C2DFED0DF9970F"> <p> <span class="codeph"> PTMediaPlayerStatusCreated </span> </p> </li> 
     <li id="li_EDFB0765CF14422A95C9119DA3394163"> <p> <span class="codeph"> PTMediaPlayerStatusInitializing </span> </p> </li> 
     <li id="li_06E1576D50C646C19E88F0F14912F2C0"> <p> <span class="codeph"> PTMediaPlayerStatusInitialized </span> </p> </li> 
     <li id="li_E8B7157B5B234DFFABC2E5BEC241AB84"> <p> <span class="codeph"> PTMediaPlayerStatusReady </span> </p> </li> 
     <li id="li_FF2E66B390154EAA8791B4D874CC62E1"> <p> <span class="codeph"> PTMediaPlayerStatusPlaying </span> </p> </li> 
     <li id="li_6F3306832B7642E4BEE84068383AFAF3"> <p> <span class="codeph"> PTMediaPlayerStatusPaused </span> </p> </li> 
     <li id="li_AE579AB888954F89A7F1115CAC0655E6"> <p> <span class="codeph"> PTMediaPlayerStatusStopped </span> </p> </li> 
     <li id="li_A4CEB39374E84B4AA4F7202E67B9BE43"> <p> <span class="codeph"> PTMediaPlayerStatusCompleted </span> </p> </li> 
     <li id="li_C50EB9C459264641A9FF70EF901D7474"> <p> <span class="codeph"> PTMediaPlayerStatusError </span> </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerTimeChangeNotification </span> </td> 
   <td colname="2"> Die aktuelle Wiedergabedauer wurde geändert. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerTimelineChangedNotification </span> </td> 
   <td colname="2"> Die Zeitleiste des aktuellen Players wurde geändert. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" colsep="1" rowsep="1"> <span class="codeph"> PTTimedMetadataChangedNotification </span> </td> 
   <td colname="2"> Das TVSDK hat das erste Vorkommen eines abonnierten Tags festgestellt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTTimedMetadataChangedInBackgroundNotification </span> </td> 
   <td colname="2"> <p>Ein abonniertes Tag wird im Hintergrundmanifest identifiziert und es wird eine neue <span class="codeph"> PTTimedMetadata- </span> Instanz vorbereitet. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Beispiel-Handler für Benachrichtigungen {#section_D729C2403A234DD09596829D26882ADC}

Die folgenden Codebeispiele illustrieren einige Möglichkeiten zur Verwendung von Benachrichtigungen.

Rufen Sie die `PTAdBreak` Instanz mit `PTMediaPlayerAdBreakKey`:

```
 - (void) onMediaPlayerAdBreakStarted:(NSNotification *) notification { 
   // Fetch the PTAdBreak instance using PTMediaPlayerAdBreakKey 
   PTAdBreak *adBreak = [notification.userInfo objectForKey:PTMediaPlayerAdBreakKey]; 
   ... 
   ... 
} 
```

Festlegen `subtitlesOptions` und `audioOptions`:

```
 - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification \*) notification { 
   //SubtitlesOptions and audioOptions are set and accessible now. 
   NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions;  
   NSArray* audioOp tions = self.player.currentItem.audioOptions; 
   ... 
   ... 
} 
```

Rufen Sie die `PTAd` Instanz mit `PTMediaPlayerAdKey`:

```
 - (void) onMediaPlayerAdPlayStarted:(NSNotification \*)  notification { 
   // Fetch the PTAdinstance using PTMediaPlayerAdKey 
   PTAd *ad = [notification.userInfo objectForKey:PTMediaPlayerAdKey]; 
   ... 
   ... 
} 
```
