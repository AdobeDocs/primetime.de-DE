---
title: Befehlszeilenverwendung
description: Befehlszeilenverwendung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Befehlszeilenverwendung {#command-line-usage}

Bevor Sie Media Packager verwenden, stellen Sie sicher, dass Sie die unter Anforderungen aufgelisteten Anforderungen erfüllen und dass die Konfigurationsdatei die erforderlichen Informationen enthält (siehe Konfigurationsdatei im Abschnitt *Verwenden der Adobe Access Reference-Implementierungen*.

Media Packager befindet sich im [!DNL \Reference Implementation\Command Line tools] auf der DVD. Verwenden Sie die folgende Syntax, um eine einzelne Datei zu verschlüsseln:

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

* `source` ist die zu verschlüsselende Datei.
* `dest` Gibt an, wo der verschlüsselte Inhalt geschrieben wird. Wenn ein Verzeichnis angegeben ist, wird die verschlüsselte Datei in diesem Ordner unter demselben Dateinamen wie die Quelldatei gespeichert. Der Ordner darf jedoch nicht der Ordner sein, der die Quelldatei enthält.

Verwenden Sie die folgende Syntax, um mehrere Dateien mit demselben Schlüssel zu verschlüsseln (für Unterstützung für mehrere Bit-Raten):

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
* `dest-directory` Gibt an, wo der verschlüsselte Inhalt geschrieben wird. Die verschlüsselten Dateien werden in diesem Ordner unter Verwendung der gleichen Dateinamen wie die Quelldateien gespeichert. Der Ordner darf jedoch nicht der Ordner sein, der die Quelldateien enthält.

Verwenden Sie die folgende Syntax, um Informationen zu einer verschlüsselten Datei anzuzeigen:

```
java -jar AdobePackager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  encryptedfile [-e] [-m] 
</i class="+ topic>
```

* `encryptedfile` ist die verschlüsselte Datei.

Verwenden Sie die folgende Syntax, um Informationen zu einer Metadatendatei anzuzeigen:

```
java -jar AdobePackager.jar -dm <metadatafile> [-e]
```

* `metadatafile` ist [!DNL .metadata] -Datei mit den DRM-Metadaten.

>[!NOTE]
>
>Während der Verpackung generiert der Media Packager standardmäßig keine .header -Datei mehr. Verwenden Sie zum Generieren dieser Datei die `-h` Option während der Verpackung.

Die folgende Tabelle enthält Beschreibungen der Befehlszeilenoptionen, die in der obigen Syntax angezeigt werden:

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Speicherort der Konfigurationsdatei an. Wenn diese Option nicht verwendet wird, sucht der Media Packager nach <span class="filepath"> flashaccessHools.properties </span> im Arbeitsverzeichnis. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <span class="+ topic/ph pr-d/codeph codeph"> encryptedfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Zeigt Informationen zu einer Datei an, die bereits gepackt wurde. Die Quell- und Zieldateien sind nicht erforderlich. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dm <span class="+ topic/ph pr-d/codeph codeph"> Metadatadatei </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Zeigt Informationen zu vorhandenen Metadaten an. Die Quell- und Zieldateien sind nicht erforderlich. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Verwenden Sie diese Option mit <span class="codeph"> -d </span> , um Richtlinien aus einer gepackten Datei zu extrahieren. Eine Datei wird mit dem Dateinamen und der Richtlinienkennung im selben Ordner wie die verschlüsselte Datei erstellt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Verwenden Sie <span class="codeph"> -d </span> , um den DRM-Header aus einer gepackten Datei zu extrahieren. Eine Datei wird unter Verwendung des Dateinamens und der Erweiterung im selben Ordner wie die verschlüsselte Datei erstellt <span class="filepath"> .header </span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt eine eindeutige Kennung für dieses Inhaltselement an. Wenn keine Kennung angegeben ist, wird der Name der Zieldatei verwendet. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-k <span class="+ topic/ph pr-d/codeph codeph"> key </span>= <span class="+ topic/ph pr-d/codeph codeph"> value </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt einen benutzerdefinierten Schlüssel/Wert zum Hinzufügen zu Inhaltsmetadaten an. Mehrere <span class="codeph"> -k </span> -Optionen angegeben werden. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Verwenden Sie diese Option mit <span class="codeph"> -d </span> , um Metadaten aus einer gepackten Datei zu extrahieren. Eine Datei wird im selben Verzeichnis wie die verschlüsselte Datei erstellt, wobei der Dateiname und die Erweiterung verwendet werden. <span class="codeph"> .metadata </span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noconsole </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und <span class="codeph"> -o </span> nicht festgelegt ist, wird ein Fehler zurückgegeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Überschreibt die Zieldatei ohne Eingabeaufforderung, sofern sie bereits vorhanden ist. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> filename [domain-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Namen der Datei an, die die Richtlinie enthält. Wenn für die Richtlinie eine Domänenregistrierung bei einem Server erforderlich ist, der ein anderes als das in der Eigenschaftendatei angegebene Transportzertifikat verwendet, muss auch das Domänentransportzertifikat bereitgestellt werden. </p> <p class="- topic/p ">Mehrere <span class="codeph"> -p </span> -Optionen angegeben werden, und der Client verwendet standardmäßig die erste. Die in der Befehlszeile angegebenen Werte haben Vorrang vor den in der Konfigurationsdatei angegebenen Werten. </p> </td> 
  </tr> 
 </tbody> 
</table>
