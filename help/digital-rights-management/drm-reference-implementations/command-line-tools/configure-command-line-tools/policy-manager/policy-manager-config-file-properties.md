---
description: 'null'
keywords: hard stop
seo-description: 'null'
seo-title: Konfigurationseigenschaften
title: Konfigurationseigenschaften
uuid: 216921d1-a9c1-4650-9dce-c025836986e5
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 0%

---


# Konfigurationseigenschaften {#configuration-properties}

<!--<a id="section_20A96CDCC5C340DEAF455C6E300E5712"></a>-->

>[!NOTE]
>
>Bei eingeschlossenen Eigenschaftsnamen stellt `.n`die `n` eine Ganzzahl dar, die für jede Instanz der Eigenschaft mit 1 und erhöht wird. Beispiel: `policy.license.customProp.n`.

<table class="+ topic/table " id="table_p3x_54y_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Eigenschaft/Befehlszeilenoption </th> 
   <th colname="2" class="- topic/entry entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.name</span> <p class="- topic/p "><span class="codeph"> -n</span> <i class="+ topic/ph hi-d/i ">policyName</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Der für Menschen lesbare DRM-Richtlinienname. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.requireKeyServer</span> <p class="- topic/p "><span class="codeph"> -keyServer</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Es gelten folgende Bedingungen: 
    <ul id="ul_AF4EBD6C19DC4DFAAB4756EF24BAC57D"> 
     <li id="li_6CC48ABF78EC426E9FC51458BD946BC9">Wenn "true", ist ein HTTPS-Schlüsselserver für wichtigen Versand unter iOS erforderlich. </li> 
     <li id="li_63046A4ED7354C1E9E823B475E4AEFF7">Wenn nicht angegeben, ist der Standardwert false. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.forceJailbreak</span> <p class="- topic/p "><span class="codeph"> -forceJailbreak</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Bei Geräten, die die Jailbreak-Erkennung unterstützen (wenn "true"), ist die Wiedergabe nicht zulässig, wenn ein Jailbreak erkannt wird. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.critical</span> <p class="- topic/p "><span class="codeph"> -kritisch</span> <i class="+ topic/ph hi-d/i ">boolesch</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Legt die Kritikalität der DRM-Politik fest: 
    <ul id="ul_63F1994798894233A67AC4F8220AB642"> 
     <li id="li_D05DD9AD70464D6B9DB9DFF95846E589">Wenn "true", muss der Server alle Teile der DRM-Richtlinie verstehen, die das Standardverhalten darstellt. </li> 
     <li id="li_0211473DAF1F426787CC4A68F47643C6">Bei "false"kann der Server DRM-Richtlinienattribute ignorieren, die er nicht erkennt. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chwinning.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry ">Lizenzserverzertifikat, dessen öffentlicher Schlüssel zum Verschlüsseln des Stamm-Verschlüsselungsschlüssels für die <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> erweiterte Lizenzketten</a>verwendet wird. Diese Eigenschaft gibt eine Datei an, die nur das Zertifikat enthält. <p>Hinweis:  Sowohl PEM- als auch DER-Formate werden unterstützt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.charing.rootKey</span> <p class="- topic/p "><span class="codeph"> -rootKey</span> <i class="+ topic/ph hi-d/i ">root-key</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>Gibt den Stamm-Verschlüsselungsschlüssel für die <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> erweiterte Lizenzketten</a>an. Wenn kein Schlüssel angegeben ist und die erweiterte Lizenzketten aktiviert sind, wird automatisch ein zufälliger Schlüssel generiert. </p> <p>Der Schlüssel muss 16 Byte lang sein und als Hexadezimalwerte angegeben werden. Leerzeichen zwischen den Hexadezimalwerten sind optional. Bei Updates ist die Befehlszeilenoption nicht verfügbar und die Eigenschaft wird ignoriert. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.url</span> <p class="- topic/p "><span class="codeph"> -domainURL</span> <i class="+ topic/ph hi-d/i ">url</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Wenn die Domänenregistrierung erforderlich ist, gibt <i>url</i> die URL eines Domänenservers an. Bei Updates ist die Befehlszeilenoption nicht verfügbar und die Eigenschaft wird ignoriert. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.anonymous</span> <p class="- topic/p "><span class="codeph"> -domainAnon</span> </p> </td> 
   <td colname="2" class="- topic/entry ">Gibt an, ob eine anonyme Domänenregistrierung zulässig ist. Setzt die Eigenschaft auf "true"oder schließt diese Befehlszeilenoption ein, um den anonymen Zugriff zuzulassen. <p>Hinweis: Diese Option kann nicht mit <span class="codeph"> -domainAuthNS</span>verwendet werden. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.authNamespace</span> <p class="- topic/p "><span class="codeph"> -domainAuthNS</span> - <i class="+ topic/ph hi-d/i ">Namensraum</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>Der Authentifizierungs-Namensraum für die Domänenregistrierung. Falls angegeben, muss sich der Client mit einem Benutzernamen und einem Kennwort authentifizieren, die von der angegebenen Behörde ausgegeben wurden. </p> <p>Bei Updates ist die Befehlszeilenoption nicht verfügbar und die Eigenschaft wird ignoriert. </p> <p>Hinweis: Diese Option kann nicht mit <span class="codeph"> -domainAnon</span>verwendet werden. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.analog</span> <p class="- topic/p "><span class="codeph"> -opAnalog</span> <i class="+ topic/ph hi-d/i ">AnalogOption</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Analoge Ausgabeschränkungen und die folgenden Werte werden unterstützt: 
    <ul class="- topic/ul " id="ul_h4x_54y_n4"> 
     <li class="- topic/li " id="li_F920EC01159C4231AFBE579D487C8770"><span class="+ topic/ph pr-d/codeph codeph"> NO_PROTECTION</span> </li> 
     <li class="- topic/li " id="li_2DE0494AF8C446EB9E4567915F5E97C3"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE</span> </li> 
     <li class="- topic/li " id="li_207D2D6256D6423FBDABA7A8627A9B7D"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_ACP</span> </li> 
     <li class="- topic/li " id="li_E17D944BED5F403FAE94708EE6AE4BBE"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_CGMSA</span> </li> 
     <li class="- topic/li " id="li_66D5A0C8FE154445A522D91EFB05B7ED"><span class="+ topic/ph pr-d/codeph codeph"> ERFORDERLICH</span> </li> 
     <li class="- topic/li " id="li_AF2024F212A249ED99AEECCF3E844A11"><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_ACP</span> </li> 
     <li class="- topic/li " id="li_FFF9B7DAE77740EE895EC35D1606A527"><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_CGMSA</span> </li> 
     <li class="- topic/li " id="li_52DED572F3AE495EB6A6450C611B440E"><span class="+ topic/ph pr-d/codeph codeph"> NO_PLAYBACK</span> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -drmBlacklist</span> - <i class="+ topic/ph hi-d/i ">Name/Wert-Paare</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>DRM-Clients, die den Zugriff auf geschützte Inhalte untersagen. Diese Option gibt eine Liste von DRM-Modulversionen an, die nicht verwendet werden dürfen (blockierungsliste-). </p> <p>Der Wert besteht aus durch Kommas getrennten <span class="codeph"> Paaren namens=Wert</span> im folgenden Format: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">Weitere Name/Wert-Paare müssen durch Kommas getrennt werden. Beispiel: <span class="codeph"> os=Win,release=2.0,arch=32</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -runtimeBlacklsit</span> - <i class="+ topic/ph hi-d/i ">Name/Wert-Paare</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>Anwendungslaufzeiten sind vom Zugriff auf geschützte Inhalte eingeschränkt. Diese Option gibt eine Liste von Versionen von Laufzeitmodulen an, die nicht verwendet werden dürfen (blockierungsliste). </p> <p>Der Wert besteht aus durch Kommas getrennten <span class="codeph"> Paaren name=value</span> im folgenden Format: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|application|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">Weitere Name/Wert-Paare müssen durch Kommas getrennt werden. Beispiel: <span class="codeph"> os=Win,application=AIR</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.v1DeviceCapabilities</span> <p class="- topic/p "><span class="codeph"> -devCapacityV1</span> <i class="+ topic/ph hi-d/i ">name/value-pair</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt die Gerätefunktionen an, die für den Zugriff auf geschützten Inhalt erforderlich sind. Der Wert besteht aus durch Kommas getrennten <span class="codeph"> Paaren namens=Wert</span> im folgenden Format: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> nonUserAccessibleBus|hardwareRootOfTrust=true|false</span> </p> <p class="- topic/p ">Beispiel: <span class="codeph"> nonUserAccessibleBus=false,hardwareRootOfTrust=true</span>. </p> <p>Während einer Aktualisierung müssen Sie <span class="codeph"> -devCapabilityV1</span> ohne die verbleibenden Argumente anwenden, die die Einschränkung der Gerätefunktionen entfernen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.syncFrequency</span> <p class="- topic/p "><span class="codeph"> -sync</span> <i class="+ topic/ph hi-d/i ">name/value-pair</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, wie oft Clients Synchronisierungsmeldungen an den Server senden müssen. </p> <p>Wenn die Eigenschaft nicht eingestellt ist, senden Clients keine Synchronisierungsmeldungen, wenn sie Inhalte wiedergeben, die mit einer DRM-Richtlinie geschützt sind. Der Wert besteht aus durch Kommas getrennten <span class="codeph"> Paaren name=value</span> im folgenden Format: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> Beginn|force=numberValue</span> </p> <p class="- topic/p ">Die folgende Liste enthält weitere Informationen zu den Optionen: 
     <ul id="ul_a5j_q4t_44"> 
      <li id="li_FD2C0C6DA19E455AA1917A56E09A7F84">(erforderlich) <span class="codeph"> Beginn</span> gibt an, dass die Synchronisierung mit dem Server in den angegebenen Minuten seit der letzten Synchronisierung vom Client Beginn werden muss. </li> 
      <li id="li_9DEBC57385A442C3929AE3D0E3FA8992">(optional) <span class="codeph"> force</span> ist die Wahrscheinlichkeit (0-100), mit der der Client während der Wiedergabe eine Synchronisierungsmeldung erzwingen muss. </li> 
     </ul>Verwenden Sie während der Aktualisierung <span class="codeph"> -sync</span> ohne die restlichen Argumente, um die Synchronisierungsanforderungen zu entfernen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.useRootLicense</span> </td> 
   <td colname="2" class="- topic/entry ">Gibt an, ob diese DRM-Richtlinie über eine Stammlizenz verfügt. <p>Weitere Informationen finden Sie unter <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> Erweiterte Lizenzketten</a>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.startDate</span> </td> 
   <td colname="2" class="- topic/entry ">Das Datum, nach dem der Inhalt gültig wird. Sie können eines der folgenden Formate anwenden: 
    <ul id="ul_6610B44D0C16485098F6F45DE3F151D7"> 
     <li id="li_986707D4C6164C44B3CCBE2EEB4C09B6"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> <p>Beispielsweise bedeutet <span class="codeph"> 2009-01-31</span> den 31. Januar um 12:00 Uhr. </p> </li> 
     <li id="li_E15B782716124F6EAEFB04D16E5280DB"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec</span> <p>Beispiel: <span class="codeph"> 2009-01-31-14:30:00</span> bedeutet 31. Januar um 14:30 Uhr. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Datum, an dem der Inhalt ungültig wird. </p> <p>Hinweis: Sie können <span class="codeph"> policy.expiration.endDate</span> und <span class="codeph"> policy.expiration.duration</span> nicht gleichzeitig angeben. </p> <p>Beispiel: 2009-01-31-14:30:00 Uhr bedeutet, dass der Inhalt am 31. Januar um 14:30 Uhr abläuft. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Der Zeitpunkt in Minuten, zu dem der Inhalt ungültig wird. Der Beginn, an dem Sie Inhalte verpacken. </p> <p>Hinweis: Sie können <span class="codeph"> policy.expiration.endDate</span> und <span class="codeph"> policy.expiration.duration</span> nicht gleichzeitig angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Zeit in Minuten, zu der eine Lizenz auf dem Client zwischengespeichert werden kann. Sie können diese Eigenschaft auf 0 einstellen, um die Lizenzzwischenspeicherung zu verhindern. Der Wert muss 0 oder höher sein. </p> <p>Hinweis: Sie können <span class="codeph"> policy.licenseCaching.duration</span> und <span class="codeph"> policy.licenseCaching.endDate</span> nicht gleichzeitig angeben. </p> <p class="- topic/p ">Diese DRM-Richtlinieneinstellung wird nur auf die Lizenzzwischenspeicherung auf der Festplatte angewendet und hat keine Kontrolle über die Dauer der zwischengespeicherten Lizenz. Die Lizenz kann im Arbeitsspeicher zwischengespeichert werden, selbst wenn Sie keine DRM-Richtlinie mit einer Dauer von null angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Datum, nach dem Sie keine Lizenzen mehr zwischenspeichern können. </p> <p>Hinweis: Sie können <span class="codeph"> policy.licenseCaching.duration</span> und <span class="codeph"> policy.licenseCaching.endDate</span> nicht gleichzeitig angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.anonymous</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, ob anonymer Lizenzerwerb zulässig ist. Die Standardeinstellung ist " <span class="codeph"> false</span>", d. h. ein Benutzername und ein Kennwort sind erforderlich. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.authNamespace</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn Benutzername und Kennwort erforderlich sind, gibt diese Eigenschaft einen optionalen Namensqualifizierer für Benutzernamen an. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Benutzerdefinierte Name/Wert-Paare, die vom Server während der Lizenzerfassung verwendet werden. Sie können das folgende Format anwenden, um Eigenschaften anzugeben: <span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.playWindow </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt das Wiedergabefenster in Minuten an. Dieser Wert gibt an, wie lange die Lizenz gültig ist, nachdem der geschützte Inhalt zum ersten Mal wiedergegeben wurde. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.digital</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ausgabenschutzeinschränkungen, die einen der folgenden Werte aufweisen müssen: 
     <ul id="ul_wsb_kfp_fs"> 
      <li id="li_FE012306F22F4F3FB981FE167C7A8B94"><span class="codeph"> NO_PROTECTION</span> </li> 
      <li id="li_A5591DC8983848FE9823C2A261BF7713"><span class="codeph"> USE_IF_AVAILABLE</span> </li> 
      <li id="li_74102C36ADE841C4B9ED71156E0A4C2C"><span class="codeph"> ERFORDERLICH</span> </li> 
      <li id="li_769E15C85B4E4DD48213DBD019D60BA7"><span class="codeph"> NO_PLAYBACK</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.ota</span> </td> 
   <td colname="2" class="- topic/entry ">Gibt die Verbindungstypen über der Luft (OTA) an, die aufgelistet werden dürfen. Gültige Verbindungstypen sind: 
    <ul id="ul_iz5_4fp_fs"> 
     <li id="li_FB07519EFEFE4B95B3B1F5BFD4DE6591"><span class="codeph"> MIRAKAST</span> </li> 
     <li id="li_51E7DE83679F4630B01264407DAD0E84"><span class="codeph"> AIRPLAY</span> </li> 
     <li id="li_D499A0487AAC409CB2CEA6164265D3CF"><span class="codeph"> DLNA</span> </li> 
     <li id="li_4FCC0EC4A0FC48F99A13EC8A1B78D6A1"><span class="codeph"> WIDI</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.resolution</span> </td> 
   <td colname="2" class="- topic/entry "> Gibt die Konfigurationsdatei an, in der die auflösungsbasierten Beschränkungen definiert werden. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt die Mindestsicherheitsstufe an, mit der das DRM-Modul auf geschützten Inhalt zugreifen kann. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Anwendungslaufzeitmodul muss über mindestens die angegebene Mindestsicherheitsstufe verfügen, um auf geschützten Inhalt zugreifen zu können. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedAIRApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Eine zulassungsliste von Nicht-Flash-Anwendungen (Adobe AIR, iOS, Android usw.) die geschützte Inhalte wiedergeben dürfen. Die Eigenschaft muss das folgende Format verwenden: <span class="+ topic/ph pr-d/codeph codeph">pubId</span>[:<span class="+ topic/ph pr-d/codeph codeph">appId</span>[:[<span class="+ topic/ph pr-d/codeph codeph">min</span>]:[<span class="+ topic/ph pr-d/codeph codeph">max</span>]]] </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedSWFApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Eine zulassungsliste von SWF-Anwendungen, die geschützte Inhalte abspielen dürfen. Die Eigenschaft muss das folgende Format verwenden: </p> <p class="- topic/p "> 
     <ul id="ul_EC20F52AD95C4BE3B7F703048A43CDF0"> 
      <li id="li_3E4A47D925C24834A2C25BC5943279D4"><span class="+ topic/ph pr-d/codeph codeph">URL</span> </li> 
      <li id="li_9A7CAF081C5F488FB5CDA6D38C5552F6"><span class="+ topic/ph pr-d/codeph codeph">file=swf_file</span> </li> 
      <li id="li_E10EA4223137489CBE4015DE999F7154"><span class="codeph">time=max_time_to_verify</span> </li> 
     </ul> <i class="+ topic/ph hi-d/i ">swf_file</i> ist die SWF-Datei, die zum Berechnen des Hashs verwendet wird, und <i class="+ topic/ph hi-d/i ">max_time_to_verify</i> ist die maximale Zeit in Sekunden, die für das Herunterladen und Überprüfen der SWF-Datei zum Abschluss zulässig ist. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Benutzerdefinierte Name/Wert-Paare, die Sie bei der Lizenzerteilung an Benutzer in die Lizenzen aufnehmen müssen. Sie müssen das folgende Format angeben: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n=name</span> </p> <p class="- topic/p ">Sie können diese Option mehrmals für mehrere benutzerdefinierte Eigenschaften definieren. </p> </td> 
  </tr> 
 </tbody> 
</table>

