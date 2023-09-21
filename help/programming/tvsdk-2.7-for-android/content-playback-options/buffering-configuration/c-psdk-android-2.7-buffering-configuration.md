---
description: Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player gepuffert wird.
title: Pufferung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# Übersicht {#buffering-overview}

Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player gepuffert wird.

TVSDK definiert eine Wiedergabepufferlänge von mindestens 30 Sekunden und eine anfängliche Pufferzeit von mindestens 2 Sekunden, bevor die Medienwiedergabe beginnt. Nach den App-Aufrufen `play`, aber bevor die Wiedergabe beginnt, puffert TVSDK die Medien bis zur Anfangsphase, um einen reibungslosen Start zu ermöglichen, wenn die Wiedergabe tatsächlich beginnt.

Sie können die Pufferzeiten ändern, indem Sie neue Pufferrichtlinien definieren und ändern, wann die anfängliche Pufferung erfolgt, indem Sie Instant on verwenden.

## Pufferung von Zeitrichtlinien {#section_9B3407D52F1E4CB48E7A4836EBDA8F70}

Abhängig von Ihrer Umgebung (einschließlich Gerät, Betriebssystem oder Netzwerkbedingungen) können Sie für Ihren Player verschiedene Pufferungsrichtlinien festlegen, z. B. die Mindestdauer für die anfängliche Pufferung und für die laufende Wiedergabe ändern.

Nach dem Aufruf `play`, beginnt der Medienplayer mit der Pufferung des Videos. Wenn der Medienplayer die durch die anfängliche Pufferzeit angegebene Videomenge gepuffert hat, beginnt die Wiedergabe. Dieser Prozess verbessert die Startzeit, da der Player nicht darauf wartet, dass der gesamte Wiedergabepuffer gefüllt wird, bevor die Wiedergabe gestartet wird. Stattdessen beginnt die Wiedergabe, nachdem die ersten Sekunden gepuffert wurden.

Während das Video gerendert wird, puffert TVSDK weiterhin neue Fragmente, bis der in der Wiedergabepufferzeit angegebene Betrag gepuffert wurde. Wenn die aktuelle Pufferlänge unter die Wiedergabepufferzeit fällt, lädt der Player zusätzliche Fragmente herunter. Sobald die aktuelle Pufferlänge um einige Sekunden über der Wiedergabepufferzeit liegt, stoppt TVSDK das Herunterladen von Fragmenten.

>[!TIP]
>
>Wenn der anfängliche Pufferwert hoch ist, kann es Ihrem Benutzer eine lange anfängliche Pufferzeit geben, bevor er startet. Dies kann eine reibungslose Wiedergabe über einen längeren Zeitraum ermöglichen. Wenn jedoch die Netzwerkbedingungen schlecht sind, kann die anfängliche Wiedergabe verzögert sein.

Wenn Sie Instant On aktivieren, rufen Sie `prepareBuffer`, beginnt die anfängliche Pufferung zu diesem Zeitpunkt, anstatt auf `play`.

## Pufferzeiten festlegen {#section_05CDD927869D47EBA1D2069B1416B2E4}

Die `MediaPlayer` bietet Methoden zum Festlegen und Abrufen der anfänglichen Pufferzeit und der Wiedergabepufferzeit.

>[!TIP]
>
>Wenn Sie die Puffersteuerungsparameter nicht vor Beginn der Wiedergabe festlegen, wird der Medienplayer für den anfänglichen Puffer auf 2 Sekunden und für die laufende Wiedergabepufferzeit auf 30 Sekunden gesetzt.

1. Richten Sie die `BufferControlParameters` -Objekt, das die Steuerungsparameter für die anfängliche Pufferzeit und die Wiedergabepufferzeit einkapselt.

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

   Wenn die Parameter nicht gültig sind, geben diese Methoden `MediaPlayerException` mit Fehlercode `PSDKErrorCode.INVALID_ARGUMENT`, z. B. wenn die folgenden Bedingungen erfüllt sind:

   * Die anfängliche Pufferzeit ist kleiner als null.
   * Die anfängliche Pufferzeit ist größer als die Pufferzeit.

1. Verwenden Sie zum Festlegen der Pufferparameterwerte Folgendes `MediaPlayer` -Methode:

   ```java
   void setBufferControlParameters(BufferControlParameters params)
   ```

1. Um die aktuellen Pufferparameterwerte zu erhalten, verwenden Sie diese `MediaPlayer` -Methode:

   ```java
      BufferControlParameters getBufferControlParameters()  
   ```

<!--<a id="example_DE0580B3AD404635825D3301C1F096B6"></a>-->

So legen Sie beispielsweise den anfänglichen Puffer auf 5 Sekunden und die Wiedergabepufferzeit auf 30 Sekunden fest:

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(5000, 30000));
```
