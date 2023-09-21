---
title: Konfigurationsdateieigenschaften
description: Konfigurationsdateieigenschaften
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Konfigurationsdateieigenschaften {#configuration-file-properties}

Geben Sie vor dem Ausführen von Media Packager Werte für die Media Packager-Eigenschaften an. Die Konfigurationsdatei gibt die folgenden Eigenschaften an. Für Eigenschaftsnamen, die &quot;n*&quot;enthalten, *n* stellt eine Ganzzahl dar, die mit 1 beginnt und für jede Instanz der Eigenschaft erhöht wird.

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
   <td colname="2" class="- topic/entry ">Gibt an, ob Skriptdaten in FLVs verschlüsselt werden sollen. <i class="+ topic/ph hi-d/i ">onMetaData</i> und <i class="+ topic/ph hi-d/i ">onXMP</i> Skript-Daten-Tags werden nie verschlüsselt, auch wenn diese Option aktiviert ist. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt die Videoverschlüsselungsstufe an. Der Wert high wird zum Verschlüsseln aller Videoinhalte verwendet, während der Wert medium und low zum Verschlüsseln von Teilen des Videoinhalts für F4V-Dateien mit H.264-Inhalt verwendet wird. </p> <p class="- topic/p ">value = <span class="codeph"> high | medium | niedrig</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnencrypted</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn der Wert größer als 0 ist, wird die angegebene Anzahl von Sekunden Inhalt am Anfang der Datei nicht verschlüsselt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Zertifikatdatei des Lizenzservers, die zum Verschlüsseln des Schlüssels verwendet wird. Die <span class="codeph"> encrypt.keys.asymmetric.certfile</span> -Eigenschaft gibt eine Datei an, die nur das Zertifikat enthält (entweder das PEM- oder DAS DER-Format ist zulässig). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Diese Eigenschaft wird wiederholt zum Erstellen einer Liste von Richtlinien verwendet, die auf den Inhalt angewendet werden sollen. <span class="codeph"> n</span> ist eine Ganzzahl, deren Wert 1 oder höher ist. Der Client verwendet standardmäßig die erste Instanz. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Lizenzserver-URL. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Transportzertifikat für den Lizenzserver. Diese Eigenschaft gibt eine <span class="filepath"> .cer</span> -Datei, die nur das Zertifikat enthält (entweder das PEM- oder DAS DER-Format ist zulässig). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die PKCS12-Datei mit Paketanmeldeinformationen zum Signieren von Inhalten. Die <span class="codeph"> encrypt.sign.certfile</span> sollte sich auf eine <span class="filepath"> .pfx</span> -Datei, die ein Zertifikat und einen privaten Schlüssel enthält. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Kennwort zum Schutz der Datei, die durch <span class="codeph"> encrypt.sign.certfile</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Legt die erforderliche Mindestserverversion fest, um Lizenzen für die gepackten Inhalte auszustellen. Geben Sie x (Adobe-Zugriff x.0) an, wobei x = die Hauptversionsnummer ist. Server vor Adobe Access 3.0 unterstützen diese Einstellung nicht. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n.domain.transport.cert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn eine Richtlinie <span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.n</span> erfordert eine Domänenregistrierung bei einem Server, der ein anderes Transportzertifikat verwendet als in <span class="+ topic/ph pr-d/codeph codeph"> encrypt.license.servercert</span>muss das Domänentransportzertifikat bereitgestellt werden. </p> <p class="- topic/p ">Diese Eigenschaft gibt eine Datei an, die nur das Zertifikat enthält (entweder das PEM- oder DAS DER-Format ist zulässig). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geben Sie den Lizenzschlüssel an. Wenn kein Schlüssel angegeben ist, wird der Schlüssel nach dem Zufallsprinzip generiert. Wenn die Schlüsselrotation nicht aktiviert ist, ist dies der Schlüssel zum Verschlüsseln des Inhalts. </p> <p class="- topic/p ">Wenn die Schlüsselrotation aktiviert ist, wird dieser Schlüssel zum Schutz der Drehschlüssel verwendet. Der Schlüssel muss 16 Byte lang sein und als Hex-Werte angegeben werden. Leerzeichen zwischen den Hex-Werten sind optional. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, ob die Schlüsselrotation aktiviert ist. Wenn der Wert auf false (Standard) gesetzt ist, ist die Schlüsselrotation deaktiviert und der Master-CEK wird verwendet, um alle Beispiele im Inhalt zu verschlüsseln. </p> <p class="- topic/p ">Wenn der Wert auf "true"gesetzt ist, wird die Schlüsselrotation aktiviert und es können verschiedene Schlüssel verwendet werden, um Teile des Inhalts zu verschlüsseln. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Reihenfolge der gedrehten Schlüssel, die zum Verschlüsseln von Inhalten verwendet werden, wenn die Schlüsselrotation aktiviert ist. Wenn keine Schlüssel angegeben sind, werden Schlüssel nach dem Zufallsprinzip generiert. Die Schlüssel müssen eine Länge von 16 Byte aufweisen und als Hex-Werte angegeben werden. </p> <p class="- topic/p ">Leerzeichen zwischen den Hex-Werten sind optional. <i class="+ topic/ph hi-d/i ">n</i> müssen monoton erhöht werden, beginnend mit 1. Wenn mehrere Schlüssel angegeben sind, werden die Schlüssel in der angegebenen Reihenfolge durchlaufen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt das Intervall (in Sekunden) an, in dem ein Rotationsschlüssel zum Verschlüsseln von Inhaltsmustern verwendet wird. </p> <p class="- topic/p ">Nachdem diese Zeit im Inhalt verschlüsselt wurde, wird der nächste Rotationsschlüssel verwendet. Wenn die Schlüsselrotation aktiviert ist und kein Intervall angegeben ist, werden die Schlüssel alle 15 Minuten gedreht. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn "true", gibt es keinen Lizenzserver, von dem die Lizenzen abgerufen werden können. Lizenzen müssen eingebettet oder außerhalb des Band erworben werden. Der Standardwert ist "false", wenn nicht angegeben. Wird nur in Adobe Access Professional unterstützt. </p> </td> 
  </tr> 
 </tbody> 
</table>
