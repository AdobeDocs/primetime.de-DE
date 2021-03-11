---
description: Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.
title: Pufferzeiten einstellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---


# Pufferung {#buffering}

Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player zwischenspeichert.

TVSDK definiert eine Wiedergabepufferlänge von mindestens 30 Sekunden und eine anfängliche Pufferzeit von mindestens 2 Sekunden, bevor die Beginn abgespielt werden. Nachdem die Anwendung &quot;`play`&quot;aufruft, aber bevor die Wiedergabe beginnt, puffert TVSDK die Medien bis zur Anfangsphase, um einen glatten Beginn zu erhalten, wenn die Wiedergabe tatsächlich Beginn ist.

Sie können die Pufferzeiten ändern, indem Sie neue Pufferrichtlinien definieren und ändern, wann die anfängliche Pufferung erfolgt, indem Sie Instant-on verwenden.

## Pufferzeiten {#set-buffering-times} festlegen

Das `MediaPlayer` stellt Methoden zum Festlegen und Abrufen der anfänglichen Pufferzeit und der Wiedergabepufferzeit bereit.

>[!TIP]
>
>Wenn Sie die Parameter für die Puffersteuerung nicht vor Beginn der Wiedergabe festlegen, wird der Medienplayer standardmäßig auf 2 Sekunden für den anfänglichen Puffer und auf 30 Sekunden für die laufende Wiedergabepufferzeit eingestellt.

1. Richten Sie das `BufferControlParameters`-Objekt ein, das die Steuerungsparameter für die anfängliche Pufferzeit und die Wiedergabepufferzeit enthält:

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

      Diese Methoden geben ein `IllegalArgumentException` aus, wenn die Parameter nicht gültig sind, z. B. wenn:

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

   Wenn AVE die angegebenen Werte nicht festlegen kann, gibt der Medienplayer den Status `ERROR` mit dem Fehlercode `SET_BUFFER_PARAMETERS_ERROR` ein.

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

So legen Sie beispielsweise den anfänglichen Puffer auf 2 Sekunden und die Wiedergabepufferzeit auf 30 Sekunden fest:

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(2000, 30000));
```

Die Primetime-Referenzimplementierung zeigt diese Funktion. Verwenden Sie die Einstellungen der Anwendung, um die Pufferwerte festzulegen.