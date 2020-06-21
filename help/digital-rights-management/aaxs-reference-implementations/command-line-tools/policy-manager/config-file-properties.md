---
seo-title: Konfigurationsdateieigenschaften
title: Konfigurationsdateieigenschaften
uuid: aec5fee7-4d77-4299-8d85-3e9042b2bbd1
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '1121'
ht-degree: 0%

---


# Konfigurationsdateieigenschaften {#configuration-file-properties}

Die Konfigurationsdatei gibt die folgenden Eigenschaften an. Bei eingeschlossenen Eigenschaftsnamen `n``n` steht für eine Ganzzahl, die mit 1 beginnt und für jede Instanz der Eigenschaft erhöht wird.

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
   <td colname="2" class="- topic/entry "> Der für Menschen lesbare Richtlinienname. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.requireKeyServer</span> <p class="- topic/p "><span class="codeph"> -keyServer</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Wenn "true", ist ein HTTPS-Schlüsselserver für wichtigen Versand unter iOS erforderlich. Der Standardwert ist "false", wenn nicht angegeben. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.forceJailbreak</span> <p class="- topic/p "><span class="codeph"> -forceJailbreak</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Wenn "true", sollten Sie bei Geräten, die die Erkennung von Jailbreak unterstützen, die Wiedergabe nicht zulassen, wenn ein Jailbreak erkannt wurde. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.critical</span> <p class="- topic/p "><span class="codeph"> -kritisch</span> <i class="+ topic/ph hi-d/i ">boolesch</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Legen Sie die politische Kritikalität fest. Wenn "true", muss der Server alle Teile der Richtlinie verstehen (dies ist das Standardverhalten). Bei "false"ignoriert der Server möglicherweise Richtlinienattribute, die er nicht versteht. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chwinning.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry ">Lizenzserverzertifikat, dessen öffentlicher Schlüssel zum Verschlüsseln des Stamm-Verschlüsselungsschlüssels für die <a href="../../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md" format="dita" scope="local"> erweiterte Lizenzketten verwendet wird </a>Diese Eigenschaft gibt eine Datei an, die nur das Zertifikat enthält (entweder das PEM- oder das DER-Format ist akzeptabel). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.charing.rootKey</span> <p class="- topic/p "><span class="codeph"> -rootKey</span> <i class="+ topic/ph hi-d/i ">root-key</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Geben Sie den Verschlüsselungsschlüssel für die erweiterte Lizenzketten an. Wenn kein Schlüssel angegeben ist und die erweiterte Lizenzketten aktiviert sind, wird ein zufälliger Schlüssel generiert. Der Schlüssel muss 16 Byte lang sein und als Hexadezimalwerte angegeben werden. Leerzeichen zwischen den Hex-Werten sind optional. Bei Updates ist die Befehlszeilenoption nicht zulässig und die Eigenschaft wird ignoriert. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.url</span> <p class="- topic/p "><span class="codeph"> -domainURL</span> <i class="+ topic/ph hi-d/i ">url</i> </p> </td> 
   <td colname="2" class="- topic/entry "> URL des Domänenservers, wenn eine Domänenregistrierung erforderlich ist. Bei Updates ist die Befehlszeilenoption nicht zulässig und die Eigenschaft wird ignoriert. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.anonymous</span> <p class="- topic/p "><span class="codeph"> -domainAnon</span> </p> </td> 
   <td colname="2" class="- topic/entry "> Gibt an, ob eine anonyme Domänenregistrierung zulässig ist. Setzen Sie die Eigenschaft auf true oder schließen Sie diese Befehlszeilenoption ein, um den anonymen Zugriff zuzulassen. Diese Option kann nicht mit -domainAuthNS verwendet werden. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.authNamespace</span> <p class="- topic/p "><span class="codeph"> -domainAuthNS</span> - <i class="+ topic/ph hi-d/i ">Namensraum</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Der Authentifizierungs-Namensraum für die Domänenregistrierung. Falls angegeben, muss sich der Client mit einem Benutzernamen und einem Kennwort authentifizieren, das von der angegebenen Behörde ausgegeben wird. Bei Updates ist die Befehlszeilenoption nicht zulässig und die Eigenschaft wird ignoriert. Diese Option kann nicht mit -domainAnon verwendet werden. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.analog</span> <p class="- topic/p "><span class="codeph"> -opAnalog</span> <i class="+ topic/ph hi-d/i ">AnalogOption</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Analoge Ausgabeschutzeinschränkungen. Die folgenden Werte werden unterstützt: 
    <ul class="- topic/ul " id="ul_h4x_54y_n4"> 
     <li class="- topic/li " id="li_5BC8F39B61894E83A7B27570FF848F09"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> NO_PROTECTION</span> </p> </li> 
     <li class="- topic/li " id="li_FF14594A0714480496793A82C3FA1610"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE</span> </p> </li> 
     <li class="- topic/li " id="li_721FCC4DC1F34AE398EFAE4C0D3F50F5"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_ACP</span> </p> </li> 
     <li class="- topic/li " id="li_D588BB278BEE4CEAB034BD48550EBCDC"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_CGMSA</span> </p> </li> 
     <li class="- topic/li " id="li_7E5F006D2F114502BA6D0A9C4173004E"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> ERFORDERLICH</span> </p> </li> 
     <li class="- topic/li " id="li_9EBFAA4AACF249C2A94432D88E12C3B9"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_ACP</span> </p> </li> 
     <li class="- topic/li " id="li_6720C6A085864BEB957C0BF2C38551C9"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_CGMSA</span> </p> </li> 
     <li class="- topic/li " id="li_6FD98473ECDB4A66AC4B506FB9B3B360"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> NO_PLAYBACK</span> </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -drmBlacklist</span> - <i class="+ topic/ph hi-d/i ">Name/Wert-Paare</i> </p> </td> 
   <td colname="2" class="- topic/entry ">DRM-Clients haben keinen Zugriff auf geschützte Inhalte. Diese Option gibt eine Liste von nicht verwendeten DRM-Modulen an (blockierungsliste). Der Wert besteht aus durch Kommas getrennten Paaren "name=Wert"mit folgendem Format: <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">Weitere Name/Wert-Paare müssen durch Kommas getrennt werden. Beispiel: <span class="codeph"> os=Win,release=2.0,arch=32</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -runtimeBlacklsit</span> - <i class="+ topic/ph hi-d/i ">Name/Wert-Paare</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Anwendungslaufzeiten sind vom Zugriff auf geschützte Inhalte eingeschränkt. Diese Option gibt eine Liste von nicht verwendeten Laufzeitmodulversionen an (blockierungsliste). Der Wert besteht aus durch Kommas getrennten Paaren "name=Wert"mit folgendem Format: <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|application|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">Weitere Name/Wert-Paare müssen durch Kommas getrennt werden. Beispiel: <span class="codeph"> os=Win,application=AIR</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.v1DeviceCapabilities</span> <p class="- topic/p "><span class="codeph"> -devCapacityV1</span> <i class="+ topic/ph hi-d/i ">name/value-pair</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt die zum Zugriff auf geschützten Inhalt erforderlichen Gerätefunktionen an. Der Wert besteht aus durch Kommas getrennten Paaren "name=Wert"mit folgendem Format: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> nonUserAccessibleBus|hardwareRootOfTrust=true|false</span> </p> <p class="- topic/p ">Beispiel: <span class="codeph"> nonUserAccessibleBus=false,hardwareRootOfTrust=true</span>. Verwenden Sie während der Aktualisierung <span class="codeph"> -devCapabilityV1</span> ohne die verbleibenden Argumente, um die Einschränkung der Gerätefunktionen zu entfernen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.syncFrequency</span> <p class="- topic/p "><span class="codeph"> -sync</span> <i class="+ topic/ph hi-d/i ">name/value-pair</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geben Sie an, wie oft Clients zum Senden von Synchronisierungsmeldungen an den Server erforderlich sind. Ist dies nicht der Fall, senden Clients keine Synchronisierungsmeldungen, wenn mit dieser Richtlinie geschützte Inhalte wiedergegeben werden. Der Wert besteht aus durch Kommas getrennten <span class="codeph"> Paaren namens=Wert</span> mit folgendem Format: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> Beginn|force|hardStop=numberValue</span> </p> <p class="- topic/p "> 
     <ul id="ul_a5j_q4t_44"> 
      <li id="li_25CAF96C27F34848A95B2E3693847C71"><span class="codeph"> Beginn</span> (erforderlich) - Beginn-Intervall gibt an, dass der Beginn die Synchronisierung mit dem Server einige Minuten seit der letzten Synchronisierung durchführen soll. </li> 
      <li id="li_CC9068CFE75645029C947C9E1B53351F"><span class="codeph"> force</span> (optional) - Die Wahrscheinlichkeit der erzwungenen Synchronisierung ist die Wahrscheinlichkeit (0-100), mit der der Client während der Wiedergabe eine Synchronisierungsmeldung erzwingen soll. </li> 
      <li id="li_C31A6250F19348FBB8B7569D00C6314E"><span class="codeph"> hardStop</span> (optional) - Das Intervall für die feste Beendigung ist der Zeitraum in Minuten, nach dem der Client die Wiedergabe fehlschlägt, wenn eine Synchronisierung nicht möglich ist. Wenn festgelegt, muss das Intervall größer als der Beginn sein. </li> 
     </ul>Verwenden Sie während der Aktualisierung <span class="codeph"> -sync</span> ohne die restlichen Argumente, um die Synchronisierungsanforderungen zu entfernen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.useRootLicense</span> </td> 
   <td colname="2" class="- topic/entry ">Gibt an, ob diese Richtlinie über eine Stammlizenz verfügt (siehe <i class="+ topic/ph hi-d/i ">Erweiterte Lizenzketten</i> in <i class="+ topic/ph hi-d/i ">Verwenden von Adobe Access zum Schutz von Inhalten</i>). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.startDate</span> </td> 
   <td colname="2" class="- topic/entry ">Das Datum, nach dem der Inhalt gültig ist. Verwenden Sie das Format <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> (z. B. entspricht <span class="codeph"> 2009-01-31</span> dem 31. Januar um 12:00 Uhr) oder <span class="+ topic/ph pr-d/codeph codeph">yyy-mm-dd-h24:min:sec</span> (z. B. <span class="codeph"> 2009-01-31-1-1-1-1-1-14:4) 30:00</span> steht für den 31. Januar um 14:30 Uhr). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Datum, vor dem der Inhalt gültig ist. Es ist nicht möglich, <span class="codeph"> policy.expiration.endDate</span> und policy.expiration.duration gleichzeitig anzugeben. Verwenden Sie das Format <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> oder <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec</span> (z. B. stellt 2009-01-31-14:30:00 den 31. Januar um 14:30 Uhr dar). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Gültigkeitsdauer des Inhalts (in Minuten), beginnend mit dem Verpacken. Es ist nicht möglich, <span class="codeph"> policy.expiration.endDate</span> und <span class="codeph"> policy.expiration.duration</span> gleichzeitig anzugeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Zeit, die eine Lizenz auf dem Client zwischengespeichert werden kann (in Minuten). Setzen Sie diese Eigenschaft auf 0, um die Lizenzzwischenspeicherung zu deaktivieren. Der Wert muss 0 oder höher sein. Sowohl <span class="codeph"> policy.licenseCaching.duration</span> als auch <span class="codeph"> policy.licenseCaching.endDate</span> dürfen nicht gleichzeitig verwendet werden. </p> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Hinweis</b>: Diese Richtlinieneinstellung wird nur auf die Lizenzzwischenspeicherung auf der Festplatte angewendet. Die Dauer der zwischengespeicherten Lizenz im Arbeitsspeicher wird nicht gesteuert. Die Lizenz kann auch dann auf dem Speicher zwischengespeichert werden, wenn die von der Richtlinie angegebene Dauer null ist. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Datum, nach dem Lizenzen nicht zwischengespeichert werden dürfen. Sowohl <span class="codeph"> policy.licenseCaching.duration</span> als auch <span class="codeph"> policy.licenseCaching.endDate</span> dürfen nicht gleichzeitig verwendet werden. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.anonymous</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, ob anonymer Lizenzerwerb zulässig ist. Die Standardeinstellung ist "false"(Benutzername-/Kennwortauthentifizierung ist erforderlich), wenn kein Wert angegeben wurde. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.authNamespace</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn die Authentifizierung mit Benutzername und Kennwort erforderlich ist, gibt diese Eigenschaft einen optionalen Namensqualifizierer für Benutzernamen an. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Benutzerdefinierte Name/Wert-Paare, die vom Server während der Lizenzerfassung verwendet werden. Verwenden Sie das folgende Format zum Festlegen von Eigenschaften: <span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.playWindow</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt das Wiedergabefenster (in Minuten) an, bei dem es sich um die Dauer handelt, für die die Lizenz gültig ist, nachdem zum ersten Mal geschützter Inhalt wiedergegeben wurde. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.digital</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ausgabenschutzbeschränkungen. Die Werte müssen einer der folgenden sein: </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">NO_PROTECTION, USE_IF_AVAILABLE, REQUIRED, NO_PLAYBACK</i> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Für den Zugriff auf geschützte Inhalte muss das DRM-Modul die angegebene Mindestsicherheitsstufe oder höher aufweisen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Anwendungslaufzeitmodul muss über die angegebene Mindestsicherheitsstufe oder höher verfügen, um auf geschützten Inhalt zugreifen zu können. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedAIRApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Eine zulassungsliste von Adobe AIR- oder iOS-Anwendungen, die geschützte Inhalte abspielen dürfen. Die Eigenschaft muss das folgende Format verwenden: <span class="+ topic/ph pr-d/codeph codeph">pubId</span>[:<span class="+ topic/ph pr-d/codeph codeph">appId</span>[:[<span class="+ topic/ph pr-d/codeph codeph">min</span>]:[<span class="+ topic/ph pr-d/codeph codeph">max</span>]]] </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedSWFApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Eine zulassungsliste von SWF-Anwendungen, die geschützte Inhalte abspielen dürfen. Verwenden Sie das folgende Format: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">URL</span> oder file=<span class="+ topic/ph pr-d/codeph codeph">swf_file</span>,time=<i class="+ topic/ph hi-d/i ">max_time_to_verify</i> <i class="+ topic/ph hi-d/i ">swf_file</i> ist die SWF-Datei, für die der Hash berechnet wird, und <i class="+ topic/ph hi-d/i ">max_time_to_verify</i> ist die maximale Zeit, die für den Download und die Überprüfung der SWF-Datei (in Sekunden) erforderlich ist. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Benutzerdefinierte Name/Wert-Paare, die in den Anwenderlizenzen enthalten sein sollen. Verwenden Sie das folgende Format: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> <p class="- topic/p ">Diese Option kann mehrmals für mehrere benutzerdefinierte Eigenschaften definiert werden. </p> </td> 
  </tr> 
 </tbody> 
</table>

