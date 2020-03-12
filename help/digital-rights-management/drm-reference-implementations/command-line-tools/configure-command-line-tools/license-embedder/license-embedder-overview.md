---
seo-title: Übersicht
title: Übersicht
uuid: 5487d1d3-7eb8-410d-a4b1-cde3e94c00a1
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# DRM-Lizenzeinbettung {#license-embedder}

Verwenden Sie diese Option, [!DNL AdobeLicenseEmbedder.jar] um vorab generierte Lizenzen in Inhalte einzubetten, die vom Media Packager geschützt werden.

## Befehlszeilenverwendung für License Embedder {#license-embedder-command-line-usage}

```
java -jar AdobeLicenseEmbedder.jar sourcefile destfile [options]
```

* `sourcefile` stellt eine verschlüsselte Datei dar.
* `destfile` gibt den Namen der Datei an, in der der verschlüsselte Inhalt mit der eingebetteten Lizenz gespeichert wird.

   Wenn Sie einen Ordner angeben, wird die Datei im Zielverzeichnis gespeichert. Der Name der Quelldatei wird auch der Name der Datei, die im Zielverzeichnis gespeichert wird.

In der folgenden Tabelle werden die Befehlszeilenoptionen beschrieben, die Sie angeben können:

**Tabelle 7: Optionen**

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
   <td colname="2" class="- topic/entry "> Name der Datei, die die einzubettende Lizenz enthält. Sie können mehrere <span class="codeph"> -l- </span> Optionen angeben, um mehrere Lizenzen einzubetten. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -m metadata-filename </span> </td> 
   <td colname="2" class="- topic/entry "> Gibt die Inhaltsmetadaten an, für die Sie eine Lizenz generieren können. Diese Option ist zum Generieren einer Lizenz erforderlich. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und das <span class="codeph"> -o </span> nicht angewendet wurde, tritt ein Fehler auf. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> Wenn die Zieldatei bereits vorhanden ist, können Sie sie überschreiben, ohne dazu aufgefordert zu werden. </td> 
  </tr> 
 </tbody> 
</table>
