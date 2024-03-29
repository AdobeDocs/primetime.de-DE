---
title: Befehlszeilenverwendung
description: Befehlszeilenverwendung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Befehlszeilenverwendung {#command-line-usage}

Verwenden Sie die folgende Syntax, um eine Lizenz einzubetten:

```
    java -jar AdobeLicenseEmbedder.jar  
<i class="+ topic ph hi-d="" i "="">
  sourcefile destfile [options] 
</i class="+ topic>
```

* `sourcefile` ist eine verschlüsselte FLV- oder F4V-Datei.
* `destfile` Gibt an, wo der verschlüsselte Inhalt mit der eingebetteten Lizenz geschrieben wird. Wenn ein Verzeichnis angegeben ist, wird die Datei in diesem Verzeichnis unter Verwendung des gleichen Dateinamens wie die Quelldatei gespeichert. Der Ordner darf jedoch nicht der Ordner sein, der die Quelldatei enthält.

In der folgenden Tabelle werden die Befehlszeilenoptionen beschrieben, die zusammen mit der oben erwähnten Syntax angegeben werden können:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_hnl_2sy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Befehlszeilenoption </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l license-filename </span> </td> 
   <td colname="2" class="- topic/entry "> Name der Datei mit der einzubettenden Lizenz. Mehrere <span class="codeph"> -l </span> -Optionen angegeben werden, um mehrere Lizenzen einzubetten. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -m metadata-filename </span> </td> 
   <td colname="2" class="- topic/entry "> Geben Sie die Inhaltsmetadaten an, für die eine Lizenz generiert werden soll. (Erforderlich zum Generieren einer Lizenz) </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noconsole </span> </td> 
   <td colname="2" class="- topic/entry "> Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und <span class="codeph"> -o </span> nicht festgelegt ist, wird ein Fehler zurückgegeben. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> Wenn die Zieldatei bereits vorhanden ist, überschreiben Sie sie ohne Eingabeaufforderung. </td> 
  </tr> 
 </tbody> 
</table>
