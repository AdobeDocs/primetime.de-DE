---
description: Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.
seo-description: Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.
seo-title: Pufferung
title: Pufferung
uuid: 7f9f0deb-5f18-441d-b7a4-67c631a798f4
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---


# Übersicht {#buffering-overview}

Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.

TVSDK definiert eine Wiedergabepufferlänge von mindestens 30 Sekunden und eine anfängliche Pufferzeit von mindestens 2 Sekunden, bevor die Beginn abgespielt werden. Nachdem die Anwendung &quot;`play`&quot;aufruft, aber bevor die Wiedergabe beginnt, puffert TVSDK die Medien bis zur Anfangsphase, um einen glatten Beginn zu erhalten, wenn die Wiedergabe tatsächlich Beginn ist.

Sie können die Pufferzeiten ändern, indem Sie neue Pufferrichtlinien definieren. Sie können auch ändern, wann die anfängliche Pufferung erfolgt, indem Sie Instant on verwenden.

## Zeitrichtlinien für die Pufferung {#section_9B3407D52F1E4CB48E7A4836EBDA8F70}

Abhängig von Ihrer Umgebung (einschließlich des Geräts, des Betriebssystems oder der Netzwerkbedingungen) können Sie verschiedene Pufferrichtlinien für Ihren Player festlegen, z. B. die Änderung der Mindestdauer für die anfängliche Pufferung und für die kontinuierliche Wiedergabe-Pufferung.

Nach dem Aufruf von `play` beginnt der Medienplayer mit der Pufferung des Videos. Wenn der Medienplayer die durch die anfängliche Pufferzeit angegebene Videomenge gepuffert hat, beginnt die Wiedergabe. Dieser Vorgang verbessert die Beginn-Up-Zeit, da der Player nicht darauf wartet, dass der gesamte Wiedergabepuffer gefüllt wird, bevor die Wiedergabe gestartet wird. Stattdessen beginnt die Wiedergabe, nachdem die ersten Sekunden gepuffert wurden.

Während das Video wiedergegeben wird, puffert TVSDK weiterhin neue Fragmente, bis der in der Wiedergabepufferzeit angegebene Betrag gepuffert wurde. Wenn die aktuelle Pufferlänge unter die Wiedergabepufferzeit fällt, lädt der Player zusätzliche Fragmente herunter. Sobald die aktuelle Pufferlänge um einige Sekunden über der Wiedergabepufferzeit liegt, beendet TVSDK das Herunterladen von Fragmenten.

>[!TIP]
>
>Wenn der anfängliche Pufferwert hoch ist, kann dies dem Benutzer eine lange anfängliche Pufferzeit geben, bevor er beginnt. Dies kann eine reibungslose Wiedergabe über einen längeren Zeitraum ermöglichen. Bei schlechten Netzwerkbedingungen kann die anfängliche Wiedergabe jedoch verzögert sein.

Wenn Sie den InstantOn-Modus durch Aufruf von `prepareBuffer` aktivieren, beginnt die anfängliche Pufferung zu diesem Zeitpunkt, anstatt auf `play` zu warten.

## Pufferzeiten {#section_05CDD927869D47EBA1D2069B1416B2E4} festlegen

Das `MediaPlayer` stellt Methoden zum Festlegen und Abrufen der anfänglichen Pufferzeit und der Wiedergabepufferzeit bereit.

>[!TIP]
>
>Wenn Sie die Parameter für die Puffersteuerung nicht vor Beginn der Wiedergabe festlegen, wird der Medienplayer standardmäßig auf 2 Sekunden für den anfänglichen Puffer und auf 30 Sekunden für die laufende Wiedergabepufferzeit eingestellt.

1. Richten Sie das `BufferControlParameters`-Objekt ein, das die Steuerungsparameter für die anfängliche Pufferzeit und die Wiedergabepufferzeit enthält.

   Diese Klasse stellt die folgenden Factory-Methoden bereit:

   * So legen Sie die anfängliche Pufferzeit auf die Wiedergabepufferzeit fest:

      ```
      public static BufferControlParameters createSimple(long bufferTime)
      ```

   * So legen Sie die Start- und Wiedergabepufferzeiten fest:

      ```
      public static BufferControlParameters createDual( 
        long initialBuffer,  
        long bufferTime)
      ```
   Wenn die Parameter nicht gültig sind, geben diese Methoden `MediaPlayerException` mit dem Fehlercode `PSDKErrorCode.INVALID_ARGUMENT` aus, z. B. wenn die folgenden Bedingungen erfüllt sind:

   * Die anfängliche Pufferzeit ist kleiner als null.
   * Die anfängliche Pufferzeit ist größer als die Pufferzeit.


1. Verwenden Sie zum Festlegen der Pufferparameterwerte die folgende `MediaPlayer`-Methode:

   ```java
   void setBufferControlParameters(BufferControlParameters params)
   ```

1. Um die aktuellen Pufferparameterwerte abzurufen, verwenden Sie die folgende `MediaPlayer`-Methode:

   ```java
      BufferControlParameters getBufferControlParameters()  
   ```

<!--<a id="example_DE0580B3AD404635825D3301C1F096B6"></a>-->

So legen Sie beispielsweise den anfänglichen Puffer auf 5 Sekunden und die Wiedergabepufferzeit auf 30 Sekunden fest:

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(5000, 30000));
```
