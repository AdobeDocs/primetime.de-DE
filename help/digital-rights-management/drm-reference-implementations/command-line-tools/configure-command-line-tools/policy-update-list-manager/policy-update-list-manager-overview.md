---
title: Übersicht
description: Übersicht
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# DRM Policy Update Liste Manager {#policy-update-list-manager}

Verwenden Sie das Befehlszeilenwerkzeug Primetime DRM Policy Update Liste Manager ( [!DNL AdobePolicyUpdateListManager.jar]), um Listen zur Aktualisierung von DRM-Richtlinien zu erstellen und zu verwalten und zu überprüfen, ob Richtlinien aktualisiert oder widerrufen wurden.

Bevor Sie das Befehlszeilenwerkzeug &quot;Policy Update Liste Manager&quot;ausführen, müssen Sie die Eigenschaften im Abschnitt *Liste-Manager für Richtlinienaktualisierungen und Eigenschaften für Listen-Manager für Sperrung* in Ihrer Konfigurationsdatei festlegen.

>[!NOTE]
>
>Sie können auch alle Eigenschaften von Policy Update Liste Manager über die Befehlszeile angeben.

## Befehlszeilenverwendung von &quot;Policy Update Liste Manager&quot; {#policy-update-list-manager-command-line-usage}

**Erstellen Sie eine Liste zur Richtlinienaktualisierung:**

```
java -jar AdobePolicyUpdateListManager.jar  
<i class="+ topic ph hi-d="" i "="">
  destfile [ 
 <i class="+ topic ph hi-d="" i "="">
   options]  
 </i class="+ topic> 
</i class="+ topic>
```

* `destfile` gibt den Namen der Datei an, in die die DRM-Liste zur Richtlinienaktualisierung geschrieben wird.

**Ansicht einer bestehenden Liste zur Richtlinienaktualisierung:**

```
java -jar AdobePolicyUpdateListManager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  filename 
</i class="+ topic>
```

* `filename` Der Name der Liste der Richtlinienaktualisierung.

**Tabelle 4: Befehlszeilenoptionen**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_ghb_jqy_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Befehlszeilenoption </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Namen und den Speicherort der Konfigurationsdatei an. </p> <p class="- topic/p ">Wenn Sie keinen Namen oder einen Speicherort angeben, sucht der DRM Policy Update Liste Manager im aktuellen Arbeitsverzeichnis nach <span class="filepath"> flashaccessStols.properties </span>. </p> <p>Hinweis:  Die Optionen, die Sie in der Befehlszeile angeben, haben Vorrang vor den Optionen, die Sie in der Konfigurationsdatei angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -d Dateiname  </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Zeigt Informationen zur DRM-Liste zur Richtlinienaktualisierung an. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e Datum  </span> </td> 
   <td colname="2" class="- topic/entry "> <p>(Optional) Das Ablaufdatum der DRM-Liste zur Richtlinienaktualisierung. </p> <p>Verwenden Sie das Format <span class="+ topic/ph pr-d/codeph codeph"> yyy-mm-dd </span> oder <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:sec </span> (z. B. 2009-01-31-14:30:00 steht für den 31. Januar um 20:30 Uhr). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -f filename [certfile]  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fügt alle Einträge aus der Liste zur Aktualisierung der DRM-Richtlinie hinzu. Sie können nur eine vorhandene Datei angeben. </p> <p class="- topic/p ">Wenn die vorhandene Liste mit einer anderen Berechtigung als der zum Signieren der neuen Liste signiert wurde, müssen Sie die zugehörige Zertifikatdatei angeben, um die Signatur zu überprüfen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -noprompt  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und <span class="codeph"> -o </span> nicht eingestellt ist, tritt ein Fehler auf. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn die Zieldatei bereits vorhanden ist, überschreiben Sie sie ohne Eingabeaufforderung. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r policyID  </span> <span class="+ topic/ph pr-d/codeph codeph"> date  </span> "  <span class="+ topic/ph pr-d/codeph codeph"> reasonCode  </span>"  <span class="+ topic/ph pr-d/codeph codeph"> reasonText  </span>"  <span class="+ topic/ph pr-d/codeph codeph"> reasonURL  </span>" </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Optional) Sperrt die DRM-Richtlinien-ID am angegebenen Datum. Sie können optional einen Grund-, Grund- und Grund-URL angeben. Sie müssen eine leere Zeichenfolge ""angeben, um anzugeben, dass für die optionalen Parameter kein Wert angegeben wurde. Sie können das Datum in den folgenden Formaten unter <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> oder <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:sec </span> angeben. Beispiel: 2008-12-1 oder 2008-12-1-00:00:00 steht für Mitternacht am 1. Dezember 2008). Wenn Sie kein Datum angeben, wird das aktuelle Datum automatisch angewendet. Daher muss der Grund-Code größer oder gleich 0 sein. Sie können auch mehrere -r-Optionen angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-rf <span class="+ topic/ph pr-d/codeph codeph"> policyFilename </span> <span class="+ topic/ph pr-d/codeph codeph"> date </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Führt dieselbe Aktion wie die Option <span class="codeph"> -r </span> durch. Der DRM-Richtlinien-Bezeichner wird jedoch aus einer angegebenen Datei extrahiert. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -u policyFilename " reasonCode" " reasonText" " reasonURL"  </span> </td> 
   <td colname="2" class="- topic/entry "> <p>Ersetzt alle passenden DRM-Richtlinien in einer Lizenzanforderung durch diese DRM-Richtlinie unter Verwendung des angegebenen Begründungs-Codes (optional), des Begründungstextes (optional) und der Grund-URL (optional). </p> <p>Eine leere Zeichenfolge ""gibt an, dass Sie keinen Wert für die optionalen Parameter angegeben haben. </p> <p>Der Grund-Code muss größer oder gleich <span class="codeph"> 0 </span> sein. Sie können mehrere <span class="codeph"> -u </span>-Optionen angeben. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Konfigurationseigenschaften {#configuration-properties}

Die folgenden Eigenschaften von Primetime DRM Policy Update Liste Manager geben eine PKCS12-Datei an, die Anmeldeinformationen für das Signieren von Listen zum Sperren (Lizenzserverzertifikat) sowie ein Kennwort enthält.

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`