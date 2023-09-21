---
title: Übersicht
description: Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# Listen-Manager für DRM-Richtlinien-Update {#policy-update-list-manager}

Verwenden Sie das Befehlszeilenwerkzeug Primetime DRM Policy Update List Manager ( [!DNL AdobePolicyUpdateListManager.jar]), um Listen zur Aktualisierung von DRM-Richtlinien zu erstellen und zu verwalten und zu überprüfen, ob Richtlinien aktualisiert oder widerrufen wurden.

Bevor Sie das Befehlszeilen-Tool &quot;Policy Update List Manager&quot;ausführen, müssen Sie die Eigenschaften im *Eigenschaften für Listen-Manager und Sperrlisten-Manager für Richtlinienaktualisierungen* -Abschnitt Ihrer Konfigurationsdatei.

>[!NOTE]
>
>Sie können auch alle Eigenschaften des Listen-Managers für Richtlinienaktualisierungen über die Befehlszeile angeben.

## Befehlszeilenverwendung für Listen-Manager für Richtlinienaktualisierungen {#policy-update-list-manager-command-line-usage}

**Erstellen Sie eine Liste mit Richtlinienaktualisierungen:**

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

**Vorhandene Richtlinienaktualisierungsliste anzeigen:**

```
java -jar AdobePolicyUpdateListManager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  filename 
</i class="+ topic>
```

* `filename` Der Name der Datei mit der Liste der aktualisierten Richtlinien.

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
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Namen und Speicherort der Konfigurationsdatei an. </p> <p class="- topic/p ">Wenn Sie keinen Namen oder Speicherort angeben, sucht der DRM Policy Update List Manager nach <span class="filepath"> flashaccessHools.properties </span> im aktuellen Arbeitsverzeichnis. </p> <p>Hinweis: Die Optionen, die Sie in der Befehlszeile angeben, haben Vorrang vor den Optionen, die Sie in der Konfigurationsdatei angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -d filename </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Zeigt Informationen zur Liste der aktualisierten DRM-Richtlinien an. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e date </span> </td> 
   <td colname="2" class="- topic/entry "> <p>(Optional) Das Ablaufdatum der Liste der DRM-Richtlinienaktualisierungen. </p> <p>Format verwenden <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> oder <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:Sek </span> (z. B. 2009-01-31-14:30:00 steht für den 31. Januar um 14:30 Uhr). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -f filename [certfile] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fügt alle Einträge aus der Liste der vorhandenen DRM-Richtlinienaktualisierungen hinzu. Sie können nur eine vorhandene Datei angeben. </p> <p class="- topic/p ">Wenn die vorhandene Liste mit einer anderen Berechtigung als der zum Signieren der neuen Liste signiert wurde, müssen Sie die Zertifikatdatei angeben, damit die Signatur überprüft werden kann. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -noconsole </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und <span class="codeph"> -o </span> nicht festgelegt ist, tritt ein Fehler auf. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn die Zieldatei bereits vorhanden ist, überschreiben Sie sie ohne Eingabeaufforderung. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r policyID </span> <span class="+ topic/ph pr-d/codeph codeph"> date </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Optional) Sperrt die DRM-Richtlinien-ID am angegebenen Datum. Sie können einen optionalen Grund-Code, den Begründungstext und die Grund-URL angeben. Sie müssen eine leere Zeichenfolge ""angeben, um anzugeben, dass für die optionalen Parameter kein Wert angegeben ist. Sie können das Datum unter <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> oder <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:Sek </span> in diesen Formaten. Beispiel: 12.1.2008 oder 2008-12-1-00:00:00 bedeutet Mitternacht am 1. Dezember 2008). Wenn Sie kein Datum angeben, wird das aktuelle Datum automatisch angewendet. Daher muss der Grund-Code größer oder gleich 0 sein. Sie können auch mehrere -r-Optionen angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-rf <span class="+ topic/ph pr-d/codeph codeph"> policyFilename </span> <span class="+ topic/ph pr-d/codeph codeph"> date </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Führt dieselbe Aktion wie die <span class="codeph"> -r </span> -Option. Die DRM-Richtlinienkennung wird jedoch aus einer angegebenen Datei extrahiert. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -u policyFilename " reasonCode" " reasonText" " reasonURL" </span> </td> 
   <td colname="2" class="- topic/entry "> <p>Ersetzt alle übereinstimmenden DRM-Richtlinien in einer Lizenzanfrage durch diese DRM-Richtlinie, indem der angegebene Grund-Code (optional), der Begründungstext (optional) und die Grund-URL (optional) verwendet werden. </p> <p>Eine leere Zeichenfolge ""gibt an, dass Sie für die optionalen Parameter keinen Wert angegeben haben. </p> <p>Der Grund für den Code muss größer oder gleich sein als <span class="codeph"> 0 </span>. Sie können mehrere <span class="codeph"> -u </span> Optionen. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Konfigurationseigenschaften {#configuration-properties}

Die folgenden Eigenschaften des Primetime DRM Policy Update List Manager geben eine PKCS12-Datei an, die Anmeldeinformationen zum Signieren von Sperrlisten (License Server Certificate) sowie ein Kennwort enthält.

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`
