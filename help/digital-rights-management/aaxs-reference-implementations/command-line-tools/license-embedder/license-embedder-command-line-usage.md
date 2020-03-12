---
seo-title: Befehlszeilenverwendung
title: Befehlszeilenverwendung
uuid: 72117619-a723-49d3-9aa9-5eefcf5b0916
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Befehlszeilenverwendung {#command-line-usage}

Verwenden Sie zum Einbetten einer Lizenz die folgende Syntax:

```
    java -jar AdobeLicenseEmbedder.jar  
<i class="+ topic ph hi-d="" i "="">
  sourcefile destfile [options] 
</i class="+ topic>
```

* `sourcefile` ist eine verschlüsselte FLV- oder F4V-Datei.
* `destfile` gibt an, wo der verschlüsselte Inhalt mit der eingebetteten Lizenz geschrieben werden soll. Wenn ein Ordner angegeben ist, wird die Datei in diesem Ordner unter demselben Dateinamen wie die Quelldatei gespeichert, der Ordner darf jedoch nicht der Ordner sein, der die Quelldatei enthält.

In der folgenden Tabelle werden die Befehlszeilenoptionen beschrieben, die zusammen mit der zuvor erwähnten Syntax angegeben werden können:

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
   <td colname="2" class="- topic/entry "> Name der Datei, die die einzubettende Lizenz enthält. Es können mehrere <span class="codeph"> -l- </span> Optionen angegeben werden, um mehrere Lizenzen einzubetten. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -m metadata-filename </span> </td> 
   <td colname="2" class="- topic/entry "> Geben Sie die Inhaltsmetadaten an, für die eine Lizenz generiert werden soll. (Zum Generieren der Lizenz erforderlich) </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und <span class="codeph"> -o nicht festgelegt </span> ist, wird ein Fehler zurückgegeben. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> Wenn die Zieldatei bereits vorhanden ist, überschreiben Sie sie ohne Eingabeaufforderung. </td> 
  </tr> 
 </tbody> 
</table>

