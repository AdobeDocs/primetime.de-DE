---
description: Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.
seo-description: Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.
seo-title: Pufferung
title: Pufferung
uuid: c84b98ed-0070-4a86-a409-d7702e5be23c
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Übersicht {#buffering-overview}

Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.

TVSDK definiert eine Wiedergabepufferlänge von mindestens 30 Sekunden und eine anfängliche Pufferzeit von mindestens 2 Sekunden, bevor die Beginn abgespielt werden. Nach dem Aufruf der Applikation `play`und vor dem Start der Wiedergabe puffert TVSDK die Medien bis zum anfänglichen Zeitpunkt, um einen reibungslosen Beginn zu erzielen, wenn die Beginn tatsächlich abgespielt werden.

Sie können die Pufferzeiten ändern, indem Sie neue Pufferrichtlinien definieren. Sie können auch ändern, wann die anfängliche Pufferung erfolgt, indem Sie Instant on verwenden.

## Zeitrichtlinien zwischenspeichern {#section_9B3407D52F1E4CB48E7A4836EBDA8F70}

Abhängig von Ihrer Umgebung (einschließlich des Geräts, des Betriebssystems oder der Netzwerkbedingungen) können Sie verschiedene Pufferrichtlinien für Ihren Player festlegen, z. B. die Änderung der Mindestdauer für die anfängliche Pufferung und für die kontinuierliche Wiedergabe-Pufferung.

Nach dem Aufruf `play`beginnt der Medienplayer, das Video zu puffern. Wenn der Medienplayer die durch die anfängliche Pufferzeit angegebene Videomenge gepuffert hat, beginnt die Wiedergabe. Dieser Vorgang verbessert die Beginn-Up-Zeit, da der Player nicht darauf wartet, dass der gesamte Wiedergabepuffer gefüllt wird, bevor die Wiedergabe gestartet wird. Stattdessen beginnt die Wiedergabe, nachdem die ersten Sekunden gepuffert wurden.

Während das Video wiedergegeben wird, puffert TVSDK weiterhin neue Fragmente, bis der in der Wiedergabepufferzeit angegebene Betrag gepuffert wurde. Wenn die aktuelle Pufferlänge unter die Wiedergabepufferzeit fällt, lädt der Player zusätzliche Fragmente herunter. Sobald die aktuelle Pufferlänge um einige Sekunden über der Wiedergabepufferzeit liegt, beendet TVSDK das Herunterladen von Fragmenten.

>[!TIP]
>
>Wenn der anfängliche Pufferwert hoch ist, kann dies dem Benutzer eine lange anfängliche Pufferzeit geben, bevor er beginnt. Dies kann eine reibungslose Wiedergabe über einen längeren Zeitraum ermöglichen. Bei schlechten Netzwerkbedingungen kann die anfängliche Wiedergabe jedoch verzögert sein.

Wenn Sie Instant On durch Aufruf aktivieren `prepareBuffer`, beginnt die anfängliche Pufferung zu diesem Zeitpunkt, anstatt darauf zu warten `play`.

## Pufferzeiten einstellen {#section_05CDD927869D47EBA1D2069B1416B2E4}

Die `MediaPlayer` bietet Methoden zum Festlegen und Abrufen der anfänglichen Pufferzeit und der Wiedergabepufferzeit.

>[!TIP]
>
>Wenn Sie die Parameter für die Puffersteuerung nicht vor Beginn der Wiedergabe festlegen, wird der Medienplayer standardmäßig auf 2 Sekunden für den anfänglichen Puffer und auf 30 Sekunden für die laufende Wiedergabepufferzeit eingestellt.

1. Richten Sie das `BufferControlParameters` Objekt ein, das die Steuerungsparameter für die anfängliche Pufferzeit und die Wiedergabepufferzeit enthält.

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
   Wenn die Parameter nicht gültig sind, erhalten diese Methoden `MediaPlayerException` Fehlercode, `PSDKErrorCode.INVALID_ARGUMENT`z. B. wenn die folgenden Bedingungen erfüllt sind:

   * Die anfängliche Pufferzeit ist kleiner als null.
   * Die anfängliche Pufferzeit ist größer als die Pufferzeit.


1. Verwenden Sie zum Festlegen der Pufferparameterwerte die folgende `MediaPlayer` Methode:

   ```java
   void setBufferControlParameters(BufferControlParameters params)
   ```

1. Um die aktuellen Pufferparameterwerte abzurufen, verwenden Sie folgende `MediaPlayer` Methode:

   ```java
      BufferControlParameters getBufferControlParameters()  
   ```

<!--<a id="example_DE0580B3AD404635825D3301C1F096B6"></a>-->

So legen Sie beispielsweise den anfänglichen Puffer auf 5 Sekunden und die Wiedergabepufferzeit auf 30 Sekunden fest:

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(5000, 30000));
```
