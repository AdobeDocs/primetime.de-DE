---
seo-title: Übersicht
title: Übersicht
uuid: 857390be-dd14-46c0-b8f7-2bc661c515d4
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---


# DRM-Lizenzgenerator {#license-generator}

Verwenden Sie [!DNL AdobeLicenseGenerator.jar] zum Generieren von Lizenzen, ohne dass der Client eine Lizenzanforderung an einen Server senden muss. Anschließend können Sie eine vorab generierte Lizenz in den Inhalt einbetten oder die Lizenz über andere Mechanismen, wie einen einfachen HTTP-Webserver, an den Client senden.

## Befehlszeilenverwendung von License Generator {#license-generator-command-line-usage}

**Eine Lizenz generieren:**

```
java -jar AdobeLicenseGenerator.jar -m 
<i class="+ topic ph hi-d="" i "="">
 metadata 
 <i class="+ topic ph hi-d="" i "="">
   [options]
 </i class="+ topic>
</i class="+ topic>
```

* `metadata` - Enthält die Adobe Primetime DRM-Metadaten.

   Sie können diese Datei mit den `-d -m` Optionen im Media Packager aus geschützten Inhalten abrufen.

**Anzeigen einer zuvor erstellten Lizenz:**

```
java -jar AdobeLicenseGenerator.jar -d 
<i class="+ topic ph hi-d="" i "="">
  license
</i class="+ topic>
```

* `license` - Enthält eine vom Lizenzgenerator generierte Adobe Primetime DRM-Lizenz.

**Tabelle 6: Optionen**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_skr_vry_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Befehlszeilenoption </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-c configfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Namen und den Speicherort der Konfigurationsdatei an. </p> <p class="- topic/p ">Wenn Sie keinen Namen oder Speicherort angeben, sucht der DRM-Lizenzgenerator im aktuellen Arbeitsverzeichnis nach <span class="filepath"> flashaccessStols.properties</span> . </p> <p>Hinweis:  Die Optionen, die Sie in der Befehlszeile angeben, haben Vorrang vor den Optionen, die Sie in der Konfigurationsdatei angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <i class="+ topic/ph hi-d/i "><span class="+ topic/ph pr-d/codeph codeph"> licensefile</span></i> </p> </td> 
   <td colname="2" class="- topic/entry "> Zeigt Informationen über eine bereits generierte Lizenz an. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-leaf-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Generiert eine Laublizenz und speichert die Ausgabe in einer angegebenen Datei. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-m metadata-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Gibt die Inhaltsmetadaten an, für die Sie eine Lizenz generieren müssen. Diese Option ist zum Generieren einer Lizenz erforderlich. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und der Wert <span class="codeph"> -o</span> nicht eingestellt wurde, tritt ein Fehler auf. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Wenn die Zieldatei bereits vorhanden ist, können Sie sie überschreiben, ohne dazu aufgefordert zu werden. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-policy policy policy-num</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Wenn die Metadaten mehrere DRM-Richtlinien enthalten, können Sie die Anzahl der DRM-Richtlinien angeben, die Sie zum Generieren einer Lizenz verwenden können. </p> <p>Wenn Sie die Anzahl der DRM-Richtlinien nicht angeben, wird die erste DRM-Richtlinie automatisch angewendet. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-r Empfänger-cert</span> </td> 
   <td colname="2" class="- topic/entry ">Erstellt eine Lizenz für einen bestimmten Empfänger. Sie können ein Geräte- oder Domänenzertifikat verwenden und mehrere <span class="+ topic/ph pr-d/codeph codeph"> -r- </span>Optionen angeben, um eine Lizenz für mehrere Empfänger zu erstellen. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-root root root-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Erstellt eine Root-Lizenz und speichert die Ausgabe in einer von Ihnen angegebenen Datei. </td> 
  </tr> 
 </tbody> 
</table>

## Konfigurationsdateieigenschaften {#configuration-file-properties}

Bevor Sie License Generator ausführen, müssen Sie Werte für die Eigenschaften von License Generator in der Konfigurationsdatei angeben.

>[!NOTE]
>
>Bei Eigenschaftsnamen, die *n* enthalten, stellt *n* eine Ganzzahl dar, die für jede Instanz der Eigenschaft mit 1 und erhöht wird.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_qk1_rry_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Eigenschaft </th> 
   <th colname="2" class="- topic/entry entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.minClientVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Legt die derzeit unterstützte Mindestversion des Clients fest. Wenn Sie diese Eigenschaft nicht festlegen, werden alle Versionen standardmäßig automatisch unterstützt. </p> <p>Sie können diesen Wert festlegen, um zu steuern, wie ältere Clients auf die Lizenzanforderungen reagieren, die sie nicht unterstützen. Geben Sie <span class="codeph"> x</span> (für Adobe Primetime DRM x.0) an, wobei <span class="codeph"> x</span> eine größere Versionsnummer darstellt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keyServerCert</span> </td> 
   <td colname="2" class="- topic/entry "> Key Server-Zertifikat, ein von der Adobe ausgestelltes Lizenzserverzertifikat, das vom Key Server verwendet wird. Dieses Zertifikat wird nur angewendet, wenn die Metadaten-/DRM-Richtlinie angibt, dass ein Schlüsselserver für wichtigen Versand auf iOS-Geräten erforderlich ist. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> Die PKCS12-Datei, die die Anmeldeinformationen des Lizenzservers zum Signieren von Lizenzen enthält. Diese Eigenschaft muss auf eine .pfx-Datei verweisen, die ein Zertifikat und einen privaten Schlüssel enthält. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry ">Das Kennwort zum Schutz der Datei, die Sie mit der Option <span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile</span> angegeben haben. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.domainca.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Wenn Sie domänengebundene Lizenzen generieren, müssen Sie ein oder mehrere CA-Domänenzertifikate angeben, um die Domänenbehörden anzugeben, denen der Lizenzaussteller vertrauen kann. </p> <p>Wenn der Empfänger ein Domänenzertifikat ist, das nicht von einem der angegebenen Domänenzertifikate ausgestellt wurde, kann keine Lizenz generiert werden. Diese Eigenschaft gibt eine <span class="filepath"> .cer</span> -Datei an, die das Zertifikat im PEM- oder DER DER-Format enthält. <span class="codeph">n</span> muss monotonisch erhöht werden, beginnend mit 1. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <code>licensegen.keys.asymmetric. licenseServerCredential.n</code>
   </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Optionale PKCS12-Datei, die zusätzliche Lizenzserver-Anmeldeinformationen zum Entschlüsseln des CEK in den Metadaten- und DRM-Richtlinien enthält. Sie können zusätzliche Berechtigungen konfigurieren, wenn Inhalte zuvor mit einem Lizenzserver-Zertifikat gepackt wurden, das nicht mit den mit <span class="codeph"> licensegen.sign.certfile</span>angegebenen Anmeldeinformationen identisch ist. Diese Eigenschaft muss auf eine <span class="filepath"> .pfx</span> -Datei verweisen, die ein Zertifikat und einen privaten Schlüssel enthält. <span class="codeph">n</span> muss monotonisch erhöht werden, beginnend mit 1. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <code>licensegen.keys.asymmetric. licenseServerCredential.n.password</code>
   </td> 
   <td colname="2" class="- topic/entry "> <p>Das Kennwort wird angewendet, um die Datei zu schützen, die Sie mit der<span class="+ topic/ph pr-d/codeph codeph"> Eigenschaft licensegen.keys.asymmetric.licenseServerCredential.n</span> angegeben haben. </p> </td> 
  </tr> 
 </tbody> 
</table>