---
seo-title: Konfigurationsdateieigenschaften
title: Konfigurationsdateieigenschaften
uuid: f0d36240-e5fa-4bf9-9a82-7e963d03cdd0
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Konfigurationsdateieigenschaften {#configuration-file-properties}

Geben Sie vor dem Ausführen von Media Packager Werte für die Media Packager-Eigenschaften an. Die Konfigurationsdatei gibt die folgenden Eigenschaften an. Bei Eigenschaftsnamen, die * n* enthalten, steht *n* für eine Ganzzahl, die mit 1 beginnt und für jede Instanz der Eigenschaft erhöht wird.

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
   <td colname="2" class="- topic/entry ">Gibt an, ob Skriptdaten in FLVs verschlüsselt werden sollen. <i class="+ topic/ph hi-d/i ">onMetaData</i> - und <i class="+ topic/ph hi-d/i ">onXMP</i> -Skript-Daten-Tags werden nie verschlüsselt, auch wenn diese Option aktiviert ist. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt die Videoverschlüsselungsstufe an. Der Wert high wird zum Verschlüsseln aller Videoinhalte verwendet, während mittel- und niedrige Werte zum Verschlüsseln von Teilen des Videoinhalts für F4V-Dateien mit H.264-Inhalt verwendet werden. </p> <p class="- topic/p ">value = <span class="codeph"> high| medium| niedrig</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnverschlüsselt</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn der Wert größer als 0 ist, wird die angegebene Anzahl von Sekunden Inhalt am Anfang der Datei nicht verschlüsselt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Lizenzserver-Zertifikatdatei, die zum Verschlüsseln des Schlüssels verwendet wird. Die <span class="codeph"> encrypt.keys.asymmetric.certfile</span> -Eigenschaft gibt eine Datei an, die nur das Zertifikat enthält (entweder das PEM- oder DAS-Format ist akzeptabel). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Diese Eigenschaft wird wiederholt verwendet, um eine Liste von Richtlinien zu erstellen, die auf den Inhalt angewendet werden sollen. <span class="codeph"> n</span> ist eine Ganzzahl mit einem Wert größer/gleich 1. Der Client verwendet standardmäßig die erste Instanz. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die URL des Lizenzservers. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Transportzertifikat für den Lizenzserver. Diese Eigenschaft gibt eine <span class="filepath"> .cer</span> -Datei an, die nur das Zertifikat enthält (entweder das PEM- oder DAS-Format ist zulässig). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die PKCS12-Datei, die die Anmeldeinformationen des Pakets zum Signieren von Inhalten enthält. Die Datei <span class="codeph"> encrypt.sign.certfile</span> sollte auf eine <span class="filepath"> .pfx</span> -Datei verweisen, die ein Zertifikat und einen privaten Schlüssel enthält. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Kennwort zum Schutz der Datei, die durch <span class="codeph"> encrypt.sign.certfile</span>angegeben wird. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Legt die Mindestserverversion fest, die erforderlich ist, um Lizenzen für die Inhalte auszustellen, die verpackt werden. Geben Sie x (Adobe Access x.0) an, wobei x = die Hauptveröffentlichungsnummer ist. Server vor Adobe Access 3.0 unterstützen diese Einstellung nicht. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n.domain.transportcert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn eine Richtlinie <span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.n</span> die Domänenregistrierung bei einem Server erfordert, der ein anderes Transportzertifikat verwendet als in " <span class="+ topic/ph pr-d/codeph codeph"> encrypt.license.servercert</span>"angegeben, muss das Domänentransportzertifikat bereitgestellt werden. </p> <p class="- topic/p ">Diese Eigenschaft gibt eine Datei an, die nur das Zertifikat enthält (entweder das PEM- oder DAS-Format ist akzeptabel). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geben Sie den Lizenzschlüssel an. Wenn kein Schlüssel angegeben ist, wird der Schlüssel zufällig generiert. Wenn die Schlüsselrotation nicht aktiviert ist, ist dies der Schlüssel zum Verschlüsseln des Inhalts. </p> <p class="- topic/p ">Wenn die Schlüsseldrehung aktiviert ist, wird dieser Schlüssel zum Schutz der Drehschlüssel verwendet. Der Schlüssel muss 16 Byte lang sein und als Hexadezimalwerte angegeben werden. Leerzeichen zwischen den Hex-Werten sind optional. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, ob die Schlüsseldrehung aktiviert ist. Bei der Einstellung false (Standard) ist die Schlüsselrotation deaktiviert und der Master-CEK wird verwendet, um alle Beispiele im Inhalt zu verschlüsseln. </p> <p class="- topic/p ">Wenn "true"festgelegt ist, wird die Schlüsselrotation aktiviert und verschiedene Schlüssel können verwendet werden, um Teile des Inhalts zu verschlüsseln. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Sequenz gedrehter Schlüssel, die zum Verschlüsseln von Inhalten verwendet werden, wenn die Schlüsseldrehung aktiviert ist. Wenn keine Schlüssel angegeben sind, werden Schlüssel zufällig generiert. Die Schlüssel müssen 16 Byte lang sein und als Hexadezimalwerte angegeben werden. </p> <p class="- topic/p ">Leerzeichen zwischen den Hex-Werten sind optional. <i class="+ topic/ph hi-d/i ">n</i> muss monotonisch erhöht werden, beginnend mit 1. Wenn mehrere Schlüssel angegeben sind, werden die Schlüssel in der angegebenen Reihenfolge durchlaufen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt das Intervall (in Sekunden) an, in dem ein Rotationsschlüssel zum Verschlüsseln von Inhaltsmustern verwendet wird. </p> <p class="- topic/p ">Nachdem diese Zeit im Inhalt verschlüsselt wurde, wird der nächste Rotationsschlüssel verwendet. Wenn die Schlüsseldrehung aktiviert ist und kein Intervall angegeben ist, werden die Schlüssel alle 15 Minuten gedreht. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn "true", gibt es keinen Lizenzserver, von dem die Lizenzen bezogen werden können. Lizenzen müssen eingebettet oder außerhalb des Bandes erworben werden. Der Standardwert ist "false", wenn nicht angegeben. Wird nur in Adobe Access Professional unterstützt. </p> </td> 
  </tr> 
 </tbody> 
</table>

