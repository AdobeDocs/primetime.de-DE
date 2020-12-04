---
seo-title: Servereigenschaften-Referenz
title: Servereigenschaften-Referenz
uuid: 24a187fe-9b7d-411f-a358-d10c70a5dd0e
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---


# Referenz zu Servereigenschaften{#server-properties-reference}

<!--<a id="section_EC8810492A454BDBA6013FE376360F4E"></a>-->

## Individualisierungsserver

<table id="table_ats_tk2_jr">  
 <thead> 
  <tr> 
   <th class="entry"> Konfiguration </th> 
   <th class="entry"> Beschreibung </th> 
   <th class="entry"> Beispiel </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> Transportberechtigung </td> 
   <td>Die Transportberechtigung wird verwendet, um vom Client empfangene Anforderungen zu entschlüsseln und die zurückgesendeten Antworten zu signieren. Stellen Sie sicher, dass Sie die Datei <span class="filepath"> AdobeInitial.properties</span> sowohl mit dem Pfad zur Datei mit den Transportberechtigungen als auch mit dem verschlüsselten PKCS12-Kennwort entsprechend konfigurieren. </td> 
   <td> 
    <ul id="ul_itx_fl2_jr"> 
     <li id="li_A2E65253F37245268A41E6B9C958C8DF"><span class="codeph"> cert.i15n.transport.file =  </span> [PKCS12-Datei, die das Zertifikat und den Schlüssel für den Individualisierungstransport enthält] </li> 
     <li id="li_28CDFC0B3D684795AF4708B6D26DF83F"><span class="codeph"> cert.i15n.transport.password =</span> [Verschlüsseltes Kennwort für PKCS12-Datei] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> CA-Berechtigung für Individualisierung </td> 
   <td>Der Individualisierungsserver verwendet die Berechtigung "Individualization CA", um die ausgegebenen Computerzertifikate zu signieren. Stellen Sie sicher, dass Sie die Datei <span class="filepath"> AdobeInitial.properties</span> sowohl mit dem Pfad zur I15N CA-Berechtigungsdatei als auch mit dem verschlüsselten PKCS12-Kennwort ordnungsgemäß konfigurieren. </td> 
   <td> 
    <ul id="ul_xsj_nl2_jr"> 
     <li id="li_5A770D8A482F41A4A9AB63CA52C2EB90"><span class="codeph"> cert.i15n.ica.file =</span> [PKCS12-Datei, die den CA-Zertifikat und -Schlüssel für die Individualisierung enthält] </li> 
     <li id="li_C3C4A2D9AA2A4F86B6DDCFFD9CB55CBB"><span class="codeph"> cert.i15n.ica.password =</span> [Verschlüsseltes Kennwort für PKCS12-Datei] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Berechtigung zur Verschlüsselung von Individualisierungen </td> 
   <td> Der Individualisierungsserver verwendet die Encryption-Berechtigung zum Verschlüsseln vertraulicher Dateien, die an die Individualisierungsserver übertragen werden müssen. Dieses Zertifikat unterstützt z. B. die Lizenzmigration und wird auch zum Verschlüsseln der privaten DRM-Schlüssel für die Individualisierungsserver verwendet. </td> 
   <td> 
    <ul id="ul_nbr_kpd_w5"> 
     <li id="li_4226AD6CC85740669DAF467EFD00BBBE"><span class="codeph"> cert.i15n.decryption.file=i15n_transport.pfx</span> </li> 
     <li id="li_F51BDD94F4724FA58CEF9470B6FEE33B"><span class="codeph"> cert.i15n.decryption.password=password</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Content Cache </td> 
   <td>Diese Einstellungen steuern den Speicherort, von dem der Individualisierungsserver Inhalte herunterlädt und an dem der Inhalt auf dem Datenträger zwischengespeichert wird. Der Individualisierungsserver überprüft den Inhaltsserver beim Start und dann mit der von diesen Eigenschaften festgelegten Häufigkeit/Uhrzeit auf neue Inhalte. <p>Für den On Premises Individualization Server wurde ein erster Satz von Daten aus dem Inhaltscache eingefügt. Stellen Sie sicher, dass Sie den Ordner <i>CONTENTS</i> des Cache-Ordners (nicht den Cache-Ordner selbst) in den konfigurierten Ordner <span class="filepath"> AdobeInitial.properties</span> <span class="codeph"> contentServer.localDirectory</span> kopieren. </p> </td> 
   <td> 
    <ul id="ul_r4n_1r2_jr"> 
     <li id="li_CA5F562577B04B4A9966EF46E039A137"><span class="codeph"> contentServer.localDirectory = </span> [Verzeichnis, in dem lokale Inhalte gespeichert werden (normalerweise tomcat/temp)] </li> 
     <li id="li_9A78FBD6C54D47708226378340B46E8E"><span class="codeph"> contentServer.server =</span> [Webserver, der für ECI-Informationen kontaktiert wird (in dieser Version<i> </i> nicht unterstützt)] </li> 
     <li id="li_4E7D7F76085D411688B5003E855F860B"><span class="codeph"> contentServer.timeout = </span> [Zeitüberschreitung bei Verbindung in Sekunden] </li> 
     <li id="li_4B751F238A1643A7AC730CD9354887B6"><span class="codeph"> contentServer.pollFrequency = </span> [Wie oft der Server in Tagen abgefragt wird (mindestens 1 Tag)] </li> 
     <li id="li_8E23C3C6E7EF46B0AFDD7993DE79F142"><span class="codeph"> contentServer.pollTime = </span> [Uhrzeit der Serverabfrage in Minuten seit Mitternacht] </li> 
    </ul> <p>Lesen Sie dazu unbedingt den Abschnitt <i>CRL- und ECI-Dateien</i>, wie Sie den Cache auf dem neuesten Stand halten. </p> </td> 
  </tr> 
  <tr> 
   <td> Individualisierungs-CA-Zertifikatsperrliste </td> 
   <td> <p>Dieser Zertifikatsperrlisten-Verteilungspunkt (Certificate Revocation Liste, CRL) ist in jedem vom Individualisierungsserver ausgestellten Computerzertifikat enthalten. Während der Validierung des Computerzertifikats auf dem Lizenzserver wird die Zertifikatsperrliste von dem im Zertifikat aufgeführten Verteilungspunkt heruntergeladen (oder aus dem Cache gelesen, wenn bereits heruntergeladen) und überprüft, ob das Zertifikat nicht widerrufen wurde. Es wird empfohlen, diese Änderung der Serverkonfiguration durchzuführen, nachdem der Vorgang zum Erstellen und Bereitstellen der CRL für die Zertifizierungsstelle für die individuelle Behandlung (Individualization CA) durchgeführt wurde. Starten Sie den Individualisierungsserver nach jeder Konfigurationsänderung neu. </p> <p>Um die URL für den Zertifikatsperrlisten-Verteilungspunkt festzulegen, müssen Sie das Feld <span class="filepath"> AdobeInitial.properties</span> <span class="codeph"> cert.machine.crldp</span> festlegen. </p> </td> 
   <td> 
    <ul id="ul_eq3_lv2_jr"> 
     <li id="li_5E37A9E318D742B6A5E1035120888819"><span class="codeph"> cert.machine.crldp = </span> [CRL-Verteilungspunkt] </li> 
    </ul> <p>Beispiel: </p>
    <p> <code>
      cert.machine.crldp__DEV=<span>tps://onprem-individualization.com</span>CRL/onprem-individualization-ca.crl
     </code></p>
     <p>Sobald eine Lizenzanforderung bearbeitet wurde, sollte der Lizenzserver diese Zertifikatssperrliste automatisch herunterladen. </p> <p importance="high">Hinweis: Dieser Verteilungspunkt ist <i>nicht</i> von Primetime DRM auf Gültigkeit überprüft. Sie müssen überprüfen, ob diese URL gültig ist. Fehler, die durch eine ungültige URL verursacht werden, werden erst angezeigt, wenn Überprüfungsfehler vom Lizenzserver angezeigt werden. </p> </td> 
  </tr> 
  <tr> 
   <td> Protokollierung </td> 
   <td>Konfigurieren Sie die <span class="filepath"> AdobeInitial.properties</span> für die Protokollierung nach Bedarf. </td> 
   <td> 
    <ul id="ul_j1v_kw2_jr"> 
     <li id="li_B60002B33A3042FCBE1F694454966469"><span class="codeph"> adobe.weblogs.loc =</span> [Verzeichnis, in dem Protokolldateien erstellt werden] </li> 
     <li id="li_2DD4406FBBF047589BAAAE1C9082D8B3"><span class="codeph"> log.Level = </span> [Die niedrigste Ebene der Protokollmeldungen, die möglicherweise in den Protokollen angezeigt werden  <span class="codeph"> [DEBUG] | INFO]</span> ] </li> 
     <li id="li_610FAF239A554CE59DAC455174F0CF0A"><span class="codeph"> log.FileName = </span> [Präfix für Protokolldateien. Datum/Uhrzeit und die Erweiterung ".log"werden dem Dateinamen hinzugefügt] </li> 
     <li id="li_1F2913B209BE4A0E8207FAAD052D1764"><span class="codeph"> log.RollInterval =</span> [Gibt an, wie oft die Protokolle rolliert werden.] </li> 
     <li id="li_3F46C15488114BB5B41035F710E7A19F"><span class="codeph"> log.RollSize = </span> [Rollen Sie die Protokolle, wenn sie diese Größe erreichen (Protokolle werden ausgeführt, wenn entweder der  <span class="codeph"> </span> RollIntervalor  <span class="codeph"> </span> RollSizeis erreicht hat, je nachdem, was zuerst eintritt)] </li> 
     <li id="li_DA32E862F7B0413885DA20633B682484"><span class="codeph"> log.ReportLogging.Enabled = </span>[ [true | false ] Gibt an, ob eine separate Datei generiert werden soll, die Daten enthält, die von der Adobe zum Generieren von Individualisierungsberichten verwendet werden.] </li> 
     <li id="li_465CC6D81B8A484CBF4E7A39F7AF86AA"><span class="codeph"> log.ReportLogging.FileName = </span> [Präfix für Protokolldateien des Berichts. Datum/Uhrzeit und die Erweiterung <span class="filepath"> .log</span> werden dem Dateinamen hinzugefügt. Die Eigenschaft l<span class="codeph"> og.Level</span> gilt nicht für diese Protokolldatei, aber <span class="codeph"> log.RollInterval</span> und <span class="codeph"> log.RollSize</span> tun dies.] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Sonstiges </td> 
   <td></td> 
   <td> 
    <ul id="ul_b3b_g1f_jr"> 
     <li id="li_FACF07CB332D416E91FD34DE48152FAA"><span class="codeph"> deviceinfo.key = </span> [Encrypted Base64 encoded key used to HMAC device info before include it in the machine token. Der Schlüssel kann für die Dev/Staging/Production-Umgebung unterschiedlich sein, muss jedoch für alle Server in einer bestimmten Umgebung gleich sein. _ </li> 
     <li id="li_B19C77FD6F91496294DBF836A1922EE1"><span class="codeph"> keys.kgs.server =</span> [Speicherort des Key Gen-Servers (ein einzelner Host/Port, der einen Pool von Schlüsselservern darstellt)] </li> 
     <li id="li_5DA3C89770804B148EF6FAF01A5AD958"><span class="codeph"> keys.MinQueueSize = </span> [Abrufen eines weiteren Schlüssels aus dem KGS, wenn noch viele Schlüssel in der Warteschlange verbleiben] </li> 
     <li id="li_0C2E5F2FDB824182A6BE418B041D2F28"><span class="codeph"> status.Timeout = </span> [Statusseite pinkelt die KGS, um zu ermitteln, ob sie den Server erreichen kann. Es wird ein Timeout ausgegeben, wenn eine Antwort nicht in der angegebenen Zeit zurückgegeben wird.] </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Key Generation Server {#section_37FA8EEBA258461F8CFA3ADF37714577}

<table id="table_ats_tk2_js"> 
 <thead> 
  <tr> 
   <th class="entry"> Konfiguration </th> 
   <th class="entry"> Beschreibung </th> 
   <th class="entry"> Beispiel </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> Schlüsselgeneration </td> 
   <td></td> 
   <td> 
    <ul id="ul_nlj_ydf_jr"> 
     <li id="li_E4347D572F004BF0B237A662BFE7F3ED"><span class="codeph"> kgs.Threads = </span> [Anzahl der Threads, die zum Generieren von Schlüsseln verwendet werden sollen (sollte der Anzahl der auf dem Computer verfügbaren Prozessoren entsprechen)] </li> 
     <li id="li_EDBC2535D48E4A66AEB240DB337187FC"><span class="codeph"> kgs.BatchSize = </span> [Anzahl der pro Stapel zu generierenden Schlüssel] </li> 
     <li id="li_07B41546D94F42349103BF8AF4605E14"><span class="codeph"> kgs.KeyDirectory = </span> [Verzeichnis, in dem Schlüssel-Batch-Dateien gespeichert werden] </li> 
     <li id="li_F4962C97DC3D491DA7FAC826E38A4459"><span class="codeph"> kgs.MaxQueueSize = </span> [Maximale Anzahl der zu generierenden Schlüsselstapeldateien] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Protokollierung </td> 
   <td></td> 
   <td> 
    <ul id="ul_kwq_12f_jr"> 
     <li id="li_5E5D34FE5EB44BB898090494C7DDEBD8"><span class="codeph"> adobe.weblogs.loc =</span> [Verzeichnis, in dem Protokolldateien erstellt werden] </li> 
     <li id="li_0E34CD32CD5E47729B69B50414F93678"><span class="codeph"> log.FileName = </span> [Präfix für Protokolldateien. Datum/Uhrzeit und die Erweiterung <span class="filepath"> .log</span> werden dem Dateinamen hinzugefügt] </li> 
     <li id="li_8AB15ACEC39041A2A04C7301154C6EDB"><span class="codeph"> log.Level = </span> [Die niedrigste Ebene der Protokollmeldungen, die möglicherweise in den Protokollen angezeigt werden] </li> 
     <li id="li_A17E84DA3ED243F381FF3A6184A3CAA0"><span class="codeph"> log.RollInterval =</span> [Gibt an, wie oft die Protokolle rolliert werden.] </li> 
     <li id="li_C2B3D111608945DA9D1428BE98D61664"><span class="codeph"> log.RollSize = </span> [Rollen Sie die Protokolle, wenn sie diese Größe erreichen (Protokolle werden ausgeführt, wenn entweder der  <span class="codeph"> </span> RollIntervalor  <span class="codeph"> </span> RollSizeis erreicht hat, je nachdem, was zuerst eintritt)] </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
