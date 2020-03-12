---
seo-title: DRM Revocation Liste Manager
title: DRM Revocation Liste Manager
uuid: 30ab5f54-4aac-4535-b30c-b4e5dbfbc475
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# DRM Revocation Liste Manager {#policy-revocation-list-manager}

Verwenden Sie das Befehlszeilenwerkzeug Primetime DRM Revocation Liste Manager ( [!DNL AdobeRevocationListManager.jar]), um Listen für den Widerruf zu erstellen und zu verwalten und zu überprüfen, ob Richtlinien widerrufen wurden.

Vor der Ausführung müssen Sie [!DNL AdobeRevocationListManager.jar]die Eigenschaften im Abschnitt *Policy Update Liste Manager und Revocation Liste Manager-Eigenschaften* Ihrer Konfigurationsdatei festlegen.

>[!NOTE]
>
>Sie können auch alle Eigenschaften von Revocation Liste Manager über die Befehlszeile angeben.

## Befehlszeilenverwendung von Revocation Liste Manager {#revocation-list-manager-command-line-usage}

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

* `destfile` gibt den Dateinamen an, in dem die Eigenschaften der Liste zum Sperren gespeichert werden.
* `crlNumber` stellt eine nicht negative Versionsnummer der Zertifikatsperrliste (Certificate Revocation Liste, CRL) dar. Sie müssen diese Zahl jedes Mal erhöhen, wenn die Zertifikatsperrliste aktualisiert wird.

**Tabelle 5: Befehlszeilenoptionen**

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
   <td colname="2" class="- topic/entry "><p class="- topic/p ">Gibt den Namen und den Speicherort der Konfigurationsdatei an. </p><p class="- topic/p ">Wenn Sie keinen Namen oder Speicherort angeben, sucht der DRM Revocation Liste Manager im aktuellen Arbeitsverzeichnis nach " <span class="filepath"> flashaccessStols.properties</span> ". </p><p>Hinweis:  Die Optionen, die Sie in der Befehlszeile angeben, haben Vorrang vor den Optionen, die Sie in der Konfigurationsdatei angeben. </p>Gibt den Speicherort der Konfigurationsdatei an. Wenn Sie diese Option nicht aktivieren, sucht der Revocation Liste Manager im Arbeitsverzeichnis nach <span class="filepath"> flashaccessStols.properties</span> . </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-d Dateiname</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Zeigt Informationen zur Liste zum Sperren an. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e Datum</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Optional) Das Ablaufdatum der Liste zum Widerruf. Verwenden Sie eines der folgenden Formate: 
     <ul id="ul_2C89F8183C3647C593CB67576D9DED07"> 
      <li id="li_A866F6CBCB464193A119A6609C8F3B2A"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> </li> 
      <li id="li_B5F9F6C995E64464838DDE447848F707"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec</span> </li> 
     </ul>Beispiel: 2009-01-31-14:30:00 steht für den 31. Januar um 14:30 Uhr. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f filename[certfile]</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Fügt alle Einträge aus der vorhandenen Liste zum Sperren hinzu. Sie können nur eine vorhandene Datei angeben. </p> <p class="- topic/p ">Wenn die vorhandene Liste mit einer anderen Berechtigung als der zum Signieren der neuen Liste signiert wurde, müssen Sie die zugehörige Zertifikatdatei angeben, um die Signatur zu überprüfen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und <span class="codeph"> -o</span> nicht eingestellt ist, tritt ein Fehler auf. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Wenn die Zieldatei bereits vorhanden ist, können Sie sie überschreiben, ohne dazu aufgefordert zu werden. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-r producerName serialNumber revocationDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Sperrt das Zertifikat, das am angegebenen Datum von <span class="codeph"> Ausstellername</span> und <span class="codeph"> Seriennummer</span> identifiziert wurde. Der <span class="codeph"> Name des Ausstellers</span> muss das Namensformat 509 verwenden. Beispiel: <span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>. </p> <p>Sie müssen die Seriennummern im Hexadezimalformat angeben. Sie müssen das Sperrdatum auch in einem der folgenden Formate angeben: 
     <ul id="ul_1524FBC6818248F3A2B271243E649400"> 
      <li id="li_BC618EA2332D42A59B1B5434CAFFD2AF"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> </li> 
      <li id="li_97F77810D20C4CF2944EFCFF5DFAE467"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec</span> </li> 
     </ul>Beispiel: 2008-12-1 oder 2008-12-1-00:00:00 Uhr für Mitternacht am 1. Dezember 2008. Wenn Sie das Sperrdatum nicht angeben, wird das aktuelle Datum automatisch angewendet. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Konfigurationseigenschaften {#configuration-properties}

Sie müssen Anmeldeinformationen anwenden, um Listen zum Signieren von Sperren zu signieren. Die folgenden Eigenschaften von Revocation Liste Manager geben eine PKCS12-Datei mit Anmeldeinformationen für die Signierung von Listen zum Sperren (Lizenzserverzertifikat) und dem Kennwort für das Zertifikat an:

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`