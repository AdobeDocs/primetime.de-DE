---
title: Befehlszeilenverwendung
description: Befehlszeilenverwendung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Befehlszeilenverwendung {#command-line-usage}

Der Sperrlisten-Manager befindet sich im Ordner \Reference Implementation\Command Line Tools auf der DVD. Verwenden Sie eine der folgenden Syntaxen, um das Tool auszuführen:

```
    java -jar AdobeRevocationListManager.jar 
<i class="+ topic ph hi-d="" i "="">
 destfile 
 <i class="+ topic ph hi-d="" i "="">
  crlNumber [
  <i class="+ topic ph hi-d="" i "="">
   options] 
       java -jar AdobeRevocationListManager.jar -d 
   <i class="+ topic ph hi-d="" i "="">
     filename
   </i class="+ topic>
  </i class="+ topic>
 </i class="+ topic>
</i class="+ topic>
```

* `destfile` gibt an, wo die Sperrliste geschrieben wird.
* `crlNumber` ist eine nicht negative Versionsnummer der Zertifikatsperrliste (CRL). Diese Zahl sollte bei jeder Aktualisierung der Zertifikatsperrliste erhöht werden.

Die folgende Tabelle enthält Beschreibungen der Befehlszeilenoptionen, die in der obigen Syntax angezeigt werden:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_a3y_wqy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Befehlszeilenoption </th> 
   <th colname="2" class="- topic/entry entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-c configfile</span> </td> 
   <td colname="2" class="- topic/entry ">Gibt den Speicherort der Konfigurationsdatei an. Wenn diese Option nicht verwendet wird, sucht der Sperrlisten-Manager nach <span class="filepath"> flashaccessHools.properties</span> im Arbeitsverzeichnis. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-d filename</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Zeigt Informationen zur Sperrliste an. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e date</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Optional) Das Ablaufdatum der Sperrliste. Format verwenden <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> oder <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:Sek</span> (z. B. 2009-01-31-14:30:00 steht für den 31. Januar um 14:30 Uhr). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f filename[certfile]</span> </td> 
   <td colname="2" class="- topic/entry ">Fügt alle Einträge aus der vorhandenen Sperrliste hinzu. Es kann nur eine vorhandene Datei angegeben werden. <p class="- topic/p ">Wenn diese vorhandene Liste mit einer anderen Berechtigung als der zum Signieren der neuen Liste signiert wurde, geben Sie als Nächstes die Zertifikatdatei an, damit die Signatur überprüft werden kann. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noconsole</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden und -o nicht festgelegt ist, wird ein Fehler zurückgegeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Wenn die Zieldatei bereits vorhanden ist, überschreiben Sie sie ohne Eingabeaufforderung. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-r issuameName serialNumber revocationDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Löscht das Zertifikat, das durch <span class="codeph"> issuameName</span> und <span class="codeph"> serialNumber</span> am angegebenen Datum. Die <span class="codeph"> issuameName</span> muss dem Namensformat 509 entsprechen (z. B. <span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>). Geben Sie Seriennummern in hexadezimaler Form an. Geben Sie das Sperrdatum als <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> oder <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:Sek</span>, z. B. 2008-12-1 oder 2008-12-1-00:00:00 für Mitternacht am 1. Dezember 2008. Wenn das Sperrdatum nicht angegeben ist, wird das aktuelle Datum verwendet. </p> </td> 
  </tr> 
 </tbody> 
</table>
