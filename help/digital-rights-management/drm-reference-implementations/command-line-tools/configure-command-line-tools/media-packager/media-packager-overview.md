---
title: Übersicht
description: Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 0%

---

# DRM Media Packager {#media-packager}

Verwenden Sie den Media Packager ( [!DNL AdobePackager.jar]), um eine DRM-Richtlinie anzugeben, die auf Ihren Inhalt angewendet werden soll, und um anzugeben, welcher Teil des Inhalts verschlüsselt werden soll. Sie können beispielsweise angeben, dass der Packager die Videodaten verschlüsseln soll, nicht aber die Audiodaten.

Vor der Ausführung [!DNL AdobePackager.jar]müssen Sie die Eigenschaften im Abschnitt Eigenschaften des Media Packager in Ihrer Konfigurationsdatei festlegen.

>[!NOTE]
>
>Sie können auch alle Media Packager-Eigenschaften über die Befehlszeile angeben.

## Befehlszeilenverwendung in Media Packager {#media-packager-command-line-usage}

**Eine Datei verpacken:**

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

* `source` - Der Name der Datei, die verschlüsselt werden soll.
* `dest` - Der Name der resultierenden verschlüsselten Datei.

  Wenn Sie einen Ordner angeben, wird die verschlüsselte Datei automatisch im angegebenen Verzeichnis mit demselben Dateinamen gespeichert, den Sie als Quelldatei angegeben haben. Sie können jedoch kein Zielverzeichnis angeben, das die Quelldatei enthält.

**Mehrere Dateien mit demselben Schlüssel verpacken** (für Unterstützung mehrerer Bitraten):

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

* `sourcefiles` - Eine Reihe von durch Leerzeichen getrennten Quelleinträgen für die Dateien, die Sie verschlüsseln möchten.
* `dest-directory` - Das Zielverzeichnis, in das Sie verschlüsselten Inhalt schreiben möchten. Die verschlüsselten Dateien werden automatisch in diesem Verzeichnis unter Verwendung derselben Dateinamen wie die Quelldateien gespeichert. Das Zielverzeichnis kann jedoch keine Quelldateien enthalten.

**Informationen zu einer verschlüsselten Datei anzeigen:**

```
java -jar AdobePackager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  encryptedfile [-e] [-m] 
</i class="+ topic>
```

**Informationen zu einer Metadatendatei anzeigen:**

```
java -jar AdobePackager.jar -dm <metadatafile> [-e]
```

* `metadatafile` ist [!DNL .metadata] -Datei, die DRM-Metadaten enthält.

>[!NOTE]
>
>Während der Verpackung kann der Media Packager keine [!DNL .header] -Datei. So generieren Sie eine [!DNL .header] -Datei, verwenden Sie die `-h` Option während der Verpackung.

**Tabelle 3: Optionen**

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Namen und Speicherort der Konfigurationsdatei an. </p> <p class="- topic/p ">Wenn Sie keinen Namen oder Speicherort angeben, sucht der DRM Media Packager nach <span class="filepath"> flashaccessHools.properties </span> im aktuellen Arbeitsverzeichnis. </p> <p>Hinweis: Die Optionen, die Sie in der Befehlszeile angeben, haben Vorrang vor den Optionen, die Sie in der Konfigurationsdatei angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <span class="+ topic/ph pr-d/codeph codeph"> encryptedfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ermöglicht das Anzeigen von Informationen zu einer Datei, die bereits gepackt wurde. </p> <p class="- topic/p ">Die Quell- und Zieldateien sind nicht erforderlich. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dm <span class="+ topic/ph pr-d/codeph codeph"> Metadatadatei </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ermöglicht das Anzeigen von Informationen zu vorhandenen Metadaten. </p> <p class="- topic/p ">Die Quell- und Zieldateien sind nicht erforderlich. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Extrahiert DRM-Richtlinien aus einer gepackten Datei, wenn Sie diese Option in Verbindung mit dem <span class="codeph"> -d </span> -Option. </p> <p class="- topic/p ">Eine Datei wird automatisch im selben Ordner erstellt, in dem sich die verschlüsselte Datei mit einem Dateinamen und einer DRM-Richtlinienkennung befindet. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Extrahiert den DRM-Header aus einer gepackten Datei, wenn Sie diese Option zusammen mit der <span class="codeph"> -d </span> -Option. </p> <p class="- topic/p ">Eine Datei wird automatisch im selben Ordner erstellt, in dem sich die verschlüsselte Datei mit dem Dateinamen und der Erweiterung befindet. <span class="filepath"> .header </span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt eine eindeutige Kennung für dieses Inhaltssegment an. </p> <p class="- topic/p ">Wenn Sie keine Kennung angeben, wird der Name der Zieldatei automatisch angewendet. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-k <span class="+ topic/ph pr-d/codeph codeph"> key </span>= <span class="+ topic/ph pr-d/codeph codeph"> value </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt einen benutzerdefinierten Schlüssel/Wert zum Hinzufügen zu Inhaltsmetadaten an. </p> <p class="- topic/p ">Sie können mehrere <span class="codeph"> -k </span> Optionen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Extrahieren Sie Metadaten aus einer gepackten Datei, wenn Sie diese Option zusammen mit der <span class="codeph"> -d </span> -Option. </p> <p class="- topic/p ">Eine Datei wird automatisch im selben Ordner wie die verschlüsselte Datei mit einem Dateinamen und einer <span class="codeph"> .metadata </span> -Erweiterung. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noconsole </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. </p> <p class="- topic/p ">Wenn die Zieldatei bereits vorhanden ist und <span class="codeph"> -o </span> nicht festgelegt ist, tritt ein Fehler auf. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Überschreibt die Zieldatei, ohne dass Sie dazu aufgefordert werden, es sei denn, sie ist bereits vorhanden. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> filename [domain-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Namen der Datei an, die die DRM-Richtlinie enthält. </p> <p class="- topic/p ">Wenn die DRM-Richtlinie die Domänenregistrierung bei einem Server erfordert, der ein anderes Transportzertifikat als das in der Eigenschaftendatei angegebene verwendet, müssen Sie das Domänentransportzertifikat bereitstellen. </p> <p class="- topic/p ">Sie können mehrere <span class="codeph"> -p </span> Optionen. Der Client wendet standardmäßig immer die erste Option an. Die Werte, die Sie in der Befehlszeile angegeben haben, haben Vorrang vor den Werten, die Sie in der Konfigurationsdatei angegeben haben. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Konfigurationseigenschaften {#configuration-properties}

<!--<a id="section_3081C60BE54D47569FD1E3793513A2D9"></a>-->

>[!NOTE]
>
>Für Eigenschaftsnamen, die &quot;n*&quot;enthalten, *n* steht für eine Ganzzahl, die mit 1 beginnt und für jede Instanz der Eigenschaft erhöht wird.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_dx4_mpy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Eigenschaft </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video</span> </td> 
   <td colname="2" class="- topic/entry "> Gibt an, ob Videoinhalte verschlüsselt werden sollen. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.audio</span> </td> 
   <td colname="2" class="- topic/entry "> Gibt an, ob Audio verschlüsselt werden soll. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.script</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Gibt an, ob Skriptdaten in mp4s verschlüsselt werden sollen. </p> <p><i class="+ topic/ph hi-d/i ">onMetaData</i> und <i class="+ topic/ph hi-d/i ">onXMP</i> Skript-Daten-Tags werden auch dann nie verschlüsselt, wenn Sie diese Option aktivieren. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt die Videoverschlüsselungsstufe an. </p> <p class="- topic/p ">Ein Wert von <span class="codeph"> high</span> wird zum Verschlüsseln aller Videoinhalte verwendet, während Werte von <span class="codeph"> medium</span> und <span class="codeph"> low</span> werden verwendet, um Teile des Videoinhalts für MP4-Dateien zu verschlüsseln, die H.264-Inhalte enthalten. </p> <p class="- topic/p ">value = <span class="codeph"> high | medium | niedrig</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnencrypted</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn ein Wert größer als 0 ist, wird die angegebene Anzahl von Sekunden Inhalt am Anfang der Datei nicht verschlüsselt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Zertifikatdatei des Lizenzservers, die zum Verschlüsseln des Schlüssels verwendet wird. </p> <p class="- topic/p ">Die <span class="codeph"> encrypt.keys.asymmetric.certfile</span> -Eigenschaft gibt eine Datei an, die nur das Zertifikat enthält (entweder das PEM- oder DAS DER-Format ist zulässig). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Diese Eigenschaft wird wiederholt verwendet, um eine Liste von DRM-Richtlinien zu erstellen, die auf den Inhalt angewendet werden sollen. <span class="codeph"> n</span> steht für eine Ganzzahl, deren Wert 1 oder höher ist. Der Client verwendet standardmäßig die erste Instanz. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Lizenzserver-URL </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Transportzertifikat für den Lizenzserver. </p> <p class="- topic/p ">Diese Eigenschaft gibt eine <span class="filepath"> .cer</span> -Datei, die nur das Zertifikat enthält (entweder das PEM- oder DAS DER-Format ist zulässig). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die PKCS12-Datei, die Paketanmeldeinformationen zum Signieren von Inhalten enthält. </p> <p class="- topic/p ">Die <span class="codeph"> encrypt.sign.certfile</span> muss auf einen <span class="filepath"> .pfx</span> -Datei, die ein Zertifikat und einen privaten Schlüssel enthält. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Kennwort, das Sie anwenden können, um die Datei zu schützen, die durch <span class="codeph"> encrypt.sign.certfile</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Legt die Mindestversion des Servers fest, die erforderlich ist, um Lizenzen für den gepackten Inhalt zu erteilen. </p> <p class="- topic/p ">Geben Sie x (für Primetime DRM x.0) an, wobei x eine Hauptversionsnummer darstellt. Serverversionen, die vor Adobe Primetime Version 3.0 verfügbar sind, unterstützen diese Einstellung nicht. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n .domain.transport.cert </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn eine DRM-Richtlinie <span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.n</span> erfordert eine Domänenregistrierung bei einem Server, der ein anderes als das in <span class="+ topic/ph pr-d/codeph codeph"> encrypt.license.servercert</span>angeben, müssen Sie die Anforderungen an das Domänentransportzertifikat angeben. </p> <p class="- topic/p ">Diese Eigenschaft gibt eine Datei an, die nur das Zertifikat enthält (entweder das PEM- oder DAS DER-Format ist zulässig). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt einen Lizenzschlüssel an. </p> <p class="- topic/p ">Wenn Sie keinen Schlüssel angeben, wird der Schlüssel nach dem Zufallsprinzip generiert. Wenn Sie die Schlüsselrotation nicht aktivieren, können Sie diesen Schlüssel zum Verschlüsseln von Inhalten verwenden. </p> <p class="- topic/p ">Wenn Sie die Schlüsselrotation aktivieren, können Sie diesen Schlüssel verwenden, um die Drehschlüssel zu schützen. Der Schlüssel muss 16 Byte lang sein und als Hex-Werte angegeben werden. Leerzeichen zwischen den Hex-Werten sind optional. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, ob die Schlüsselrotation aktiviert ist. </p> <p class="- topic/p ">Wenn der Wert auf "false"gesetzt ist, was die Standardeinstellung ist, wird die Schlüsselrotation deaktiviert und der Master-CEK wird verwendet, um alle Beispiele im Inhalt zu verschlüsseln. </p> <p class="- topic/p ">Wenn der Wert auf "true"gesetzt ist, wird die Schlüsselrotation aktiviert und es können verschiedene Schlüssel zum Verschlüsseln von Segmenten beliebigen Inhalts verwendet werden. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Reihenfolge der gedrehten Schlüssel, die Sie zum Verschlüsseln von Inhalten festlegen können, wenn die Schlüsselrotation aktiviert ist. </p> <p class="- topic/p ">Wenn Sie keine Schlüssel angeben, werden Schlüssel zufällig generiert. Die Schlüssel müssen eine Länge von 16 Byte aufweisen und als Hex-Werte angegeben werden. </p> <p class="- topic/p ">Leerzeichen zwischen den Hex-Werten sind optional. <i class="+ topic/ph hi-d/i ">n</i> müssen monoton erhöht werden, beginnend mit 1. Wenn Sie mehrere Schlüssel angeben, werden die Schlüssel in der angegebenen Reihenfolge durchlaufen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt das Zeitintervall in Sekunden an, in dem Sie einen Rotationsschlüssel anwenden können, um Inhaltsbeispiele zu verschlüsseln. </p> <p class="- topic/p ">Nach Ablauf des Zeitintervalls, in dem der Inhalt verschlüsselt wurde, wird der nächste Rotationsschlüssel angewendet. Wenn Sie die Schlüsselrotation aktiviert, aber kein Zeitintervall angegeben haben, werden die Schlüssel alle 15 Minuten automatisch gedreht. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn diese Option auf true gesetzt ist, ist kein Lizenzserver verfügbar, von dem Lizenzen abgerufen werden können. </p> <p class="- topic/p ">Lizenzen müssen eingebettet oder außerhalb des Band erworben werden. Der Standardwert ist "false", es sei denn, Sie geben einen anderen Wert an. Diese Option wird nur in Primetime DRM Professional unterstützt. </p> </td> 
  </tr> 
 </tbody> 
</table>
