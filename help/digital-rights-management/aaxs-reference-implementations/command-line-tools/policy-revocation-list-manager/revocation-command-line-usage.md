---
seo-title: Befehlszeilenverwendung
title: Befehlszeilenverwendung
uuid: 273e9d3b-efeb-46fa-a4b1-f13247b4e498
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Befehlszeilenverwendung {#command-line-usage}

Revocation Liste Manager befindet sich im Ordner \Reference Implementation\Command Line Tools auf der DVD. Verwenden Sie zum Ausführen des Tools eine der folgenden Syntax:

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

* `destfile` gibt an, wo die Liste zum Widerruf geschrieben werden soll.
* `crlNumber` ist eine nicht negative Versionsnummer der Zertifikatsperrliste (Certificate Revocation Liste, CRL). Diese Zahl sollte bei jeder Aktualisierung der Zertifikatsperrliste erhöht werden.

Die folgende Tabelle enthält Beschreibungen der Befehlszeilenoptionen, die in der obigen Syntax aufgeführt sind:

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
   <td colname="2" class="- topic/entry ">Gibt den Speicherort der Konfigurationsdatei an. Wenn diese Option nicht verwendet wird, sucht der Revocation Liste Manager im Arbeitsverzeichnis nach <span class="filepath"> flashaccessStols.properties</span> . </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-d Dateiname</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Zeigt Informationen zur Liste zum Sperren an. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e Datum</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Optional) Das Ablaufdatum der Liste zum Widerruf. Verwenden Sie das Format <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> oder <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec</span> (z. B. stellt 2009-01-31-14:30:00 den 31. Januar um 14:30 Uhr dar). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f filename[certfile]</span> </td> 
   <td colname="2" class="- topic/entry ">Fügt alle Einträge aus der vorhandenen Liste zum Sperren hinzu. Es kann nur eine vorhandene Datei angegeben werden. <p class="- topic/p ">Wenn diese bestehende Liste mit einer anderen Berechtigung als der zum Signieren der neuen Liste signiert wurde, geben Sie als Nächstes die Zertifikatdatei an, damit die Signatur überprüft werden kann. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und -o nicht eingestellt ist, wird ein Fehler zurückgegeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Wenn die Zieldatei bereits vorhanden ist, überschreiben Sie sie ohne Eingabeaufforderung. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-r producerName serialNumber revocationDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Sperrt das Zertifikat, das am angegebenen Datum durch <span class="codeph"> Ausstellername</span> und <span class="codeph"> Seriennummer</span> identifiziert wurde. Der <span class="codeph"> Ausstellername</span> muss dem Namensformat 509 entsprechen (z. B. <span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>). Geben Sie die Seriennummern als Hexadezimalformat an. Geben Sie das Widerrufsdatum als <span class="+ topic/ph pr-d/codeph codeph">yyy-mm-dd</span> oder <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec</span>an, z. B. 2008-12-1 oder 2008-12-1-00:00:00 für Mitternacht am 1. Dezember 2000008. Wenn das Sperrdatum nicht angegeben ist, wird das aktuelle Datum verwendet. </p> </td> 
  </tr> 
 </tbody> 
</table>

