---
description: Sie können die aktuelle Wiedergabeposition in einem Video speichern und die Wiedergabe an derselben Position in einer zukünftigen Sitzung fortsetzen.
title: Speichern Sie die Videoposition und nehmen Sie den Vorgang später wieder auf
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---


# Speichern Sie die Videoposition und setzen Sie die Wiedergabe später fort.{#save-the-video-position-and-resume-later}

Sie können die aktuelle Wiedergabeposition in einem Video speichern und die Wiedergabe an derselben Position in einer zukünftigen Sitzung fortsetzen.

Dynamisch eingefügte Anzeigen unterscheiden sich von Benutzersitzung zu Benutzersitzung. Daher bezieht sich das Speichern der Position **mit** geteilten Anzeigen auf eine andere Position in einer zukünftigen Sitzung. TVSDK stellt Methoden zum Abrufen der Wiedergabeposition bereit, während geteilte Anzeigen ignoriert werden.

1. Wenn der Benutzer ein Video beendet, ruft Ihre Anwendung die Position im Video ab und speichert sie.

   >[!TIP]
   >
   >Die Anzeigendauer ist nicht inbegriffen.

   Werbeunterbrechungen können je nach Sitzung unterschiedlich ausfallen, da Anzeigenmuster, Frequenzbegrenzungen usw. gelten. Die aktuelle Zeit des Videos in einer Sitzung kann in einer zukünftigen Sitzung anders sein. Beim Speichern einer Position im Video ruft die Anwendung die Ortszeit ab. Verwenden Sie die `localTime`-Eigenschaft, um diese Position zu lesen, die Sie auf dem Gerät oder in einer Datenbank auf dem Server speichern können.

   ```
   var resumeTime:Number = player.localTime; 
   // save the resumeTime to a persistent location
   ```

   Wenn sich der Benutzer zum Beispiel in der 20. Minute des Videos befindet und diese Position fünf Minuten der Anzeigen umfasst, wird `currentTime` `be` 1200 Sekunden, während `localTime` an dieser Position `be` 900 Sekunden beträgt.

1. Stellen Sie die Benutzersitzung wieder her, wenn die Player-Aktivität fortgesetzt wird.

   TVSDK nimmt die Wiedergabe zwischen TVSDK-Initialisierungen nicht wieder auf, da keine Informationen lokal gespeichert werden. Ihre Anwendung muss diese Logik implementieren.

   ```
   // retrieve the resumeTime from the persistent location 
   var resumeTime:Number:Number = ...;
   ```

1. So setzen Sie das Video an derselben Position fort:

   * Um das Video von der Position wiederzugeben, die in einer vorherigen Sitzung gespeichert wurde, verwenden Sie `seekToLocal`.

      >[!TIP]
      >
      >Diese Methode wird nur mit lokalen Zeitwerten aufgerufen. Wenn die Methode mit den aktuellen Zeitergebnissen aufgerufen wird, tritt ein falsches Verhalten auf.

   * Um zur aktuellen Zeit zu suchen, verwenden Sie `seek`.

1. Wenn Ihre Anwendung das Ereignis `onStatusChanged` zur Statusänderung erhält, suchen Sie nach der gespeicherten Ortszeit.
1. Stellen Sie die Werbeunterbrechungen gemäß den Angaben in der Benutzeroberfläche der Anzeigenrichtlinie bereit.
1. Implementieren Sie eine benutzerdefinierte Anzeigenrichtlinienauswahl, indem Sie die standardmäßige Anzeigenrichtlinien-Auswahl erweitern.
1. Geben Sie die Werbeunterbrechungen an, die dem Benutzer durch Implementierung von `selectAdBreaksToPlay` angezeigt werden müssen.

   Wenn der Player den Status &quot;VORBEREITET&quot;aufruft, werden alle Anzeigen bereits aufgelöst, sodass die Eigenschaft `AdPolicyInfo.adBreakTimelineItem` alle Werbeunterbrechungen vor der lokalen Zeitposition enthält. Ihre Anwendung kann beschließen, eine Pre-Roll-Werbeunterbrechung auszuführen und zur angegebenen Ortszeit wiederaufzunehmen, eine Mid-Roll-Werbeunterbrechung abzuspielen und zur angegebenen Ortszeit fortzufahren oder keine Werbeunterbrechungen wiederzugeben.
