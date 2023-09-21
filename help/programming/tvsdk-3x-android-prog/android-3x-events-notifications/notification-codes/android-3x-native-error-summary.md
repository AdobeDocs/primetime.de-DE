---
title: Details zur NATIVE_ERROR-Benachrichtigung
description: Details zur NATIVE_ERROR-Benachrichtigung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '6868'
ht-degree: 2%

---

# Details zur NATIVE_ERROR-Benachrichtigung {#details-for-the-native-error-notification}

Wenn TVSDK einen nativen Fehler verarbeitet, werden einige oder alle der folgenden Metadaten-Schlüsselwerte als Zeichenfolgen zurückgegeben.

<table id="table_7F713B7A56024D8DA3C84E449D09CC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>Metadaten-Schlüsselname</b></th> 
   <th colname="col2" class="entry"><b>Metadatenwert</b></th> 
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
   <td colname="col2"> Lange Beschreibung der Benachrichtigung (z. B. fehlgeschlagene Anzeigenauflösung). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> PSDK_ERROR_CODE</span> </td> 
   <td colname="col2"><span class="codeph"> com.adobe.mediacore.PSDKErrorCode</span> numerischer Wert als Zeichenfolge (z. B. "13"). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> PSDK_ERROR</span> </td> 
   <td colname="col2"><span class="codeph"> com.adobe.mediacore.PSDKErrorCode</span> als Zeichenfolge (z. B. <span class="codeph"> kECNetworkError</span>). </td> 
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
   <td colname="col2"> Geringfügiger Fehler vom DRM-Modul. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DRM_ERROR_STRING</span> </td> 
   <td colname="col2"> Beschreibung des Fehlers. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DRM_ERROR_SERVER_URL</span> </td> 
   <td colname="col2"> URL des DRM-Servers, mit dem TVSDK versucht hat zu reden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Fehler beim Laden des Anzeigenmanifests</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_URL</span> </td> 
   <td colname="col2"> URL des Inhalts, der nicht geladen werden konnte. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_TYPE</span> </td> 
   <td colname="col2">Art der Anzeige (eine Konstante aus der <span class="codeph"> MediaResource.Type</span> enum). </td> 
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
   <td colname="col2"> Beschreibung des Fehlers beim Herunterladen von Mediendateien. </td> 
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
   <td colname="col2">Beschreibung des Fehlers während des Fragments (z. B. <span class="codeph"> ts</span>) herunterladen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Fehler bei Audio-Tracking</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDIO_TRACK_NAME</span> </td> 
   <td colname="col2"> Name des Audiotracks, der nicht geladen werden konnte, wie im Manifest angegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDIO_TRACK_LANGUAGE</span> </td> 
   <td colname="col2"> Sprache des Audiotracks, wie im Manifest angegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Suchfehler</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DESIRED_SEEK_PERIOD</span> </td> 
   <td colname="col2"> ID des Zeitraums (Integer). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DESIRED_SEEK_POSITION</span> </td> 
   <td colname="col2"> <p>Position (in Millisekunden) gesucht (double). </p> </td> 
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

Die Video Encoder-Benutzeroberfläche der Adobe-Video-Engine gibt diese DRM-Benachrichtigungen im `NATIVE_ERROR` Metadatenobjekt.

Stellen Sie bei der Meldung von DRM-Fehlern an Adobe sicher, dass Sie die `NATIVE_SUBERROR_CODE` und `DRM_ERROR_STRING` für Unterstützung bei der Fehlerbehebung.

>[!TIP]
>
>Diese Liste enthält TVSDK-spezifische Informationen zu den Fehlern. Vollständige Beschreibungen finden Sie unter [ActionScript-Referenz zum ActionScript von Laufzeitfehlern für Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html#3300).

<table id="table_CD59A859865F4FFDBAA249C89C74770A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>Wert: NATIVE_- ERROR_CODE-Metadatenschlüssel</b></th> 
   <th colname="col2" class="entry"><b>Wert für den Metadatenschlüssel NATIVE_ERROR_NAME</b></th> 
   <th colname="col3" class="entry"><b>Bedeutung</b></th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 3300 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidVoucher</span> </td> 
   <td colname="col3"> 
    <ul id="ul_516E4CB32D624B22892DDB9266CB04CA"> 
     <li id="li_348FC0F38B11417994119B61C9244076">Was die Software des Distributors tun sollte: 
      <ul id="ul_7AFD45CF92454BA4927783FAA628FBC4"> 
       <li id="li_0D9CCE61612643648C12DCDDD252E52A">Wenn Sie Google Chrome verwenden und sich im Inkognito-Modus befinden und Ihre Flash Player-Version unter 11.6 liegt, kann dieser Fehler auftreten. <p>Es wird empfohlen, dass der Player die Versionsnummer des Browsers überprüft und dem Benutzer empfiehlt, den Inkognito-Modus zu beenden. </p> </li> 
       <li id="li_1DC6B755BD0840D48BEC92568FD330BA">Fordern Sie die Lizenz erneut an. <p>Wenn die Anfrage erfolgreich war, müssen Sie sie nicht protokollieren oder eskalieren. Wenn die Anfrage nicht erfolgreich war, protokollieren Sie den Inhalt, der den Fehler verursacht hat. <span class="codeph"> subErrorId</span> enthält einen Zeilenfehler, falls vorhanden. </p> </li> 
      </ul> </li> 
     <li id="li_060B5D60C9BB419CBFA7B062FBCF2632">Was sollte der Händler tun: 
      <ul id="ul_FADB29DBF0DA4A0E8E54134AEB7DCD8A"> 
       <li id="li_FC5B1C04D21E4AECB0EBD9ADD3198504">Wenn weitere Versuche bei anderen Konfigurationen als Chrome mit Flash unter Version 11.6 nicht erfolgreich sind, ist möglicherweise ein Fehler in der Verpackung aufgetreten. </li> 
       <li id="li_A720ECE591254021879B335B81B1F76D">Überprüfen Sie, ob das Problem für bestimmte Inhalte und Umpackungen spezifisch ist. </li> 
      </ul> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3301 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AuthenticationFailed</span> </td> 
   <td colname="col3"> <p>Der Server konnte den Client nicht authentifizieren oder autorisieren. </p> 
    <ul id="ul_BE77AC1848FB4C09B6318359ACF1B8EE"> 
     <li id="li_6FB37D317D174E8488C5070D20CD241C">Die Software des Distributors sollte alle erforderlichen Maßnahmen ergreifen, um die Anmeldeinformationen des Benutzers wiederherzustellen oder den Benutzer zum Erwerb des Zugriffs auf den Inhalt zu führen. </li> 
     <li id="li_BE071D59805B42D38E3E7650BC936417">Der Händler sollte bestätigen, dass der Autorisierungs- und Authentifizierungsmechanismus des Distributors ordnungsgemäß funktioniert. <p>Wenn die Distributoren nicht planen, die Authentifizierungs- oder Autorisierungsfunktionen zu verwenden, sollten sie überprüfen, ob die Richtlinie des fehlerhaften Inhalts eine Authentifizierung erfordert, und sich über Diskrepanzen bei der Diagnoserichtlinie/Lizenz informieren. </p> </li> 
    </ul> <p>Weitere Informationen zu diesem Fehlercode finden Sie unter <a href="https://forums.adobe.com/thread/1277149" format="https" scope="external"> Ursachen und Auflösung des DRM-Fehlers 3301</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3302 </td> 
   <td colname="col2"><span class="codeph"> AAXS_RequireSSL</span> </td> 
   <td colname="col3"> <p>Auf Access 4.0 und höher wird dieser Fehler in iOS ausgegeben, wenn die Remote-Schlüssel-URL HTTPS nicht als Schema verwendet. HTTPS ist erforderlich. </p> 
    <ul id="ul_3D47777BBCA14B67B107FBBE3E37E40C"> 
     <li id="li_7F7BBB27AE754CC39ABAAF9269739C49">Wenn der Distributor eine Version verwendet, die älter als Access v4 ist, oder die Version mindestens 4, die Plattform jedoch nicht iOS ist, sollte die Software des Distributors den Fehler protokollieren. <p>Der Fehler wird nur bei iOS ausgegeben. </p> </li> 
     <li id="li_D83C427D2A0D47408F723EF7195070B6">Wenn die Software des Distributors mindestens Adobe Access Version 4 ist und die Plattform iOS ist, müssen die Distributoren die Remote-Key-Server-URL, die sie verwenden, in HTTPS ändern. <p>Wenn sie nur HTTP verwenden, müssen Distributoren möglicherweise einen HTTPS-Server einrichten. Andernfalls müssen die Distributoren die protokollierten Informationen an die Adobe senden und das Problem eskalieren. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3303 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentExpired</span> </td> 
   <td colname="col3"> <p>Der angezeigte Inhalt ist gemäß den vom Inhaltsanbieter festgelegten Regeln abgelaufen. subErrorId enthält einen clientspezifischen Fehler oder Zeilenfehler. </p> <p> 
     <ul id="ul_1E4B3B8AE87A4E79997553BB2A0E52B9"> 
      <li id="li_EE3F2EEBF73743B9A38E4FCB7531E275">Die Software des Distributors sollte versuchen, die Lizenz einmal vom Server zu erwerben, um festzustellen, ob eine neue nicht abgelaufene Lizenz verfügbar ist. <p>Wenn keine Lizenz verfügbar ist oder die Lizenz abgelaufen ist, erlauben Sie dem Benutzer, eine neue Lizenz zu erwerben oder den Benutzer darüber zu informieren, dass der Inhalt nicht mehr angesehen werden kann. Wenn der Inhalt mit einer Richtlinie gepackt wurde, die ein abgelaufenes Ablaufdatum hat, protokolliert der Lizenzserver den Bericht <span class="codeph"> PolicyEvaluationException</span> und geben an, dass das Enddatum der Richtlinie abgelaufen ist (Server-Fehler-Code 303). Überprüfen Sie die Protokolldateien des Servers. </p> <p>Wenn möglich, sollten Kunden die Richtlinie überprüfen, die sie während der Verpackung verwendet haben, um festzustellen, ob sie abgelaufen ist. Das Java-Befehlszeilen-Tool lautet: <code> java&nbsp;-jar&nbsp;libs/AdobePolicyManager.jar&nbsp;&nbsp;&nbsp;detail&nbsp;demo.pol</code> </p> </li> 
      <li id="li_50DBE680D8F04E7DA3E29C65A93188E7">Der Distributor sollte bestätigen, ob die Ablaufdaten für die Lizenz wie gewünscht konfiguriert sind. </li> 
     </ul> </p> <p>Weitere Informationen zu diesem Fehlercode finden Sie unter <a href="https://forums.adobe.com/thread/1300813" format="https" scope="external"> 3303 (Inhalt abgelaufen) mit AMS/FMS unter Verwendung eines Live-Streams?</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3304 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AuthorizationFailed</span> </td> 
   <td colname="col3">Weitere Informationen zu diesem Fehlercode finden Sie unter <a href="https://forums.adobe.com/thread/1277149" format="https" scope="external"> Ursachen und Auflösung des DRM-Fehlers 3301</a>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3305 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerConnectionFailed</span> </td> 
   <td colname="col3"> <p>Die Verbindung zu den Lizenz- oder Domänenservern ist abgelaufen, entweder aufgrund einer Netzwerkverzögerung oder aufgrund der Offline-Verbindung des Clients. Normalerweise enthält subErrorId den HTTP-Rückgabecode. </p> 
    <ul id="ul_938C7D8F07F64B4FA71A09DDF37E2E64"> 
     <li id="li_6648EA0049094E369BD9AE9CCA6B148D">Die Software des Distributors sollte versuchen, eine Netzwerkverbindung zu einem zweifelsfrei funktionierenden Server herzustellen. <p>Wenn der Versuch fehlschlägt, fordern Sie den Benutzer auf, erneut eine Verbindung zum Netzwerk herzustellen. Wenn der Versuch erfolgreich war, protokollieren Sie ihn. </p> </li> 
     <li id="li_2ECA2C04BA08449DA3AD79A52EFAA229">Der Distributor sollte sicherstellen, dass alle verwendeten Lizenz- und Domain-Server online und im Netzwerk des Kunden sichtbar sind. </li> 
    </ul> <p>Weitere Informationen zu diesem Fehlercode finden Sie unter <a href="https://forums.adobe.com/thread/1284947" format="https" scope="external"> DRM 3305 [ServerConnectionFailed]-Ursachen und -Auflösung</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3306 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ClientUpdateRequire</span> </td> 
   <td colname="col3"> Verwenden Sie eine neuere Version von TVSDK für Android. <p>Der aktuelle Client kann die angeforderte Aktion nicht abschließen, aber ein aktualisierter Client kann die Anfrage möglicherweise ausführen. </p> <p>Dies kann mehrere Ursachen haben: 
     <ul id="ul_2EC4D42D5273439FA1AFDA1A2578B3D6"> 
      <li id="li_FCA926F5FAED4E7190BE855545AB6ACF">Es wurde eine freigegebene Domäne verwendet, die auf diesem Client nicht verfügbar ist. Dies ist wahrscheinlich der Fall, wenn die Wiedergabe in Chrome funktioniert, aber nicht in jedem anderen Browser und umgekehrt. <p> <p>Tipp: Chrome verwendet einen anderen PHDS/PHLS-Schlüssel als die anderen Browser. Weitere Informationen finden Sie unter <a href="https://adobeprimetime.zendesk.com/agent/tickets/2891" format="https" scope="external"> https://adobeprimetime.zendesk.com/agent/tickets/2891</a>. </p> </p> </li> 
      <li id="li_3B633FB699234DCEA136E9BE3CC3386D">Die Anwendung versucht, mehrere DRMSessions hinzuzufügen, wenn sie auf einer iOS-Version ausgeführt wird, die älter als Version 5.0 ist. </li> 
      <li id="li_F7ED993AF0B941A7A27216B4D587A999">Die Metadaten haben eine Version von 3 oder höher, wenn nur Version 2 unterstützt wird. </li> 
     </ul> </p> 
     <ul id="ul_EE4AE6AD4F1745A5B5623E53B599DB62"> 
      <li id="li_7A83869D4262443DA35FA1DF8D3097DD">Die Software des Distributors sollte den Benutzer warnen und den Betrieb abbrechen. <p>Wenn die Software ermitteln kann, ob ein Upgrade verfügbar ist, leiten Sie den Benutzer auf die geeignete Weise zu diesem Upgrade für die Plattform. </p> </li> 
      <li id="li_AF9C2711FDE54DA196EB9D2864632000">Tritt das Problem aufgrund einer freigegebenen Domäne auf, muss der Distributor mit Adobe nach einer aktualisierten Laufzeitumgebung oder Bibliothek suchen. <p>Für Flash-Laufzeitumgebungen kann der Distributor die Aktualisierung in seiner Anwendung direkt erzwingen. Im Fall einer Bibliothek muss der Distributor eine aktualisierte Bibliothek abrufen, seine Anwendung neu erstellen und sie für seine Benutzer bereitstellen. </p> <p>Tritt das Problem aufgrund mehrerer DRMSessions auf, muss der Distributor seine Anwendung aktualisieren, um die iOS-Versionsnummer zu überprüfen, bevor mehrere DRMSessions hinzugefügt werden. Oder sie können die Verteilung ihrer Anwendung auf iOS v5 und höher einschränken. </p> <p>Wenn das Problem auftritt, weil die Metadatenversion höher als Version 2 ist, ist das Problem wahrscheinlich mit den Metadaten beschädigt. Sie können versuchen, die Metadaten neu zu erstellen und sich die Ergebnisse anzusehen. Wenn das Problem weiterhin auftritt, protokollieren Sie das Problem und eskalieren Sie zu Adobe. </p> </li> 
     </ul> <p>Weitere Informationen zu diesem Fehlercode finden Sie unter <a href="https://forums.adobe.com/thread/1266675" format="https" scope="external"> Beheben eines 3306 DRMErrorEvent-Fehlercodes</a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3307 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InternalFailure</span> </td> 
   <td colname="col3"> <p>Dies stellt im Allgemeinen einen Fehler im Adobe Access-Code dar und ist unerwartet, es sei denn, es gibt einen bekannten Fehler, wie unten dargestellt. subErrorId enthält einen clientspezifischen Fehler oder Zeilenfehler. </p> 
    <ul id="ul_79F4A9655A2148519B1E9509C41F78C3"> 
     <li id="li_0E093AB4D6BD489B852279E6C1525A15">Wenn der Browser unter Windows Chrome ist und die Flash-Version 11.6 ist (SWF-Version 19 oder höher), sollte die Software des Distributors davon ausgehen, dass der Benutzer gepresst hat <span class="uicontrol"> Ablehnen</span> mit dem Infobar zu verabreichen und mit dem gleichen Arzneimittel wie 3368 zu behandeln. </li> 
     <li id="li_0215D1089B344861A2C0A73E1067CFEF">Wenn 3307 auftritt, wenn der Browser nicht Chrome- oder Flash-Version 11.6 ist, sollte der Distributor auf Adobe eskalieren. </li> 
    </ul> <p>Wichtig: <span class="codeph"> 3307:1107296344 (FailedToGetBrokerHandle)</span> kann mit den Chrome-Browserversionen 24-28 auftreten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3308 </td> 
   <td colname="col2"><span class="codeph"> AAXS_WrongLicenseKey</span> </td> 
   <td colname="col3"> <p>Dieser Fehler wird immer dann ausgegeben, wenn die verwendete Lizenz den falschen Schlüssel zum Entschlüsseln des Inhalts enthält. subErrorId enthält einen clientspezifischen Fehler oder Zeilenfehler. </p> <p>Es gibt offenbar nur zwei Möglichkeiten, diesen Fehler zu generieren: 
    <ul id="ul_1C955BD74C7843809D1B5A0CDCA5ED7B"> 
     <li id="li_18F0A7FDA6584887AD9DB3EDE54080D8">Der Kunde hat die standardmäßigen Adobe-Tools für die Erstellung von Lizenzen geändert (z. B. das Java-Framework des Lizenzservers). <p>In diesem Fall enthält die Lizenz einen ungültigen Schlüssel, der möglicherweise keinem Inhalt entspricht. </p> </li> 
     <li id="li_21D04ED1F1FA464785BC297D385766FF">Der Kunde hat mehrere Lizenzen mit derselben Lizenz-ID ausgestellt. <p>In diesem Fall gibt es mehrere Lizenzen, die auf dem Client verfügbar sind und mit den Inhaltsmetadaten übereinstimmen. Der Zugriffs-Code hat die falsche zur Verwendung ausgewählt. </p> </li> 
    </ul> </p> 
    <ul id="ul_64AEE62BE36946F290067CF475A36ECA"> 
     <li id="li_9EEB2B11A4DA41E78C5840D8FAA81F0D">Die Software des Distributors sollte versuchen, die Lizenz vom Server erneut zu erwerben. 
      <ul id="ul_ACADC5518B054D0A853AEED2B675DB23"> 
       <li id="li_394835C8731048A5BF7D9370AC12448C">Wenn keine Lizenz verfügbar ist oder die Lizenz abgelaufen ist, stellen Sie einen Workflow bereit, mit dem Benutzer eine neue Lizenz erwerben können, oder informieren Sie den Benutzer, dass der Inhalt nicht überwacht werden kann, und protokollieren Sie das Problem. </li> 
       <li id="li_3FE50518BE53405F9563FA620F7EAD5F">Wenn es sich um domänengebundenen Inhalt handelt (für AIR), bieten Sie eine Möglichkeit für den Benutzer, der Domäne beizutreten. </li> 
      </ul> </li> 
     <li id="li_C80B353C1AEA4E9398241420CB491E84">Der Händler sollte 
      <ul id="ul_B5C50009374C4EED9B2B050B48F5F0F6"> 
       <li id="li_D5E6B760E0BC4B5C949ED1544B398838">Vergewissern Sie sich, dass die Lizenzausgabebereiche des Access License Servers nicht angepasst wurden. </li> 
       <li id="li_AA8F4E4B6DDD40BA8807C0920A92186B">Stellen Sie sicher, dass sie eindeutige Lizenzkennungen für alle Lizenzen ausstellen. </li> 
       <li id="li_A2C53FE779AC4FDDB65E00A2C4F43EC4">Eskalieren Sie das Problem mit Adobe. </li> 
      </ul> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3309 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptedAdditionalHeader </span> </td> 
   <td colname="col3"> <p>Dies tritt auf, wenn die Kopfzeile größer als 65536 Byte ist. </p> 
    <ul id="ul_82C0F688519B4F43A764D59A891F1903"> 
     <li id="li_E66AC9149A0649E88A79C5289C12C395">Die Software des Distributors sollte protokollieren, welcher Inhalt den Fehler verursacht hat. </li> 
     <li id="li_1C5916A33E7B4DC9968105B9BD20A727">Der Distributor sollte bestätigen, dass der Fehler mit bestimmten Inhaltselementen reproduzierbar ist. Beschädigte Inhalte neu verpacken. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3310 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AppIDMismatch </span> </td> 
   <td colname="col3">Die Android-Anwendung entspricht nicht der verwendeten. <p>Die richtige AIR-Anwendung oder Flash-SWF wird nicht verwendet. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3311 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AppVersionMismatch </span> </td> 
   <td colname="col3"> Nicht in Verwendung. Dieses Problem kann weiterhin durch den Stack der Version 1.x in AIR verursacht werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3312 </td> 
   <td colname="col2"><span class="codeph"> AAXS_LicenseIntegrity </span> </td> 
   <td colname="col3"> Um dies zu beheben, laden Sie die Lizenz erneut vom Server herunter. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3313 </td> 
   <td colname="col2"><span class="codeph"> AAXS_WriteMicrosafeFailed </span> </td> 
   <td colname="col3"> <p>Dieses Problem tritt auf, wenn das System nicht in das Dateisystem schreiben kann. <span class="codeph"> subErrorId</span> enthält einen Client-spezifischen Fehler oder Zeilenfehler. </p> <p>Unter Microsoft Windows wird der Fehler 3313 möglicherweise vom Active X- oder NPAPI-Plug-Flash-Player ausgegeben, wenn der verschlüsselte Inhalt eine licenseID oder eine policyID aufweist, die zu lang ist. Dies liegt an der maximalen Pfadlänge in Windows. (Das Pepper-Plug-in hat dieses Problem nicht.) </p> <p>Siehe Aufgaben 3549660 </p> 
    <ul id="ul_DFD527D1E1224A439766DF7BED878E3B"> 
     <li id="li_FAF8FD98A4E8478CA7A92F770676ADFC">Die Software des Distributors sollte den Benutzer auffordern, zu bestätigen, dass sein Benutzerverzeichnis weder gesperrt noch auf einem vollen oder gesperrten Volume gespeichert ist. </li> 
     <li id="li_6D1136EA750A459BBECEEE5F73F527BB">Wenn der Distributor AIR anstelle von Flash verwendet, kann das Problem durch eine Pfadlängenbegrenzung verursacht werden. <p>Distributoren sollten den Namen ihrer AIR-Anwendung auf einen vernünftigen Wert kürzen. Veröffentlichen Sie auch Inhalte erneut mit einer kürzeren <span class="codeph"> licenseID</span> und <span class="codeph"> policyID</span>. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3314 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptedDRMMetadata </span> </td> 
   <td colname="col3"> <p>Dieser Fehler zeigt oft an, dass der Inhalt mit Test-PKI-Zertifikaten gepackt wurde und der Player mit Produktions-PKI erstellt wurde oder umgekehrt. subErrorId enthält einen clientspezifischen Fehler oder Zeilenfehler. </p> 
    <ul id="ul_A122EF304CAF48A8B4DA1E3F4413E29B"> 
     <li id="li_A9A1A5B23E884C22A71E2DE7535FEB3B">Die Software des Distributors sollte protokollieren, welcher Inhalt den Fehler verursacht hat. </li> 
     <li id="li_7AD7F13A4B1B4998A7E49664E7645815">Der Distributor sollte bestätigen, dass der Fehler mit bestimmten Inhaltselementen reproduzierbar ist. <p>Möglicherweise müssen Sie fehlerhafte Inhalte erneut verpacken. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3315 </td> 
   <td colname="col2"><span class="codeph"> AAXS_PermissionDenied </span> </td> 
   <td colname="col3"> <p>Es gibt bekannte Fehler, bei denen dieser Fehlercode ausgegeben wird, wenn ein 3305-Fehler vorgesehen ist. Weitere Informationen finden Sie unter <a href="https://forums.adobe.com/thread/1284947" format="https" scope="external"> DRM 3305 [ServerConnectionFailed]-Ursachen und -Auflösung</a>. </p> <p>Von AIR geladene Remote-SWF ist nicht berechtigt, auf die Funktionalität von Flash Accessen zuzugreifen. Dieser Fehlercode kann auch ausgegeben werden, wenn während des Netzwerkzugriffs ein Sicherheitsfehler auftritt. Beispiele sind, dass der Zielserver nicht den Client zur Verbindung über crossdomain.xml nutzt oder dass crossdomain.xml nicht erreichbar ist. </p> <p>Weitere Informationen finden Sie unter <a href="https://forums.adobe.com/thread/1266592" format="https" scope="external"> DRM-Fehler 3315 mögliche Ursache und Auflösung</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3316 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NOTUSED_MOVED </span> </td> 
   <td colname="col3"> was <span class="codeph"> ADOBECPSHIM_MinorErr_MissingAdobeCPModul</span>. Aufgrund eines Konflikts mit Flash-Fehlercode wurde auf 3344 verschoben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3317 </td> 
   <td colname="col2"><span class="codeph"> AAXS_LoadAdobeCPFailed </span> </td> 
   <td colname="col3"> <p>Wichtig: Dies ist ein seltener Fehler, der normalerweise nicht in einer Produktionsumgebung auftritt. </p> <p>Wenn der Fehler auftritt, können Sie einen der folgenden Schritte ausführen: 
     <ul id="ul_BC435E61623444BB98A86216531DC892"> 
      <li id="li_FA433D0758B642D2AFDCF04906B3FE18">Wenn Sie AIR verwenden, installieren Sie es neu. </li> 
      <li id="li_F08D9AAFF46244F8842DEE5FD9CBBE0A">Wenn Sie Flash Player verwenden, laden Sie die <span class="codeph"> AdobeCP</span> -Module erneut. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3318 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InkompatibleAdobeCPVersion </span> </td> 
   <td colname="col3"> Gilt nicht für Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3319 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MissingAdobeCPGetAPI </span> </td> 
   <td colname="col3"> Gilt nicht für Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3320 </td> 
   <td colname="col2"><span class="codeph"> AAXS_HostAuthenticateFailed </span> </td> 
   <td colname="col3"> Gilt nicht für Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3321 </td> 
   <td colname="col2"><span class="codeph"> AAXS_I15nFailed </span> </td> 
   <td colname="col3"> <p>Die Bereitstellung von Schlüsseln für den Client ist fehlgeschlagen. subErrorId enthält einen Client-spezifischen, Server-spezifischen oder Zeilenfehler. </p> 
    <ul id="ul_98D919B9060A441AACB6106F6D8E8DA7"> 
     <li id="li_DCAB00A8AC4A426CBBD377374B3F71AE">Die Software des Distributors sollte den Betrieb mindestens einmal wiederholen. <p>Wenn Sie Google Chrome unter Windows verwenden, erläutern Sie, wie Sie den Zugriff auf Plug-ins zulassen, die sich nicht in einer Sandbox befinden. Nicht-Sandbox-Zugriff von Google Chrome verweigert</a>. </p> </li> 
     <li id="li_7FB7681FE32D444BB1BDBA3E5953A2C3">Der Händler sollte eine der folgenden Aufgaben ausführen: 
      <ul id="ul_486B64F187C44AE3B4775953A6142836"> 
       <li id="li_095B1D4CD051427CB2BFA7082B454056">Wenn der Fehler plattformübergreifend konsistent ist, sollten Sie das Problem mit Adobe eskalieren. </li> 
       <li id="li_0C6EB7B912FA41E59657216498DA3515">Wenn der Fehler unter Windows auf Chrome beschränkt ist, weisen Sie den Benutzer an, den Zugriff auf das unsandbox-Plug-in zuzulassen. </li> 
      </ul> <p>Distributoren sollten ihre SWF auf Version 19 oder höher aktualisieren. Beim Chrome-spezifischen 3321-Fehler wird ein 3368-Fehler ausgegeben. Fehler 3368 kann genauer von der Software des Distributors verarbeitet werden. Diese Änderung wurde in der Chrome Stable Channel-Version 26.0.1410.43 eingeführt. </p> <p>Tipp: Fehler <span class="codeph"> 3321:1090519056</span> kann bei Flash Player-Versionen 11.1 bis 11.6 auftreten. Wir empfehlen ein Upgrade auf die neueste Flash Player-Version. </p> </li> 
    </ul> <p>Weitere Informationen finden Sie unter <a href="https://forums.adobe.com/thread/1277138" format="https" scope="external"> DRM-Fehler 3321 Ursachen und Lösung</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Fehler bei der Beschädigung im globalen Store</b> </td> 
   <td colname="col2"> </td> 
   <td colname="col3"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3322 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DeviceBindingFailed </span> </td> 
   <td colname="col3"> <p>Das Gerät scheint nicht mit der Konfiguration übereinzustimmen, die bei der Initialisierung vorhanden war. subErrorId enthält einen clientspezifischen Fehler oder einen Zeilenfehler. </p> <p>Die Software des Distributors sollte eine der folgenden Aufgaben ausführen: 
     <ul id="ul_444401051A2E407B95BC44491E9BB71C"> 
      <li id="li_93493EA05DB44CB1AEC368663F1ABA8D"> <p>Wenn das Gerät kein Flash Player verwendet und AIR, iOS usw. verwendet, rufen Sie <span class="codeph"> DRMManager.resetDRMVouchers()</span>. </p> <p>Wenn das Problem in einer Entwicklungsphase auf iOS auftritt, bitten Sie den Entwickler zu bestätigen, ob das Problem beim Wechsel zwischen Builds, die von Drittanbieter-Distributionssystemen (z. B. HockeyApp) heruntergeladen wurden, und einem lokalen Build aus Xcode behoben wird. Attribute einer vorherigen Installation werden beim Wechsel zwischen einem von HockeyApp verteilten Build und einem Build aus Xcode nicht vollständig überschrieben. Diese Situation könnte den Fehler 3322 Trigger haben. </p> <p>Um dieses Problem zu beheben, sollte der Entwickler den älteren Build vom Gerät entfernen, bevor er den neuen Build installiert. </p> </li> 
      <li id="li_A5C9633F11584C788A2D9A23CC18FA6D">Wenn das Gerät Flash Player verwendet und aus einem 3322- oder 3346-Fehlercode nicht verwendet werden kann, lesen Sie die Anweisungen von Adobe, wie Sie Ihren DRM-Lizenzspeicher programmgesteuert auf zurücksetzen <a href="https://forums.adobe.com/message/5535907#5535907" format="https" scope="external"> DRM-Fehler 3322/3346/3368 in Chrome (Info-Bar-Probleme)</a>. </li> 
     </ul> </p> <p>Es wird nicht erwartet, dass dieser Fehler häufig auftritt. In Unternehmensumgebungen, die Roamingprofile verwenden, steigt die Wahrscheinlichkeit, dass ein Benutzer Inhalte anzeigt, die durch DRM geschützt sind, dass der Fehler 3322 auftritt, wenn sich der Benutzer von verschiedenen Computern aus anmeldet. Wenn möglich, sollte der Distributor versuchen, diese Informationen vom Benutzer zu erhalten. </p> <p>Wenn der Fehler häufig auftritt, eskalieren Sie auf Adobe. Sie müssen Adobe darüber informieren, ob das Zurücksetzen des Lizenzspeichers das Problem gelöst hat (oder nicht), und Adobe mitteilen, auf welchen Browsern der Fehler auftritt. </p> <p>Weitere Informationen finden Sie in den folgenden Artikeln: 
     <ul id="ul_C468409D1EA046178CA7F54DCDCB84EA"> 
      <li id="li_20C8CA3853574CE486F21E7A3667DAB9"><a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> https://forums.adobe.com/message/5520902</a> </li> 
      <li id="li_6E6F1BD6FE7843449B3E2F06F342EFF7"><a href="https://forums.adobe.com/message/5535911" format="https" scope="external"> https://forums.adobe.com/message/5535911</a> </li> 
      <li id="li_2BE40E513A0C4BAD900C7B69FEF5D690"><a href="https://forums.adobe.com/message/5748618" format="https" scope="external"> https://forums.adobe.com/message/5748618</a> </li> 
      <li id="li_9C2BD122E3874E2893DD43E082A877E0"><a href="https://forums.adobe.com/message/6061165" format="https" scope="external"> https://forums.adobe.com/message/6061165</a> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3323 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptGlobalStateStore </span> </td> 
   <td colname="col3"> <p>Die vom DRM-Client verwendeten Dateien wurden unerwartet geändert. subErrorId enthält einen clientspezifischen Fehler oder einen Zeilenfehler. </p> 
    <ul id="ul_96EA771046CA4B2B9FAE24D493F43FF2"> 
     <li id="li_D2693CD8EFEF46108828BA17E3F54FF6">Die Software des Distributors sollte den Benutzer dazu bringen, auf dieselbe Weise zurückzusetzen wie für 3322. </li> 
     <li id="li_0149B82436B64E28AC2B8C9B0EB09898">Wenn der GlobalStore einen Fehler meldet, der größer ist als die erwartete Fehlerrate der Festplatten Ihrer Benutzerbasis, eskalieren Sie das Problem auf Adobe. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3324 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MachineTokenInvalid </span> </td> 
   <td colname="col3"> Setzen Sie den lokalen DRM-Speicher für diese Anwendung zurück. Rufen Sie DRMManager.resetDRM auf. <p>Der Lizenzserver kann möglicherweise keine Verbindung zum CRL-Server (Certificate Revocation List) herstellen, um seine Zertifikatsperrlisten-Dateien zu aktualisieren, oder der Clientcomputer fordert eine Lizenz/Authentifizierung an, die vom Lizenzserver widerrufen wurde. </p> <p>In den Serverprotokollen lautet der Fehlercode 111 MachineTokenInvalid. Auf Client-Ebene wird jedoch der Fehlercode 111 in den Fehlercode 3324 übersetzt. </p> <p>Der Administrator des DRM-Lizenzservers sollte prüfen, ob der Lizenzserver des Kunden die Adobe-CRL-Dateien jemals abrufen konnte. Wenn der Kunde Tomcat verwendet, kann der Kunde die<span class="filepath"> tomcat/temp/</span> -Verzeichnis, um zu sehen, ob es 4 CRL-Dateien gibt. </p> 
    <ul id="ul_23B7F1A104AF49E79EA87DB8E15E337E"> 
      <li id="li_855D87F251184FE688A8D5FA0F6C9EF5">Wenn sich die Dateien in diesem Ordner befinden, doppelklicken Sie in Windows Explorer auf die Dateien und in der CRL-Viewer-Anwendung, um zu ermitteln, ob eine der Dateien abgelaufen ist. </li> 
      <li id="li_58EC4EDA2B5146188A0FF7B33C91E2FD">Wenn keine Dateien in tomcat/temp/ vorhanden sind, kann davon ausgegangen werden, dass dieser Lizenzserver aufgrund eines Firewall-/Routing-Problems nie in der Lage war, den Adobe-Zertifikatsperrlisten-Server zu erreichen. Weitere Informationen finden Sie unter <a href="https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_secure_deployment_guidelines.pdf" format="http" scope="external"> Firewall-Regeln.</a></li>
    </ul> </p> <p>Wenn die Zertifikatsperrlisten-Dateien nicht verfügbar sind oder abgelaufen sind, müssen Sie überprüfen, ob der Lizenzserver erreicht werden kann. Öffnen Sie einen Netzwerk-Sniffer auf dem Lizenzserver des Kunden, starten Sie den Server neu und veranlassen Sie einen Clientversuch, eine Lizenz vom Server anzufordern. Sie können den Netzwerk-Traffic beobachten, um festzustellen, ob Aufrufe der folgenden URL-Endpunkte erfolgreich sind: <p>Tipp: Sie können auch die folgenden URLs in einen Browser eingeben, um zu sehen, ob Sie jede Datei manuell herunterladen können. </p> 
    <ul id="ul_9B65C7ABBDEC4AC9BF3755FFD3587971"> 
      <li id="li_6867A9050E8D421C9138AC853D1784C9"><a href="https://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl</a> </li> 
      <li id="li_6431689260554EAFAFDA2EC31798DCB5"><a href="https://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl</a> </li> 
      <li id="li_2939674D0F854ADEB67E45FD216288A2"><a href="https://crl2.adobe.com/Adobe/FlashAccessRootCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessRootCA.crl</a> </li> 
      <li id="li_96386E00BE9D4CB99D100057A5F7C6DD">crl3.adobe.com/AdobeSystemsIncorporated FlashAccessRuntime/LatestCRL.crl</li> 
    </ul> </p> <p>Wenn die Firewall-Regeln geöffnet sind und keine aktuellen 3324-Fehler vorliegen, ist möglicherweise ein temporäres Netzwerkproblem aufgetreten. Überprüfen Sie die Serverprotokolle des Kunden, die sich wahrscheinlich in der <span class="codeph"> /tomcat/logs/</span> -Verzeichnis, um zu ermitteln, ob ein Fehler aufgetreten ist, wenn der Lizenzserver versucht hat, die Zertifikatsperrlisten abzurufen. <p>Wichtig: Es kann zu einem Fehler kommen, wenn eine große Anzahl von Clients (oder ein Absturz) einen 3324-Fehler bei einem temporären Netzwerkproblem meldet, wenn eine Zertifikatsperrlisten-Datei erneuert wird. Als das Netzwerkproblem behoben wurde, wurden auch die 3324-Probleme behoben. </p> </p> <p>Wenn alle 4 CRL-Dateien im <span class="filepath"> tomcat/temp/</span> und Clients weiterhin 3324-Fehlercodes erhalten, kann es zu Problemen mit dem Dateizugriff auf die CRL-Dateien kommen. Um dieses Problem zu beheben, sollten Sie die Protokolle überprüfen und die vorhandenen Zertifikatsperrlisten-Dateien bereinigen. </p> <p>Wenn keine Serverprobleme vorliegen, fordern Sie den Benutzer auf, sich wie in 3322 beschrieben zurückzusetzen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Fehler bei der Beschädigung des Serverspeichers</b> </td> 
   <td colname="col2"> </td> 
   <td colname="col3"> </td> 
</tr> 
  <tr> 
   <td colname="col1"> 3325 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptServerStateStore </span> </td> 
   <td colname="col3"> <p>Die vom DRM-Client verwendeten Dateien wurden unerwartet geändert. <span class="codeph"> subErrorId</span> enthält einen Client-spezifischen Fehler oder Zeilenfehler. </p> 
    <ul id="ul_860D2402DA61460AB0D938F1116F6D64"> 
     <li id="li_CF368C43452B4265B62ADA3E223894BA">Die Software des Distributors sollte den Vorgang erneut versuchen, da AdobeCP den fehlerhaften Serverspeicher intern gelöscht hat und ein erneuter Versuch erfolgreich sein sollte. Wenn ein erneuter Versuch fehlschlägt, protokollieren Sie das Problem. </li> 
     <li id="li_51A5803A1F754970BB4EBD6494F5DC96">Wenn weitere Zustellversuche in einer Geschwindigkeit fehlschlagen, die größer ist als die erwartete Fehlerrate der Festplatten Ihrer Benutzerbasis, eskalieren Sie das Problem auf Adobe. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3326 </td> 
   <td colname="col2"><span class="codeph"> AAXS_StoreTamperingDetected </span> </td> 
   <td colname="col3"> Aufruf <span class="codeph"> DRMManager.resetDRM</span>. <p>Der Lizenzspeicher wurde verändert/beschädigt und kann nicht mehr verwendet werden. </p> <p>Die Software des Distributors sollte den Benutzer dazu bringen, auf die in 3322 beschriebene Weise zurückzusetzen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3327 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ClockTamperingDetected </span> </td> 
   <td colname="col3"> Korrigieren Sie die Uhr oder erwerben Sie sie. <span class="codeph"> Authoring/Lic/Domain</span> erneut zu lizenzieren. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Fehler bei Authentifizierung/Lizenz/Domain-Server</b> </td> 
   <td colname="col2"> </td> 
   <td colname="col3"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3328 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerErrortryAwiederum </span> </td> 
   <td colname="col3"> <p>Dies ist ein Server-seitiger Fehler, bei dem der Server die Anfrage vom Client nicht ausführen konnte. Dieser Fehler kann auftreten, wenn beispielsweise der Server ausgelastet ist, HTTP/500, der Server nicht über den erforderlichen Schlüssel zum Entschlüsseln der Anforderung verfügt usw. </p> <p>Auf dem Client gibt es keine Möglichkeit zu bestimmen, was schiefgelaufen ist. Der Kunde muss die Adobe Access Server-Protokolle überprüfen, die normalerweise als <span class="codeph"> AdobeFlashAccess.log</span>, um festzustellen, was schiefgelaufen ist. Es gibt immer einen beschreibenden Stacktrace im Protokoll, um das Problem anzuzeigen. <span class="codeph"> subErrorId</span> enthält einen Server-spezifischen oder Zeilenfehler. </p> <p>Der Distributor sollte sich die Serverprotokolle ansehen, um zu ermitteln, welcher Server diesen Fehler sendet. Bei 3328-Fehlern mit dem Unterfehlercode 101 kann der Server die Anforderung nicht entschlüsseln. Der Kunde muss überprüfen, ob die auf dem Lizenzserver installierten Lizenz-/Transportserverzertifikate mit den während der Verpackung verwendeten Zertifikaten übereinstimmen und damit übereinstimmen. </p> <p>Wenn Kunden außerdem die Referenzimplementierung verwenden, müssen sie sicherstellen, dass in der Variablen <span class="codeph"> flashaccess-refimpl.properties</span> -Datei, in der die primären und zusätzlichen Zertifikate angegeben sind. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3329 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ApplicationSpecificError </span> </td> 
   <td colname="col3"> <p>Der anwendungsspezifische Unterfehlercode ist für Flash Access nicht bekannt. <span class="codeph"> subErrorId</span> enthält einen Server-spezifischen Fehler vom benutzerdefinierten Lizenzserver des Herausgebers. Der Server gab einen Fehler im anwendungsspezifischen Namespace zurück. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3330 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NeedAuthentication </span> </td> 
   <td colname="col3"> <p>Dieser Fehler tritt auf, wenn der Inhalt so konfiguriert ist, dass Clients vor dem Erhalt der Lizenzen aufgefordert werden, sich zu authentifizieren. </p> 
    <ul id="ul_712D29B8B5A6401FB014C4A283918E32"> 
     <li id="li_2D56905EB50D4FDEAD69CA8EAE38AD1A">Die Software des Distributors sollte den Benutzer authentifizieren und dann die Lizenz erneut erwerben. <p>Wenn Ihr Dienst keine Authentifizierung verwenden möchte, protokollieren Sie die Identifizierung des Inhalts, der diesen Fehler verursacht. </p> </li> 
     <li id="li_B3BCF899B8BE41C7A4F7CF84B0503483">Dieser Fehler sollte keine Eskalation erfordern, es sei denn, der Inhalt sollte nicht so konfiguriert sein, dass eine Authentifizierung erforderlich ist. <p>Komprimieren Sie in diesem Fall den fehlerhaften Inhalt mit einer korrekten Richtlinie. Wenn der Inhalt richtig verpackt ist, lesen Sie den Abschnitt Richtlinie/Lizenzdiskrepanzen diagnostizieren . </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Fehler bei der Lizenzdurchsetzung, die oben nicht behandelt werden</b> </td> 
   <td colname="col2"> </td> 
   <td colname="col3"> </td> 
</tr> 
  <tr> 
   <td colname="col1"> 3331 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentNotStillValid </span> </td> 
   <td colname="col3"> <p>Die erworbene Lizenz ist noch nicht gültig. Um dieses Problem zu beheben, überprüfen Sie, ob die Client-Uhr nicht richtig eingestellt ist. Um die Client-Uhr festzulegen, verpacken Sie den Inhalt neu oder ändern Sie die Konfiguration des Lizenzservers. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3332 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CachedLicenseExpired </span> </td> 
   <td colname="col3"> Erneutes Lizenzieren vom Server. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3333 </td> 
   <td colname="col2"><span class="codeph"> AAXS_PlaybackWindowExpired </span> </td> 
   <td colname="col3"> <p>Sie müssen Benutzer darüber informieren, dass sie diesen Inhalt erst abspielen können, wenn die Richtlinie abläuft. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3334 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidDRMPlatform </span> </td> 
   <td colname="col3"> <p>Diese Plattform ist nicht berechtigt, den Inhalt wiederzugeben, da der Inhaltsanbieter beispielsweise Adobe Access so konfiguriert hat, dass er den Adobe-Zugriff auf Inhalte auf einer Plattform verweigert, oder eine freigegebene Domain-gebundene Lizenz an ein freigegebenes Domain-Token gebunden ist, das für eine andere Partition bestimmt ist. </p> <p>Der CDM kann diesen Fehler auslösen, wenn Inhalt nicht mithilfe einer entsprechenden (CDM Feature Gated) Packager-Zertifizierung gepackt wurde. </p> <p>Wenn der Inhalt mit einem falschen PHDS-/PHLS-Zertifikat gepackt ist, funktioniert der Inhalt möglicherweise in Chrome, nicht aber in anderen Browsern (oder umgekehrt). <p>Tipp: Dies liegt daran, dass Chrome verschiedene PHDS/PHLS-Zertifikate verwendet. </p>Um zu bestätigen, welches Zertifikat verwendet wird, speichern Sie die Details der Inhaltsmetadaten und suchen Sie nach der <i>Empfängerzertifikate</i>. Weitere Informationen finden Sie unter <a href="https://adobeprimetime.zendesk.com/agent/tickets/2891" format="https" scope="external"> https://adobeprimetime.zendesk.com/agent/tickets/2891</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3335 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidDRMVersion </span> </td> 
   <td colname="col3"> Aktualisieren Sie auf die neueste Version des TVSDK für Android. <p>Führen Sie zur Behebung dieses Problems eine der folgenden Aufgaben aus: 
     <ul id="ul_BF1742948BC9461CB8686DE70124D3CD"> 
      <li id="li_690D440C94CC45A0AE55EC319B1C4C23">AIR aktualisieren </li> 
      <li id="li_CDD20251C881466E88BE7BBB53D61EBC">Aktualisieren Sie zum Flash Player das AdobeCP-Modul und versuchen Sie es erneut. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3336 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidRuntimePlatform </span> </td> 
   <td colname="col3"> <p>Diese Plattform ist nicht berechtigt, den Inhalt wiederzugeben, da der Inhaltsanbieter beispielsweise den Zugriff so konfiguriert hat, dass FP/AIR auf einer Plattform Inhalte verweigert werden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3337 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidRuntimeVersion </span> </td> 
   <td colname="col3"> Aktualisieren Sie auf die neueste Version von TVSDK für Android. <p>Dies tritt auf, wenn der Inhalt oder der Server so konfiguriert ist, dass die Wiedergabe für eine bestimmte Version der Flash- oder AIR-Laufzeitumgebungen verweigert wird. </p> 
    <ul id="ul_B0732D941256483CABBDD30C9BF43249"> 
     <li id="li_72782B1D638F48C0B87084689FB9C798">Wenn sich der Benutzer auf einem Betriebssystem befindet, auf dem Flash aktualisiert werden kann, sollte die Software des Distributors den Benutzer auffordern, Flash zu aktualisieren und es erneut zu versuchen. Ansonsten empfehlen Sie dem Benutzer, einen anderen Computer zu verwenden. </li> 
     <li id="li_1E3FD93CE39E43F2B7D961299B1211DA">Wenn der Fehler 3337s vermutet wird, ermitteln Sie, ob er für bestimmte Inhalte auftritt, und verpacken Sie diesen Inhalt neu. Informationen zum korrekten Packen von Inhalten finden Sie unter Diskrepanzen bei der Diagnoserichtlinie/Lizenz . </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3338 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UnknownConnectionType </span> </td> 
   <td colname="col3"> <p>Der Verbindungstyp kann nicht erkannt werden. Die Richtlinie erfordert, dass Sie den Output Protection aktivieren. Dieses Problem wird nur erwartet, wenn der Inhalt so verpackt ist, dass er einen digitalen oder analogen Ausgabeschutz erfordert. </p> <p>Ein Problem in Versionen von Flash Player, die älter als Version 11.8.800.168 sind, führte gelegentlich zu Fehler 3338 bei Inhalten, für die die Richtlinie anzeigte, dass der Inhaltsschutz <span class="codeph"> VERWENDEN, WENN VERFÜGBAR</span>. Dieses Problem wurde in Version 11.8.800.168 und höher behoben. </p> 
    <ul id="ul_4B6CA26A53F84838B5B95400925464D4"> 
     <li id="li_CBD890F467E449EBB5116E1561252058">Die Software des Distributors wählt eine Variante des Inhalts aus, die keinen Ausgabeschutz erfordert (z. B. SD-Variante eines HD-Streams). <p>Wenn der Fehler 3338 auf <span class="codeph"> USE_IF_AVAILABLE </span> Inhalt, suchen Sie nach der Player-Versionsnummer. Wenn die Player-Version kleiner als 11.8.800.168 ist, empfehlen Sie dem Benutzer, das Flash Player zu aktualisieren. Wenn bei Versionen über 11.8.800.168 der Fehler 3338 auftritt, protokollieren Sie, welcher Inhalt den Fehler verursacht hat. </p> </li> 
     <li id="li_62886C1D96264B129928A7E29E6C70E1">Der Distributor sollte überprüfen, welcher Inhalt diesen Fehler verursacht, und überprüfen, ob die Richtlinie des Inhalts <span class="codeph"> NO_PROTECTION</span> oder <span class="codeph"> USE_IF_AVAILABLE</span> für analoge und digitale Ausgaben. <p>Wenn Inhalt versehentlich mit <span class="codeph"> NO_OUTPUT</span> oder <span class="codeph"> ERFORDERLICH</span>, verpacken Sie den Inhalt neu. Wenn der Inhalt richtig verpackt ist, lesen Sie die Informationen zu Diagnoserichtlinien/Lizenzdiskrepanzen. Eskalieren Sie andernfalls auf Adobe. </p> </li> 
    </ul> <p>Weitere Informationen finden Sie unter <a href="https://forums.adobe.com/message/5518688" format="https" scope="external"> Unerwartete 3338-Fehler erhalten, wenn Ihre DRM-Richtlinie auf USE_IF_AVAILABLE gesetzt ist?</a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3339 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoAnalogPlaybackAllowed </span> </td> 
   <td colname="col3"> Wiedergabe auf einem analogen Gerät nicht möglich. Um das Problem zu beheben, verbinden Sie ein digitales Gerät. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3340 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoAnalogProtectionAvail </span> </td> 
   <td colname="col3"> Inhalt kann nicht wiedergegeben werden, da das angeschlossene externe Anzeigegerät (Monitor/TV) nicht über die richtigen Funktionen verfügt (z. B. hat das Gerät keine Macrovision oder AKP). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3341 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDigitalPlaybackAllowed </span> </td> 
   <td colname="col3"> Inhalt kann auf einem digitalen Gerät nicht wiedergegeben werden. <p>Wichtig: Dieses Problem sollte nicht in einer Produktionsumgebung auftreten, da Herausgeber von Inhalten die digitale Wiedergabe nicht deaktivieren sollten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3342 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDigitalProtectionAvail </span> </td> 
   <td colname="col3"> Das angeschlossene externe Anzeigegerät (Monitor/TV) verfügt nicht über die richtigen Funktionen. Beispielsweise verfügt das Gerät nicht über HDCP. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3343 </td> 
   <td colname="col2"><span class="codeph"> AAXS_IntegrityVerificationFailed </span> </td> 
   <td colname="col3"> <p>Gilt nicht für Android. </p> <p>Dieser Fehler tritt derzeit erst nach der Veröffentlichung einer neuen Version von Flash auf. Dies geschieht, weil Flash aktualisiert wurde, während Flash geöffnet war, was die Flash in einen schlechten Zustand versetzt, bis der Browser neu gestartet wird. </p> 
    <ul id="ul_A0AC4A77550E40409A04BD33748EA987"> 
     <li id="li_F41C1ABD838D41ABB0DF65093E664A29">Die Software des Distributors sollte die folgenden Aufgaben ausführen: 
      <ul id="ul_79B2AB1372074D448F129851AA24F985"> 
       <li id="li_B93EDD263D78434FAF198A01938D3508">Es wird empfohlen, dass der Benutzer alle Browser schließt oder beendet und dann erneut geöffnet wird. </li> 
       <li id="li_ADFBCFA66AD849E18DB390455458528E">Überprüfen Sie, ob die Flash-Version aktuell ist. <p>Wenn die Version nicht aktuell ist, empfehlen Sie dem Kunden, ein Upgrade durchzuführen, alle Registerkarten in seinem Browser zu schließen und erneut zu öffnen. </p> </li> 
      </ul> </li> 
     <li id="li_281B54582B5949AEA7D166246917EE41">Wenn nach einem erfolgreichen Neustart des Browsers ein Fehler auftritt, eskalieren Sie zu Adobe. <p>Wenn eine neue Version veröffentlicht wird, empfehlen wir Ihnen, sich an den Adobe-Support zu wenden, um zu sehen, ob das Problem mit Hintergrundaktualisierungen behoben wurde. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3344 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MissingAdobeCPModul </span> </td> 
   <td colname="col3"> Gilt nicht für Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3345 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DRMNoAccessError </span> </td> 
   <td colname="col3"> <p>Gilt nicht für Android. </p> <p>Dieser Fehler tritt auf, wenn Flash oder AIR nicht ordnungsgemäß installiert wurde. </p> <p>Die Software des Distributors sollte einen der folgenden Schritte ausführen: 
     <ul id="ul_D1188E2D4FDF4BD89A04F5629D75D981"> 
      <li id="li_B33FBCA5D4534D668B86A5E93DB3A809">Bitten Sie den Benutzer, AIR zu deinstallieren und neu zu installieren. </li> 
      <li id="li_B7D2388E9FA84C26AF1C87B48AF9EF16">Für Flash Player rufen Sie <span class="codeph"> System.update</span>. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3346 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MigrationFailed </span> </td> 
   <td colname="col3"> 
    <ul id="ul_518AD4931CC64EB3A962DD451E6C5067"> 
     <li id="li_3C44F0740B08490E9C62D89C40B57DC2">Die Software des Distributors sollte einen der folgenden Schritte ausführen: 
      <ul id="ul_7D90526684BF4EB2BBADCF598AA13086"> 
       <li id="li_D15B4BEDAF7340F6B9BC886DF6E346EC">Wenn AIR, rufen Sie <span class="codeph"> DRMManager.resetDRMVouchers()</span> </li> 
       <li id="li_40A51D35408249CFA28DBC49FDA3408B">Wenn Flash aufgrund des Fehlercodes 3322 oder 3346 unbrauchbar ist, sollten Benutzer zu <a href="https://forums.adobe.com/message/5535907#5535907" format="http" scope="external"> https://forums.adobe.com/message/5535907#5535907</a> und befolgen Sie die Anweisungen des Adobe-Artikels, um ihren DRM-Lizenzspeicher programmgesteuert zurückzusetzen. </li> 
      </ul> </li> 
     <li id="li_0464471E4A094C80BF2986694341921A">Tritt dieser Fehler häufig auf, sollte der Distributor die Details zur Frequenzplayer-Version und zur Browserversion zum Adobe angeben. </li> 
    </ul> <p>Weitere Informationen finden Sie in den folgenden Forumsartikeln: 
     <ul id="ul_44E0077FEAA749CC9549BF3846065304"> 
      <li id="li_2BE3B2443380415DA73B7AA3B6547B31"><a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> DRM-Fehler 3322/3346/3368 in Chrome (Info-Bar-Probleme)</a> </li> 
      <li id="li_4E5C7414756644E1AB78BE7B8112228C"><a href="https://forums.adobe.com/message/5535911" format="https" scope="external"> 3322- oder 3346-Fehler nach Hardwareänderung</a> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3347 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InhinreichendDeviceCapabilites </span> </td> 
   <td colname="col3"> <p>Die primäre Bedeutung dieses Fehlers besteht darin, dass die Lizenz eine Einschränkung aufweist, die das DRM-Zertifikat des Clients angibt, dass sie nicht erfüllt werden kann. Die folgenden "Hardwarefunktionen"werden definiert, wenn das DRM-Zertifikat der Clients ausgegeben wird: 
     <ul id="ul_1EB6F1469C244CF0BA52C212495C053D"> 
      <li id="li_646043CE045C4DE2BBC939E1F4963DFE"><b>Nicht für Benutzer zugänglicher Bus</b>. Wenn <b>true</b>, fließen die entschlüsselten Medien nie über einen Bus oder in den Hauptspeicher, auf den eine Anwendung zugreifen kann. <p>Wenn <b>false</b>, können Inhalte für die Anwendung nach der Entschlüsselung verfügbar sein. </p> </li> 
      <li id="li_02AAECAF4D35447BA10554541B46DE67"><b>Hardware-Stamm des Vertrauens</b>. Wenn <b>true</b>, wurde die gesamte Software, die beim Booten auf dem Gerät geladen wird, anhand eines Schlüssels oder Digest validiert, der nur in der Hardware verfügbar ist. <p>Beide Einschränkungen werden Client-seitig überprüft, wenn die Lizenz für das DRM-Zertifikat für den Client geöffnet wird und der Fehler sofort auftritt. Diese Einschränkungen können vor der Lizenzerteilung auch serverseitig überprüft werden. </p> </li> 
     </ul> </p> <p>Die sekundäre Bedeutung dieses Fehlers besteht darin, dass für die Lizenz die Richtlinie "Jailbreak Enforcement"festgelegt wurde und auf dem Gerät eine Jailbreak-Funktion erkannt wurde. Diese Prüfung erfolgt regelmäßig clientseitig und kann nicht serverseitig überprüft werden. </p> <p>Die Distributoren können die Richtlinien aktualisieren und die Einschränkungen entfernen. Stellen Sie für Gerätefunktionsrichtlinien den Befehl zur Richtlinienaktualisierung mit dem <span class="codeph"> -devCapabilitiesV1</span> -Markierung und keine Argumente. Zur Durchsetzung von Inhaftierungen <span class="codeph"> policy.forcedJailbreak=false</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3348 </td> 
   <td colname="col2"><span class="codeph"> AAXS_HardStopIntervalExpired </span> </td> 
   <td colname="col3"> Das Hardbounce-Intervall ist abgelaufen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3349 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerVersionTooHigh </span> </td> 
   <td colname="col3"> Der Server wird mit einer Version ausgeführt, die höher ist als die höchste vom Client unterstützte Version. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3350 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerVersionTooLow </span> </td> 
   <td colname="col3"> Der Server wird mit einer Version ausgeführt, die unter der vom Client unterstützten Mindestversion liegt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3351 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenInvalid </span> </td> 
   <td colname="col3"> Domain-Token war ungültig. Um dieses Problem zu beheben, registrieren Sie sich erneut bei der Domäne . </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3352 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenTooOld </span> </td> 
   <td colname="col3"> Das Domänen-Token ist älter als das Token, das für die Lizenz erforderlich ist. Um das Problem zu beheben, registrieren Sie sich erneut bei der Domäne . </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3353 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenTooNew </span> </td> 
   <td colname="col3"> Das Domänen-Token ist neuer als das Token, das für die Lizenz erforderlich ist. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3354 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenExpired </span> </td> 
   <td colname="col3"> Das Domänen-Token ist abgelaufen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3355 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainJoinFailed </span> </td> 
   <td colname="col3"> Domänenbeitritt fehlgeschlagen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3356 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoCorrespondenceRoot </span> </td> 
   <td colname="col3"> Eine Root-Lizenz für eine V3-Laublizenz wurde nicht gefunden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3357 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoValidEmbeddedLicense </span> </td> 
   <td colname="col3"> Es wurde keine gültige eingebettete Lizenz gefunden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3358 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoACPProtectionAvail </span> </td> 
   <td colname="col3"> Wiedergabe nicht möglich, da das angeschlossene analoge Gerät keinen AKP-Schutz aufweist. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3359 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoCGMSAProtectionAvail </span> </td> 
   <td colname="col3"> Wiedergabe nicht möglich, da angeschlossene analoge Geräte keinen CGMS-A-Schutz haben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3360 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainRegistrationRequired </span> </td> 
   <td colname="col3"> Inhalt erfordert eine Domänenregistrierung. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3361 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NotRegisteredToDomain </span> </td> 
   <td colname="col3"> Der Computer ist nicht für die angegebenen Metadaten in der Domäne registriert. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3362 </td> 
   <td colname="col2"><span class="codeph"> AAXS_OperationTimeoutError </span> </td> 
   <td colname="col3"> Der asynchrone Vorgang dauerte länger als <span class="codeph"> maxOperationTimeout</span>. Nur von iOS DRMNative Framework zurückgegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3363 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UnsupportedIOSPlaylistError </span> </td> 
   <td colname="col3"> Die übergebene M3U8-Wiedergabeliste enthielt nicht unterstützte Inhalte. Nur von iOS DRMNative Framework zurückgegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3364 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDeviceId </span> </td> 
   <td colname="col3"> <p>Das Framework hat die Geräte-ID angefordert, aber der zurückgegebene Wert war leer. </p> <p>Der Benutzer sollte die <span class="uicontrol"> Kennungen für geschützten Inhalt zulassen</span> in den Chrome-Einstellungen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3365 </td> 
   <td colname="col2"><span class="codeph"> AAXS_IncognitoModeNotAllowed </span> </td> 
   <td colname="col3"> <p>Diese Kombination aus Browser und Plattform ermöglicht keine DRM-geschützte Wiedergabe im Inkognito-Modus. </p> <p>Die Software des Distributors sollte den Benutzer anweisen, den Inkognito-Modus zu beenden oder einen anderen Browser zu verwenden. Weitere Informationen finden Sie unter <a href="https://forums.adobe.com/thread/1266622" format="https" scope="external"> DRM-Fehler 3365 Ursache und Auflösung</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3366 </td> 
   <td colname="col2"><span class="codeph"> AAXS_BadParameter </span> </td> 
   <td colname="col3"> <p>Die Host-Laufzeitumgebung rief die Zugriffsbibliothek mit einem ungültigen Parameter auf. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3367 </td> 
   <td colname="col2"><span class="codeph"> AAXS_BadSignature </span> </td> 
   <td colname="col3"> Die Manifestsignatur m3u8 ist fehlgeschlagen. Nur von iOS DRMNative Framework oder AVE zurückgegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3368 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UserSettingsNoAccess</span> </td> 
   <td colname="col3"> <p>Der Benutzer hat den Vorgang abgebrochen oder Einstellungen eingegeben, die den Zugriff auf das System untersagen. </p> <p>Dieser Fehler wird nur ausgegeben, wenn die SWF-Version 19 oder höher ist. Aus Gründen der Abwärtskompatibilität wird 3321 ausgegeben, wenn die SWF Version 18 oder früher ist. </p> <p>Die Software des Distributors sollte den Benutzer zu einer Erläuterung führen, wie der Zugriff auf nicht-sandbox-Plug-ins zugelassen werden kann. Nicht-Sandbox-Zugriff von Google Chrome verweigert</a> und <a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> DRM-Fehler 3322/3346/3368 in Chrome (Info-Bar-Probleme)</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3369 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InterfaceNotAvailable</span> </td> 
   <td colname="col3"> <p>Eine erforderliche Browser-Oberfläche ist nicht verfügbar. Dieses Problem tritt nur bei Pepper auf. Zwischen dem Flash-Plug-in und der Browserversion kann es zu Abweichungen kommen. </p> <p>Die Software des Verteilers sollte den Benutzer anweisen, sicherzustellen, dass die neueste Version des Browsers installiert ist. </p> <p> Wenn die Häufigkeit dieses Fehlers zunimmt und einer Browseraktualisierung entspricht, eskalieren Sie auf Adobe. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3370 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentIdSettingsNoAccess</span> </td> 
   <td colname="col3"> <p>Der Benutzer hat die <span class="uicontrol"> Kennungen für geschützten Inhalt zulassen</span> -Einstellung. </p> <p>Tipp: Dieser Fehler trat bei den Pepper-Versionen 13.0.0.x oder höher auf. </p> <p>Die Software des Distributors sollte den Benutzer anleiten, die <span class="uicontrol"> Kennungen für geschützten Inhalt zulassen</span> -Einstellung. </p> <p>Das Betriebsteam des Distributors sollte den Benutzer anleiten, die <span class="uicontrol"> Kennungen für geschützten Inhalt zulassen</span> -Einstellung. </p> <p>Weitere Informationen finden Sie unter <a href="https://forums.adobe.com/message/6518323#6518323" format="https" scope="external"> https://forums.adobe.com/message/6518323#6518323</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3371 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoOPConstraintInPixel</span><span class="codeph"> Einschränkungen</span> </td> 
   <td colname="col3"> <p>Fehlerhafte Auflösung basierend auf Ausgabeschutzbegrenzungen in der Lizenz. </p> <p>Die Software des Distributors sollte eine Fehlermeldung anzeigen. Bitten Sie den Benutzer, das Problem dem Distributor mit einem Inhaltstitel zu melden. </p> <p>Der Distributor sollte Inhalte mit einer gültigen Richtlinie neu verpacken. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3372 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ResolutionLargerThanMaxResolution</span> </td> 
   <td colname="col3"> <p>Die Auflösung des Inhalts ist größer als die in der Ausgabeschutzbegrenzung angegebene maximale Auflösung. </p> <p>Wenn das Betriebsteam des Distributors diesen Fehler in seinen Protokollen sieht, sollte es die auflösungsbasierte Ausgabeschutzrichtlinie überprüfen und den Inhalt ggf. neu verpacken. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3373 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MinorErr_DisplayResolutionLargerThanConfirm</span> </td> 
   <td colname="col3"> <p>Die Auflösung des Inhalts ist größer als die Auflösung, die durch die derzeit aktive Ausgabeschränkung angegeben wird. </p> <p>Wenn das Betriebsteam des Distributors diesen Fehler in seinen Protokollen sieht, sollte es die auflösungsbasierte Ausgabeschutzrichtlinie überprüfen und den Inhalt ggf. neu verpacken. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3374 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MinorErr_ClientCommProcessFailed</span> </td> 
   <td colname="col3"> <p>Fehlgeschlagen bei der clientseitigen Kommunikationsverarbeitung, z. B. Anforderungsgenerierung, Antwortverarbeitung, ungültiges Authentifizierungstoken usw. </p> <p>Wenn das Betriebsteam des Distributors diesen Fehler in seinen Protokollen sieht, sollte es die auflösungsbasierte Ausgabeschutzrichtlinie überprüfen und bei Bedarf Inhalte neu verpacken. </p> </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR: Werte für die Videowiedergabe {#section_7079501250C2487499639F92EC774525}

Die Video Encoder-Oberfläche von AVE gibt diese Benachrichtigungen zur Videowiedergabe im `NATIVE_ERROR` Metadatenobjekt.

<table id="table_5EEB1F60E5854452A8B0BABBE9B32651"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>Wert für den Metadatenschlüssel NATIVE_ERROR_CODE</b></th> 
   <th colname="col2" class="entry"><b>Wert für den Metadatenschlüssel NATIVE_ERROR_NAME</b></th> 
   <th colname="col3" class="entry"><b>Beschreibung</b></th> 
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
   <td colname="col3"> Asynchroner Vorgang. Die Vorgangsanfrage wurde durchgeführt. Erfolgs-/Fehlerinformationen sind später verfügbar. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 2 </td> 
   <td colname="col2"><span class="codeph"> EOF</span> </td> 
   <td colname="col3"> Vorgang aufgrund der Dateiende-Bedingung (EOF) nicht möglich. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3 </td> 
   <td colname="col2"><span class="codeph"> DECODER_FAILED</span> </td> 
   <td colname="col3"> Der Decoder schlug zur Laufzeit fehl. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 4 </td> 
   <td colname="col2"><span class="codeph"> DEVICE_OPEN_ERROR</span> </td> 
   <td colname="col3"> Hardware-Decoder konnte nicht geöffnet werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 5 </td> 
   <td colname="col2"><span class="codeph"> FILE_NOT_FOUND </span> </td> 
   <td colname="col3"> Die Ressource kann nicht gefunden werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 6 </td> 
   <td colname="col2"><span class="codeph"> GENERIC_ERROR </span> </td> 
   <td colname="col3"> Allgemeiner Fehler. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 7 </td> 
   <td colname="col2"><span class="codeph"> IRRECOVERABLE_ERROR </span> </td> 
   <td colname="col3"> Eine Fehlerbedingung, von der die Video-Engine keine Wiederherstellung durchführen kann. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 8 </td> 
   <td colname="col2"><span class="codeph"> LOST_CONNECTION_RECOVERABLE </span> </td> 
   <td colname="col3"> Netzwerkfehler, der versucht, den Fehler wiederherzustellen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 9 </td> 
   <td colname="col2"><span class="codeph"> NO_FIXED_SIZE </span> </td> 
   <td colname="col3"> Die Größe der Ressource kann nicht bestimmt werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 10 </td> 
   <td colname="col2"><span class="codeph"> NOT_IMPLEMENTED </span> </td> 
   <td colname="col3"> Funktion nicht implementiert </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 11 </td> 
   <td colname="col2"><span class="codeph"> OUT_OF_MEMORY </span> </td> 
   <td colname="col3"> Nicht genügend Arbeitsspeicher. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 12 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR </span> </td> 
   <td colname="col3"> Fehler beim Parsen der Mediendatei. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 13 </td> 
   <td colname="col2"><span class="codeph"> SIZE_UNKNOWN </span> </td> 
   <td colname="col3"> Die Ressource hat eine Größe, aber sie ist unbekannt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 14 </td> 
   <td colname="col2"><span class="codeph"> UNDER_FLOW </span> </td> 
   <td colname="col3"> Flussbedingung. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 15 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_CONFIG </span> </td> 
   <td colname="col3"> Konfiguration wird nicht unterstützt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 16 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_OPERATION </span> </td> 
   <td colname="col3"> Der Vorgang wird nicht unterstützt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 17 </td> 
   <td colname="col2"><span class="codeph"> WAITING_FOR_INIT </span> </td> 
   <td colname="col3"> Noch nicht initialisiert. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 18 </td> 
   <td colname="col2"><span class="codeph"> INVALID_PARAMETER </span> </td> 
   <td colname="col3"> Ungültiger Parameter. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 19 </td> 
   <td colname="col2"><span class="codeph"> INVALID_OPERATION</span> </td> 
   <td colname="col3"> Vorgang nicht erlaubt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 20 </td> 
   <td colname="col2"><span class="codeph"> OP_ONLY_ALLOWED_IN_PAUSED_STATE</span> </td> 
   <td colname="col3"> Der Vorgang ist nur während der Pause zulässig. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 21 </td> 
   <td colname="col2"><span class="codeph"> OP_INVALID_WITH_AUDIO_ONLY_FILE</span> </td> 
   <td colname="col3"> Der Vorgang kann nicht für Audiodateien verwendet werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 22 </td> 
   <td colname="col2"><span class="codeph"> PREVIOUS_STEP_SEEK_IN_PROGRESS</span> </td> 
   <td colname="col3"> Der vorherige Suchvorgang wird noch ausgeführt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 23 </td> 
   <td colname="col2"><span class="codeph"> SOURCE_NOT_SPECIFIED </span> </td> 
   <td colname="col3"> Ressource nicht angegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 24 </td> 
   <td colname="col2"><span class="codeph"> RANGE_ERROR</span> </td> 
   <td colname="col3"> Der angegebene Wert liegt außerhalb des Bereichs. </td> 
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
   <td colname="col2"><span class="codeph"> CONTAINER_NOT_SUPPORTED </span> </td> 
   <td colname="col3"> Container-Typ wird nicht unterstützt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 30 </td> 
   <td colname="col2"><span class="codeph"> SEEK_FAILED</span> </td> 
   <td colname="col3"> Die Suche ist fehlgeschlagen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 31 </td> 
   <td colname="col2"><span class="codeph"> CODEC_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> Nicht unterstützter Codec. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 32 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_UNAVAILABLE</span> </td> 
   <td colname="col3"> Das Netzwerk ist nicht verfügbar. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 33 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_ERROR</span> </td> 
   <td colname="col3"> Fehler beim Abrufen von Daten aus dem Netzwerk. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 34 </td> 
   <td colname="col2"><span class="codeph"> ÜBERFLUSS</span> </td> 
   <td colname="col3"> Überlauf. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 35 </td> 
   <td colname="col2"><span class="codeph"> VIDEO_PROFILE_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> Nicht unterstütztes Videoprofil. </td> 
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
   <td colname="col3"> API kann nicht aus dem falschen Thread aufgerufen werden. Meistens für API-Elemente, die nur aus dem Haupt-Thread aufgerufen werden sollten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 39 </td> 
   <td colname="col2"><span class="codeph"> FRAGMENT_READ_ERROR</span> </td> 
   <td colname="col3"> Fehler beim Lesen von Fragmenten. Kein Failover vorhanden. Die Engine versucht, das nächste Fragment zu lesen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 40 </td> 
   <td colname="col2"><span class="codeph"> ABORTED</span> </td> 
   <td colname="col3"> Der Vorgang wurde durch einen expliziten Abort - oder Zerstörungsaufruf abgebrochen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 41 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_HLS_VERSION</span> </td> 
   <td colname="col3"> Diese Version von HLS-Medien kann nicht wiedergegeben werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 42 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_FAIL_OVER</span> </td> 
   <td colname="col3"> Kann nicht durchfallen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 43 </td> 
   <td colname="col2"><span class="codeph"> HTTP_TIME_OUT</span> </td> 
   <td colname="col3"> HTTP-Download ist abgelaufen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 44 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_DOWN </span> </td> 
   <td colname="col3"> Die Netzwerkverbindung des Benutzers ist ausgeschaltet. Die Wiedergabe kann jeden Moment unterbrochen werden und wird fortgesetzt, sobald die Verbindung verfügbar ist. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 45 </td> 
   <td colname="col2"><span class="codeph"> NO_USABLE_BITRATE_PROFILE</span> </td> 
   <td colname="col3"> Es wurde kein nutzbares Bitratenprofil im Stream gefunden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 46 </td> 
   <td colname="col2"><span class="codeph"> BAD_MANIFEST_SIGNATURE</span> </td> 
   <td colname="col3"> Das Manifest hat eine ungültige Signatur. Der Manifestsignierungstest ist fehlgeschlagen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 47 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_LOAD_PLAYLIST</span> </td> 
   <td colname="col3"> Wiedergabeliste kann nicht geladen werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 48 </td> 
   <td colname="col2"><span class="codeph"> REPLACEMENT_FAILED</span> </td> 
   <td colname="col3"> Die in einer Einfügen-API angegebene Ersetzung konnte nicht erfolgreich sein. Dies bedeutet, dass die Einfügung erfolgreich war, die Ersetzung jedoch nicht. Die Ersetzung konnte fehlschlagen, wenn das zu ersetzende Manifest aus der Timeline entfernt wurde. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 49 </td> 
   <td colname="col2"><span class="codeph"> SWITCH_TO_ASYMMETRIC_PROFILE</span> </td> 
   <td colname="col3"> DRM wechselt zu einem asymmetrischen Profil. Es wird erwartet, dass alle Profile an der Dauer ausgerichtet werden. Andernfalls wird diese Warnung ausgegeben und es kann zu Sprüngen bei der Wiedergabe kommen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 50 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_BACKWARD</span> </td> 
   <td colname="col3"> Es wird erwartet, dass das Live-Fenster nur weiter geht. Andernfalls wird diese Warnung ausgegeben und das Fenster wird nicht gelesen. Aus diesem Grund kann es bei der Wiedergabe zu Sprüngen (oder Stopp/Long Pause) kommen. </td> 
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
   <td colname="col3"> Der Medienleser kann nicht weiter lesen, da er die durch die setHoldAt-API festgelegte Zeit erreicht hat. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 54 </td> 
   <td colname="col2"><span class="codeph"> LIVE_HOLD </span> </td> 
   <td colname="col3">Der Medienleser kann keine Segmente laden, da das Ende des Live-Fensters erreicht wurde. Das Laden des Segments wird fortgesetzt, wenn der Server neue Medien zum Live-Fenster hinzufügt. Dieser Status wird normalerweise erreicht, wenn: 
    <ul id="ul_FCFF658EDA4144E59970B317D6DEB624"> 
     <li id="li_2F6EEEB782D54CD999BC7CC7C0B78B48">Die <span class="codeph"> bufferTime</span> zu hoch ist (entspricht oder höher als die Dauer des Live-Fensters). </li> 
     <li id="li_25CE97115ED64E44AA89977FB5F0DCF7">Eine Kombination aus einer oder mehreren der API zum Einfügen/Löschen ersetzte mehr Medien als hinzugefügt. </li> 
     <li id="li_1B14716B2157492AB1859306D1250523">Der nächste Zeitraum ist ein Live-Zeitraum mit einem ausstehenden Medienersatz (aufgrund des InsertBy-API-Aufrufs). </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 55 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_INTERLEAVING </span> </td> 
   <td colname="col3"> Die Audio- und Videointeraktion in den Medien erfolgt nicht ordnungsgemäß. Dies ist ein Verpackungsfehler. Die Warnung wird ausgelöst, wenn die Differenz zwei Sekunden überschreitet. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 56 </td> 
   <td colname="col2"><span class="codeph"> DRM_NOT_AVAILABLE</span> </td> 
   <td colname="col3"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 57 </td> 
   <td colname="col2"><span class="codeph"> PLAYBACK_NOT_AUTHORIZED</span> </td> 
   <td colname="col3"> Die HLS-Wiedergabe wurde im Flash Player nicht aktiviert. Siehe AuthorizedFeatures.enableHLSPlayback . </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 58 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_SAMPLE_FOUND</span> </td> 
   <td colname="col3"> Der Decoder erhielt eine ungültige Stichprobe, die nicht dekodiert werden kann. Dies ist normalerweise kein schwerwiegender Fehler, weist aber darauf hin, dass es möglicherweise zu Fehlern im Audio/Video kommt. Zu viele Instanzen dieses Fehlers weisen auf eine fehlerhafte Kodierung oder eine fehlerhafte Datei hin. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 59 </td> 
   <td colname="col2"><span class="codeph"> RANGE_SPANS_READ_HEAD</span> </td> 
   <td colname="col3"> Nachdem die Wiedergabe gestartet wurde, sollte der Bereich "Einfügen/Ersetzen"den Lesekopf nicht enthalten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 60 </td> 
   <td colname="col2"><span class="codeph"> POSTROLL_WITH_LIVE_NOT_ALLOWED</span> </td> 
   <td colname="col3"> Einfügungen nach dem Roll sind auf einem Live-Medium nicht zulässig. Sie sind jedoch zulässig, nachdem der Server die Medien als abgeschlossen markiert hat. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 61 </td> 
   <td colname="col2"><span class="codeph"> INTERNAL_ERROR</span> </td> 
   <td colname="col3"> Ein sehr seltenes Problem, das niemals auftreten sollte. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 62 </td> 
   <td colname="col2"><span class="codeph"> SPS_PPS_FOUND_OUTSIDE_AVCC</span> </td> 
   <td colname="col3"> Der Stream folgt nicht der Verpackungsempfehlung, immer H264 SPS/PPS in einen AVCC einzufügen. Möglicherweise treten Probleme bei der Suche/Wiedergabe auf. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 63 </td> 
   <td colname="col2"><span class="codeph"> PARTIAL_REPLACEMENT</span> </td> 
   <td colname="col3"> Die in einer Einfügen-API angegebene Ersetzung wurde nur teilweise durchgeführt. Dies geschieht, wenn die Option replaceDuration über die Zeitleistendauer erstreckt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 64 </td> 
   <td colname="col2"><span class="codeph"> RENDITION_M3U8_ERROR</span> </td> 
   <td colname="col3"> Die Wiedergabeliste für Ausgabedarstellungen hatte einen Fehler beim Laden. Dies gilt nur für AVE, nicht für FlashPlayer. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 65 </td> 
   <td colname="col2"><span class="codeph"> NULL_OPERATION</span> </td> 
   <td colname="col3"> Der Vorgang führt nichts aus. </td> 
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
   <td colname="col2"><span class="codeph"> PROTOCOL_NOT_SUPPORTED </span> </td> 
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
   <td colname="col3"> Es kann kein Aufspaltungsvorgang für eine Timeline durchgeführt werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 72 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_ERASE_TIMELINE</span> </td> 
   <td colname="col3"> Kann keine Löschoperation für eine Timeline durchführen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 73 </td> 
   <td colname="col2"><span class="codeph"> DID_NOT_GET_NEXT_FRAGMENT</span> </td> 
   <td colname="col3"> Das nächste Fragment wurde nicht erhalten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 74 </td> 
   <td colname="col2"><span class="codeph"> NO_TIMELINE</span> </td> 
   <td colname="col3"> In einer internen Datenstruktur ist keine Timeline vorhanden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 75 </td> 
   <td colname="col2"><span class="codeph"> LISTENER_NOT_FOUND</span> </td> 
   <td colname="col3"> In einer internen Datenstruktur wurde kein Listener gefunden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 76 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_START_ERROR</span> </td> 
   <td colname="col3"> Audio kann nicht gestartet werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 77 </td> 
   <td colname="col2"><span class="codeph"> NO_AUDIO_SINK</span> </td> 
   <td colname="col3"> In einer internen Datenstruktur ist kein Audio-Senken vorhanden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 78 </td> 
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
   <td colname="col3"> Beim Analysieren von ID3-Daten ist ein Fehler aufgetreten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 82 </td> 
   <td colname="col2"><span class="codeph"> SECURITY_ERROR </span> </td> 
   <td colname="col3"> Das Laden des Inhalts ist aufgrund von Sicherheitsbeschränkungen fehlgeschlagen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 83 </td> 
   <td colname="col2"><span class="codeph"> TIMELINE_TOO_SHORT</span> </td> 
   <td colname="col3"> Die Timeline-Dauer ist zu kurz. Wenn es sich um einen Live-Stream handelt, kann es zu häufigen Pufferungen kommen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 84 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_START</span> </td> 
   <td colname="col3"> Der Stream wurde auf einen reinen Audio-Stream umgestellt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 85 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_END</span> </td> 
   <td colname="col3"> Der Stream wurde mit Video von Nur-Audio in einen Stream umgeschaltet. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 87 </td> 
   <td colname="col2"><span class="codeph"> KEY_NOT_FOUND </span> </td> 
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
   <td colname="col3"> Nicht gemeldete Diskontinuität (PTS) festgestellt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 92 </td> 
   <td colname="col2"> <span class="codeph"> UNMATCHED_AV_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> Nicht übereinstimmende Audio- und Videounterbrechung gefunden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 93 </td> 
   <td colname="col2"><span class="codeph"> TRICKPLAY_ENDED_DUE_TO_ERROR</span> </td> 
   <td colname="col3">Beim Abspielen von Medien in <i>Trick Play</i> -Modus. Der Trick Play-Modus wird beendet und der Stream wird angehalten. Aufruf <span class="codeph"> Play()</span> , um die Medien im normalen Modus wiederzugeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 95 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_AHEAD</span> </td> 
   <td colname="col3"> Der Spieler ist nicht im Live-Fenster und muss nach vorn suchen, um aufzuholen. </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR: Crypto-Werte {#section_39365E545CAC49B9A4D4678657BB2155}

Das Kryptomodul der Adobe-Video-Engine gibt diese Benachrichtigungen im `NATIVE_ERROR` Metadatenobjekt.

| **Wert für den Metadatenschlüssel NATIVE_ERROR_CODE** | **Wert für den Metadatenschlüssel NATIVE_ERROR_NAME** | **Bedeutung** |
|---|---|---|
| 300 | `CRYPTO_ALGORITHM_NOT_SUPPORTED` | Der verwendete Algorithmus wird nicht unterstützt. |
| 301 | `CRYPTO_ERROR_CORRUPTED_DATA` | Daten sind beschädigt. |
| 302 | `CRYPTO_ERROR_BUFFER_TOO_SMALL` | Puffer zu klein. |
| 303 | `CRYPTO_ERROR_BAD_CERTIFICATE` | Ungültiges Zertifikat. |
| 304 | `CRYPTO_ERROR_DIGEST_UPDATE` | Digest Update. |
| 305 | `CRYPTO_ERROR_DIGEST_FINISH` | Digest Finish. |
| 306 | `CRYPTO_ERROR_BAD_PARAMETER` | Unangemessener Parameter. |
