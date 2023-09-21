---
description: Wenn die Wiedergabe eine Werbeunterbrechung erreicht, eine Werbeunterbrechung durchläuft oder in einer Werbeunterbrechung endet, definiert TVSDK ein Standardverhalten für die Positionierung der aktuellen Abspielleiste.
title: Wiedergabe mit Anzeigen anpassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---

# Wiedergabe mit Anzeigen anpassen {#customize-playback-with-ads}

Wenn die Wiedergabe eine Werbeunterbrechung erreicht, eine Werbeunterbrechung durchläuft oder in einer Werbeunterbrechung endet, definiert TVSDK ein Standardverhalten für die Positionierung der aktuellen Abspielleiste.

>[!TIP]
>
>Sie können das Standardverhalten überschreiben, indem Sie die `PTAdPolicySelector` -Klasse.

Das Standardverhalten variiert je nachdem, ob der Benutzer die Werbeunterbrechung während der normalen Wiedergabe oder durch die Suche in einem Video übergibt.

Sie können das Verhalten der Anzeigenwiedergabe wie folgt anpassen:

* Speichern Sie die Position, an der der Benutzer das Video angehalten und die Wiedergabe an derselben Position in einer zukünftigen Sitzung fortgesetzt hat.
* Wenn dem Benutzer eine Werbeunterbrechung angezeigt wird, zeigen Sie für eine Anzahl von Minuten keine zusätzlichen Anzeigen an, selbst wenn der Benutzer zu einer neuen Position springt.
* Wenn die Wiedergabe des Inhalts nach einigen Minuten fehlschlägt, starten Sie den Stream neu oder wechseln Sie für denselben Inhalt zu einer anderen Quelle.

  In der Failover-Wiedergabesitzung können Sie Pre-Roll- und/oder Mid-Roll-Anzeigen deaktivieren, damit der Benutzer Anzeigen überspringen und zur vorherigen fehlgeschlagenen Position zurückkehren kann. TVSDK bietet Methoden zum Überspringen von Pre-Roll- und Mid-Roll-Anzeigen.

## API-Elemente für die Anzeigenwiedergabe {#section_296ADE00CFEA40CBA1B46142720D13A5}

TVSDK bietet Klassen und Methoden, mit denen Sie das Wiedergabeverhalten von Inhalt anpassen können, der Werbung enthält.
Die folgenden API-Elemente sind zum Anpassen der Wiedergabe nützlich:

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>API-Element</b></th> 
   <th colname="col2" class="entry"><b>Inhalte, die Werbung unterstützen</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdMetadata </span> </td> 
   <td colname="col2"> Legen Sie fest, ob eine Werbeunterbrechung von einem Viewer als überwacht markiert werden soll und wann sie mit einer Markierung versehen werden soll. Überwachte Richtlinie mithilfe von festlegen und abrufen <span class="codeph"> adBreakAsWatched </span> -Eigenschaft. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdPolicySelector </span> </td> 
   <td colname="col2"> Protokoll, das die Anpassung des TVSDK-Anzeigenverhaltens ermöglicht. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTDefaultAdPolicySelector </span> </td> 
   <td colname="col2"> Klasse, die das standardmäßige TVSDK-Verhalten implementiert. Ihre Anwendung kann diese Klasse überschreiben, um das Standardverhalten anzupassen, ohne die vollständige Benutzeroberfläche zu implementieren. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTMediaPlayer </span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"> <span class="codeph"> localTime </span>. <p>Dies ist die lokale Zeit der Wiedergabe ohne die platzierten Werbeunterbrechungen. </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"> <span class="codeph"> searchToLocalTime </span> . <p>Hier erfolgt die Suche relativ zu einer lokalen Zeit im Stream. </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"> <span class="codeph"> getTimeline.convertToLocalTime </span>. <p>Die virtuelle Position auf der Timeline wird in die lokale Position konvertiert. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdBreak </span> </td> 
   <td colname="col2"> <span class="codeph"> isWatched </span> -Eigenschaft. Gibt an, ob der Viewer die Anzeige gesehen hat. </td> 
  </tr> 
 </tbody> 
</table>

## Einrichten der benutzerdefinierten Wiedergabe {#section_8209BAACC7814C9399988DC7DE9CF4CA}

Bevor Sie Anzeigenverhalten anpassen oder überschreiben können, registrieren Sie die Anzeigenrichtlinieninstanz bei TVSDK.

Führen Sie einen der folgenden Schritte aus, um das Anzeigenverhalten anzupassen:

* Mit dem `PTAdPolicySelector` alle erforderlichen Methoden zur Richtlinienauswahl implementieren.

  Diese Option wird empfohlen, wenn Sie **all** Standardverhalten der Anzeige.

* Überschreiben Sie die `PTDefaultAdPolicySelector` -Klasse und stellen Implementierungen nur für jene Verhaltensweisen bereit, die angepasst werden müssen.

  Diese Option wird empfohlen, wenn Sie nur **some** des Standardverhaltens.

Führen Sie für beide Optionen die folgenden Aufgaben aus:

1. Registrieren Sie die Richtlinieninstanz, die von TVSDK über die Client-Factory verwendet werden soll.

   >[!NOTE]
   >
   >Benutzerdefinierte Anzeigenrichtlinien, die zu Beginn der Wiedergabe registriert werden, werden gelöscht, wenn die Variable `PTMediaPlayer` -Instanz nicht zugewiesen wurde. Ihre Anwendung muss bei jeder Erstellung einer neuen Wiedergabesitzung eine Richtlinienselektorinstanz registrieren.

   Beispiel:

   ```
   // Create an instance of the custom policy selector 
   PTS5MinuteSkipBreakPolicySelector *adPolicySelector  
        = [[[PTS5MinuteSkipBreakPolicySelector alloc] initWithMediaPlayer:self.player] autorelease]; 
   
   // register this instance 
   [[PTDefaultMediaPlayerClientFactory defaultFactory] registerAdPolicySelector:adPolicySelector];
   ```

1. Implementieren Sie Ihre Anpassungen.

## Werbeunterbrechungen für einen bestimmten Zeitraum überspringen {#section_99809BE4D9BB4DEEBBF596C746CA428A}

Standardmäßig erzwingt TVSDK die Wiedergabe einer Werbeunterbrechung, wenn der Benutzer die Suche über eine Werbeunterbrechung durchführt. Sie können das Verhalten so anpassen, dass eine Werbeunterbrechung übersprungen wird, wenn die seit dem Abschluss einer vorherigen Werbeunterbrechung verstrichene Zeit innerhalb einer bestimmten Anzahl von Minuten liegt.

>[!IMPORTANT]
>
>Wenn eine interne Suche besteht, um eine Anzeige zu überspringen, kann es bei der Wiedergabe zu einer leichten Pause kommen.

Im folgenden Beispiel einer benutzerdefinierten Anzeigenrichtlinienauswahl werden Anzeigen in den nächsten fünf Minuten (Uhrzeit) übersprungen, nachdem ein Benutzer eine Werbeunterbrechung gesehen hat.

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

## Speichern Sie die Videoposition und nehmen Sie die Fortsetzung später vor {#section_FAE252E38CED48D4BDD38BAA4A6A20A4}

Sie können die aktuelle Wiedergabeposition in einem Video speichern und die Wiedergabe an derselben Position in einer zukünftigen Sitzung fortsetzen.

Dynamisch eingefügte Anzeigen unterscheiden sich zwischen Benutzersitzungen, sodass die Position gespeichert wird **mit** Geteilte Anzeigen beziehen sich auf eine andere Position in einer zukünftigen Sitzung. TVSDK bietet Methoden zum Abrufen der Wiedergabeposition bei gleichzeitigem Ignorieren von geteilten Anzeigen.

1. Wenn der Benutzer ein Video beendet, ruft die Anwendung die Position im Video ab und speichert sie.

   >[!TIP]
   >
   >Anzeigendauern sind nicht enthalten.

   Werbeunterbrechungen können in jeder Sitzung aufgrund von Anzeigenmustern, Frequenzlimitierung usw. variieren. Die aktuelle Zeit des Videos in einer Sitzung kann in einer zukünftigen Sitzung anders sein. Beim Speichern einer Position im Video ruft die Anwendung die Ortszeit ab. Verwenden Sie die  `localTime` -Eigenschaft, um diese Position zu lesen, die Sie auf dem Gerät oder in einer Datenbank auf dem Server speichern können.

   Wenn sich der Benutzer beispielsweise in der 20. Minute des Videos befindet und diese Position fünf Minuten Anzeigen enthält, `currentTime` auf 1200 Sekunden eingestellt ist, während `localTime` an dieser Position 900 Sekunden.

   >[!IMPORTANT]
   >
   >Die lokale Zeit und die aktuelle Zeit sind für Live-/lineare Streams identisch. In diesem Fall `convertToLocalTime` hat keine Auswirkung. Für VOD bleibt die Ortszeit unverändert, während Anzeigen abgespielt werden.

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

1. Um das Video an der Stelle wiederaufzunehmen, die in der vorherigen Sitzung gespeichert wurde, verwenden Sie `seekToLocalTime`.

   >[!TIP]
   >
   >Diese Methode wird nur mit lokalen Zeitwerten aufgerufen. Wenn die Methode mit aktuellen Zeitergebnissen aufgerufen wird, tritt ein falsches Verhalten auf.

   Um zur aktuellen Zeit zu gelangen, verwenden Sie `seekToTime`.

1. Wenn Ihre Anwendung die `PTMediaPlayerStatusReady` Statusänderungsereignis, suchen Sie nach der gespeicherten lokalen Zeit.

   ```
   [self.player seekToLocalTime:CMTimeMake(900, 1) completionHandler:^(BOOL finished) { 
       [self.player play]; 
   }];
   ```

1. Stellen Sie die Werbeunterbrechungen bereit, wie in der Benutzeroberfläche der Anzeigenrichtlinie angegeben.
1. Implementieren Sie eine benutzerdefinierte Anzeigenrichtlinienauswahl, indem Sie die standardmäßige Anzeigenrichtlinienauswahl erweitern.
1. Stellen Sie die Werbeunterbrechungen bereit, die dem Benutzer durch Implementierung von `selectAdBreaksToPlay`

   >[!NOTE]
   >
   >Diese Methode umfasst eine Pre-Roll-Werbeunterbrechung und die Mid-Roll-Werbeunterbrechungen vor der lokalen Zeitposition. Ihre Anwendung kann entscheiden, eine Pre-Roll-Werbeunterbrechung wiederzugeben und zur festgelegten lokalen Zeit fortzufahren, eine Mid-Roll-Werbeunterbrechung abzuspielen und zur festgelegten lokalen Zeit fortzufahren oder keine Werbeunterbrechungen wiederzugeben.
