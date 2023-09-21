---
description: Der MediaPlayer bietet Methoden zum Festlegen und Abrufen der anfänglichen Pufferzeit und der Wiedergabepufferzeit.
title: Pufferzeiten festlegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Pufferzeiten festlegen{#set-buffering-times}

Der MediaPlayer bietet Methoden zum Festlegen und Abrufen der anfänglichen Pufferzeit und der Wiedergabepufferzeit.

>[!TIP]
>
>Wenn Sie die Puffersteuerungsparameter nicht vor Beginn der Wiedergabe festlegen, wird der Medienplayer für den anfänglichen Puffer auf 2 Sekunden und für die laufende Wiedergabepufferzeit auf 30 Sekunden gesetzt.

1. Richten Sie die `BufferControlParameters` -Objekt, das die Steuerungsparameter für die anfängliche Pufferzeit und die Wiedergabepufferdauer enthält:

       Diese Klasse stellt die folgenden Factory-Methoden bereit:
   
   * So legen Sie die anfängliche Pufferzeit auf die Wiedergabepufferzeit fest:

     ```
     createSimple(bufferTime:uint):BufferControlParameters
     ```

   * So legen Sie sowohl die Start- als auch die Wiedergabepufferzeiten fest:

     ```
     createDual(initialBufferTime:uint, playbackBufferTime:uint):BufferControlParameters 
     ```

     Diese Methoden geben `IllegalArgumentException` wenn die Parameter nicht gültig sind, z. B. wenn:

   * Die anfängliche Pufferzeit ist kleiner als null.
   * Die anfängliche Pufferzeit ist größer als die Pufferzeit.

1. Verwenden Sie zum Festlegen der Pufferparameterwerte Folgendes `MediaPlayer` -Methode:

   ```
   public function set bufferControlParameters(value:BufferControlParameters):void
   ```

1. Um die aktuellen Pufferparameterwerte zu erhalten, verwenden Sie diese `MediaPlayer` -Methode:

   ```
   public function get bufferControlParameters():BufferControlParameters
   ```

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

So legen Sie beispielsweise den anfänglichen Puffer auf 2 Sekunden und die Wiedergabepufferzeit auf 30 Sekunden fest:

```
mediaPlayer.bufferControlParameters = BufferControlParameters.createDual(2000, 30000); 
```

Die `psdkdemo` zeigt diese Funktion an. Verwenden Sie die Einstellungen der Anwendung, um die Pufferwerte festzulegen.
