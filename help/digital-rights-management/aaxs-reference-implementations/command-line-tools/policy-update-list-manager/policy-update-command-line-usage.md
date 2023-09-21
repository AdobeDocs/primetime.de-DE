---
title: Befehlszeilenverwendung
description: Befehlszeilenverwendung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Befehlszeilenverwendung {#command-line-usage}

Der Listen-Manager für Richtlinienaktualisierungen befindet sich im Ordner \Referenz-Implementierung\Befehlszeilenwerkzeuge auf der DVD. Verwenden Sie die folgende Syntax, um eine Liste mit Richtlinienaktualisierungen zu erstellen:

```
    java -jar AdobePolicyUpdateListManager.jar  
<i class="+ topic ph hi-d="" i "="">
  destfile [ 
 <i class="+ topic ph hi-d="" i "="">
   options]  
 </i class="+ topic> 
</i class="+ topic>
```

* `destfile` gibt an, wo die Liste der Richtlinienaktualisierungen geschrieben wird.

Verwenden Sie die folgende Syntax, um eine vorhandene Liste der Richtlinienaktualisierungen anzuzeigen:

```
    java -jar AdobePolicyUpdateListManager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  filename 
</i class="+ topic>
```

Die folgende Tabelle enthält Beschreibungen der Befehlszeilenoptionen, die in der obigen Syntax angezeigt werden:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_ghb_jqy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Befehlszeilenoption </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Speicherort der Konfigurationsdatei an. Wenn diese Option nicht verwendet wird, sucht der Listen-Manager für Richtlinienaktualisierungen nach <span class="filepath"> flashaccessHools.properties </span> im Arbeitsverzeichnis. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -d filename </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Zeigt Informationen zur Liste der Richtlinienaktualisierungen an. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e date </span> </td> 
   <td colname="2" class="- topic/entry "> (Optional) Das Ablaufdatum der Liste der Richtlinienaktualisierungen. Format verwenden <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> oder <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:Sek </span> (z. B. 2009-01-31-14:30:00 steht für den 31. Januar um 14:30 Uhr). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -f filename [certfile] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fügt alle Einträge aus der Liste der vorhandenen Richtlinienaktualisierungen hinzu. Es kann nur eine vorhandene Datei angegeben werden. </p> <p class="- topic/p ">Wenn diese vorhandene Liste mit einer anderen Berechtigung als der zum Signieren der neuen Liste signiert wurde, geben Sie die Zertifikatdatei an, damit die Signatur überprüft werden kann. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -noconsole </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und <span class="codeph"> -o </span> nicht festgelegt ist, wird ein Fehler zurückgegeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn die Zieldatei bereits vorhanden ist, überschreiben Sie sie ohne Eingabeaufforderung. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r policyID </span> <span class="+ topic/ph pr-d/codeph codeph"> date </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Optional) Sperrt die Richtlinien-ID am angegebenen Datum. Es kann auch ein optionaler Grund-Code, Begründungstext und Grund-URL angegeben werden. Geben Sie eine leere Zeichenfolge ""an, um anzugeben, dass für die optionalen Parameter kein Wert angegeben ist. Geben Sie das Datum als <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> oder <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:Sek </span> (z. B. 2008-12-1 oder 2008-12-1-00:00:00 für Mitternacht am 1. Dezember 2008). Wenn kein Datum angegeben ist, wird das aktuelle Datum verwendet. Der Grund-Code muss größer oder gleich 0 sein. Es können mehrere -r-Optionen angegeben werden. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-rf <span class="+ topic/ph pr-d/codeph codeph"> policyFilename </span> <span class="+ topic/ph pr-d/codeph codeph"> date </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Führt dieselbe Aktion wie das -r-Flag aus, extrahiert jedoch die Richtlinienkennung aus der angegebenen Datei. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -u policyFilename " reasonCode" " reasonText" " reasonURL" </span> </td> 
   <td colname="2" class="- topic/entry "> <p>Ersetzt alle übereinstimmenden Richtlinien in einer Lizenzanfrage durch diese Richtlinie unter Verwendung des angegebenen Grund-Codes (optional), des Begründungstextes (optional) und der Grund-URL (optional). </p> <p>Geben Sie eine leere Zeichenfolge ""an, um anzugeben, dass für die optionalen Parameter kein Wert angegeben ist. </p> <p>Der Grund für den Code muss größer oder gleich sein als <span class="codeph"> 0 </span>. Mehrere <span class="codeph"> -u </span> -Optionen angegeben werden. </p> </td> 
  </tr> 
 </tbody> 
</table>
