---
description: Wenn die Wiedergabe eine Werbeunterbrechung erreicht, eine Werbeunterbrechung durchläuft oder in einer Werbeunterbrechung endet, definiert TVSDK ein Standardverhalten für die Positionierung der aktuellen Abspielleiste.
seo-description: Wenn die Wiedergabe eine Werbeunterbrechung erreicht, eine Werbeunterbrechung durchläuft oder in einer Werbeunterbrechung endet, definiert TVSDK ein Standardverhalten für die Positionierung der aktuellen Abspielleiste.
seo-title: Wiedergabe mit Anzeigen anpassen
title: Wiedergabe mit Anzeigen anpassen
uuid: 58002ec2-65ab-4e3b-8e3b-f755ced5cb5a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Wiedergabe mit Anzeigen anpassen{#customize-playback-with-ads}

Wenn die Wiedergabe eine Werbeunterbrechung erreicht, eine Werbeunterbrechung durchläuft oder in einer Werbeunterbrechung endet, definiert TVSDK ein Standardverhalten für die Positionierung der aktuellen Abspielleiste.

>[!TIP]
>
>Sie können das Standardverhalten mithilfe der `PTAdPolicySelector` Klasse außer Kraft setzen.

Das Standardverhalten variiert je nachdem, ob der Benutzer die Werbeunterbrechung während der normalen Wiedergabe oder bei der Suche in einem Video durchläuft.

Sie können das Verhalten der Anzeigenwiedergabe wie folgt anpassen:

* Speichern Sie die Position, an der der Benutzer das Video nicht mehr ansah, und nehmen Sie die Wiedergabe an derselben Position in einer zukünftigen Sitzung wieder auf.
* Wenn dem Benutzer eine Werbeunterbrechung angezeigt wird, zeigen Sie für einige Minuten keine zusätzlichen Anzeigen an, selbst wenn der Benutzer nach einer neuen Position sucht.
* Wenn der Inhalt nach einigen Minuten nicht wiedergegeben werden kann, starten Sie den Stream neu oder wechseln Sie zu einer anderen Quelle für denselben Inhalt.

   Um dem Benutzer zu ermöglichen, Anzeigen zu überspringen und zur vorherigen fehlgeschlagenen Position zurückzukehren, können Sie während der Wiedergabesitzung Pre-Roll- und/oder Mid-Roll-Anzeigen deaktivieren. TVSDK bietet Methoden, um das Überspringen von Pre-Roll- und Mid-Roll-Anzeigen zu aktivieren.

## API-Elemente für die Anzeigenwiedergabe {#section_296ADE00CFEA40CBA1B46142720D13A5}

TVSDK bietet Klassen und Methoden, mit denen Sie das Wiedergabeverhalten von Inhalten, die Werbung enthalten, anpassen können.
Die folgenden API-Elemente eignen sich zum Anpassen der Wiedergabe:

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API-Element </th> 
   <th colname="col2" class="entry"> Inhalte, die Werbung unterstützen </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdMetadata </span> </td> 
   <td colname="col2"> Legen Sie fest, ob eine Werbeunterbrechung als von einem Viewer gesehen gekennzeichnet werden soll, und wann, wenn ja, wann sie markiert werden soll. Legen Sie die überwachte Richtlinie mit der <span class="codeph"> Eigenschaft adBreakAsWatched </span> fest und rufen Sie sie ab. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdPolicySelector </span> </td> 
   <td colname="col2"> Protokoll, das die Anpassung des TVSDK-Anzeigenverhaltens ermöglicht. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTDefaultAdPolicySelector </span> </td> 
   <td colname="col2"> Klasse, die das standardmäßige TVSDK-Verhalten implementiert. Ihre Anwendung kann diese Klasse außer Kraft setzen, um das Standardverhalten anzupassen, ohne die vollständige Schnittstelle zu implementieren. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTMediaPlayer </span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"> <span class="codeph"> localTime </span>. <p>Dies ist die lokale Zeit der Wiedergabe, wobei die platzierten Werbeunterbrechungen ausgeschlossen werden. </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"> <span class="codeph"> searchToLocalTime </span> . <p>Hier erfolgt die Suche relativ zu einer lokalen Zeit im Stream. </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"> <span class="codeph"> getTimeline.convertToLocalTime </span>. <p>Die virtuelle Position auf der Zeitleiste wird in die lokale Position umgewandelt. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdBreak </span> </td> 
   <td colname="col2"> <span class="codeph"> isWatched- </span> Eigenschaft. Gibt an, ob der Viewer die Anzeige gesehen hat. </td> 
  </tr> 
 </tbody> 
</table>

## Einrichten der benutzerdefinierten Wiedergabe {#section_8209BAACC7814C9399988DC7DE9CF4CA}

Bevor Sie Anzeigenrichtlinien-Instanzen anpassen oder außer Kraft setzen können, registrieren Sie sie bei TVSDK.

Führen Sie zum Anpassen des Anzeigenverhaltens einen der folgenden Schritte aus:

* Erfüllen Sie das `PTAdPolicySelector` Protokoll und implementieren Sie alle erforderlichen Methoden zur Richtlinienauswahl.

   Diese Option wird empfohlen, wenn Sie **alle** standardmäßigen Werbeverhaltensweisen außer Kraft setzen müssen.

* Überschreiben Sie die `PTDefaultAdPolicySelector` Klasse und stellen Sie Implementierungen nur für Verhalten bereit, die angepasst werden müssen.

   Diese Option wird empfohlen, wenn Sie nur **einige** der Standardverhaltensweisen außer Kraft setzen müssen.

Führen Sie für beide Optionen die folgenden Aufgaben aus:

1. Registrieren Sie die Richtlinieninstanz, die von TVSDK über die Client-Factory verwendet werden soll.

   >[!NOTE]
   >
   >Benutzerdefinierte Anzeigenrichtlinien, die zu Beginn der Wiedergabe registriert werden, werden gelöscht, wenn die `PTMediaPlayer` Instanz dezugeordnet wird. Ihre Anwendung muss jedes Mal, wenn eine neue Wiedergabesitzung erstellt wird, eine Richtliniensatzinstanz registrieren.

   Beispiel:

   ```
   // Create an instance of the custom policy selector 
   PTS5MinuteSkipBreakPolicySelector *adPolicySelector  
        = [[[PTS5MinuteSkipBreakPolicySelector alloc] initWithMediaPlayer:self.player] autorelease]; 
   
   // register this instance 
   [[PTDefaultMediaPlayerClientFactory defaultFactory] registerAdPolicySelector:adPolicySelector];
   ```

1. Implementieren Sie Ihre Anpassungen.

## Werbeunterbrechungen für einen Zeitraum überspringen {#section_99809BE4D9BB4DEEBBF596C746CA428A}

Standardmäßig erzwingt TVSDK die Wiedergabe einer Werbeunterbrechung, wenn der Benutzer über eine Werbeunterbrechung sucht. Sie können das Verhalten anpassen, um einen Werbeunterbrechung zu überspringen, wenn der Zeitraum, der nach dem Abschluss eines vorherigen Umbruchs abgelaufen ist, innerhalb einer bestimmten Anzahl von Minuten liegt.

>[!IMPORTANT]
>
>Bei einer internen Suche, eine Anzeige zu überspringen, kann es zu einer leichten Pause bei der Wiedergabe kommen.

Im folgenden Beispiel einer benutzerdefinierten Anzeigenrichtlinienauswahl werden Anzeigen in den nächsten fünf Minuten (Pinnwandzeit) übersprungen, nachdem ein Benutzer eine Werbeunterbrechung gesehen hat.

1. Registrieren Sie die Richtlinieninstanz, die von TVSDK über die Client-Factory verwendet werden soll.

   ```
   // Create an instance of the custom policy selector 
   PTS5MinuteSkipBreakPolicySelector *adPolicySelector  
        = [[[PTS5MinuteSkipBreakPolicySelector alloc] initWithMediaPlayer:self.player] autorelease]; 
   
   // register this instance 
   [[PTDefaultMediaPlayerClientFactory defaultFactory] registerAdPolicySelector:adPolicySelector];
   ```

1. Implementieren Sie Ihre Anpassung.

**PTS5MinuteSkipBreakPolicySelector.h**

```
#import "PTMediaPlayerNotifications.h" 
#import "PTMediaPlayer.h" 
#import "PTDefaultAdPolicySelector.h" 
 
//  extend the default policy  
selector@interface PTS5MinuteSkipBreakPolicySelector : PTDefaultAdPolicySelector 
  
- (id)initWithMediaPlayer:(PTMediaPlayer *)player; 
  
@end
```

**PTS5MinuteSkipBreakPolicySelector.m**

```
#import "PTS5MinuteSkipBreakPolicySelector.h" 
  
double MIN_BREAK_INTERVAL  = 60 * 5; // 5 minutes 
  
@implementation PTS5MinuteSkipBreakPolicySelector 
{ 
    PTMediaPlayer *_player; 
    NSTimeInterval _lastAdBreakPlayedTime; 
} 
  
- (id)initWithMediaPlayer:(PTMediaPlayer *)player 
{ 
    if (self = [super init]) 
    { 
        _lastAdBreakPlayedTime = 0; 
        _player = [player retain]; 
        [self addobservers]; 
    } 
    
    return self; 
} 
  
- (NSArray *)selectAdBreaksToPlay:(PTAdPolicyInfo *)info 
{ 
    NSLog(@"%@ - selectAdBreaksToPlay (%f): %f", self,  
        CMTimeGetSeconds(info.currentTime), _lastAdBreakPlayedTime); 
    
    BOOL shouldPlay = [self shouldPlayAdBreaks]; 
    if (shouldPlay) 
    { 
        return [super selectAdBreaksToPlay:info]; 
    } 
    
    return nil; 
} 
  
- (PTAdBreakPolicyType)selectPolicyForAdBreak:(PTAdPolicyInfo *)info 
{ 
    NSLog(@"%@ - selectPolicyForAdBreak (%f): %f  %f", self,  
            CMTimeGetSeconds(info.currentTime), _lastAdBreakPlayedTime,  
            [[NSDate date] timeIntervalSince1970]); 
    
    BOOL shouldPlay = [self shouldPlayAdBreaks]; 
    if (shouldPlay) 
    { 
        return [super selectPolicyForAdBreak:info]; 
    } 
    
    return PTAdBreakPolicyTypeSkip; 
} 
  
- (BOOL)shouldPlayAdBreaks 
{ 
    NSTimeInterval currentTime = [[NSDate date] timeIntervalSince1970]; 
    if (_lastAdBreakPlayedTime <= 0) 
    { 
        return YES; 
    } 
    
    if (_lastAdBreakPlayedTime > 0 && (currentTime - _lastAdBreakPlayedTime) > MIN_BREAK_INTERVAL) 
    { 
        return YES; 
    } 
    
    // don't play any ad break if 5 minutes hasn't elapsed 
    return NO; 
} 
  
- (void) onMediaPlayerAdBreakStarted:(NSNotification *) notification 
{ 
    NSLog(@"%@ - AdBreak Start", self); 
} 
  
- (void) onMediaPlayerAdBreakCompleted:(NSNotification *) notification 
{ 
    _lastAdBreakPlayedTime = [[NSDate date] timeIntervalSince1970]; 
    NSLog(@"%@ - AdBreak Complete at: %f", self, _lastAdBreakPlayedTime); 
} 
  
- (void)addobservers 
{ 
    [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdBreakStarted:)  
                name:PTMediaPlayerAdBreakStartedNotification object:_player]; 
    [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdBreakCompleted:)  
                name:PTMediaPlayerAdBreakCompletedNotification object:_player]; 
} 
  
- (void)removeObservers 
{ 
    [[NSNotificationCenter defaultCenter] removeObserver:self]; 
} 
  
- (void)dealloc 
{ 
    [self removeObservers]; 
    [_player release]; 
    [super dealloc]; 
} 
  
@end
```

## Speichern Sie die Videoposition und nehmen Sie den Vorgang später wieder auf {#section_FAE252E38CED48D4BDD38BAA4A6A20A4}

Sie können die aktuelle Wiedergabeposition in einem Video speichern und die Wiedergabe an derselben Position in einer zukünftigen Sitzung fortsetzen.

Dynamisch eingefügte Anzeigen unterscheiden sich zwischen Benutzersitzungen. Daher bezieht sich das Speichern der Position **mit** geteilten Anzeigen auf eine andere Position in einer zukünftigen Sitzung. TVSDK stellt Methoden zum Abrufen der Wiedergabeposition bereit, während geteilte Anzeigen ignoriert werden.

1. Wenn der Benutzer ein Video beendet, ruft Ihre Anwendung die Position im Video ab und speichert sie.

   >[!TIP]
   >
   >Die Anzeigendauer ist nicht inbegriffen.

   Werbeunterbrechungen können je nach Sitzung unterschiedlich ausfallen, da Anzeigenmuster, Frequenzbegrenzungen usw. gelten. Die aktuelle Zeit des Videos in einer Sitzung kann in einer zukünftigen Sitzung anders sein. Beim Speichern einer Position im Video ruft die Anwendung die Ortszeit ab. Verwenden Sie die `localTime` Eigenschaft, um diese Position zu lesen, die Sie auf dem Gerät oder in einer Datenbank auf dem Server speichern können.

   Wenn sich der Benutzer z. B. zur 20. Minute des Videos befindet und diese Position fünf Minuten Anzeigen umfasst, `currentTime` beträgt sie 1200 Sekunden, während `localTime` an dieser Position 900 Sekunden betragen.

   >[!IMPORTANT]
   >
   >Die lokale Zeit und die aktuelle Zeit sind für Live-/lineare Streams identisch. In diesem Fall hat `convertToLocalTime` keine Wirkung. Bei VOD bleibt die Ortszeit unverändert, während Anzeigen abgespielt werden.

   ```
   - (void) onMediaPlayerTimeChange:(NSNotification *)notification { 
       CMTimeRange seekableRange = self.player.seekableRange; 
   
       if (CMTIMERANGE_IS_VALID(seekableRange)) { 
           double seekableRangeStart = CMTimeGetSeconds(seekableRange.start); 
           double seekableRangeDuration = CMTimeGetSeconds(seekableRange.duration); 
           double currentTime = CMTimeGetSeconds(self.player.currentTime); // includes ads 
           double localTime = CMTimeGetSeconds(self.player.localTime); // no ads 
       } 
   }
   ```

1. So setzen Sie das Video an derselben Position fort: Um das Video von der Position wiederzugeben, die in einer vorherigen Sitzung gespeichert wurde, verwenden Sie `seekToLocalTime`

   >[!TIP]
   >
   >Diese Methode wird nur mit lokalen Zeitwerten aufgerufen. Wenn die Methode mit den aktuellen Zeitergebnissen aufgerufen wird, tritt ein falsches Verhalten auf.

   Verwenden Sie zum Suchen nach der aktuellen Zeit `seekToTime`.

1. Wenn Ihre Anwendung das Ereignis zur Änderung des `PTMediaPlayerStatusReady` Status erhält, suchen Sie nach der gespeicherten Ortszeit.

   ```
   [self.player seekToLocalTime:CMTimeMake(900, 1) completionHandler:^(BOOL finished) { 
       [self.player play]; 
   }];
   ```

1. Stellen Sie die Werbeunterbrechungen gemäß den Angaben in der Benutzeroberfläche der Anzeigenrichtlinie bereit.
1. Implementieren Sie eine benutzerdefinierte Anzeigenrichtlinienauswahl, indem Sie die standardmäßige Anzeigenrichtlinien-Auswahl erweitern.
1. Stellen Sie die Werbeunterbrechungen bereit, die dem Benutzer durch Implementierung von `selectAdBreaksToPlay`

   >[!NOTE]
   >
   >Diese Methode umfasst eine Pre-Roll-Werbeunterbrechung und die Mid-Roll-Werbeunterbrechungen vor der lokalen Zeitposition. Ihre Anwendung kann beschließen, eine Pre-Roll-Werbeunterbrechung auszuführen und zur angegebenen Ortszeit wiederaufzunehmen, eine Mid-Roll-Werbeunterbrechung abzuspielen und zur angegebenen Ortszeit fortzufahren oder keine Werbeunterbrechungen wiederzugeben.

