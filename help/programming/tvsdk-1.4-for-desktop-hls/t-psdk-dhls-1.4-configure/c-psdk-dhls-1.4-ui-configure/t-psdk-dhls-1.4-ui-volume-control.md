---
description: Sie können ein Steuerelement der Benutzeroberfläche für die Lautstärke einrichten.
title: Volumensteuerung bereitstellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# Volumensteuerung{#provide-volume-control}

Sie können ein Steuerelement der Benutzeroberfläche für die Lautstärke einrichten.

1. Warten Sie, bis sich die MediaPlayer-Instanz in einem gültigen Status für diesen Befehl befindet.

   Jeder Status außer RELEASED ist gültig.
1. Rufen Sie die Volume Set-Methode für die `MediaPlayer`-Instanz auf, um die Audiolautstärke festzulegen.

   ```
   public function set volume(value:Number):void
   ```

   Der Wert für das Volumen entspricht dem beantragten Volumen, ausgedrückt als Anteil des Höchstvolumens, wobei 0 stumm und 1 das Höchstvolumen ist.

   <table id="table_144A2B1260374FBE8D976194F602DDC7"> 
   <thead> 
   <tr> 
      <th colname="col1" class="entry"> Wenn das angegebene Volumen </th> 
      <th colname="col2" class="entry"> Das resultierende Volumen ist </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col1"> Kleiner als 0 </td> 
      <td colname="col2"> 0 </td> 
   </tr> 
   <tr> 
      <td colname="col1"> Zwischen 0 und 1 </td> 
      <td colname="col2"> Das angegebene Volumen </td> 
   </tr> 
   <tr> 
      <td colname="col1"> Größer als 1 </td> 
      <td colname="col2"> Der durch 100 geteilte Wert, der auf einen der folgenden Werte eingestellt ist: 
      <ul id="ul_8C2282F0EDC44A408820F5768709214F"> 
      <li id="li_B00BC6F4812D4000891358F762C8E492">Das Ergebnis, wenn es zwischen 0 und 1 liegt </li> 
      <li id="li_03B7F30662554F299320040CAC2DEB7A">1, wenn das Ergebnis größer als 1 ist </li> 
      </ul> <p>Tipp:  Diese Logik verarbeitet Werte, die von Clients basierend auf früheren Versionen der Variablen 
      <span class="codeph">Wortgruppen/primetime-sdk-name</span>, wobei die Volumenwerte zwischen 0 und 100 liegen. </p> </td> 
   </tr> 
   </tbody> 
   </table>
