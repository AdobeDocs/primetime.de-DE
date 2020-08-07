---
description: 'null'
seo-description: 'null'
seo-title: Overview
title: Overview
uuid: f4474837-9460-479d-89c2-dd697e0fb997
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 0%

---


# DRM Media Packager {#media-packager}

Use the Media Packager ( [!DNL AdobePackager.jar]) to specify a DRM policy to apply to your content, and to specify which part of the content to encrypt. For example, you can specify that the packager should encrypt the video data, but not the audio data.

Before you run [!DNL AdobePackager.jar], you must set properties in the Media Packager Properties section of your configuration file.

>[!NOTE]
>
>You can also specify all Media Packager properties from the command line.

## Media Packager command-line usage {#media-packager-command-line-usage}

**Package one file:**

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

* `source` - The name of the file that you want to encrypt.
* `dest` - Der Name der resultierenden verschlüsselten Datei.

   Wenn Sie einen Ordner angeben, wird die verschlüsselte Datei automatisch im angegebenen Ordner mit demselben Dateinamen gespeichert, den Sie als Quelldatei angegeben haben. Sie können jedoch kein Zielverzeichnis angeben, das die Quelldatei enthält.

**Verpacken Sie mehrere Dateien mit demselben Schlüssel** (für Unterstützung mehrerer Bitraten):

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
* `dest-directory` - Der Zielordner, in dem Sie verschlüsselten Inhalt schreiben möchten. Die verschlüsselten Dateien werden in diesem Ordner automatisch unter denselben Dateinamen wie die Quelldateien gespeichert. Der Zielordner kann jedoch keine Quelldateien enthalten.

**Informationen zur Ansicht einer verschlüsselten Datei:**

```
java -jar AdobePackager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  encryptedfile [-e] [-m] 
</i class="+ topic>
```

**View information about a metadata file:**

```
java -jar AdobePackager.jar -dm <metadatafile> [-e]
```

* `metadatafile` ist eine [!DNL .metadata] Datei mit DRM-Metadaten.

>[!NOTE]
>
>During packaging, the Media Packager can no longer generate a [!DNL .header] file by default. To generate a [!DNL .header] file, use the `-h` option during packaging.

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Namen und den Speicherort der Konfigurationsdatei an. </p> <p class="- topic/p ">Wenn Sie keinen Namen oder Speicherort angeben, sucht der DRM Media Packager im aktuellen Arbeitsverzeichnis nach <span class="filepath"> flashaccessStols.properties </span> . </p> <p>Hinweis:  Die Optionen, die Sie in der Befehlszeile angeben, haben Vorrang vor den Optionen, die Sie in der Konfigurationsdatei angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <span class="+ topic/ph pr-d/codeph codeph"> encryptedfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ermöglicht die Ansicht von Informationen zu einer bereits verpackten Datei. </p> <p class="- topic/p ">Die Quell- und Zieldateien sind nicht erforderlich. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dm <span class="+ topic/ph pr-d/codeph codeph"> metadataFile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ermöglicht die Ansicht von Informationen zu vorhandenen Metadaten. </p> <p class="- topic/p ">Die Quell- und Zieldateien sind nicht erforderlich. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Extrahiert DRM-Richtlinien aus einer Paketdatei, wenn Sie diese Option zusammen mit der <span class="codeph"> -d- </span> Option anwenden. </p> <p class="- topic/p ">Eine Datei wird automatisch in demselben Ordner erstellt, in dem sich die verschlüsselte Datei mit einem Dateinamen und einer DRM-Richtlinienkennung befindet. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Extrahiert den DRM-Header aus einer gepackten Datei, wenn Sie diese Option zusammen mit der <span class="codeph"> -d- </span> Option anwenden. </p> <p class="- topic/p ">Eine Datei wird automatisch in demselben Ordner erstellt, in dem sich die verschlüsselte Datei mit dem Dateinamen und der Erweiterung <span class="filepath"> .header befindet </span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt eine eindeutige ID für dieses Inhaltssegment an. </p> <p class="- topic/p ">Wenn Sie keinen Bezeichner angeben, wird der Name der Zieldatei automatisch angewendet. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-k <span class="+ topic/ph pr-d/codeph codeph"> key </span>= <span class="+ topic/ph pr-d/codeph codeph"> value </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt einen benutzerdefinierten Schlüssel/Wert an, der den Inhaltsmetadaten hinzugefügt werden soll. </p> <p class="- topic/p ">Sie können mehrere <span class="codeph"> -k- </span> Optionen angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Extrahieren Sie Metadaten aus einer gepackten Datei, wenn Sie diese Option zusammen mit der <span class="codeph"> -d- </span> Option anwenden. </p> <p class="- topic/p ">Eine Datei wird automatisch im gleichen Verzeichnis wie die verschlüsselte Datei mit einem Dateinamen und einer <span class="codeph"> .metadata- </span> Erweiterung erstellt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noprompt </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. </p> <p class="- topic/p ">Wenn die Zieldatei bereits vorhanden ist und <span class="codeph"> -o nicht festgelegt </span> ist, tritt ein Fehler auf. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Überschreibt die Zieldatei, ohne dass Sie dazu aufgefordert werden, es sei denn, sie ist bereits vorhanden. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> filename [domain-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Specifies the name of the file that includes the DRM policy. </p> <p class="- topic/p ">Wenn die DRM-Richtlinie die Domänenregistrierung bei einem Server erfordert, der ein anderes als das in der Eigenschaftendatei angegebene Transportzertifikat verwendet, müssen Sie das Domänentransportzertifikat bereitstellen. </p> <p class="- topic/p ">You can specify multiple <span class="codeph"> -p </span> options. The client always applies the first option by default. The values that you have specified on the command line takes precedence over those that you have specified in the configuration file. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Configuration properties {#configuration-properties}

<!--<a id="section_3081C60BE54D47569FD1E3793513A2D9"></a>-->

>[!NOTE]
>
>For property names that include* n*, *n* represents an integer that starts with 1 and increases for each instance of the property.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_dx4_mpy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Property </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video</span> </td> 
   <td colname="2" class="- topic/entry "> Indicates whether to encrypt video content. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.audio</span> </td> 
   <td colname="2" class="- topic/entry "> Indicates whether to encrypt audio. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.script</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Gibt an, ob Skriptdaten in mp4s verschlüsselt werden sollen. </p> <p><i class="+ topic/ph hi-d/i ">onMetaData</i> - und <i class="+ topic/ph hi-d/i ">onXMP</i> -Skript-Daten-Tags werden nie verschlüsselt, selbst wenn Sie diese Option aktivieren. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt die Videoverschlüsselungsstufe an. </p> <p class="- topic/p ">Der Wert <span class="codeph"> high</span> wird zum Verschlüsseln aller Videoinhalte verwendet, während die Werte <span class="codeph"> medium</span> und <span class="codeph"> low</span> verwendet werden, um Teile des Videoinhalts für MP4-Dateien zu verschlüsseln, die H.264-Inhalte enthalten. </p> <p class="- topic/p ">value = <span class="codeph"> high | medium | niedrig</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnverschlüsselt</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn ein Wert größer als 0 ist, wird die angegebene Anzahl von Sekunden Inhalt am Anfang der Datei nicht verschlüsselt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">The license server certificate file used to encrypt the key. </p> <p class="- topic/p ">The <span class="codeph"> encrypt.keys.asymmetric.certfile</span> property specifies a file that includes the certificate only (either PEM or DER format is acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Diese Eigenschaft wird wiederholt verwendet, um eine Liste von DRM-Richtlinien zu erstellen, die auf den Inhalt angewendet werden. <span class="codeph"> n</span> steht für eine Ganzzahl mit einem Wert größer/gleich 1. Der Client verwendet standardmäßig die erste Instanz. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die URL des Lizenzservers </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Transportzertifikat für den Lizenzserver. </p> <p class="- topic/p ">Diese Eigenschaft gibt eine <span class="filepath"> .cer</span> -Datei an, die nur das Zertifikat enthält (entweder das PEM- oder DAS-Format ist akzeptabel). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die PKCS12-Datei, die die Anmeldeinformationen des Pakets zum Signieren von Inhalten enthält. </p> <p class="- topic/p ">Die Datei <span class="codeph"> encrypt.sign.certfile</span> muss auf eine <span class="filepath"> .pfx</span> -Datei verweisen, die ein Zertifikat und einen privaten Schlüssel enthält. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Kennwort, das Sie zum Schutz der Datei anwenden können, die durch <span class="codeph"> encrypt.sign.certfile</span>angegeben wurde. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Legt die Mindestversion des Servers fest, die erforderlich ist, um Lizenzen für den zu verpackenden Inhalt auszustellen. </p> <p class="- topic/p ">Geben Sie x (für Primetime DRM x.0) an, wobei x für eine größere Versionsnummer steht. Serverversionen, die vor Adobe Primetime Version 3.0 stehen, unterstützen diese Einstellung nicht. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n .domain.transportcert </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn eine DRM-Richtlinie <span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.n</span> die Domänenregistrierung bei einem Server erfordert, der ein anderes als das in " <span class="+ topic/ph pr-d/codeph codeph"> encrypt.license.servercert</span>"angegebene Transportzertifikat unterstützt, müssen Sie das Domänentransportzertifikat bereitstellen. </p> <p class="- topic/p ">Diese Eigenschaft gibt eine Datei an, die nur das Zertifikat enthält (entweder das PEM- oder DAS-Format ist akzeptabel). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt einen Lizenzschlüssel an. </p> <p class="- topic/p ">Wenn Sie keinen Schlüssel angeben, wird der Schlüssel zufällig generiert. Wenn Sie die Schlüsselrotation nicht aktivieren, können Sie diesen Schlüssel zum Verschlüsseln von Inhalten verwenden. </p> <p class="- topic/p ">Wenn Sie die Schlüsselrotation aktivieren, können Sie diese Taste verwenden, um die Drehtasten zu schützen. Der Schlüssel muss 16 Byte lang sein und als Hexadezimalwerte angegeben werden. Leerzeichen zwischen den Hex-Werten sind optional. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, ob die Schlüsseldrehung aktiviert ist. </p> <p class="- topic/p ">Wenn der Wert auf "false"gesetzt ist (Standardeinstellung), wird die Schlüsselrotation deaktiviert und der Übergeordnet-CEK wird verwendet, um alle Beispiele im Inhalt zu verschlüsseln. </p> <p class="- topic/p ">Bei der Einstellung "true"ist die Schlüsselrotation aktiviert und es können verschiedene Schlüssel verwendet werden, um Segmente beliebiger Inhalte zu verschlüsseln. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Sequenz gedrehter Schlüssel, die Sie angeben können, um Inhalte zu verschlüsseln, wenn die Schlüsseldrehung aktiviert ist. </p> <p class="- topic/p ">Wenn Sie keine Schlüssel angeben, werden Schlüssel zufällig generiert. Die Schlüssel müssen 16 Byte lang sein und als Hexadezimalwerte angegeben werden. </p> <p class="- topic/p ">Whitespace between the Hex values is optional. <i class="+ topic/ph hi-d/i ">n</i> must be monotonically increasing, starting from 1. When you specify multiple keys, then keys are cycled through in the order that you indicated. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Specifies the interval of time in seconds during which you can apply a rotation key to encrypt content samples. </p> <p class="- topic/p ">After the interval of time has elapsed in which the content has been encrypted, then the next rotation key is then applied. If you have enabled key rotation but have not specified any interval of time, then the keys are automatically rotated every 15 minutes. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">If this option is set to true, then a license server from which licenses can be obtained is not available. </p> <p class="- topic/p ">Licenses must be embedded or obtained out-of-band. The default value is set to false unless you specify a different value. This option is only supported in Primetime DRM Professional. </p> </td> 
  </tr> 
 </tbody> 
</table>