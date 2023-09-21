---
description: Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player gepuffert wird.
title: Pufferzeiten festlegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# Pufferung {#buffering}

Um eine reibungslosere Anzeige zu ermöglichen, puffert TVSDK manchmal den Videostream. Sie können konfigurieren, wie der Player gepuffert wird.

TVSDK definiert eine Wiedergabepufferlänge von mindestens 30 Sekunden und eine anfängliche Pufferzeit innerhalb dieser Zeit, bevor die Medienwiedergabe beginnt, von mindestens 2 Sekunden. Nach den App-Aufrufen `play` aber vor Beginn der Wiedergabe puffert TVSDK die Medien bis zur Anfangsphase, um einen reibungslosen Start bei der tatsächlichen Wiedergabe zu gewährleisten.

Sie können die Pufferzeiten ändern, indem Sie neue Pufferrichtlinien definieren und ändern, wann die anfängliche Pufferung erfolgt, indem Sie Instant-on verwenden.

## Pufferzeiten festlegen {#set-buffering-times}

Die `MediaPlayer` bietet Methoden zum Festlegen und Abrufen der anfänglichen Pufferzeit und der Wiedergabepufferzeit.

>[!TIP]
>
>Wenn Sie die Puffersteuerungsparameter nicht vor Beginn der Wiedergabe festlegen, wird der Medienplayer für den anfänglichen Puffer auf 2 Sekunden und für die laufende Wiedergabepufferzeit auf 30 Sekunden gesetzt.

1. Richten Sie die `BufferControlParameters` -Objekt, das die Steuerungsparameter für die anfängliche Pufferzeit und die Wiedergabepufferdauer enthält:

       Diese Klasse stellt zwei Factory-Methoden bereit:
   
   * So legen Sie die anfängliche Pufferzeit auf die Wiedergabepufferzeit fest:

     ```java
     public static BufferControlParameters createSimple( 
         long bufferTime)
     ```

   * So legen Sie sowohl die Start- als auch die Wiedergabepufferzeiten fest:

     ```java
     public static BufferControlParameters createDual( 
         long initialBuffer,   
         long bufferTime)
     ```

     Diese Methoden geben `IllegalArgumentException` wenn die Parameter nicht gültig sind, z. B. wenn:

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

   Wenn die AVE die angegebenen Werte nicht festlegen kann, gibt der Medienplayer die `ERROR` state mit dem Fehlercode `SET_BUFFER_PARAMETERS_ERROR`.

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

So legen Sie beispielsweise den anfänglichen Puffer auf 2 Sekunden und die Wiedergabepufferzeit auf 30 Sekunden fest:

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(2000, 30000));
```

Die Primetime-Referenzimplementierung veranschaulicht diese Funktion. Verwenden Sie die Einstellungen der Anwendung, um die Pufferwerte festzulegen.
