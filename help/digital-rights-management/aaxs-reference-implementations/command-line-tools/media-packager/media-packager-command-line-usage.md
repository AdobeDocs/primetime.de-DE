---
seo-title: Befehlszeilenverwendung
title: Befehlszeilenverwendung
uuid: 5f24f18d-09ef-400a-9404-50a9fcf4316d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Befehlszeilenverwendung {#command-line-usage}

Bevor Sie Media Packager verwenden, stellen Sie sicher, dass Sie die unter &quot;Anforderungen&quot;aufgelisteten Anforderungen erfüllen und dass die Konfigurationsdatei die erforderlichen Informationen enthält (siehe Konfigurationsdatei im Abschnitt *Verwenden der Adobe Access-Referenzimplementierungen*.

Media Packager befindet sich im [!DNL \Reference Implementation\Command Line tools] Ordner auf der DVD. Verwenden Sie zum Verschlüsseln einer einzelnen Datei die folgende Syntax:

```
java -jar AdobePackager.jar  
<i class="+ topic ph hi-d="" i "="">
  source  
 <i class="+ topic ph hi-d="" i "="">
   dest [ 
  <i class="+ topic ph hi-d="" i "="">
    options] 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

* `source` ist die zu verschlüsselnde Datei.
* `dest` gibt an, wo der verschlüsselte Inhalt geschrieben werden soll. Wenn ein Ordner angegeben ist, wird die verschlüsselte Datei in diesem Ordner unter demselben Dateinamen wie die Quelldatei gespeichert. Der Ordner darf jedoch nicht der Ordner sein, der die Quelldatei enthält.

Um mehrere Dateien mit demselben Schlüssel zu verschlüsseln (für Unterstützung mehrerer Bitraten), verwenden Sie die folgende Syntax:

```
java -jar AdobePackager.jar  
<i class="+ topic ph hi-d="" i "="">
  sourcefiles  
 <i class="+ topic ph hi-d="" i "="">
   dest-directory [ 
  <i class="+ topic ph hi-d="" i "="">
    options] 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

* `sourcefiles` ist eine Reihe von durch Leerzeichen getrennten Quelleinträgen, die die zu verschlüsselnden Dateien darstellen.
* `dest-directory` gibt an, wo der verschlüsselte Inhalt geschrieben werden soll. Die verschlüsselten Dateien werden in diesem Ordner unter denselben Dateinamen wie die Quelldateien gespeichert, der Ordner darf jedoch nicht der Ordner sein, der die Quelldateien enthält.

Verwenden Sie zur Ansicht von Informationen zu einer verschlüsselten Datei die folgende Syntax:

```
java -jar AdobePackager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  encryptedfile [-e] [-m] 
</i class="+ topic>
```

* `encryptedfile` ist die verschlüsselte Datei.

Um Informationen zu einer Metadatendatei Ansicht, verwenden Sie die folgende Syntax:

```
java -jar AdobePackager.jar -dm <metadatafile> [-e]
```

* `metadatafile` ist eine [!DNL .metadata] Datei, die die DRM-Metadaten enthält.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Beim Verpacken generiert der Media Packager standardmäßig keine .header-Datei mehr. Um diese Datei zu erstellen, verwenden Sie die `-h` Option beim Verpacken.

Die folgende Tabelle enthält Beschreibungen der Befehlszeilenoptionen, die in der obigen Syntax aufgeführt sind:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_wgz_spy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Befehlszeilenoption </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-c <span class="+ topic/ph pr-d/codeph codeph"> configfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Speicherort der Konfigurationsdatei an. Wenn diese Option nicht verwendet wird, sucht der Media Packager im Arbeitsverzeichnis nach <span class="filepath"> flashaccessStols.properties </span> . </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <span class="+ topic/ph pr-d/codeph codeph"> encryptedfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Zeigt Informationen zu einer Datei an, die bereits verpackt wurde. Die Quell- und Zieldateien sind nicht erforderlich. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dm <span class="+ topic/ph pr-d/codeph codeph"> metadataFile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Zeigt Informationen zu vorhandenen Metadaten an. Die Quell- und Zieldateien sind nicht erforderlich. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Verwenden Sie diese Option mit <span class="codeph"> -d, </span> um Richtlinien aus einer gepackten Datei zu extrahieren. Eine Datei wird unter Verwendung des Dateinamens und der Richtlinien-ID im selben Verzeichnis wie die verschlüsselte Datei erstellt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Verwenden Sie <span class="codeph"> -d, </span> um den DRM-Header aus einer Paketdatei zu extrahieren. Eine Datei wird unter Verwendung des Dateinamens und der Erweiterung <span class="filepath"> .header im selben Verzeichnis wie die verschlüsselte Datei erstellt. </span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt eine eindeutige ID für dieses Inhaltselement an. Wenn kein Bezeichner angegeben ist, wird der Name der Zieldatei verwendet. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-k <span class="+ topic/ph pr-d/codeph codeph"> key </span>= <span class="+ topic/ph pr-d/codeph codeph"> value </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt einen benutzerdefinierten Schlüssel/Wert an, der den Inhaltsmetadaten hinzugefügt werden soll. Es können mehrere <span class="codeph"> -k- </span> Optionen angegeben werden. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Verwenden Sie diese Option mit <span class="codeph"> -d, </span> um Metadaten aus einer gepackten Datei zu extrahieren. Eine Datei wird im selben Verzeichnis wie die verschlüsselte Datei mit dem Dateinamen und der Erweiterung <span class="codeph"> .metadata erstellt </span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noprompt </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und <span class="codeph"> -o nicht festgelegt </span> ist, wird ein Fehler zurückgegeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Überschreibt die Zieldatei ohne Eingabeaufforderung, sofern sie bereits vorhanden ist. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> filename [domain-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Namen der Datei an, die die Richtlinie enthält. Wenn die Richtlinie die Domänenregistrierung bei einem Server erfordert, der ein anderes als das in der Eigenschaftendatei angegebene Transportzertifikat verwendet, muss auch das Domänentransportzertifikat bereitgestellt werden. </p> <p class="- topic/p ">Es können mehrere <span class="codeph"> -p- </span> Optionen angegeben werden, und der Client verwendet standardmäßig die erste. Die in der Befehlszeile angegebenen Werte haben Vorrang vor den in der Konfigurationsdatei angegebenen Werten. </p> </td> 
  </tr> 
 </tbody> 
</table>

