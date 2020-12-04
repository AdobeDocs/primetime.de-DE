---
description: Der MediaPlayer bietet Methoden zum Festlegen und Abrufen der anfänglichen Pufferzeit und der Wiedergabepufferzeit.
seo-description: Der MediaPlayer bietet Methoden zum Festlegen und Abrufen der anfänglichen Pufferzeit und der Wiedergabepufferzeit.
seo-title: Pufferzeiten einstellen
title: Pufferzeiten einstellen
uuid: 25142b01-5381-49c9-b89a-24c858faaf13
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# Festlegen der Pufferzeiten{#set-buffering-times}

Der MediaPlayer bietet Methoden zum Festlegen und Abrufen der anfänglichen Pufferzeit und der Wiedergabepufferzeit.

>[!TIP]
>
>Wenn Sie die Parameter für die Puffersteuerung nicht vor Beginn der Wiedergabe festlegen, wird der Medienplayer standardmäßig auf 2 Sekunden für den anfänglichen Puffer und auf 30 Sekunden für die laufende Wiedergabepufferzeit eingestellt.

1. Richten Sie das `BufferControlParameters`-Objekt ein, das die Steuerungsparameter für die anfängliche Pufferzeit und die Wiedergabepufferzeit enthält:

       Diese Klasse stellt die folgenden Factory-Methoden bereit:
   
   * So legen Sie die anfängliche Pufferzeit auf die Wiedergabepufferzeit fest:

      ```
      createSimple(bufferTime:uint):BufferControlParameters
      ```

   * So legen Sie sowohl die Anfangs- als auch die Wiedergabepufferzeit fest:

      ```
      createDual(initialBufferTime:uint, playbackBufferTime:uint):BufferControlParameters 
      ```

      Diese Methoden geben ein `IllegalArgumentException` aus, wenn die Parameter nicht gültig sind, z. B. wenn:

   * Die anfängliche Pufferzeit ist kleiner als null.
   * Die anfängliche Pufferzeit ist größer als die Pufferzeit.

1. Verwenden Sie zum Festlegen der Pufferparameterwerte die folgende `MediaPlayer`-Methode:

   ```
   public function set bufferControlParameters(value:BufferControlParameters):void
   ```

1. Um die aktuellen Pufferparameterwerte abzurufen, verwenden Sie die folgende `MediaPlayer`-Methode:

   ```
   public function get bufferControlParameters():BufferControlParameters
   ```

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

So legen Sie beispielsweise den anfänglichen Puffer auf 2 Sekunden und die Wiedergabepufferzeit auf 30 Sekunden fest:

```
mediaPlayer.bufferControlParameters = BufferControlParameters.createDual(2000, 30000); 
```

Diese Funktion wird mit dem `psdkdemo`-Zeichen veranschaulicht. Verwenden Sie die Einstellungen der Anwendung, um die Pufferwerte festzulegen.
