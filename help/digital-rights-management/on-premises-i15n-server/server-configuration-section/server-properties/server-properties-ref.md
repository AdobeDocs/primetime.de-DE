---
title: Referenz zu Servereigenschaften
description: Referenz zu Servereigenschaften
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
   <td>Die Transportberechtigung wird verwendet, um vom Client empfangene Anforderungen zu entschlüsseln und die zurückgesendeten Antworten zu signieren. Stellen Sie sicher, dass die <span class="filepath"> AdobeInitial.properties</span> -Datei mit dem Pfad zur Datei mit den Transportberechtigungen sowie dem verschlüsselten PKCS12-Kennwort ordnungsgemäß. </td> 
   <td> 
    <ul id="ul_itx_fl2_jr"> 
     <li id="li_A2E65253F37245268A41E6B9C958C8DF"><span class="codeph"> cert.i15n.transport.file = </span> [PKCS12-Datei, die das Individualization Transport-Zertifikat und den Schlüssel enthält] </li> 
     <li id="li_28CDFC0B3D684795AF4708B6D26DF83F"><span class="codeph"> cert.i15n.transport.password =</span> [Verschlüsseltes Kennwort für PKCS12-Datei] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> CA-Berechtigung für Individualisierungen </td> 
   <td>Der Individualisierungsserver verwendet die Berechtigung Individualization CA , um die ausgestellten Maschinenzertifikate zu signieren. Stellen Sie sicher, dass die <span class="filepath"> AdobeInitial.properties</span> -Datei entsprechend mit dem Pfad zur I15N CA-Berechtigungsdatei sowie dem verschlüsselten PKCS12-Kennwort. </td> 
   <td> 
    <ul id="ul_xsj_nl2_jr"> 
     <li id="li_5A770D8A482F41A4A9AB63CA52C2EB90"><span class="codeph"> cert.i15n.ica.file =</span> [PKCS12-Datei, die das Zertifikat und den Schlüssel des Individualization CA enthält] </li> 
     <li id="li_C3C4A2D9AA2A4F86B6DDCFFD9CB55CBB"><span class="codeph"> cert.i15n.ica.password =</span> [Verschlüsseltes Kennwort für PKCS12-Datei] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Individualisierungsverschlüsselungsberechtigungen </td> 
   <td> Der Individualisierungsserver verwendet die Verschlüsselungsberechtigung, um sensible Dateien zu verschlüsseln, die an die Individualisierungsserver übertragen werden müssen. Beispielsweise unterstützt dieses Zertifikat die Lizenzmigration und wird auch zum Verschlüsseln der privaten DRM-Schlüssel für die Individualisierungsserver verwendet. </td> 
   <td> 
    <ul id="ul_nbr_kpd_w5"> 
     <li id="li_4226AD6CC85740669DAF467EFD00BBBE"><span class="codeph"> cert.i15n.decryption.file=i15n_transport.pfx</span> </li> 
     <li id="li_F51BDD94F4724FA58CEF9470B6FEE33B"><span class="codeph"> cert.i15n.decryption.password=password</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Inhalts-Cache </td> 
   <td>Diese Einstellungen steuern den Speicherort, von dem aus der Individualisierungsserver Inhalte herunterlädt und wo der Inhalt auf dem Datenträger zwischengespeichert wird. Der Personalisierungsserver prüft beim Start den Inhaltsserver auf neue Inhalte und dann in der durch diese Eigenschaften festgelegten Häufigkeit/Uhrzeit. <p>Für den On-Premises-Individualisierungsserver haben wir einen ersten Satz von Inhalts-Cache-Daten eingefügt. Kopieren Sie unbedingt die <i>INHALT</i> des Cache-Ordners (nicht des Cache-Ordners selbst) zum konfigurierten <span class="filepath"> AdobeInitial.properties</span> <span class="codeph"> contentServer.localDirectory</span> Standort. </p> </td> 
   <td> 
    <ul id="ul_r4n_1r2_jr"> 
     <li id="li_CA5F562577B04B4A9966EF46E039A137"><span class="codeph"> contentServer.localDirectory =</span> [Verzeichnis, in dem lokale Inhalte gespeichert werden sollen (normalerweise tomcat/temp)] </li> 
     <li id="li_9A78FBD6C54D47708226378340B46E8E"><span class="codeph"> contentServer.server =</span> [Webserver für ECI-Informationen (<i>in dieser Version nicht unterstützt</i>)] </li> 
     <li id="li_4E7D7F76085D411688B5003E855F860B"><span class="codeph"> contentServer.timeout =</span> [Zeitüberschreitung bei Verbindung, in Sekunden] </li> 
     <li id="li_4B751F238A1643A7AC730CD9354887B6"><span class="codeph"> contentServer.pollFrequency =</span> [Wie häufig der Server in Tagen abgefragt wird (mindestens 1 Tag)] </li> 
     <li id="li_8E23C3C6E7EF46B0AFDD7993DE79F142"><span class="codeph"> contentServer.pollTime =</span> [Uhrzeit der Serverabfrage in Minuten seit Mitternacht] </li> 
    </ul> <p>Lesen Sie unbedingt den Abschnitt . <i>CRL- und ECI-Dateien</i> über die Aktualisierung des Caches. </p> </td> 
  </tr> 
  <tr> 
   <td> Individualization CA CRL </td> 
   <td> <p>Dieser Zertifikatsperrlisten-Verteilungspunkt (CRL) ist in jedem vom Individualisierungsserver ausgestellten Maschinenzertifikat enthalten. Während der Validierung des maschinellen Zertifikats auf dem Lizenzserver wird die Zertifikatsperrliste von dem im Zertifikat aufgelisteten Verteilungspunkt heruntergeladen (oder aus dem Cache gelesen, falls bereits heruntergeladen) und überprüft, ob das Zertifikat nicht widerrufen wurde. Es wird empfohlen, diese Änderung der Serverkonfiguration durchzuführen, nachdem Sie die CRL der individuellen Zertifizierungsstelle erstellt und bereitgestellt haben. Starten Sie den Individualisierungsserver nach jeder Konfigurationsänderung neu. </p> <p>Um die URL für den Zertifikatsperrlisten-Verteilungspunkt festzulegen, müssen Sie die <span class="filepath"> AdobeInitial.properties</span> <span class="codeph"> cert.machine.crldp</span> -Feld. </p> </td> 
   <td> 
    <ul id="ul_eq3_lv2_jr"> 
     <li id="li_5E37A9E318D742B6A5E1035120888819"><span class="codeph"> cert.machine.crldp =</span> [CRL-Verteilungspunkt] </li> 
    </ul> <p>Beispiel: </p>
    <p> <code>
      cert.machine.crldp__DEV=<span>tps://onprem-individualization.com</span>CRL/onprem-individualization-ca.crl
     </code></p>
     <p>Der Lizenzserver sollte diese Zertifikatsperrliste automatisch herunterladen, sobald eine Lizenzanfrage verarbeitet wurde. </p> <p importance="high">Hinweis: Dieser Verteilungspunkt ist <i>not</i> von Primetime DRM auf Gültigkeit überprüft. Sie müssen sicherstellen, dass diese URL gültig ist. Fehler, die aus einer ungültigen URL resultieren, werden erst angezeigt, wenn vom Lizenzserver Überprüfungsfehler angezeigt werden. </p> </td> 
  </tr> 
  <tr> 
   <td> Protokollierung </td> 
   <td>Konfigurieren Sie die <span class="filepath"> AdobeInitial.properties</span> für die Protokollierung nach Bedarf. </td> 
   <td> 
    <ul id="ul_j1v_kw2_jr"> 
     <li id="li_B60002B33A3042FCBE1F694454966469"><span class="codeph"> adobe.weblogs.loc =</span> [Verzeichnis, in dem Protokolldateien erstellt werden] </li> 
     <li id="li_2DD4406FBBF047589BAAAE1C9082D8B3"><span class="codeph"> log.Level =</span> [Die niedrigste Protokollierungsstufe, die in den Protokollen angezeigt werden kann. <span class="codeph"> [DEBUG] | INFO</span> ] </li> 
     <li id="li_610FAF239A554CE59DAC455174F0CF0A"><span class="codeph"> log.FileName =</span> [Präfix für Protokolldateien. Datum/Uhrzeit und die Erweiterung ".log"werden dem Dateinamen hinzugefügt.] </li> 
     <li id="li_1F2913B209BE4A0E8207FAAD052D1764"><span class="codeph"> log.RollInterval =</span> [Gibt an, wie oft die Protokolle rollierend sind.] </li> 
     <li id="li_3F46C15488114BB5B41035F710E7A19F"><span class="codeph"> log.RollSize =</span> [Rollen Sie die Protokolle, wenn sie diese Größe erreichen (Protokolle werden ausgeführt, wenn entweder die <span class="codeph"> RollInterval</span> oder <span class="codeph"> RollSize</span> erreicht wird, je nachdem, welcher Zeitpunkt zuerst eintritt)] </li> 
     <li id="li_DA32E862F7B0413885DA20633B682484"><span class="codeph"> log.ReportLogging.Enabled =</span>[ [true] | false ] Gibt an, ob eine separate Datei generiert werden soll, die von Adobe zum Generieren von Individualisierungsberichten verwendete Daten enthält.] </li> 
     <li id="li_465CC6D81B8A484CBF4E7A39F7AF86AA"><span class="codeph"> log.ReportLogging.FileName =</span> [Präfix für Berichtprotokolldateien. Datum/Uhrzeit und <span class="filepath"> .log</span> wird dem Dateinamen hinzugefügt. l<span class="codeph"> og.Level</span> -Eigenschaft gilt nicht für diese Protokolldatei, aber <span class="codeph"> log.RollInterval</span> und <span class="codeph"> log.RollSize</span> do.] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Sonstiges </td> 
   <td></td> 
   <td> 
    <ul id="ul_b3b_g1f_jr"> 
     <li id="li_FACF07CB332D416E91FD34DE48152FAA"><span class="codeph"> deviceinfo.key =</span> [Verschlüsselter Base64-kodierter Schlüssel, der für HMAC-Geräteinformationen verwendet wird, bevor er in das Computer-Token aufgenommen wird. Der Schlüssel kann für die Entwicklungs-/Staging-/Produktionsumgebungen unterschiedlich sein, muss jedoch für alle Server in einer bestimmten Umgebung gleich sein. ] </li> 
     <li id="li_B19C77FD6F91496294DBF836A1922EE1"><span class="codeph"> keys.kgs.server =</span> [Speicherort von Key Gen Server (ein einzelner Host/Port, der einen Pool von Schlüsselservern darstellt)] </li> 
     <li id="li_5DA3C89770804B148EF6FAF01A5AD958"><span class="codeph"> keys.MinQueueSize =</span> [Rufen Sie einen weiteren Schlüssel-Batch aus dem KGS ab, wenn diese viele Schlüssel noch in der Warteschlange sind.] </li> 
     <li id="li_0C2E5F2FDB824182A6BE418B041D2F28"><span class="codeph"> status.Timeout =</span> [Die Statusseite pingt die KGS, um zu bestimmen, ob der Server erreicht werden kann. Es wird eine Zeitüberschreitung ausgegeben, wenn eine Antwort nicht innerhalb der angegebenen Zeit zurückerhalten wird.] </li> 
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
   <td> Schlüsselgenerierung </td> 
   <td></td> 
   <td> 
    <ul id="ul_nlj_ydf_jr"> 
     <li id="li_E4347D572F004BF0B237A662BFE7F3ED"><span class="codeph"> kgs.Threads =</span> [Anzahl der Threads, die zum Generieren von Schlüsseln verwendet werden sollen (sollte der Anzahl der auf dem Computer verfügbaren Prozessoren entsprechen)] </li> 
     <li id="li_EDBC2535D48E4A66AEB240DB337187FC"><span class="codeph"> kgs.BatchSize =</span> [Anzahl der Schlüssel, die pro Batch generiert werden] </li> 
     <li id="li_07B41546D94F42349103BF8AF4605E14"><span class="codeph"> kgs.KeyDirectory =</span> [Ordner, in dem die Batch-Schlüsseldateien gespeichert werden] </li> 
     <li id="li_F4962C97DC3D491DA7FAC826E38A4459"><span class="codeph"> kgs.MaxQueueSize =</span> [Maximale Anzahl der zu erzeugenden Schlüssel-Batch-Dateien] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Protokollierung </td> 
   <td></td> 
   <td> 
    <ul id="ul_kwq_12f_jr"> 
     <li id="li_5E5D34FE5EB44BB898090494C7DDEBD8"><span class="codeph"> adobe.weblogs.loc =</span> [Verzeichnis, in dem Protokolldateien erstellt werden] </li> 
     <li id="li_0E34CD32CD5E47729B69B50414F93678"><span class="codeph"> log.FileName =</span> [Präfix für Protokolldateien. Datum/Uhrzeit und <span class="filepath"> .log</span> Erweiterung wird zum Dateinamen hinzugefügt.] </li> 
     <li id="li_8AB15ACEC39041A2A04C7301154C6EDB"><span class="codeph"> log.Level =</span> [Die niedrigste Protokollierungsstufe, die in den Protokollen angezeigt werden kann] </li> 
     <li id="li_A17E84DA3ED243F381FF3A6184A3CAA0"><span class="codeph"> log.RollInterval =</span> [Gibt an, wie oft die Protokolle rollierend sind.] </li> 
     <li id="li_C2B3D111608945DA9D1428BE98D61664"><span class="codeph"> log.RollSize =</span> [Rollen Sie die Protokolle, wenn sie diese Größe erreichen (Protokolle werden ausgeführt, wenn entweder die <span class="codeph"> RollInterval</span> oder <span class="codeph"> RollSize</span> erreicht wird, je nachdem, welcher Zeitpunkt zuerst eintritt)] </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
