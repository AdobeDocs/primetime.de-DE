---
title: DRM-Sperrlisten-Manager
description: DRM-Sperrlisten-Manager
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# DRM-Sperrlisten-Manager {#policy-revocation-list-manager}

Verwenden Sie das Befehlszeilen-Tool Primetime DRM Revocation List Manager ( [!DNL AdobeRevocationListManager.jar]), um Sperrlisten zu erstellen und zu verwalten und zu überprüfen, ob Richtlinien widerrufen wurden.

Vor der Ausführung [!DNL AdobeRevocationListManager.jar], müssen Sie Eigenschaften in der Variablen *Eigenschaften für Listen-Manager und Sperrlisten-Manager für Richtlinienaktualisierungen* -Abschnitt Ihrer Konfigurationsdatei.

>[!NOTE]
>
>Sie können auch alle Eigenschaften des Sperrlisten-Managers über die Befehlszeile angeben.

## Befehlszeilenverwendung im Sperrlisten-Manager {#revocation-list-manager-command-line-usage}

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

* `destfile` gibt den Namen der Datei an, in der die Eigenschaften der Sperrliste gespeichert werden.
* `crlNumber` stellt eine nicht negative Versionsnummer der Zertifikatsperrliste (CRL) dar. Sie müssen diese Zahl jedes Mal erhöhen, wenn die Zertifikatsperrliste aktualisiert wird.

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
   <td colname="2" class="- topic/entry "><p class="- topic/p ">Gibt den Namen und Speicherort der Konfigurationsdatei an. </p><p class="- topic/p ">Wenn Sie keinen Namen oder Speicherort angeben, sucht der DRM-Sperrlisten-Manager nach <span class="filepath"> flashaccessHools.properties</span> im aktuellen Arbeitsverzeichnis. </p><p>Hinweis: Die Optionen, die Sie in der Befehlszeile angeben, haben Vorrang vor den Optionen, die Sie in der Konfigurationsdatei angeben. </p>Gibt den Speicherort der Konfigurationsdatei an. Wenn Sie diese Option nicht anwenden, sucht der Sperrlisten-Manager nach <span class="filepath"> flashaccessHools.properties</span> im Arbeitsverzeichnis. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-d filename</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Zeigt Informationen zur Sperrliste an. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e date</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Optional) Das Ablaufdatum der Sperrliste. Verwenden Sie eines der folgenden Formate: 
     <ul id="ul_2C89F8183C3647C593CB67576D9DED07"> 
      <li id="li_A866F6CBCB464193A119A6609C8F3B2A"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> </li> 
      <li id="li_B5F9F6C995E64464838DDE447848F707"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:Sek</span> </li> 
     </ul>Beispiel: 2009-01-31-14:30:00 steht für den 31. Januar um 14:30 Uhr. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f filename[certfile]</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Fügt alle Einträge aus der vorhandenen Sperrliste hinzu. Sie können nur eine vorhandene Datei angeben. </p> <p class="- topic/p ">Wenn die vorhandene Liste mit einer anderen Berechtigung als der zum Signieren der neuen Liste signiert wurde, müssen Sie die Zertifikatdatei neben der Signatur angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noconsole</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und <span class="codeph"> -o</span> nicht festgelegt ist, tritt ein Fehler auf. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Wenn die Zieldatei bereits vorhanden ist, können Sie sie überschreiben, ohne dazu aufgefordert zu werden. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-r issuameName serialNumber revocationDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Sperrt das Zertifikat, das durch <span class="codeph"> issuameName</span> und <span class="codeph"> serialNumber</span> am angegebenen Datum. Die <span class="codeph"> issuameName</span> muss das Namensformat 509 verwenden. Beispiel: <span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>. </p> <p>Sie müssen die Seriennummern im hexadezimalen Format angeben. Außerdem müssen Sie das Sperrdatum in einem der folgenden Formate angeben: 
     <ul id="ul_1524FBC6818248F3A2B271243E649400"> 
      <li id="li_BC618EA2332D42A59B1B5434CAFFD2AF"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> </li> 
      <li id="li_97F77810D20C4CF2944EFCFF5DFAE467"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:Sek</span> </li> 
     </ul>Beispiel: 12.1.2008 oder 2008-12-1-00:00:00 für Mitternacht am 1. Dezember 2008. Wenn Sie das Sperrdatum nicht angeben, wird das aktuelle Datum automatisch angewendet. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Konfigurationseigenschaften {#configuration-properties}

Sie müssen Anmeldeinformationen anwenden, um Sperrlisten zu signieren. Die folgenden Eigenschaften des Sperrlisten-Managers geben eine PKCS12-Datei an, die Anmeldeinformationen zum Signieren von Sperrlisten (Lizenzserver-Zertifikat) zusammen mit dem Kennwort für das Zertifikat enthält:

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`
