---
title: Befehlszeilenverwendung
description: Befehlszeilenverwendung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Befehlszeilenverwendung {#command-line-usage}

Verwenden Sie die folgende Syntax, um eine Lizenz zu generieren:

```
    java -jar AdobeLicenseGenerator.jar -m 
<i class="+ topic ph hi-d="" i "="">
 metadata 
 <i class="+ topic ph hi-d="" i "="">
   [options]
 </i class="+ topic>
</i class="+ topic>
```

`metadata` ist eine .metadata-Datei, die die Adobe Access DRM-Metadaten enthält. Diese Datei kann mithilfe der `-d -m` Option von Media Packager.

Verwenden Sie die folgende Syntax, um eine zuvor generierte Lizenz anzuzeigen:

```
    java -jar AdobeLicenseGenerator.jar -d 
<i class="+ topic ph hi-d="" i "="">
  license
</i class="+ topic>
```

`license` ist eine Datei, die eine vom Lizenzgenerator generierte Adobe Access-Lizenz enthält.

In der folgenden Tabelle werden die Befehlszeilenoptionen beschrieben, die zusammen mit der oben erwähnten Syntax angegeben werden können:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_skr_vry_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Befehlszeilenoption </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-c configfile</span> </td> 
   <td colname="2" class="- topic/entry "> Geben Sie den Speicherort der Konfigurationsdatei an. Wenn diese Option nicht verwendet wird, sucht der Lizenzgenerator im Arbeitsverzeichnis nach "flashaccess.properties". Die in der Befehlszeile angegebenen Optionen haben Vorrang vor den Optionen in der Konfigurationsdatei. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <i class="+ topic/ph hi-d/i "><span class="+ topic/ph pr-d/codeph codeph"> licensefile</span></i> </p> </td> 
   <td colname="2" class="- topic/entry "> Zeigt Informationen zu einer bereits generierten Lizenz an. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-leaf-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Generieren Sie eine Leaf-Lizenz und schreiben Sie die Ausgabe in eine bestimmte Datei. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-m metadata-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Geben Sie die Inhaltsmetadaten an, für die eine Lizenz generiert werden soll. (Erforderlich zum Generieren einer Lizenz) </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noconsole</span> </td> 
   <td colname="2" class="- topic/entry ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und <span class="codeph"> -o</span> nicht festgelegt ist, wird ein Fehler zurückgegeben. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Wenn die Zieldatei bereits vorhanden ist, überschreiben Sie sie ohne Eingabeaufforderung. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-policy-num</span> </td> 
   <td colname="2" class="- topic/entry "> Wenn die Metadaten mehrere Richtlinien enthalten, geben Sie die Nummer der Richtlinie an, die zum Generieren der Lizenz verwendet werden soll (beginnend bei 1). Wenn kein Wert angegeben ist, wird die erste Richtlinie verwendet. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-r recipient-cert</span> </td> 
   <td colname="2" class="- topic/entry ">Generieren Sie eine Lizenz für den angegebenen Empfänger. Es kann ein Geräte- oder Domänenzertifikat verwendet werden. Mehrere <span class="+ topic/ph pr-d/codeph codeph"> -r </span>-Optionen angegeben werden, um eine Lizenz für mehrere Empfänger zu erstellen. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-root root root-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Generieren Sie eine Stammlizenz und schreiben Sie die Ausgabe in die angegebene Datei. </td> 
  </tr> 
 </tbody> 
</table>
