---
description: Sie können die aktuelle Wiedergabeposition in einem Video speichern und die Wiedergabe an derselben Position in einer zukünftigen Sitzung fortsetzen.
title: Speichern Sie die Videoposition und nehmen Sie die Fortsetzung später vor
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# Speichern Sie die Videoposition und nehmen Sie die Fortsetzung später vor{#save-the-video-position-and-resume-later}

Sie können die aktuelle Wiedergabeposition in einem Video speichern und die Wiedergabe an derselben Position in einer zukünftigen Sitzung fortsetzen.

Dynamisch eingefügte Anzeigen unterscheiden sich zwischen Benutzersitzungen, sodass die Position gespeichert wird **mit** Geteilte Anzeigen beziehen sich auf eine andere Position in einer zukünftigen Sitzung. TVSDK bietet Methoden zum Abrufen der Wiedergabeposition bei gleichzeitigem Ignorieren von geteilten Anzeigen.

1. Wenn der Benutzer ein Video beendet, ruft die Anwendung die Position im Video ab und speichert sie.

   >[!TIP]
   >
   >Anzeigendauern sind nicht enthalten.

   Werbeunterbrechungen können in jeder Sitzung aufgrund von Anzeigenmustern, Frequenzlimitierung usw. variieren. Die aktuelle Zeit des Videos in einer Sitzung kann in einer zukünftigen Sitzung anders sein. Beim Speichern einer Position im Video ruft die Anwendung die Ortszeit ab. Verwenden Sie die `localTime` -Eigenschaft, um diese Position zu lesen, die Sie auf dem Gerät oder in einer Datenbank auf dem Server speichern können.

   ```
   var resumeTime:Number = player.localTime; 
   // save the resumeTime to a persistent location
   ```

   Wenn sich der Benutzer beispielsweise in der 20. Minute des Videos befindet und diese Position fünf Minuten Anzeigen enthält, `currentTime` will `be` 1200 Sekunden, während `localTime` an dieser Stelle `be` 900 Sekunden.

1. Stellen Sie die Benutzersitzung wieder her, wenn die Player-Aktivität wieder aufgenommen wird.

   TVSDK nimmt die Wiedergabe zwischen TVSDK-Initialisierungen nicht wieder auf, da keine Informationen lokal gespeichert werden. Ihre Anwendung muss diese Logik implementieren.

   ```
   // retrieve the resumeTime from the persistent location 
   var resumeTime:Number:Number = ...;
   ```

1. So setzen Sie das Video an derselben Position fort:

   * Um die Wiedergabe des Videos von der Position aus fortzusetzen, die in einer vorherigen Sitzung gespeichert wurde, verwenden Sie `seekToLocal`.

     >[!TIP]
     >
     >Diese Methode wird nur mit lokalen Zeitwerten aufgerufen. Wenn die Methode mit aktuellen Zeitergebnissen aufgerufen wird, tritt ein falsches Verhalten auf.

   * Um zur aktuellen Zeit zu gelangen, verwenden Sie `seek`.

1. Wenn Ihre Anwendung die `onStatusChanged` Statusänderungsereignis, suchen Sie nach der gespeicherten lokalen Zeit.
1. Stellen Sie die Werbeunterbrechungen bereit, wie in der Benutzeroberfläche der Anzeigenrichtlinie angegeben.
1. Implementieren Sie eine benutzerdefinierte Anzeigenrichtlinienauswahl, indem Sie die standardmäßige Anzeigenrichtlinienauswahl erweitern.
1. Stellen Sie die Werbeunterbrechungen bereit, die dem Benutzer durch Implementierung von `selectAdBreaksToPlay`.

   Wenn der Player den Status &quot;VORBEREITT&quot;erhält, werden alle Anzeigen bereits aufgelöst, sodass die `AdPolicyInfo.adBreakTimelineItem` -Eigenschaft enthält alle Werbeunterbrechungen vor der lokalen Zeitposition. Ihre Anwendung kann entscheiden, eine Pre-Roll-Werbeunterbrechung wiederzugeben und zur festgelegten lokalen Zeit fortzufahren, eine Mid-Roll-Werbeunterbrechung abzuspielen und zur festgelegten lokalen Zeit fortzufahren oder keine Werbeunterbrechungen wiederzugeben.
