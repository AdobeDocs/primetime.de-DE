---
description: Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.
seo-description: Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.
seo-title: Pufferzeiten einstellen
title: Pufferzeiten einstellen
uuid: 5a3945a4-1935-4797-b19d-84989850a487
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Pufferung {#buffering}

Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.

TVSDK definiert eine Wiedergabepufferlänge von mindestens 30 Sekunden und eine anfängliche Pufferzeit von mindestens 2 Sekunden, bevor die Beginn abgespielt werden. Nach dem Aufruf der Applikation, `play` aber vor dem Start der Wiedergabe puffert TVSDK die Medien bis zum anfänglichen Zeitpunkt, um einen glatten Beginn zu erhalten, wenn die Beginn tatsächlich abgespielt werden.

Sie können die Pufferzeiten ändern, indem Sie neue Pufferrichtlinien definieren und ändern, wann die anfängliche Pufferung erfolgt, indem Sie Instant-on verwenden.

## Pufferzeiten einstellen {#set-buffering-times}

Die `MediaPlayer` bietet Methoden zum Festlegen und Abrufen der anfänglichen Pufferzeit und der Wiedergabepufferzeit.

>[!TIP]
>
>Wenn Sie die Parameter für die Puffersteuerung nicht vor Beginn der Wiedergabe festlegen, wird der Medienplayer standardmäßig auf 2 Sekunden für den anfänglichen Puffer und auf 30 Sekunden für die laufende Wiedergabepufferzeit eingestellt.

1. Richten Sie das `BufferControlParameters` Objekt ein, das die Steuerungsparameter für die anfängliche Pufferzeit und die Wiedergabepufferzeit enthält:

       Diese Klasse stellt zwei Factory-Methoden bereit:
   
   * So legen Sie die anfängliche Pufferzeit auf die Wiedergabepufferzeit fest:

      ```java
      public static BufferControlParameters createSimple( 
          long bufferTime)
      ```

   * So legen Sie sowohl die Anfangs- als auch die Wiedergabepufferzeit fest:

      ```java
      public static BufferControlParameters createDual( 
          long initialBuffer,   
          long bufferTime)
      ```

      Diese Methoden lösen einen Fehler aus, `IllegalArgumentException` wenn die Parameter nicht gültig sind, z. B. wenn:

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

   Wenn AVE die angegebenen Werte nicht festlegen kann, wird der Medienplayer mit dem `ERROR` Fehlercode in den Status versetzt `SET_BUFFER_PARAMETERS_ERROR`.

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

So legen Sie beispielsweise den anfänglichen Puffer auf 2 Sekunden und die Wiedergabepufferzeit auf 30 Sekunden fest:

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(2000, 30000));
```

Die Primetime-Referenzimplementierung zeigt diese Funktion. Verwenden Sie die Einstellungen der Anwendung, um die Pufferwerte festzulegen.