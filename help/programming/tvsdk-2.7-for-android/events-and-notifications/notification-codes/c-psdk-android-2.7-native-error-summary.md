---
seo-title: Details zur NATIVE_ERROR-Benachrichtigung
title: Details zur NATIVE_ERROR-Benachrichtigung
uuid: 750ee0e2-15d4-4602-9574-94015a6e1b57
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '6888'
ht-degree: 2%

---


# Details für die NATIVE_ERROR-Benachrichtigung {#details-for-the-native-error-notification}

Wenn TVSDK einen nativen Fehler verarbeitet, werden einige oder alle der folgenden Metadatenschlüsselwerte als Zeichenfolgen zurückgegeben.

<table id="table_7F713B7A56024D8DA3C84E449D09CC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Metadaten-Schlüsselname </th> 
   <th colname="col2" class="entry"> Metadatenwert </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_ERROR_CODE</span> </td> 
   <td colname="col2"> <p>Nativer Fehlercode aus der AVE. </p> <p>Diese Codes stellen Folgendes dar: 
     <ul id="ul_1F33D523DDFE4CE8B4F0DC279FF7E4F8"> 
      <li id="li_07A2D9BEE6364935A61EF3BD4AB6DE27">DRM-Fehler (Codes 3300 bis 3367). Diese sind mit den entsprechenden Flash Player-Fehlercodes identisch. </li> 
      <li id="li_433BA22DE3504AEEB623598BB4F939FA">Fehler bei der Videowiedergabe (-1 bis 89) </li> 
      <li id="li_B347CB151DB94DE0A1DDEB1B33D2DABA">Kryptographiefehler (300 bis 307) </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_ERROR</span> </td> 
   <td colname="col2">Kurze Beschreibung der Benachrichtigung (z. B. <span class="codeph"> AAXS_InvalidVoucher</span> oder <span class="codeph"> DECODER_FAILED</span>). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> BESCHREIBUNG</span> </td> 
   <td colname="col2"> Lange Beschreibung der Benachrichtigung (z. B. der Vorgang zur Anzeigenauflösung ist fehlgeschlagen). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> PSDK_ERROR_CODE</span> </td> 
   <td colname="col2"><span class="codeph"> com.adobe.mediacore.</span> PSDKErrorCodenumeric-Wert als Zeichenfolge (z. B. "13"). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> PSDK_ERROR</span> </td> 
   <td colname="col2"><span class="codeph"> com.adobe.mediacore.</span> PSDKErrorCodeas eine Zeichenfolge (z. B.  <span class="codeph"> kECNetworkError</span>). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> WARNUNG</span> </td> 
   <td colname="col2"> Beschreibung der Warnung. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> FEHLER</span> </td> 
   <td colname="col2"> Beschreibung des Fehlers. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>DRM</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_SUBERROR_CODE</span> </td> 
   <td colname="col2"> Geringfügiger Fehler des DRM-Moduls. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DRM_ERROR_STRING</span> </td> 
   <td colname="col2"> Beschreibung des Fehlers. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DRM_ERROR_SERVER_URL</span> </td> 
   <td colname="col2"> URL des DRM-Servers, zu dem TVSDK versuchte zu sprechen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Anzeigenmanifestladefehler</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_URL</span> </td> 
   <td colname="col2"> URL des Inhalts, der nicht geladen werden konnte. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_TYPE</span> </td> 
   <td colname="col2">Typ der Anzeige (eine Konstante aus der Enum <span class="codeph"> MediaResource.Type</span>). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_DURATION</span> </td> 
   <td colname="col2"> Anzeigendauer in Millisekunden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_ID</span> </td> 
   <td colname="col2"> Die der Anzeige zugewiesene ID. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Dateifehler</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DOWNLOAD_ERROR</span> </td> 
   <td colname="col2"> Beschreibung des Fehlers beim Herunterladen der Mediendatei. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> URL</span> </td> 
   <td colname="col2"> URL der heruntergeladenen Datei. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> MANIFEST_ERROR</span> </td> 
   <td colname="col2"> Beschreibung des Fehlers beim Herunterladen der Manifestdatei. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> CONTENT_ERROR</span> </td> 
   <td colname="col2">Beschreibung des Fehlers beim Herunterladen des Fragments (z. B. <span class="codeph"> ts</span>). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Fehler in der Audiospur</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDIO_TRACK_NAME</span> </td> 
   <td colname="col2"> Name der Audiospur, die nicht geladen werden konnte, wie im Manifest angegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDIO_TRACK_LANGUAGE</span> </td> 
   <td colname="col2"> Die Sprache der Audiospur, wie im Manifest angegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Suchfehler</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DESIRED_SEEK_PERIOD</span> </td> 
   <td colname="col2"> ID des Zeitraums (Ganzzahl). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DESIRED_SEEK_POSITION</span> </td> 
   <td colname="col2"> <p>Position (in Millisekunden) gesucht (Dublette). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Sonstiges</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDITUDE_ERROR_CODE</span> </td> 
   <td colname="col2"> Auditude-Fehlercode (Zahl). </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR: DRM-Werte {#section_D240082B93D34902A18C3923C1C717B3}

Die Video Encoder-Schnittstelle der Adobe Video Engine gibt diese DRM-Benachrichtigungen im Metadatenobjekt `NATIVE_ERROR` zurück.

Wenn DRM-Fehler des Berichte zur Adobe auftreten, stellen Sie sicher, dass Sie die Variablen `NATIVE_SUBERROR_CODE` und `DRM_ERROR_STRING` zur Fehlerbehebung einschließen.

>[!TIP]
>
>Diese Liste enthält TVSDK-spezifische Informationen zu den Fehlern. Eine vollständige Beschreibung finden Sie unter [ActionScript ActionScript Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html#3300).

<table id="table_CD59A859865F4FFDBAA249C89C74770A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Wert für NATIVE_- ERROR_CODE-Metadatenschlüssel </th> 
   <th colname="col2" class="entry"> Wert für den Metadatenschlüssel NATIVE_ERROR_NAME </th> 
   <th colname="col3" class="entry"> Bedeutung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 3300 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidVoucher</span> </td> 
   <td colname="col3"> 
    <ul id="ul_516E4CB32D624B22892DDB9266CB04CA"> 
     <li id="li_348FC0F38B11417994119B61C9244076">Was sollte die Software des Distributors tun? 
      <ul id="ul_7AFD45CF92454BA4927783FAA628FBC4"> 
       <li id="li_0D9CCE61612643648C12DCDDD252E52A">Wenn Sie Google Chrome verwenden und sich im Inkognito-Modus befinden und Ihre Flash Player-Version unter 11.6 liegt, kann dieser Fehler auftreten. <p>Es wird empfohlen, dass der Player die Versionsnummer des Browsers überprüft und den Benutzer anweist, den Inkognito-Modus zu beenden. </p> </li> 
       <li id="li_1DC6B755BD0840D48BEC92568FD330BA">Fordern Sie die Lizenz erneut an. <p>Wenn die Anforderung erfolgreich war, müssen Sie sich nicht anmelden oder eskalieren. Wenn die Anforderung nicht erfolgreich ist, protokollieren Sie den Inhalt, der den Fehler verursacht hat. <span class="codeph"> Unter </span> subErrorId enthält einen Zeilenfehler, falls vorhanden. </p> </li> 
      </ul> </li> 
     <li id="li_060B5D60C9BB419CBFA7B062FBCF2632">Was sollte der Händler tun? 
      <ul id="ul_FADB29DBF0DA4A0E8E54134AEB7DCD8A"> 
       <li id="li_FC5B1C04D21E4AECB0EBD9ADD3198504">Wenn weitere Zustellversuche in anderen Konfigurationen als Chrome mit Flash unter Version 11.6 nicht erfolgreich sind, ist möglicherweise ein Fehler in der Verpackung aufgetreten. </li> 
       <li id="li_A720ECE591254021879B335B81B1F76D">Überprüfen Sie, ob das Problem für bestimmte Inhalte spezifisch ist, und erstellen Sie ein neues Paket. </li> 
      </ul> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3301 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AuthenticationFehlgeschlagen</span> </td> 
   <td colname="col3"> <p>Der Server konnte den Client nicht authentifizieren oder autorisieren. </p> 
    <ul id="ul_BE77AC1848FB4C09B6318359ACF1B8EE"> 
     <li id="li_6FB37D317D174E8488C5070D20CD241C">Die Software des Distributors sollte alle erforderlichen Maßnahmen ergreifen, um die Benutzeranmeldeinformationen wiederherzustellen oder den Benutzer zum Erwerb des Zugriffs auf die Inhalte anzuleiten. </li> 
     <li id="li_BE071D59805B42D38E3E7650BC936417">Der Händler sollte bestätigen, dass der Autorisierungs- und Authentifizierungsmechanismus des Händlers ordnungsgemäß funktioniert. <p>Wenn die Distributoren nicht planen, die Authentifizierungs- oder Autorisierungsfunktionen zu verwenden, sollten sie prüfen, ob die Richtlinie des verletzenden Inhalts eine Authentifizierung erfordert, und siehe Diskrepanzen bei der Diagnostik/Lizenzvergabe. </p> </li> 
    </ul> <p>Weitere Informationen zu diesem Fehlercode finden Sie unter <a href="https://forums.adobe.com/thread/1277149" format="https" scope="external"> DRM-Fehler 3301 Ursachen und Auflösung</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3302 </td> 
   <td colname="col2"><span class="codeph"> AAXS_RequireSSL</span> </td> 
   <td colname="col3"> <p>Bei Access 4.0 und höher wird dieser Fehler unter iOS ausgegeben, wenn die Remote-Schlüssel-URL HTTPS nicht als Schema verwendet. HTTPS ist erforderlich. </p> 
    <ul id="ul_3D47777BBCA14B67B107FBBE3E37E40C"> 
     <li id="li_7F7BBB27AE754CC39ABAAF9269739C49">Wenn der Distributor eine Version verwendet, die älter ist als Access v4 oder die Version mindestens 4, die Plattform jedoch nicht iOS, sollte die Software des Distributors den Fehler protokollieren. <p>Der Fehler wird nur unter iOS ausgegeben. </p> </li> 
     <li id="li_D83C427D2A0D47408F723EF7195070B6">Ist die Software des Distributors mindestens Adobe Access Version 4 und die Plattform iOS, müssen Distributoren die URL des Remote-Schlüsselservers, den sie verwenden, in HTTPS ändern. <p>Wenn sie nur HTTP verwenden, müssen Distributoren möglicherweise einen HTTPS-Server einrichten. Andernfalls müssen die Distributoren die protokollierten Informationen an die Adobe senden und das Problem eskalieren. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3303 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentExpired</span> </td> 
   <td colname="col3"> <p>Der Inhalt, den Sie anzeigen, ist gemäß den vom Inhaltsanbieter festgelegten Regeln abgelaufen. subErrorId enthält einen clientspezifischen Fehler oder Zeilenfehler. </p> <p> 
     <ul id="ul_1E4B3B8AE87A4E79997553BB2A0E52B9"> 
      <li id="li_EE3F2EEBF73743B9A38E4FCB7531E275">Die Software des Distributors sollte versuchen, eine Lizenz vom Server einmal zu erwerben, um festzustellen, ob eine neue Lizenz ohne Ablaufdatum verfügbar ist. <p>Wenn keine Lizenz verfügbar ist oder die Lizenz abgelaufen ist, erlauben Sie dem Benutzer, eine neue Lizenz zu erwerben oder teilen Sie dem Benutzer mit, dass der Inhalt nicht überwacht werden kann. Wenn der Inhalt mit einer Richtlinie verpackt wurde, die ein Ablaufdatum/Enddatum aufweist, protokolliert der Lizenzserver den Bericht <span class="codeph"> PolicyEvaluationException</span> und gibt an, dass das Enddatum abgelaufen ist (Server-Fehlercode 303). Überprüfen Sie die Protokolldateien des Servers. </p> <p>Wenn möglich, sollten Kunden die Richtlinien überprüfen, die sie während der Verpackung verwendet haben, um zu sehen, ob sie abgelaufen sind. Das Java-Befehlszeilenwerkzeug ist: 
        <code>
         java&nbsp;-jar&nbsp;libs/AdobePolicyManager.jar&nbsp;&nbsp;&nbsp;detail&nbsp;demo.pol
        </code> </p> </li> 
      <li id="li_50DBE680D8F04E7DA3E29C65A93188E7">Der Händler sollte bestätigen, ob die Lizenzablaufdaten wie vorgesehen konfiguriert wurden. </li> 
     </ul> </p> <p>Weitere Informationen zu diesem Fehlercode finden Sie unter <a href="https://forums.adobe.com/thread/1300813" format="https" scope="external"> 3303 (Inhalt abgelaufen) mit AMS/FMS mit einem Live-Stream?</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3304 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AuthorizationFehlgeschlagen</span> </td> 
   <td colname="col3">Weitere Informationen zu diesem Fehlercode finden Sie unter <a href="https://forums.adobe.com/thread/1277149" format="https" scope="external"> DRM-Fehler 3301 Ursachen und Auflösung</a>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3305 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerConnectionFehlgeschlagen</span> </td> 
   <td colname="col3"> <p>Die Verbindung zu den Lizenz- oder Domänenservern ist abgelaufen, entweder aufgrund der Netzwerkverzögerung oder aufgrund der Offline-Verbindung des Clients. Normalerweise enthält subErrorId HTTP-Rückgabecode. </p> 
    <ul id="ul_938C7D8F07F64B4FA71A09DDF37E2E64"> 
     <li id="li_6648EA0049094E369BD9AE9CCA6B148D">Die Software des Distributors sollte eine Netzwerkverbindung zu einem zweifelsfrei funktionierenden Server herstellen. <p>Wenn der Versuch fehlschlägt, fordern Sie den Benutzer auf, die Verbindung zum Netzwerk wiederherzustellen. Wenn der Versuch erfolgreich war, protokollieren Sie ihn. </p> </li> 
     <li id="li_2ECA2C04BA08449DA3AD79A52EFAA229">Der Distributor sollte sicherstellen, dass alle verwendeten Lizenz- und Domänenserver online und über das Netzwerk des Kunden sichtbar sind. </li> 
    </ul> <p>Weitere Informationen zu diesem Fehlercode finden Sie unter <a href="https://forums.adobe.com/thread/1284947" format="https" scope="external"> DRM 3305 [ServerConnectionFehlgeschlagene] Ursachen und Auflösung</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3306 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ClientUpdateRequire</span> </td> 
   <td colname="col3"> Verwenden Sie eine neuere Version von TVSDK für Android. <p>Der aktuelle Client kann die angeforderte Aktion nicht ausführen, aber ein aktualisierter Client kann die Anforderung möglicherweise abschließen. </p> <p>Dies kann mehrere Ursachen haben: 
     <ul id="ul_2EC4D42D5273439FA1AFDA1A2578B3D6"> 
      <li id="li_FCA926F5FAED4E7190BE855545AB6ACF">Es wurde eine freigegebene Domäne verwendet, die auf diesem Client nicht verfügbar ist. Dies ist wahrscheinlich der Fall, wenn die Wiedergabe in Chrome funktioniert, aber nicht in einem anderen Browser und umgekehrt. <p> <p>Tipp: Chrome verwendet einen anderen PHDS/PHLS-Schlüssel als die anderen Browser. Weitere Informationen finden Sie unter <a href="https://adobeprimetime.zendesk.com/agent/tickets/2891" format="https" scope="external"> https://adobeprimetime.zendesk.com/agent/tickets/2891</a>. </p> </p> </li> 
      <li id="li_3B633FB699234DCEA136E9BE3CC3386D">Die Anwendung versucht, mehrere DRMSessions hinzuzufügen, wenn sie unter einer iOS-Version ausgeführt wird, die älter als 5.0 ist. </li> 
      <li id="li_F7ED993AF0B941A7A27216B4D587A999">Die Metadaten haben eine Version von 3 oder höher, wenn nur Version 2 unterstützt wird. </li> 
     </ul> </p> 
    <ul id="ul_EE4AE6AD4F1745A5B5623E53B599DB62"> 
     <li id="li_7A83869D4262443DA35FA1DF8D3097DD">Die Software des Distributors sollte den Benutzer warnen und den Vorgang abbrechen. <p>Wenn die Software feststellen kann, ob ein Upgrade verfügbar ist, leiten Sie den Benutzer auf die entsprechende Weise zu diesem Upgrade für die Plattform. </p> </li> 
     <li id="li_AF9C2711FDE54DA196EB9D2864632000">Tritt das Problem aufgrund einer freigegebenen Domäne auf, muss der Distributor mit der Adobe nach einer aktualisierten Laufzeit oder Bibliothek suchen. <p>Zur Laufzeit des Flashs kann der Distributor die Aktualisierung direkt erzwingen. Bei einer Bibliothek muss der Distributor eine aktualisierte Bibliothek abrufen, die Anwendung neu erstellen und für seine Benutzer bereitstellen. </p> <p>Tritt das Problem aufgrund mehrerer DRMS-Sitzungen auf, muss der Distributor seine Anwendung aktualisieren, um die iOS-Versionsnummer zu überprüfen, bevor mehrere DRMS-Sitzungen hinzugefügt werden. Oder sie können die Verteilung ihrer Anwendung auf iOS v5 und höher einschränken. </p> <p>Wenn das Problem auftritt, weil die Metadatenversion höher als Version 2 ist, ist das Problem vermutlich beschädigte Metadaten. Sie können versuchen, die Metadaten neu zu erstellen und sich die Ergebnisse anzusehen. Wenn das Problem weiterhin auftritt, protokollieren Sie das Problem und eskalieren Sie zur Adobe. </p> </li> 
    </ul> <p>Weitere Informationen zu diesem Fehlercode finden Sie unter <a href="https://forums.adobe.com/thread/1266675" format="https" scope="external"> Beheben eines 3306 DRMErrorEvent-Fehlercodes</a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3307 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InternalFailure</span> </td> 
   <td colname="col3"> <p>Dies stellt im Allgemeinen einen Fehler im Adobe Access-Code dar und ist unerwartet, es sei denn, es gibt einen bekannten Fehler, wie unten. subErrorId enthält einen clientspezifischen Fehler oder Zeilenfehler. </p> 
    <ul id="ul_79F4A9655A2148519B1E9509C41F78C3"> 
     <li id="li_0E093AB4D6BD489B852279E6C1525A15">Wenn der Browser Chrome unter Windows und Flash Version 11.6 (SWF Version 19 oder höher) ist, sollte die Software des Distributors davon ausgehen, dass der Benutzer <span class="uicontrol"> Deny</span> auf die Infobar geklickt hat und die gleiche Behandlung wie 3368 vornimmt. </li> 
     <li id="li_0215D1089B344861A2C0A73E1067CFEF">Wenn 3307 auftritt, wenn der Browser nicht Chrome ist oder die Flash-Version nicht 11.6 ist, sollte der Distributor zur Adobe eskalieren. </li> 
    </ul> <p>Wichtig: <span class="codeph"> 3307:1107296344 (FailedToGetBrokerHandle)</span> kann mit den Chrome-Browserversionen 24-28 auftreten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3308 </td> 
   <td colname="col2"><span class="codeph"> AAXS_WrongLicenseKey</span> </td> 
   <td colname="col3"> <p>Dieser Fehler wird ausgegeben, wenn die verwendete Lizenz den falschen Schlüssel zum Entschlüsseln des Inhalts enthält. subErrorId enthält einen clientspezifischen Fehler oder Zeilenfehler. </p> <p>Es gibt offenbar nur zwei Möglichkeiten, diesen Fehler zu generieren: 
     <ul id="ul_1C955BD74C7843809D1B5A0CDCA5ED7B"> 
      <li id="li_18F0A7FDA6584887AD9DB3EDE54080D8">Der Kunde hat die standardmäßige Adobe-Tooling zur Lizenzgenerierung (z. B. das Java-Framework des Lizenzservers) geändert. <p>In diesem Fall enthält die Lizenz einen ungültigen Schlüssel, der möglicherweise keinem Inhalt entspricht. </p> </li> 
      <li id="li_21D04ED1F1FA464785BC297D385766FF">Der Kunde hat mehrere Lizenzen mit derselben Lizenz-ID erteilt. <p>In diesem Fall stehen auf dem Client mehrere Lizenzen zur Verfügung, die den Inhaltsmetadaten entsprechen und für die der Zugriffscode die falsche ausgewählt hat. </p> </li> 
     </ul> </p> 
    <ul id="ul_64AEE62BE36946F290067CF475A36ECA"> 
     <li id="li_9EEB2B11A4DA41E78C5840D8FAA81F0D">Die Software des Distributors sollte versuchen, die Lizenz vom Server erneut zu erwerben. 
      <ul id="ul_ACADC5518B054D0A853AEED2B675DB23"> 
       <li id="li_394835C8731048A5BF7D9370AC12448C">Wenn keine Lizenz verfügbar ist oder die Lizenz abgelaufen ist, stellen Sie einen Arbeitsablauf für den Benutzer bereit, um eine neue Lizenz zu erwerben, oder teilen Sie dem Benutzer mit, dass der Inhalt nicht überwacht werden kann, und protokollieren Sie die Ausgabe. </li> 
       <li id="li_3FE50518BE53405F9563FA620F7EAD5F">Wenn es sich hierbei um domänengebundenen Inhalt handelt (für AIR), stellen Sie eine Möglichkeit für den Benutzer bereit, der Domäne beizutreten. </li> 
      </ul> </li> 
     <li id="li_C80B353C1AEA4E9398241420CB491E84">Der Händler sollte 
      <ul id="ul_B5C50009374C4EED9B2B050B48F5F0F6"> 
       <li id="li_D5E6B760E0BC4B5C949ED1544B398838">Vergewissern Sie sich, dass die Lizenzausgabebereiche des Access License Servers nicht angepasst wurden. </li> 
       <li id="li_AA8F4E4B6DDD40BA8807C0920A92186B">Überprüfen Sie, ob sie eindeutige Lizenz-IDs für alle Lizenzen ausstellen. </li> 
       <li id="li_A2C53FE779AC4FDDB65E00A2C4F43EC4">Eskalieren Sie das Problem mit der Adobe. </li> 
      </ul> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3309 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptedAdditionalHeader  </span> </td> 
   <td colname="col3"> <p>Dies tritt auf, wenn der Header größer als 65536 Byte ist. </p> 
    <ul id="ul_82C0F688519B4F43A764D59A891F1903"> 
     <li id="li_E66AC9149A0649E88A79C5289C12C395">Die Software des Distributors sollte protokollieren, welche Inhalte den Fehler verursacht haben. </li> 
     <li id="li_1C5916A33E7B4DC9968105B9BD20A727">Der Händler sollte bestätigen, dass der Fehler mit bestimmten Inhalten reproduzierbar ist. Umverpacken beschädigter Inhalte </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3310 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AppIDMismatch  </span> </td> 
   <td colname="col3">Die Android-Anwendung stimmt nicht mit der verwendeten überein. <p>Die richtige AIR-Anwendung oder Flash-SWF wird nicht verwendet. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3311 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AppVersionMismatch  </span> </td> 
   <td colname="col3"> Nicht in Gebrauch. Dieses Problem kann weiterhin vom Stack der Version 1.x in AIR generiert werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3312 </td> 
   <td colname="col2"><span class="codeph"> AAXS_LicenseIntegrity  </span> </td> 
   <td colname="col3"> Um dies zu beheben, laden Sie die Lizenz erneut vom Server herunter. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3313 </td> 
   <td colname="col2"><span class="codeph"> AAXS_WriteMicrosafeFailure  </span> </td> 
   <td colname="col3"> <p>Dieses Problem tritt auf, wenn das System nicht in das Dateisystem schreiben kann. <span class="codeph"> Unter </span> subErrorId enthält einen clientspezifischen Fehler oder Zeilenfehler. </p> <p>Unter Microsoft Windows wird der Fehler 3313 möglicherweise vom Active X- oder NPAPI-Plug-Flash-Player ausgegeben, wenn der verschlüsselte Inhalt eine licenseID oder eine policyID hat, die zu lang ist. Dies liegt an der maximalen Pfadlänge in Windows. (Das Pepper-Plugin hat dieses Problem nicht.) </p> <p>Siehe Watson 3549660 </p> 
    <ul id="ul_DFD527D1E1224A439766DF7BED878E3B"> 
     <li id="li_FAF8FD98A4E8478CA7A92F770676ADFC">Die Software des Distributors sollte den Benutzer auffordern, zu bestätigen, dass sein Benutzerverzeichnis weder gesperrt noch auf einem Volumes, das voll oder gesperrt ist, gespeichert ist. </li> 
     <li id="li_6D1136EA750A459BBECEEE5F73F527BB">Wenn der Distributor anstelle von Flash AIR verwendet, kann das Problem durch eine Pfadlängenbegrenzung verursacht werden. <p>Distributoren sollten den Namen ihrer AIR-Anwendung auf eine vernünftige Weise kürzen. Veröffentlichen Sie außerdem Inhalte erneut mit einer kürzeren <span class="codeph"> licenseID</span> und einer <span class="codeph"> policyID</span>. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3314 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptedDRMMetadata  </span> </td> 
   <td colname="col3"> <p>Dieser Fehler zeigt oft an, dass der Inhalt mit PKI-Zertifikaten gepackt wurde und der Player mit PKI-Produktionszertifikaten erstellt wurde oder umgekehrt. subErrorId enthält einen clientspezifischen Fehler oder Zeilenfehler. </p> 
    <ul id="ul_A122EF304CAF48A8B4DA1E3F4413E29B"> 
     <li id="li_A9A1A5B23E884C22A71E2DE7535FEB3B">Die Software des Distributors sollte protokollieren, welche Inhalte den Fehler verursacht haben. </li> 
     <li id="li_7AD7F13A4B1B4998A7E49664E7645815">Der Händler sollte bestätigen, dass der Fehler mit bestimmten Inhalten reproduzierbar ist. <p>Eventuell müssen Sie beschädigte Inhalte neu verpacken. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3315 </td> 
   <td colname="col2"><span class="codeph"> AAXS_PermissionDenfied  </span> </td> 
   <td colname="col3"> <p>Es gibt bekannte Fehler, bei denen dieser Fehlercode ausgegeben wird, wenn ein 3305 vorgesehen ist. Weitere Informationen finden Sie unter Ursachen und Auflösung<a href="https://forums.adobe.com/thread/1284947" format="https" scope="external"> von DRM 3305 [ServerConnectionFailure].</a> </p> <p>Von AIR geladene Remote SWF-Dateien dürfen nicht auf die Funktionen des Flash Accesses zugreifen. Dieser Fehlercode kann auch ausgegeben werden, wenn während des Netzwerkzugriffs ein Sicherheitsfehler auftritt. Beispiele sind der Zielserver, der keine Verbindung mit dem Client über crossdomain.xml herstellt, oder die crossdomain.xml-Datei ist nicht erreichbar. </p> <p>Weitere Informationen finden Sie unter <a href="https://forums.adobe.com/thread/1266592" format="https" scope="external"> DRM-Fehler 3315 mögliche Ursache und Auflösung</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3316 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NOTUSED_MOVED  </span> </td> 
   <td colname="col3"> War <span class="codeph"> ADOBECPSHIM_MinorErr_MissingAdobeCPModul</span>. Aufgrund von Flash-Fehlercode in 3344 verschoben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3317 </td> 
   <td colname="col2"><span class="codeph"> AAXS_LoadAdobeCPFail  </span> </td> 
   <td colname="col3"> <p>Wichtig:  Dies ist ein seltener Fehler und tritt in der Regel nicht in einer Produktions-Umgebung auf. </p> <p>Wenn der Fehler auftritt, können Sie einen der folgenden Schritte ausführen: 
     <ul id="ul_BC435E61623444BB98A86216531DC892"> 
      <li id="li_FA433D0758B642D2AFDCF04906B3FE18">Wenn Sie AIR verwenden, installieren Sie es erneut. </li> 
      <li id="li_F08D9AAFF46244F8842DEE5FD9CBBE0A">Wenn Sie Flash Player verwenden, laden Sie die Module <span class="codeph"> AdobeCP</span> erneut herunter. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3318 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InkompatibleAdobeCPVersion  </span> </td> 
   <td colname="col3"> Gilt nicht für Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3319 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MissingAdobeCPGetAPI  </span> </td> 
   <td colname="col3"> Gilt nicht für Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3320 </td> 
   <td colname="col2"><span class="codeph"> AAXS_HostAuthenticateFehlgeschlagen  </span> </td> 
   <td colname="col3"> Gilt nicht für Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3321 </td> 
   <td colname="col2"><span class="codeph"> AAXS_I15nFehlgeschlagen  </span> </td> 
   <td colname="col3"> <p>Der Prozess der Bereitstellung des Clients mit Schlüsseln ist fehlgeschlagen. subErrorId enthält einen clientspezifischen, serverspezifischen oder Zeilenfehler. </p> 
    <ul id="ul_98D919B9060A441AACB6106F6D8E8DA7"> 
     <li id="li_DCAB00A8AC4A426CBBD377374B3F71AE">Die Software des Distributors sollte den Vorgang mindestens einmal wiederholen. <p>Wenn Sie Google Chrome unter Windows verwenden, erläutern Sie, wie Sie den Zugriff auf Zusatzmodule zulassen, die sich nicht in einer Sandbox befinden. Weitere Informationen finden Sie unter <a href="https://helpx.adobe.com/adobe-access/kb/error-3321.html" format="html" scope="external"> Google Chrome' Zugriff auf die Sandbox verweigert</a>. </p> </li> 
     <li id="li_7FB7681FE32D444BB1BDBA3E5953A2C3">Der Händler sollte eine der folgenden Aufgaben ausführen: 
      <ul id="ul_486B64F187C44AE3B4775953A6142836"> 
       <li id="li_095B1D4CD051427CB2BFA7082B454056">Wenn der Fehler plattformübergreifend konsistent ist, sollten Sie das Problem mit der Adobe eskalieren. </li> 
       <li id="li_0C6EB7B912FA41E59657216498DA3515">Wenn der Fehler unter Windows auf Chrome beschränkt ist, weisen Sie den Benutzer an, den Zugriff auf nicht sandbox-Plugins zuzulassen. </li> 
      </ul> <p>Distributoren sollten ihre SWF-Datei auf Version 19 oder höher aktualisieren. Beim Chrome-spezifischen 3321-Fehler wird ein 3368-Fehler ausgegeben. Der Fehler 3368 kann genauer von der Software des Distributors verarbeitet werden. Diese Änderung wurde in Chrome Stable Kanal Version 26.0.1410.43 eingeführt. </p> <p>Tipp: Fehler <span class="codeph"> 3321:1090519056</span> kann bei den Flash Player-Versionen 11.1 bis 11.6 auftreten. Es wird empfohlen, ein Upgrade auf die neueste Flash Player-Version durchzuführen. </p> </li> 
    </ul> <p>Weitere Informationen finden Sie unter <a href="https://forums.adobe.com/thread/1277138" format="https" scope="external"> DRM-Fehler 3321 Ursachen und Auflösung</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Korruptionsfehler im globalen Store</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3322 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DeviceBindingFailure  </span> </td> 
   <td colname="col3"> <p>Das Gerät scheint nicht mit der bei der Initialisierung vorhandenen Konfiguration zu übereinstimmen. subErrorId enthält einen clientspezifischen Fehler oder Zeilenfehler. </p> <p>Die Software des Distributors muss eine der folgenden Aufgaben erfüllen: 
     <ul id="ul_444401051A2E407B95BC44491E9BB71C"> 
      <li id="li_93493EA05DB44CB1AEC368663F1ABA8D"> <p>Wenn das Gerät keinen Flash Player verwendet und AIR, iOS usw. verwendet, rufen Sie <span class="codeph"> DRMManager.resetDRMVouchers()</span> auf. </p> <p>Wenn das Problem unter iOS in einer Entwicklungsphase auftritt, bitten Sie den Entwickler, zu bestätigen, ob das Problem beim Wechsel zwischen Builds, die von Drittanbieter-Distributionssystemen (z. B. HockeyApp) heruntergeladen wurden, und einem lokalen Build aus Xcode behoben wurde. Attribute einer vorherigen Installation werden nicht vollständig überschrieben, wenn zwischen einem von HockeyApp verteilten Build und einem Build aus Xcode gewechselt wird. Diese Situation kann den 3322-Fehler auslösen. </p> <p>Um dieses Problem zu beheben, sollte der Entwickler den älteren Build vom Gerät entfernen, bevor er den neuen Build installiert. </p> </li> 
      <li id="li_A5C9633F11584C788A2D9A23CC18FA6D">Wenn das Gerät Flash Player verwendet und von 3322- oder 3346-Fehlercodes unbrauchbar ist, lesen Sie die Anweisungen in der Adobe zum programmgesteuerten Zurücksetzen des DRM-Lizenzspeichers bei <a href="https://forums.adobe.com/message/5535907#5535907" format="https" scope="external"> DRM-Fehler 3322/3346/3368 in Chrome (Info-Bar-Probleme)</a>. </li> 
     </ul> </p> <p>Dieser Fehler wird voraussichtlich nicht häufig auftreten. Bei Umgebung im Unternehmen, die Roaming-Profil verwenden, erhöht sich die Wahrscheinlichkeit, dass der Benutzer Inhalte anzeigt, die durch DRM geschützt sind, bei der Anmeldung auf verschiedenen Computern der Fehler 3322. Wenn möglich, sollte der Händler versuchen, diese Informationen vom Benutzer zu erhalten. </p> <p>Wenn der Fehler häufig auftritt, eskalieren Sie zur Adobe. Sie müssen der Adobe mitteilen, ob das Zurücksetzen des Lizenzspeichers das Problem gelöst hat (oder nicht), und die Adobe angeben, in welchen Browsern der Fehler auftritt. </p> <p>Weitere Informationen finden Sie in den folgenden Artikeln: 
     <ul id="ul_C468409D1EA046178CA7F54DCDCB84EA"> 
      <li id="li_20C8CA3853574CE486F21E7A3667DAB9"><a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> https://forums.adobe.com/message/5520902</a> </li> 
      <li id="li_6E6F1BD6FE7843449B3E2F06F342EFF7"><a href="https://forums.adobe.com/message/5535911" format="https" scope="external"> https://forums.adobe.com/message/5535911</a> </li> 
      <li id="li_2BE40E513A0C4BAD900C7B69FEF5D690"><a href="https://forums.adobe.com/message/5748618" format="https" scope="external"> https://forums.adobe.com/message/5748618</a> </li> 
      <li id="li_9C2BD122E3874E2893DD43E082A877E0"><a href="https://forums.adobe.com/message/6061165" format="https" scope="external"> https://forums.adobe.com/message/6061165</a> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3323 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptGlobalStateStore  </span> </td> 
   <td colname="col3"> <p>Dateien, die vom DRM-Client verwendet werden, wurden unerwartet geändert. subErrorId enthält einen clientspezifischen Fehler oder Zeilenfehler. </p> 
    <ul id="ul_96EA771046CA4B2B9FAE24D493F43FF2"> 
     <li id="li_D2693CD8EFEF46108828BA17E3F54FF6">Die Software des Distributors sollte den Benutzer dazu bringen, auf die gleiche Weise wie 3322 zurückzusetzen. </li> 
     <li id="li_0149B82436B64E28AC2B8C9B0EB09898">Wenn der GlobalStore mit einer Rate ausfällt, die höher ist als die erwartete Ausfallrate der Festplatten Ihrer Benutzerbasis, eskalieren Sie das Problem auf die Adobe. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3324 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MachineTokenInvalid  </span> </td> 
   <td colname="col3"> Lokale DRM-Datenspeicherung für diese Anwendung zurücksetzen. Rufen Sie DRMManager.resetDRM auf. <p>Der Lizenzserver kann möglicherweise keine Verbindung mit dem Zertifikatsperrlisten-Liste-Server herstellen, um seine Zertifikatsperrlisten zu aktualisieren, oder der Clientcomputer fordert eine Lizenz-/Authentifizierungsdatei an, die vom Lizenzserver widerrufen wurde. </p> <p>In den Serverprotokollen lautet der Fehlercode 111 MachineTokenInvalid. Auf Client-Ebene wird der Fehlercode 111 jedoch in den Fehlercode 3324 übersetzt. </p> <p>Der Administrator des DRM-Lizenzservers sollte prüfen, ob der Lizenzserver des Kunden die Adobe-Zertifikatsperrlisten jemals abrufen konnte. Wenn der Kunde Tomcat verwendet, kann der Kunde den Ordner "<span class="filepath"> tomcat/temp/</span>"überprüfen, um zu sehen, ob es 4 CRL-Dateien gibt. </p> 
    <ul id="ul_23B7F1A104AF49E79EA87DB8E15E337E"> 
     <li id="li_855D87F251184FE688A8D5FA0F6C9EF5">Wenn sich die Dateien in diesem Ordner befinden, klicken Sie im Windows Explorer und in der CRL-Viewer-Anwendung bei gedrückter Dublette auf die Dateien, um festzustellen, ob eine der Dateien abgelaufen ist. </li> 
     <li id="li_58EC4EDA2B5146188A0FF7B33C91E2FD">Wenn keine Dateien in tomcat/temp/ vorhanden sind, kann davon ausgegangen werden, dass dieser Lizenzserver aufgrund eines Firewall-/Routing-Problems nie in der Lage war, den Adobe-Zertifikatsperrlisten-Server zu erreichen. </li> 
    </ul> <p>Weitere Informationen finden Sie unter <a href="https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_secure_deployment_guidelines.pdf" format="http" scope="external"> Firewall-Regeln</a>. </p> <p>Wenn die Zertifikatsperrlisten-Dateien nicht verfügbar sind oder abgelaufen sind, müssen Sie bestätigen, dass der Lizenzserver erreicht werden kann. Öffnen Sie einen Netzwerksniffer auf dem Lizenzserver des Kunden, starten Sie den Server neu und versuchen Sie, eine Lizenz vom Server anzufordern. Sie können den Netzwerkverkehr beobachten, um zu sehen, ob Aufrufe der folgenden URL-Endpunkte erfolgreich sind: <p>Tipp:  Sie können auch die folgenden URLs für Zertifikatsperrlisten in einen Browser eingeben, um zu sehen, ob Sie die einzelnen Dateien manuell herunterladen können. </p> 
     <ul id="ul_9B65C7ABBDEC4AC9BF3755FFD3587971"> 
      <li id="li_6867A9050E8D421C9138AC853D1784C9"><a href="https://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl</a> </li> 
      <li id="li_6431689260554EAFAFDA2EC31798DCB5"><a href="https://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl</a> </li> 
      <li id="li_2939674D0F854ADEB67E45FD216288A2"><a href="https://crl2.adobe.com/Adobe/FlashAccessRootCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessRootCA.crl</a> </li> 
      <li id="li_96386E00BE9D4CB99D100057A5F7C6DD">crl3.adobe.com/AdobeSystemsIncorporated FlashAccessRuntime/LatestCRL.crl</li> 
     </ul> </p> <p>Wenn die Firewall-Regeln geöffnet sind und keine aktuellen 3324-Fehler auftreten, ist möglicherweise ein temporärer Netzwerkfehler aufgetreten. Überprüfen Sie die Serverprotokolle des Kunden, die sich wahrscheinlich im Ordner "<span class="codeph"> /tomcat/logs/</span>"befinden, um festzustellen, ob ein Fehler aufgetreten ist, wenn der Lizenzserver versucht hat, die Listen zum Zertifikatsperrvorgang abzurufen. <p>Wichtig:  Ein Fehler kann auftreten, wenn eine große Anzahl (oder ein Berst) von Clients einen 3324-Fehler bei einem temporären Netzwerkproblem meldet, wenn eine CRL-Datei erneuert wird. Als das Netzwerkproblem behoben wurde, wurden auch die 3324 Probleme behoben. </p> </p> <p>Wenn alle 4 CRL-Dateien im Ordner <span class="filepath"> tomcat/temp/</span> vorhanden sind und Clients immer noch 3324-Fehlercodes erhalten, kann es zu Problemen mit dem Dateizugriff auf die CRL-Dateien kommen. Um dieses Problem zu beheben, sollten Sie die Protokolle überprüfen und die vorhandenen Zertifikatsperrlisten-Dateien bereinigen. </p> <p>Wenn keine Serverprobleme vorliegen, fordern Sie den Benutzer auf, den Vorgang wie in 3322 beschrieben zurückzusetzen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Serverspeicher-Korruptionsfehler</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3325 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptServerStateStore  </span> </td> 
   <td colname="col3"> <p>Dateien, die vom DRM-Client verwendet werden, wurden unerwartet geändert. <span class="codeph"> Unter </span> subErrorId enthält einen clientspezifischen Fehler oder Zeilenfehler. </p> 
    <ul id="ul_860D2402DA61460AB0D938F1116F6D64"> 
     <li id="li_CF368C43452B4265B62ADA3E223894BA">Die Software des Distributors sollte den Vorgang erneut versuchen, da AdobeCP den fehlerhaften Serverspeicher intern gelöscht hat und ein erneuter Versuch erfolgreich sein sollte. Wenn der Vorgang fehlschlägt, protokollieren Sie das Problem. </li> 
     <li id="li_51A5803A1F754970BB4EBD6494F5DC96">Wenn die Ausfallrate der weitere Zustellversuche höher ist als die erwartete Ausfallrate der Festplatten Ihrer Benutzerbasis, eskalieren Sie das Problem zur Adobe. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3326 </td> 
   <td colname="col2"><span class="codeph"> AAXS_StoreTamperingDetected  </span> </td> 
   <td colname="col3"> Rufen Sie <span class="codeph"> DRMManager.resetDRM</span> auf. <p>Der Lizenzspeicher wurde manipuliert/beschädigt und kann nicht mehr verwendet werden. </p> <p>Die Software des Distributors sollte den Benutzer dazu bringen, auf die gleiche Weise zurückzusetzen wie in 3322 beschrieben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3327 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ClockTamperingDetected  </span> </td> 
   <td colname="col3"> Korrigieren Sie die Uhr oder erwerben Sie erneut die Lizenz <span class="codeph"> Autor/Lic/Domain</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Authentifizierungs-/Lizenz-/Domänenserverfehler</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3328 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerErrorTryAgain  </span> </td> 
   <td colname="col3"> <p>Dies ist ein serverseitiger Fehler, bei dem der Server die Anforderung vom Client nicht abschließen konnte. Dieser Fehler kann auftreten, wenn beispielsweise der Server ausgelastet ist (HTTP/500), der Server nicht über den erforderlichen Schlüssel zum Entschlüsseln der Anforderung verfügt usw. </p> <p>Auf dem Client gibt es keine Möglichkeit zu bestimmen, was schiefgelaufen ist. Der Kunde muss die Serverprotokolle für Adobe Access überprüfen, die in der Regel als <span class="codeph"> AdobeFlashAccess.log</span> bezeichnet werden, um festzustellen, was schiefgelaufen ist. Es gibt immer eine beschreibende Stapelablaufverfolgung im Protokoll, um das Problem anzuzeigen. <span class="codeph"> Unter </span> subErrorId enthält einen serverspezifischen oder Zeilenfehler. </p> <p>Der Distributor sollte sich die Serverprotokolle ansehen, um herauszufinden, welcher Server diesen Fehler sendet. Bei 3328-Fehlern mit dem Unterfehlercode 101 kann der Server die Anforderung nicht entschlüsseln. Der Kunde muss überprüfen, ob die auf dem Lizenzserver installierten Lizenz-/Transportserverzertifikate mit den Zertifikaten übereinstimmen, die während der Verpackung verwendet werden. </p> <p>Wenn Kunden außerdem die Referenz-Implementierung verwenden, müssen sie sicherstellen, dass in der Datei <span class="codeph"> flashaccess-refimpl.properties</span> keine Tippfehler vorhanden sind, in der die primären und zusätzlichen Zertifikate angegeben sind. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3329 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ApplicationSpecificError  </span> </td> 
   <td colname="col3"> <p>Der anwendungsspezifische Unterfehlercode ist Flash Access nicht bekannt. <span class="codeph"> Unter </span> ErrorId enthält einen serverspezifischen Fehler des benutzerdefinierten Lizenzservers des Herausgebers. Der Server gab einen Fehler im anwendungsspezifischen Namensraum zurück. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3330 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NeedAuthentication  </span> </td> 
   <td colname="col3"> <p>Dieser Fehler tritt auf, wenn der Inhalt so konfiguriert ist, dass Clients vor dem Erhalt der Lizenzen authentifiziert werden müssen. </p> 
    <ul id="ul_712D29B8B5A6401FB014C4A283918E32"> 
     <li id="li_2D56905EB50D4FDEAD69CA8EAE38AD1A">Die Software des Distributors sollte den Benutzer authentifizieren und dann die Lizenz erneut erwerben. <p>Wenn Ihr Dienst keine Authentifizierung verwenden möchte, protokollieren Sie die Identifizierung des Inhalts, der diesen Fehler verursacht. </p> </li> 
     <li id="li_B3BCF899B8BE41C7A4F7CF84B0503483">Für diesen Fehler sollte keine Eskalation erforderlich sein, es sei denn, der Inhalt sollte nicht so konfiguriert sein, dass eine Authentifizierung erforderlich ist. <p>In diesem Fall verpacken Sie die verletzenden Inhalte mit einer ordnungsgemäßen Richtlinie neu. Wenn der Inhalt richtig verpackt ist, finden Sie unter Diskrepanzen bei der Diagnose von Richtlinien/Lizenzen. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>Fehler bei der Lizenzdurchsetzung, die oben nicht behandelt werden</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3331 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentNotyetValid  </span> </td> 
   <td colname="col3"> <p>Die erworbene Lizenz ist noch nicht gültig. Um dieses Problem zu beheben, überprüfen Sie, ob die Client-Uhr nicht richtig eingestellt ist. Um die Client-Uhr festzulegen, verpacken Sie den Inhalt neu oder ändern Sie die Konfiguration des Lizenzservers. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3332 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CachedLicenseExpired  </span> </td> 
   <td colname="col3"> Erwerben Sie eine Lizenz erneut vom Server. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3333 </td> 
   <td colname="col2"><span class="codeph"> AAXS_PlaybackWindowExpired  </span> </td> 
   <td colname="col3"> <p>Sie müssen die Benutzer darüber informieren, dass sie diese Inhalte erst nach Ablauf der Richtlinie wiedergeben können. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3334 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidDRMPlatform  </span> </td> 
   <td colname="col3"> <p>Diese Plattform darf den Inhalt nicht wiedergeben, da der Content Provider beispielsweise die Adobe Access so konfiguriert hat, dass Adobe Access auf einer Plattform verweigert wird oder eine freigegebene domänengebundene Lizenz an ein Shared-Domain-Token gebunden ist, das für eine andere Partition vorgesehen ist. </p> <p>CDM gibt diesen Fehler möglicherweise aus, wenn der Inhalt nicht mit einer entsprechenden (CDM-Feature-Gated) Packager-Zertifizierung gepackt wurde. </p> <p>Wenn der Inhalt mit einem falschen PHDS/PHLS-Zertifikat verpackt wird, funktioniert der Inhalt möglicherweise in Chrome, nicht aber in anderen Browsern (oder umgekehrt). <p>Tipp:  Dies liegt daran, dass Chrome verschiedene PHDS/PHLS-Zertifikate verwendet. </p>Um zu bestätigen, welches Zertifikat verwendet wird, löschen Sie die Details der Inhaltsmetadaten und suchen Sie nach den <i>Empfänger-Zertifikaten</i>. Weitere Informationen finden Sie unter <a href="https://adobeprimetime.zendesk.com/agent/tickets/2891" format="https" scope="external"> https://adobeprimetime.zendesk.com/agent/tickets/2891</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3335 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidDRMVersion  </span> </td> 
   <td colname="col3"> Aktualisieren Sie auf die neueste Version des TVSDK für Android. <p>Führen Sie zur Behebung dieses Problems eine der folgenden Aufgaben aus: 
     <ul id="ul_BF1742948BC9461CB8686DE70124D3CD"> 
      <li id="li_690D440C94CC45A0AE55EC319B1C4C23">AIR aktualisieren </li> 
      <li id="li_CDD20251C881466E88BE7BBB53D61EBC">Aktualisieren Sie zum Flash Player das AdobeCP-Modul und versuchen Sie es erneut. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3336 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidRuntimePlatform  </span> </td> 
   <td colname="col3"> <p>Diese Plattform darf den Inhalt nicht wiedergeben, da der Content Provider beispielsweise den Zugriff konfiguriert hat, um FP/AIR auf einer Plattform Inhalte zu verweigern. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3337 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidRuntimeVersion  </span> </td> 
   <td colname="col3"> Aktualisieren Sie auf die neueste Version von TVSDK für Android. <p>Dies tritt auf, wenn der Inhalt oder der Server so konfiguriert ist, dass die Wiedergabe auf einer bestimmten Version des Flashs oder der AIR-Laufzeitumgebung verweigert wird. </p> 
    <ul id="ul_B0732D941256483CABBDD30C9BF43249"> 
     <li id="li_72782B1D638F48C0B87084689FB9C798">Befindet sich der Benutzer auf einem Betriebssystem, auf dem Flash aktualisiert werden kann, sollte die Software des Distributors den Benutzer auffordern, den Flash zu aktualisieren, und es erneut versuchen. Weisen Sie den Benutzer andernfalls an, einen anderen Computer zu verwenden. </li> 
     <li id="li_1E3FD93CE39E43F2B7D961299B1211DA">Wenn der Fehler 3337 bei Verdacht steht, stellen Sie fest, ob er für bestimmte Inhalte auftritt, und verpacken Sie diese Inhalte erneut. Wenn Inhalte korrekt verpackt sind, finden Sie unter Diskrepanzen zwischen den DiagnoRichtlinien/Lizenzen </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3338 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UnknownConnectionType  </span> </td> 
   <td colname="col3"> <p>Der Verbindungstyp kann nicht erkannt werden. Die Richtlinie erfordert, dass Sie Output Protection aktivieren. Dieses Problem wird nur erwartet, wenn der Inhalt für einen digitalen oder analogen Ausgabeschutz verpackt wird. </p> <p>Ein Problem in älteren Flash Playern als 11.8.800.168 verursachte gelegentlich den Fehler 3338 bei Inhalten, bei denen die Richtlinie darauf hinwies, dass der Inhaltsschutz <span class="codeph"> "VERWENDEN"ist, WENN VERFÜGBAR</span>. Dieses Problem wurde in Version 11.8.800.168 und höher behoben. </p> 
    <ul id="ul_4B6CA26A53F84838B5B95400925464D4"> 
     <li id="li_CBD890F467E449EBB5116E1561252058">Die Software des Distributors wählt eine Variante des Inhalts aus, die keinen Ausgabeschutz erfordert (z.B. SD-Variante eines HD-Streams). <p>Wenn der Fehler 3338 bei <span class="codeph"> USE_IF_AVAILABLE </span>-Inhalt auftritt, suchen Sie nach der Player-Versionsnummer. Wenn die Player-Version kleiner als 11.8.800.168 ist, empfehlen Sie dem Benutzer, den Flash Player zu aktualisieren. Wenn bei Versionen über 11.8.800.168 der Fehler 3338 auftritt, protokollieren Sie, welcher Inhalt den Fehler verursacht hat. </p> </li> 
     <li id="li_62886C1D96264B129928A7E29E6C70E1">Der Distributor sollte prüfen, welche Inhalte diesen Fehler verursachen, und überprüfen, ob die Richtlinie des Inhalts <span class="codeph"> NO_PROTECTION</span> oder <span class="codeph"> USE_IF_AVAILABLE</span> für analoge und digitale Ausgaben einstellt. <p>Wenn Inhalt versehentlich mit <span class="codeph"> NO_OUTPUT</span> oder <span class="codeph"> REQUIRED</span> verpackt wird, verpacken Sie den Inhalt erneut. Wenn der Inhalt richtig verpackt ist, finden Sie unter Diskrepanzen bei der Diagnostik von Richtlinien/Lizenzen. Eskalieren Sie andernfalls zur Adobe. </p> </li> 
    </ul> <p>Weitere Informationen finden Sie unter <a href="https://forums.adobe.com/message/5518688" format="https" scope="external"> Unerwartete 3338-Fehler erhalten, wenn Ihre DRM-Richtlinie auf USE_IF_AVAILABLE?</a> eingestellt ist. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3339 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoAnalogPlaybackAllowed  </span> </td> 
   <td colname="col3"> Wiedergabe auf einem analogen Gerät nicht möglich. Um das Problem zu beheben, schließen Sie ein digitales Gerät an. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3340 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoAnalogProtectionAvail  </span> </td> 
   <td colname="col3"> Inhalte können nicht wiedergegeben werden, da das angeschlossene analoge externe Anzeigegerät (Monitor/TV) nicht über die richtigen Funktionen verfügt (z. B. verfügt das Gerät nicht über Macrovision oder ACP). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3341 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDigitalPlaybackAllowed  </span> </td> 
   <td colname="col3"> Inhalte können auf einem digitalen Gerät nicht wiedergegeben werden. <p>Wichtig:  Dieses Problem sollte in einer Produktions-Umgebung nicht auftreten, da Herausgeber von Inhalten die digitale Wiedergabe nicht deaktivieren sollten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3342 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDigitalProtectionAvail  </span> </td> 
   <td colname="col3"> Das angeschlossene externe digitale Anzeigegerät (Monitor/TV) verfügt nicht über die richtigen Funktionen. Das Gerät verfügt beispielsweise nicht über HDCP. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3343 </td> 
   <td colname="col2"><span class="codeph"> AAXS_IntegrityVerificationFehlgeschlagen  </span> </td> 
   <td colname="col3"> <p>Gilt nicht für Android. </p> <p>Es ist derzeit bekannt, dass dieser Fehler zunächst auftritt, nachdem eine neue Version von Flash veröffentlicht wurde. Dies geschieht, weil Flash aktualisiert wurde, während der Flash geöffnet war, was den Flash in einen schlechten Zustand versetzt, bis der Browser neu gestartet wurde. </p> 
    <ul id="ul_A0AC4A77550E40409A04BD33748EA987"> 
     <li id="li_F41C1ABD838D41ABB0DF65093E664A29">Die Software des Distributors sollte die folgenden Aufgaben abschließen: 
      <ul id="ul_79B2AB1372074D448F129851AA24F985"> 
       <li id="li_B93EDD263D78434FAF198A01938D3508">Empfehlen Sie dem Benutzer, alle Browser zu schließen oder zu beenden und dann erneut zu öffnen. </li> 
       <li id="li_ADFBCFA66AD849E18DB390455458528E">Überprüfen Sie, ob die Flash-Version aktuell ist. <p>Wenn die Version nicht aktuell ist, raten Sie dem Kunden, ein Upgrade durchzuführen, schließen Sie alle Registerkarten in seinem Browser und öffnen Sie es erneut. </p> </li> 
      </ul> </li> 
     <li id="li_281B54582B5949AEA7D166246917EE41">Wenn nach einem erfolgreichen Neustart des Browsers ein Fehler auftritt, eskalieren Sie zur Adobe. <p>Wenn eine neue Version veröffentlicht wird, sollten Sie sich an den Support von Adoben wenden, um zu sehen, ob das Problem mit Hintergrundaktualisierungen behoben wurde. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3344 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MissingAdobeCPModul  </span> </td> 
   <td colname="col3"> Gilt nicht für Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3345 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DRMNoAccessError  </span> </td> 
   <td colname="col3"> <p>Gilt nicht für Android. </p> <p>Dieser Fehler tritt auf, wenn ein Teil des Flashs oder AIR nicht korrekt installiert wurde. </p> <p>Die Software des Distributors sollte einen der folgenden Schritte ausführen: 
     <ul id="ul_D1188E2D4FDF4BD89A04F5629D75D981"> 
      <li id="li_B33FBCA5D4534D668B86A5E93DB3A809">Bitten Sie den Benutzer, AIR zu deinstallieren und neu zu installieren. </li> 
      <li id="li_B7D2388E9FA84C26AF1C87B48AF9EF16">Rufen Sie zum Flash Player <span class="codeph"> System.update</span> auf. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3346 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MigrationFehlgeschlagen  </span> </td> 
   <td colname="col3"> 
    <ul id="ul_518AD4931CC64EB3A962DD451E6C5067"> 
     <li id="li_3C44F0740B08490E9C62D89C40B57DC2">Die Software des Distributors sollte einen der folgenden Schritte ausführen: 
      <ul id="ul_7D90526684BF4EB2BBADCF598AA13086"> 
       <li id="li_D15B4BEDAF7340F6B9BC886DF6E346EC">Bei AIR wird <span class="codeph"> DRMManager.resetDRMVouchers()</span> aufgerufen </li> 
       <li id="li_40A51D35408249CFA28DBC49FDA3408B">Wenn Flash aufgrund des Fehlercodes 3322 oder 3346 unbrauchbar ist, sollten die Benutzer zu <a href="https://forums.adobe.com/message/5535907#5535907" format="http" scope="external"> https://forums.adobe.com/message/5535907#5535907</a> navigieren und den Anweisungen des Artikels Adobe folgen, um ihren DRM-Lizenzspeicher programmgesteuert zurückzusetzen. </li> 
      </ul> </li> 
     <li id="li_0464471E4A094C80BF2986694341921A">Tritt dieser Fehler häufig auf, sollte der Distributor die Details zur Version des Frequenzplayers und zur Browserversion zur Adobe angeben. </li> 
    </ul> <p>Weitere Informationen finden Sie in den folgenden Forenartikeln: 
     <ul id="ul_44E0077FEAA749CC9549BF3846065304"> 
      <li id="li_2BE3B2443380415DA73B7AA3B6547B31"><a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> DRM-Fehler 3322/3346/3368 in Chrome (Info-Bar-Probleme)</a> </li> 
      <li id="li_4E5C7414756644E1AB78BE7B8112228C"><a href="https://forums.adobe.com/message/5535911" format="https" scope="external"> Fehler 3322 oder 3346 nach Hardwareänderung</a> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3347 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InausreichendDeviceCapabilites  </span> </td> 
   <td colname="col3"> <p>Die primäre Bedeutung dieses Fehlers besteht darin, dass die Lizenz eine Beschränkung hat, die vom DRM-Zertifikat des Kunden als nicht erfüllt angegeben wird. Die folgenden "Hardwarefunktionen"werden definiert, wenn das DRM-Zertifikat des Clients ausgestellt wird: 
     <ul id="ul_1EB6F1469C244CF0BA52C212495C053D"> 
      <li id="li_646043CE045C4DE2BBC939E1F4963DFE"><b>Barrierefreier Bus</b> ohne Benutzer. Wenn <b>true</b>, fließt der entschlüsselte Datenträger nie über einen Bus oder in den Hauptspeicher, auf den eine Anwendung zugreifen kann. <p>Wenn <b>false</b>, kann die Anwendung nach der Entschlüsselung auf Inhalte zugreifen. </p> </li> 
      <li id="li_02AAECAF4D35447BA10554541B46DE67"><b>Hardwarestamm des Vertrauens</b>. Wenn <b>true</b>, wurde die gesamte Software, die beim Booten auf dem Gerät geladen wird, für einen Schlüssel oder Digest validiert, der nur in der Hardware verfügbar ist. <p>Beide Einschränkungen werden auf der Clientseite überprüft, wenn die Lizenz für das DRM-Zertifikat für den Client geöffnet wird und der Fehler sofort auftritt. Diese Einschränkungen können auch auf der Serverseite vor der Lizenzerteilung überprüft werden. </p> </li> 
     </ul> </p> <p>Die sekundäre Bedeutung dieses Fehlers ist, dass die Lizenz die "Jailbreak Enforcement"-Richtlinie hat und auf dem Gerät ein Jailbreak erkannt wurde. Diese Prüfung erfolgt regelmäßig auf der Clientseite und kann nicht auf der Serverseite überprüft werden. </p> <p>Die Distributoren können die Richtlinien aktualisieren und die Einschränkungen entfernen. Bei Gerätefunktionsrichtlinien müssen Sie den Befehl zum Aktualisieren der Richtlinie mit dem Flag <span class="codeph"> -devCapabilityV1</span> und ohne Argumente ausgeben. Legen Sie für die Strafverfolgung von Inhaftierungen <span class="codeph"> policy.forceJailbreak=false</span> fest. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3348 </td> 
   <td colname="col2"><span class="codeph"> AAXS_HardStopIntervalExpired  </span> </td> 
   <td colname="col3"> Das Intervall für die feste Unterbrechung ist abgelaufen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3349 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerVersionTooHigh  </span> </td> 
   <td colname="col3"> Der Server wird mit einer Version ausgeführt, die höher ist als die höchste vom Client unterstützte Version. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3350 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerVersionTooLow  </span> </td> 
   <td colname="col3"> Der Server wird mit einer Version ausgeführt, die unter der vom Client unterstützten Mindestversion liegt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3351 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenInvalid  </span> </td> 
   <td colname="col3"> Das Domänen-Token war ungültig. Um dieses Problem zu beheben, registrieren Sie sich erneut bei der Domäne. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3352 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenTooOld  </span> </td> 
   <td colname="col3"> Das Domänentoken ist älter als das Token, das für die Lizenz erforderlich ist. Um das Problem zu beheben, registrieren Sie sich erneut bei der Domäne. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3353 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenTooNew  </span> </td> 
   <td colname="col3"> Das Domänentoken ist neuer als das für die Lizenz erforderliche Token. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3354 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenExpired  </span> </td> 
   <td colname="col3"> Das DomänenToken ist abgelaufen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3355 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainJoinFailure  </span> </td> 
   <td colname="col3"> Domänenbeitritt fehlgeschlagen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3356 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoCorrespondenceRoot  </span> </td> 
   <td colname="col3"> Eine Root-Lizenz für eine V3-Laublizenz wurde nicht gefunden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3357 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoValidEmbeddedLicense  </span> </td> 
   <td colname="col3"> Es wurde keine gültige eingebettete Lizenz gefunden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3358 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoACPPprotectAvail  </span> </td> 
   <td colname="col3"> Wiedergabe nicht möglich, da das angeschlossene analoge Gerät keinen AKP-Schutz besitzt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3359 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoCGMSAPprotectAvail  </span> </td> 
   <td colname="col3"> Wiedergabe nicht möglich, da das angeschlossene analoge Gerät keinen CGMS-A-Schutz besitzt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3360 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainRegistrationRequired  </span> </td> 
   <td colname="col3"> Inhalt erfordert die Domänenregistrierung. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3361 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NotRegisteredToDomain  </span> </td> 
   <td colname="col3"> Der Computer ist nicht in der Domäne für die angegebenen Metadaten registriert. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3362 </td> 
   <td colname="col2"><span class="codeph"> AAXS_OperationTimeoutError  </span> </td> 
   <td colname="col3"> Der asynchrone Vorgang dauerte länger als <span class="codeph"> maxOperationTimeout</span>. Wird nur von iOS DRMNative Framework zurückgegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3363 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UnsupportedIOSPlaylistError  </span> </td> 
   <td colname="col3"> Die weitergeleitete M3U8-Wiedergabeliste enthielt nicht unterstützten Inhalt. Wird nur von iOS DRMNative Framework zurückgegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3364 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDeviceId  </span> </td> 
   <td colname="col3"> <p>Das Framework hat die Geräte-ID angefordert, aber der zurückgegebene Wert war leer. </p> <p>Der Benutzer sollte in den Chrome-Einstellungen nicht das Kontrollkästchen <span class="uicontrol"> ID für geschützten Inhalt zulassen</span> aktivieren. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3365 </td> 
   <td colname="col2"><span class="codeph"> AAXS_IncognitoModeNotAllowed  </span> </td> 
   <td colname="col3"> <p>Diese Browser-/Plattformkombination erlaubt keine DRM-geschützte Wiedergabe im Inkognito-Modus. </p> <p>Die Software des Distributors sollte dem Benutzer empfehlen, den Incognito-Modus zu beenden oder einen anderen Browser zu verwenden. Weitere Informationen finden Sie unter <a href="https://forums.adobe.com/thread/1266622" format="https" scope="external"> DRM-Fehler 3365 Ursache und Auflösung</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3366 </td> 
   <td colname="col2"><span class="codeph"> AAXS_BadParameter  </span> </td> 
   <td colname="col3"> <p>Die Host-Laufzeitumgebung hat die Access-Bibliothek mit einem ungültigen Parameter aufgerufen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3367 </td> 
   <td colname="col2"><span class="codeph"> AAXS_BadSignature  </span> </td> 
   <td colname="col3"> Fehler beim Signieren des m3u8-Manifests. Nur von iOS DRMNative Framework oder AVE zurückgegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3368 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UserSettingsNoAccess</span> </td> 
   <td colname="col3"> <p>Der Benutzer hat den Vorgang abgebrochen oder Einstellungen eingegeben, die den Zugriff auf das System verweigern. </p> <p>Dieser Fehler wird nur ausgegeben, wenn die SWF-Version 19 oder höher ist. Aus Gründen der Abwärtskompatibilität wird 3321 ausgegeben, wenn die SWF Version 18 oder früher ist. </p> <p>Die Software des Distributors sollte den Benutzer zu einer Erklärung führen, wie der Zugriff auf nicht sandbox-Plugins möglich ist. Weitere Informationen finden Sie unter <a href="https://helpx.adobe.com/adobe-access/kb/error-3321.html" format="html" scope="external"> Google Chrome's unsandbox access verweigert</a> und <a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> DRM Error 3322/3346/3368 in Chrome (Info-Bar Problems)</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3369 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InterfaceNotAvailable</span> </td> 
   <td colname="col3"> <p>Eine erforderliche Browserschnittstelle ist nicht verfügbar. Dieses Problem tritt nur bei Pepper auf. Es kann zu Abweichungen zwischen dem Flash-Plugin und der Browserversion kommen. </p> <p>Die Software des Distributors sollte den Benutzer anleiten, um sicherzustellen, dass die neueste Version des Browsers installiert ist. </p> <p> Wenn die Häufigkeit dieses Fehlers zunimmt und mit einer veröffentlichten Browseraktualisierung übereinstimmt, eskalieren Sie die Adobe. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3370 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentIdSettingsNoAccess</span> </td> 
   <td colname="col3"> <p>Der Benutzer hat die Einstellung <span class="uicontrol"> "IDs für geschützten Inhalt zulassen</span> deaktiviert. </p> <p>Tipp:  Dieser Fehler trat bei Pepper-Versionen 13.0.0.x oder höher auf. </p> <p>Die Software des Distributors sollte den Benutzer anleiten, die Einstellung <span class="uicontrol"> Identifikatoren für geschützten Inhalt zulassen</span> zu aktivieren. </p> <p>Das Managementteam des Distributors sollte den Benutzer anleiten, die Einstellung <span class="uicontrol"> "IDs für geschützten Inhalt zulassen</span> zu aktivieren. </p> <p>Weitere Informationen finden Sie unter <a href="https://forums.adobe.com/message/6518323#6518323" format="https" scope="external"> https://forums.adobe.com/message/6518323#6518323</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3371 </td> 
   <td colname="col2"><span class="codeph"> AAXS_</span><span class="codeph"> NoOPConstraintInPixelConstraints</span> </td> 
   <td colname="col3"> <p>Fehlerhafte Auflösung basierend auf Ausgabeschutzbeschränkungen in der Lizenz. </p> <p>Die Software des Distributors sollte eine Fehlermeldung anzeigen. Bitten Sie den Benutzer, das Problem dem Distributor mit einem Inhaltstitel zu melden. </p> <p>Der Distributor sollte Inhalte mit einer gültigen Richtlinie neu verpacken. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3372 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ResolutionLargerThanMaxResolution</span> </td> 
   <td colname="col3"> <p>Die Auflösung des Inhalts ist größer als die in der Ausgabeschränkung angegebene maximale Auflösung. </p> <p>Wenn das Managementteam des Distributors diesen Fehler in seinen Protokollen sieht, sollte es die auflösungsbasierte Ausgabeschutzrichtlinie überprüfen und den Inhalt gegebenenfalls neu verpacken. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3373 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MinorErr_DisplayResolutionLargerThanConfirm</span> </td> 
   <td colname="col3"> <p>Die Auflösung des Inhalts ist größer als die Auflösung, die durch die derzeit aktive Ausgabeschränkung angegeben wird. </p> <p>Wenn das Managementteam des Distributors diesen Fehler in seinen Protokollen sieht, sollte es die auflösungsbasierte Ausgabeschutzrichtlinie überprüfen und den Inhalt gegebenenfalls neu verpacken. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3374 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MinorErr_ClientCommProcessFehlgeschlagen</span> </td> 
   <td colname="col3"> <p>Fehler bei der clientseitigen Kommunikationsverarbeitung, z. B. Anforderungsgenerierung, Antwortverarbeitung, ungültiges Authentifizierungstoken usw. </p> <p>Wenn das Managementteam des Distributors diesen Fehler in seinen Protokollen sieht, sollte es die auflösungsbasierte Ausgabeschutzrichtlinie überprüfen und gegebenenfalls Inhalte neu verpacken. </p> </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR: Videowiedergabewerte {#section_7079501250C2487499639F92EC774525}

Die Video Encoder-Schnittstelle der AVE gibt diese Videowiedergabebenachrichtigungen im Metadatenobjekt `NATIVE_ERROR` zurück.

<table id="table_5EEB1F60E5854452A8B0BABBE9B32651"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Wert für den Metadatenschlüssel NATIVE_ERROR_CODE </th> 
   <th colname="col2" class="entry"> Wert für den Metadatenschlüssel NATIVE_ERROR_NAME </th> 
   <th colname="col3" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> -1 </td> 
   <td colname="col2"><span class="codeph"> END_OF_PERIOD</span> </td> 
   <td colname="col3"> Ende des Zeitraums. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 0 </td> 
   <td colname="col2"><span class="codeph"> ERFOLG</span> </td> 
   <td colname="col3"> Vorgang erfolgreich. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 1 </td> 
   <td colname="col2"> <span class="codeph"> ASYNC_OPERATION_IN_PROGRESS</span> </td> 
   <td colname="col3"> Asynchroner Vorgang. Der Antrag wurde gestellt. Erfolgs-/Fehlerinformationen stehen später zur Verfügung. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 2 </td> 
   <td colname="col2"><span class="codeph"> EOF</span> </td> 
   <td colname="col3"> Vorgang aufgrund der Dateiende-Bedingung (EOF) nicht möglich. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 1 </td> 
   <td colname="col2"><span class="codeph"> DECODER_FAILED</span> </td> 
   <td colname="col3"> Der Decoder ist zur Laufzeit fehlgeschlagen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 4 </td> 
   <td colname="col2"><span class="codeph"> DEVICE_OPEN_ERROR</span> </td> 
   <td colname="col3"> Hardwaredecoder konnte nicht geöffnet werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 5 </td> 
   <td colname="col2"><span class="codeph"> FILE_NOT_FOUND  </span> </td> 
   <td colname="col3"> Die Ressource kann nicht gefunden werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 6 </td> 
   <td colname="col2"><span class="codeph"> GENERIC_ERROR  </span> </td> 
   <td colname="col3"> Allgemeiner Fehler. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 7 </td> 
   <td colname="col2"><span class="codeph"> IRRECOVERABLE_ERROR  </span> </td> 
   <td colname="col3"> Eine Fehlerbedingung, von der die Video-Engine nicht wiederhergestellt werden kann. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 8 </td> 
   <td colname="col2"><span class="codeph"> LOST_CONNECTION_RECOVERABLE  </span> </td> 
   <td colname="col3"> Netzwerkfehler beim Versuch der Wiederherstellung. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 9 </td> 
   <td colname="col2"><span class="codeph"> NO_FIXED_SIZE  </span> </td> 
   <td colname="col3"> Die Größe der Ressource kann nicht bestimmt werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 10 </td> 
   <td colname="col2"><span class="codeph"> NOT_IMPLEMENTITED  </span> </td> 
   <td colname="col3"> Funktion nicht implementiert. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 11 </td> 
   <td colname="col2"><span class="codeph"> OUT_OF_MEMORY  </span> </td> 
   <td colname="col3"> Nicht genügend Arbeitsspeicher. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 12 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR  </span> </td> 
   <td colname="col3"> Fehler beim Parsen der Mediendatei. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 13 </td> 
   <td colname="col2"><span class="codeph"> SIZE_UNKNOWN  </span> </td> 
   <td colname="col3"> Die Ressource hat eine Größe, aber sie ist unbekannt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 14 </td> 
   <td colname="col2"><span class="codeph"> UNDER_FLOW  </span> </td> 
   <td colname="col3"> Unterlaufbedingung. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 15 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_CONFIG  </span> </td> 
   <td colname="col3"> Konfiguration wird nicht unterstützt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 16 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_OPERATION  </span> </td> 
   <td colname="col3"> Vorgang wird nicht unterstützt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 17 </td> 
   <td colname="col2"><span class="codeph"> WAITING_FOR_INIT  </span> </td> 
   <td colname="col3"> Noch nicht initialisiert. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 18 </td> 
   <td colname="col2"><span class="codeph"> INVALID_PARAMETER  </span> </td> 
   <td colname="col3"> Ungültiger Parameter. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 19 </td> 
   <td colname="col2"><span class="codeph"> INVALID_OPERATION</span> </td> 
   <td colname="col3"> Vorgang nicht zulässig. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 20 </td> 
   <td colname="col2"><span class="codeph"> OP_ONLY_ALLOWED_IN_PAUSED_STATE</span> </td> 
   <td colname="col3"> Der Vorgang ist nur während der Pause zulässig. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 21 </td> 
   <td colname="col2"><span class="codeph"> OP_INVALID_WITH_AUDIO_ONLY_FILE</span> </td> 
   <td colname="col3"> Der Vorgang kann nicht für reinen Audiodateien verwendet werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 22 </td> 
   <td colname="col2"><span class="codeph"> PREVIOUS_STEP_SEEK_IN_PROGRESS</span> </td> 
   <td colname="col3"> Der vorherige Suchvorgang wird noch ausgeführt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 23 </td> 
   <td colname="col2"><span class="codeph"> SOURCE_NOT_SPECIFIED  </span> </td> 
   <td colname="col3"> Ressource nicht angegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 24 </td> 
   <td colname="col2"><span class="codeph"> RANGE_ERROR</span> </td> 
   <td colname="col3"> Der angegebene Wert liegt außerhalb des zulässigen Bereichs. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 25 </td> 
   <td colname="col2"><span class="codeph"> INVALID_SEEK_TIME</span> </td> 
   <td colname="col3"> Ungültige Suchzeit. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 26 </td> 
   <td colname="col2"><span class="codeph"> FILE_STRUCTURE_INVALID</span> </td> 
   <td colname="col3"> Die angegebene Datei entspricht nicht der erwarteten Syntax. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 27 </td> 
   <td colname="col2"><span class="codeph"> COMPONENT_CREATION_FAILURE</span> </td> 
   <td colname="col3"> Eine wesentliche Komponente konnte nicht erstellt werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 28 </td> 
   <td colname="col2"><span class="codeph"> DRM_INIT_ERROR</span> </td> 
   <td colname="col3"> DRM-Kontext konnte nicht erstellt werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 29 </td> 
   <td colname="col2"><span class="codeph"> CONTAINER_NOT_SUPPORTED  </span> </td> 
   <td colname="col3"> Container-Typ wird nicht unterstützt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 30 </td> 
   <td colname="col2"><span class="codeph"> SEEK_FAILED</span> </td> 
   <td colname="col3"> Suche fehlgeschlagen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 31 </td> 
   <td colname="col2"><span class="codeph"> CODEC_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> Nicht unterstützter Codec. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 32 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_UNVERFÜGBAR</span> </td> 
   <td colname="col3"> Netzwerk ist nicht verfügbar. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 33 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_ERROR</span> </td> 
   <td colname="col3"> Fehler beim Abrufen von Daten aus dem Netzwerk. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 34 </td> 
   <td colname="col2"><span class="codeph"> ÜBERLAUF</span> </td> 
   <td colname="col3"> Überlauf. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 35 </td> 
   <td colname="col2"><span class="codeph"> VIDEO_PROFIL_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> Nicht unterstütztes Video-Profil. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 36 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_NOT_LOADED</span> </td> 
   <td colname="col3"> Ein Vorgang wurde für einen HOLD-Zeitraum oder einen Zeitraum versucht, der noch nicht geladen wurde. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 37 </td> 
   <td colname="col2"><span class="codeph"> INVALID_REPLACE_DURATION</span> </td> 
   <td colname="col3"> Die angegebene Ersetzungsdauer ist ungültig oder erstreckt sich über das Ende des Streams hinaus. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 38 </td> 
   <td colname="col2"><span class="codeph"> CALLED_FROM_WRONG_THREAD</span> </td> 
   <td colname="col3"> API kann nicht aus dem falschen Thread aufgerufen werden. Meistens für API-Elemente, die nur aus dem Main-Thread aufgerufen werden sollten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 39 </td> 
   <td colname="col2"><span class="codeph"> FRAGMENT_READ_ERROR</span> </td> 
   <td colname="col3"> Fragmentlesefehler. Kein Failover vorhanden. Engine versucht, das nächste Fragment zu lesen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 40 </td> 
   <td colname="col2"><span class="codeph"> ABGESCHLOSSEN</span> </td> 
   <td colname="col3"> Der Vorgang wurde durch einen expliziten Abort- oder Destroy-Aufruf abgebrochen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 41 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_HLS_VERSION</span> </td> 
   <td colname="col3"> Diese Version des HLS-Mediums kann nicht wiedergegeben werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 42 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_FAIL_OVER</span> </td> 
   <td colname="col3"> Kann nicht übersprungen werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 43 </td> 
   <td colname="col2"><span class="codeph"> HTTP_TIME_OUT</span> </td> 
   <td colname="col3"> Beim HTTP-Download ist ein Timeout aufgetreten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 44 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_DOWN  </span> </td> 
   <td colname="col3"> Die Netzwerkverbindung des Benutzers ist nicht verfügbar. Die Wiedergabe kann jeden Moment unterbrochen werden und wird fortgesetzt, sobald die Verbindung verfügbar ist. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 45 </td> 
   <td colname="col2"><span class="codeph"> NO_USABLE_BITRATE_PROFIL</span> </td> 
   <td colname="col3"> Es wurde kein nutzbares Bitrate-Profil im Stream gefunden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 46 </td> 
   <td colname="col2"><span class="codeph"> BAD_MANIFEST_SIGNATURE</span> </td> 
   <td colname="col3"> Das Manifest hat eine ungültige Unterschrift. Der Manifestsignierungstest ist fehlgeschlagen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 47 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_LOAD_PLAYLIST</span> </td> 
   <td colname="col3"> Wiedergabeliste kann nicht geladen werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 48 </td> 
   <td colname="col2"><span class="codeph"> REPLACEMENT_FAILED</span> </td> 
   <td colname="col3"> In einer Einfüge-API angegebene Ersetzung konnte nicht erfolgreich durchgeführt werden. Das bedeutet, dass die Einfügung erfolgreich war, die Ersetzung jedoch nicht. Der Austausch kann fehlschlagen, wenn das zu ersetzende Manifest aus der Zeitleiste entfernt wurde. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 49 </td> 
   <td colname="col2"><span class="codeph"> SWITCH_TO_ASYMMETRIC_PROFIL</span> </td> 
   <td colname="col3"> DRM wechselt zu einem asymmetrischen Profil. Es wird erwartet, dass alle Profil in ihrer Dauer ausgerichtet werden. Andernfalls wird diese Warnung ausgegeben und es kann zu Sprüngen bei der Wiedergabe kommen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 50 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_BACKWARD</span> </td> 
   <td colname="col3"> Es wird erwartet, dass das Live-Fenster nur vorwärts geht. Andernfalls wird diese Warnung ausgegeben und das Fenster wird nicht gelesen. Aus diesem Grund kann es bei der Wiedergabe zu Sprüngen (oder Stopp/Long Pause) kommen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 51 </td> 
   <td colname="col2"><span class="codeph"> CURRENT_PERIOD_EXPIRED</span> </td> 
   <td colname="col3"> Das Live-Fenster wurde über den aktuellen Zeitraum hinaus verschoben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 52 </td> 
   <td colname="col2"><span class="codeph"> CONTENT_LENGTH_MISMATCH</span> </td> 
   <td colname="col3"> Die vom HTTP-Server gemeldete Inhaltslänge entsprach nicht der tatsächlichen Mediengröße. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 53 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_HOLD</span> </td> 
   <td colname="col3"> Der Medienleser kann keine weiteren Informationen lesen, da er die mit der setHoldAt-API festgelegte Zeit erreicht hat. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 54 </td> 
   <td colname="col2"><span class="codeph"> LIVE_HOLD  </span> </td> 
   <td colname="col3">Der Medienleser kann keine Segmente laden, da er das Ende des Live-Fensters erreicht hat. Das Laden des Segments wird fortgesetzt, wenn der Server neue Medien in das Live-Fenster einfügt. Dieser Status wird normalerweise erreicht, wenn: 
    <ul id="ul_FCFF658EDA4144E59970B317D6DEB624"> 
     <li id="li_2F6EEEB782D54CD999BC7CC7C0B78B48">Die Variable <span class="codeph"> bufferTime</span> ist zu hoch (entspricht oder höher als die Dauer des Live-Fensters). </li> 
     <li id="li_25CE97115ED64E44AA89977FB5F0DCF7">Eine Kombination aus einer oder mehreren der API zum Einfügen/Löschen ersetzte mehr Medien als hinzugefügt. </li> 
     <li id="li_1B14716B2157492AB1859306D1250523">Der nächste Zeitraum ist ein Live-Zeitraum mit einem ausstehenden Medienaustausch (aufgrund des InsertBy-API-Aufrufs) </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 55 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_INTERLEAVING  </span> </td> 
   <td colname="col3"> Das Audio- und Videointeragieren in den Medien wird nicht ordnungsgemäß ausgeführt. Dies ist ein Verpackungsfehler. Die Warnung wird ausgelöst, wenn der Unterschied zwei Sekunden überschreitet. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 56 </td> 
   <td colname="col2"><span class="codeph"> DRM_NOT_AVAILABLE</span> </td> 
   <td colname="col3"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 57 </td> 
   <td colname="col2"><span class="codeph"> PLAYBACK_NOT_AUTHORIZED</span> </td> 
   <td colname="col3"> Die HLS-Wiedergabe wurde im Flash Player nicht aktiviert. Siehe AuthorizedFeatures.enableHLSPlayback. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 78 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_SAMPLE_FOUND</span> </td> 
   <td colname="col3"> Der Decoder hat ein schlechtes Beispiel erhalten, das nicht dekodiert werden kann. Dies ist in der Regel kein fataler Fehler, deutet aber darauf hin, dass es möglicherweise Fehler im Audio/Video gibt. Zu viele Instanzen dieses Fehlers deuten auf eine fehlerhafte Kodierung oder fehlerhafte Datei hin. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 59 </td> 
   <td colname="col2"><span class="codeph"> RANGE_SPANS_READ_HEAD</span> </td> 
   <td colname="col3"> Nach dem Start der Wiedergabe sollte der Bereich "Einfügen/Ersetzen"den Lesekopf nicht enthalten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 60 </td> 
   <td colname="col2"><span class="codeph"> POSTROLL_WITH_LIVE_NOT_ALLOWED</span> </td> 
   <td colname="col3"> Einfügungen nach dem Rollen sind auf einem Live-Datenträger nicht zulässig. Sie sind jedoch zulässig, nachdem der Server die Medien als abgeschlossen markiert hat. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 61 </td> 
   <td colname="col2"><span class="codeph"> INTERNAL_ERROR</span> </td> 
   <td colname="col3"> Ein sehr seltenes Thema, das nie passieren sollte. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 62 </td> 
   <td colname="col2"><span class="codeph"> SPS_PPS_FOUND_OUTSIDE_AVCC</span> </td> 
   <td colname="col3"> Der Stream entspricht nicht der Verpackungsempfehlung, immer H264 SPS/PPS in einen AVCC zu setzen. Probleme mit der Suche/Wiedergabe werden möglicherweise angezeigt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 63 </td> 
   <td colname="col2"><span class="codeph"> PARTIAL_REPLACEMENT</span> </td> 
   <td colname="col3"> In der Einfüge-API angegebene Ersetzung wurde nur teilweise vorgenommen. Dies geschieht, wenn replaceDuration sich über die Zeitschienendauer erstreckt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 64 </td> 
   <td colname="col2"><span class="codeph"> RENDITION_M3U8_ERROR</span> </td> 
   <td colname="col3"> Beim Laden der Wiedergabeliste für Darstellungen ist ein Fehler aufgetreten. Dies gilt nur für AVE, nicht für FlashPlayer. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 65 </td> 
   <td colname="col2"><span class="codeph"> NULL_OPERATION</span> </td> 
   <td colname="col3"> Operation tut nichts. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 66 </td> 
   <td colname="col2"><span class="codeph"> SEGMENT_SKIPPED_ON_FAILURE</span> </td> 
   <td colname="col3"> Das Segment kann nicht wiedergegeben werden und wird bei einem Fehler übersprungen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 67 </td> 
   <td colname="col2"><span class="codeph"> INCOMPATIBLE_RENDER_MODE</span> </td> 
   <td colname="col3"> Inkompatibler Rendermodus. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 68 </td> 
   <td colname="col2"><span class="codeph"> PROTOCOL_NOT_SUPPORTED  </span> </td> 
   <td colname="col3"> Das in der URL verwendete Webprotokoll wird nicht unterstützt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 69 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR_INCOMPATIBLE_VERSION</span> </td> 
   <td colname="col3"> Fehler beim Parsen der Mediendatei. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 70 </td> 
   <td colname="col2"><span class="codeph"> MANIFEST_FILE_UNEXPECTEDLY_CHANGED</span> </td> 
   <td colname="col3"> Die Manifestdatei wurde unerwartet geändert. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 71 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_SPLIT_TIMELINE</span> </td> 
   <td colname="col3"> Split-Vorgang auf einer Zeitleiste kann nicht durchgeführt werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 72 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_ERASE_TIMELINE</span> </td> 
   <td colname="col3"> Vorgang zum Löschen auf einer Zeitleiste kann nicht ausgeführt werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 73 </td> 
   <td colname="col2"><span class="codeph"> DID_NOT_GET_NEXT_FRAGMENT</span> </td> 
   <td colname="col3"> Das nächste Fragment wurde nicht abgerufen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 74 </td> 
   <td colname="col2"><span class="codeph"> NO_TIMELINE</span> </td> 
   <td colname="col3"> Keine Zeitschiene in einer internen Datenstruktur vorhanden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 75 </td> 
   <td colname="col2"><span class="codeph"> LISTENER_NOT_FOUND</span> </td> 
   <td colname="col3"> In einer internen Datenstruktur wurde kein Listener gefunden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 76 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_BEGINN_ERROR</span> </td> 
   <td colname="col3"> Audio kann nicht Beginn werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 77 </td> 
   <td colname="col2"><span class="codeph"> NO_AUDIO_SINK</span> </td> 
   <td colname="col3"> In einer internen Datenstruktur ist kein Audiobecken vorhanden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 58 </td> 
   <td colname="col2"><span class="codeph"> FILE_OPEN_ERROR</span> </td> 
   <td colname="col3"> Datei kann nicht geöffnet werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 79 </td> 
   <td colname="col2"><span class="codeph"> FILE_WRITE_ERROR</span> </td> 
   <td colname="col3"> In eine Datei kann nicht geschrieben werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 80 </td> 
   <td colname="col2"><span class="codeph"> FILE_READ_ERROR</span> </td> 
   <td colname="col3"> Aus einer Datei kann nicht gelesen werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 81 </td> 
   <td colname="col2"><span class="codeph"> ID3PARSE_ERROR</span> </td> 
   <td colname="col3"> Bei der Analyse der ID3-Daten ist ein Fehler aufgetreten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 82 </td> 
   <td colname="col2"><span class="codeph"> SECURITY_ERROR  </span> </td> 
   <td colname="col3"> Das Laden des Inhalts ist aufgrund von Sicherheitsbeschränkungen fehlgeschlagen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 83 </td> 
   <td colname="col2"><span class="codeph"> TIMELINE_TOO_SHORT</span> </td> 
   <td colname="col3"> Die Zeitschiene ist zu kurz. Wenn es sich um einen Live-Stream handelt, kann es zu häufigen Pufferungen kommen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 84 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_BEGINN</span> </td> 
   <td colname="col3"> Der Stream wurde auf einen reinen Audiostream umgestellt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 85 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_END</span> </td> 
   <td colname="col3"> Der Stream wurde mit Video von reinem Audio auf einen Stream umgestellt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 87 </td> 
   <td colname="col2"><span class="codeph"> KEY_NOT_FOUND  </span> </td> 
   <td colname="col3"> Schlüssel kann nicht gefunden werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 88 </td> 
   <td colname="col2"><span class="codeph"> INVALID_KEY</span> </td> 
   <td colname="col3"> Der Schlüssel ist ungültig. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 89 </td> 
   <td colname="col2"> <span class="codeph"> KEY_SERVER_NOT_FOUND</span> </td> 
   <td colname="col3"> Der Schlüsselserver gibt keinen Schlüssel zurück. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 90 </td> 
   <td colname="col2"> <span class="codeph"> MAIN_MANIFEST_UPDATE_TO_BE_HANDLED</span> </td> 
   <td colname="col3"> Hauptmanifestaktualisierung kann nicht verarbeitet werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 91 </td> 
   <td colname="col2"> <span class="codeph"> UNREPORTED_TIME_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> Diskontinuität der nicht gemeldeten Zeit (PTS) festgestellt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 92 </td> 
   <td colname="col2"> <span class="codeph"> UNMATCHED_AV_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> Uneinheitliche Audio- und Videounterbrechung gefunden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 93 </td> 
   <td colname="col2"><span class="codeph"> TRICKPLAY_ENDED_DUE_TO_ERROR</span> </td> 
   <td colname="col3">Beim Abspielen von Medien im Modus <i>trick play</i> ist ein Fehler aufgetreten. Der Trick Play-Modus wird beendet und der Stream wird angehalten. Rufen Sie <span class="codeph"> Play()</span> auf, um das Medium im normalen Modus abzuspielen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 95 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_AHEAD</span> </td> 
   <td colname="col3"> Der Spieler ist außerhalb des Live-Fensters und muss nach vorn suchen, um aufzuholen. </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR: Crypto-Werte {#section_39365E545CAC49B9A4D4678657BB2155}

Das crypto-Modul der Adobe Video Engine gibt diese Benachrichtigungen im Metadatenobjekt `NATIVE_ERROR` zurück.

| Wert für den Metadatenschlüssel NATIVE_ERROR_CODE | Wert für den Metadatenschlüssel NATIVE_ERROR_NAME | Bedeutung |
|---|---|---|
| 300 | `CRYPTO_ALGORITHM_NOT_SUPPORTED` | Der verwendete Algorithmus wird nicht unterstützt. |
| 301 | `CRYPTO_ERROR_CORRUPTED_DATA` | Daten sind beschädigt. |
| 302 | `CRYPTO_ERROR_BUFFER_TOO_SMALL` | Puffer zu klein. |
| 303 | `CRYPTO_ERROR_BAD_CERTIFICATE` | Ungültiges Zertifikat. |
| 304 | `CRYPTO_ERROR_DIGEST_UPDATE` | Digest-Aktualisierung. |
| 305 | `CRYPTO_ERROR_DIGEST_FINISH` | Digest-Finish. |
| 306 | `CRYPTO_ERROR_BAD_PARAMETER` | Ungültiger Parameter. |
