---
description: Sie können ein Benutzeroberflächensteuerelement für die Lautstärke einrichten.
title: Bereitstellen der Lautstärkeregelung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Bereitstellen der Lautstärkeregelung{#provide-volume-control}

Sie können ein Benutzeroberflächensteuerelement für die Lautstärke einrichten.

1. Warten Sie, bis die MediaPlayer-Instanz für diesen Befehl einen gültigen Status aufweist.

   Jeder Status außer RELEASED ist gültig.
1. Rufen Sie die Volumensatzmethode auf der `MediaPlayer` -Instanz, um die Lautstärke festzulegen.

   ```
   public function set volume(value:Number):void
   ```

   Der Wert für das Volumen stellt das angeforderte Volumen dar, ausgedrückt als Anteil des maximalen Volumens, wobei 0 stumm und 1 das maximale Volumen ist.

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
      <li id="li_B00BC6F4812D4000891358F762C8E492">Das Ergebnis ist zwischen 0 und 1 </li> 
      <li id="li_03B7F30662554F299320040CAC2DEB7A">1, wenn das Ergebnis größer als 1 ist </li> 
      </ul> <p>Tipp: Diese Logik verarbeitet Werte, die von Kunden basierend auf früheren Versionen der Variablen 
      <span class="codeph">phrases/primetime-sdk-name</span>, wobei die Volumenwerte zwischen 0 und 100 lagen. </p> </td> 
   </tr> 
   </tbody> 
   </table>
