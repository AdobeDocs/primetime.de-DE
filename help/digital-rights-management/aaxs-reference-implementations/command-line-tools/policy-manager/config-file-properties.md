---
title: Konfigurationsdateieigenschaften
description: Konfigurationsdateieigenschaften
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 0%

---

# Konfigurationsdateieigenschaften {#configuration-file-properties}

Die Konfigurationsdatei gibt die folgenden Eigenschaften an. Für Eigenschaftsnamen, die `n`, `n` stellt eine Ganzzahl dar, die mit 1 beginnt und für jede Instanz der Eigenschaft erhöht wird.

<table class="+ topic/table " id="table_p3x_54y_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Eigenschaft/Befehlszeilenoption </th> 
   <th colname="2" class="- topic/entry entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.name</span> <p class="- topic/p "><span class="codeph"> -n</span> <i class="+ topic/ph hi-d/i ">PoliceName</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Der für Menschen lesbare Richtlinienname. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.requireKeyServer</span> <p class="- topic/p "><span class="codeph"> -keyServer</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Wenn "true", ist ein HTTPS-Schlüsselserver erforderlich, um eine Schlüsselbereitstellung in iOS zu ermöglichen. Der Standardwert ist "false", falls nicht angegeben. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.forcedJailbreak</span> <p class="- topic/p "><span class="codeph"> -forcedJailbreak</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Wenn der Wert "true"lautet, sollten Sie bei Geräten, die die Erkennung von Ausfällen im Gefängnis unterstützen, die Wiedergabe nicht zulassen, wenn eine Ausrottung erkannt wurde. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.critical</span> <p class="- topic/p "><span class="codeph"> -critical</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Legen Sie die Kritikalität der Richtlinie fest. Wenn "true", muss der Server alle Teile der Richtlinie verstehen (dies ist das Standardverhalten). Bei "false"ignoriert der Server möglicherweise Richtlinienattribute, die er nicht versteht. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry ">Lizenzserver-Zertifikat, dessen öffentlicher Schlüssel zum Verschlüsseln des Stamm-Verschlüsselungsschlüssels für <a href="../../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md" format="dita" scope="local"> Verbesserte Lizenzketten </a>
   Diese Eigenschaft gibt eine Datei an, die nur das Zertifikat enthält (entweder das PEM- oder DAS DER-Format ist zulässig). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.rootKey</span> <p class="- topic/p "><span class="codeph"> -rootKey</span> <i class="+ topic/ph hi-d/i ">root-key</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Geben Sie den Stamm-Verschlüsselungsschlüssel für die erweiterte Lizenzketten an. Wenn kein Schlüssel angegeben und die erweiterte Lizenzketten-Funktion aktiviert ist, wird ein zufälliger Schlüssel generiert. Der Schlüssel muss 16 Byte lang sein und als Hex-Werte angegeben werden. Leerzeichen zwischen den Hex-Werten sind optional. Bei Aktualisierungen ist die Befehlszeilenoption nicht zulässig und die Eigenschaft wird ignoriert. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.url</span> <p class="- topic/p "><span class="codeph"> -domainURL</span> <i class="+ topic/ph hi-d/i ">url</i> </p> </td> 
   <td colname="2" class="- topic/entry "> URL des Domänenservers, wenn eine Domänenregistrierung erforderlich ist. Bei Aktualisierungen ist die Befehlszeilenoption nicht zulässig und die Eigenschaft wird ignoriert. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.anonymous</span> <p class="- topic/p "><span class="codeph"> -domainAnon</span> </p> </td> 
   <td colname="2" class="- topic/entry "> Gibt an, ob eine anonyme Domänenregistrierung zulässig ist. Setzen Sie die Eigenschaft auf true oder schließen Sie diese Befehlszeilenoption ein, um den anonymen Zugriff zuzulassen. Diese Option kann nicht mit -domainAuthNS verwendet werden. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.authNamespace</span> <p class="- topic/p "><span class="codeph"> -domainAuthNS</span> <i class="+ topic/ph hi-d/i ">namespace</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Der Authentifizierungs-Namespace für die Domänenregistrierung. Falls angegeben, sollte sich der Client mit einem Benutzernamen und einem Kennwort authentifizieren, das von der angegebenen Behörde ausgegeben wurde. Bei Aktualisierungen ist die Befehlszeilenoption nicht zulässig und die Eigenschaft wird ignoriert. Diese Option kann nicht mit -domainAnon verwendet werden. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.analog</span> <p class="- topic/p "><span class="codeph"> -opAnalog</span> <i class="+ topic/ph hi-d/i ">AnalogOption</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Analog-Ausgabeschutzeinschränkungen. Die folgenden Werte werden unterstützt: 
    <ul class="- topic/ul " id="ul_h4x_54y_n4"> 
     <li class="- topic/li " id="li_5BC8F39B61894E83A7B27570FF848F09"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> NO_PROTECTION</span> </p> </li> 
     <li class="- topic/li " id="li_FF14594A0714480496793A82C3FA1610"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE</span> </p> </li> 
     <li class="- topic/li " id="li_721FCC4DC1F34AE398EFAE4C0D3F50F5"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_AKP</span> </p> </li> 
     <li class="- topic/li " id="li_D588BB278BEE4CEAB034BD48550EBCDC"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_CGMSA</span> </p> </li> 
     <li class="- topic/li " id="li_7E5F006D2F114502BA6D0A9C4173004E"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> ERFORDERLICH</span> </p> </li> 
     <li class="- topic/li " id="li_9EBFAA4AACF249C2A94432D88E12C3B9"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_AKP</span> </p> </li> 
     <li class="- topic/li " id="li_6720C6A085864BEB957C0BF2C38551C9"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_CGMSA</span> </p> </li> 
     <li class="- topic/li " id="li_6FD98473ECDB4A66AC4B506FB9B3B360"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> NO_PLAYBACK</span> </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -drmBlacklist</span> <i class="+ topic/ph hi-d/i ">Name/Wert-Paare</i> </p> </td> 
   <td colname="2" class="- topic/entry ">DRM-Clients haben keinen Zugriff auf geschützte Inhalte. Diese Option gibt eine Liste der Versionen von DRM-Modulen an, die nicht verwendet werden dürfen (Blockierungsliste). Der Wert besteht aus kommagetrennten Name=Wert-Paaren mit folgendem Format: <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">Zusätzliche Name/Wert-Paare müssen durch Kommas getrennt sein. Beispiel: <span class="codeph"> os=Win,release=2.0,arch=32</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -runtimeBlacklsit</span> <i class="+ topic/ph hi-d/i ">Name/Wert-Paare</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Anwendungslaufzeiten sind vom Zugriff auf geschützte Inhalte eingeschränkt. Diese Option gibt eine Liste der Versionen von Laufzeitmodulen an, die nicht verwendet werden dürfen (Blockierungsliste). Der Wert besteht aus kommagetrennten Name=Wert-Paaren mit folgendem Format: <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|application|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">Zusätzliche Name/Wert-Paare müssen durch Kommas getrennt sein. Beispiel: <span class="codeph"> os=Win,application=AIR</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.v1DeviceCapabilities</span> <p class="- topic/p "><span class="codeph"> -devCapabilitiesV1</span> <i class="+ topic/ph hi-d/i ">Name/Wert-Paare</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt die Gerätefunktionen an, die für den Zugriff auf geschützte Inhalte erforderlich sind. Der Wert besteht aus kommagetrennten Name=Wert-Paaren mit folgendem Format: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> nonUserAccessibleBus|hardwareRootOfTrust=true|false</span> </p> <p class="- topic/p ">Beispiel: <span class="codeph"> nonUserAccessibleBus=false,hardwareRootOfTrust=true</span>. Verwenden Sie während der Aktualisierung <span class="codeph"> -devCapabilitiesV1</span> ohne die verbleibenden Argumente, um die Einschränkung der Gerätefunktionen zu entfernen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.syncFrequency</span> <p class="- topic/p "><span class="codeph"> -sync</span> <i class="+ topic/ph hi-d/i ">Name/Wert-Paare</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geben Sie an, wie oft Clients Synchronisierungsmeldungen an den Server senden müssen. Wenn diese Option nicht festgelegt ist, senden Clients keine Synchronisierungsmeldungen, wenn mit dieser Richtlinie geschützte Inhalte wiedergegeben werden. Der Wert besteht aus kommagetrennten Werten. <span class="codeph"> name=value</span> -Paare mit dem folgenden Format: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> start|force|hardStop=numberValue</span> </p> <p class="- topic/p "> 
     <ul id="ul_a5j_q4t_44"> 
      <li id="li_25CAF96C27F34848A95B2E3693847C71"><span class="codeph"> start</span> (erforderlich) - Das Startervall gibt an, dass der Client die Synchronisation mit dem Server seit der letzten Synchronisation einige Minuten beginnen soll. </li> 
      <li id="li_CC9068CFE75645029C947C9E1B53351F"><span class="codeph"> erzwingen</span> (optional) - Die erzwungene Synchronisierungswahrscheinlichkeit ist die Wahrscheinlichkeit (0-100), mit der der Client während der Wiedergabe eine Synchronisierungsmeldung erzwingen soll. </li> 
      <li id="li_C31A6250F19348FBB8B7569D00C6314E"><span class="codeph"> hardStop</span> (optional) - Das Hard Stopp-Intervall ist die Zeit in Minuten, nach der der Client die Wiedergabe fehlschlägt, wenn er nicht synchronisieren kann. Wenn festgelegt, muss größer als das Anfangsintervall sein. </li> 
     </ul>Verwenden Sie während der Aktualisierung <span class="codeph"> -sync</span> ohne die verbleibenden Argumente, um die Synchronisierungsanforderungen zu entfernen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.useRootLicense</span> </td> 
   <td colname="2" class="- topic/entry ">Gibt an, ob diese Richtlinie über eine Stammlizenz verfügt (siehe <i class="+ topic/ph hi-d/i ">Verbesserte Lizenzketten</i> in <i class="+ topic/ph hi-d/i ">Verwenden des Adobe-Zugriffs zum Schutz von Inhalten</i>). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.startDate</span> </td> 
   <td colname="2" class="- topic/entry ">Das Datum, nach dem der Inhalt gültig ist. Format verwenden <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> (zum Beispiel: <span class="codeph"> 31.1.2009</span> für den 31. Januar um 12:00 Uhr) oder <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:Sek</span> (zum Beispiel: <span class="codeph"> 31.1.2009-2014:30:00</span> Januar um 14:30 Uhr). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Datum, vor dem der Inhalt gültig ist. Beide <span class="codeph"> policy.expiration.endDate</span> und policy.expiration.duration können nicht gleichzeitig angegeben werden. Format verwenden <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> oder <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:Sek</span> (z. B. 2009-01-31-14:30:00 steht für den 31. Januar um 14:30 Uhr). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Gültigkeitsdauer des Inhalts (in Minuten), beginnend mit dem Verpacken. Beide <span class="codeph"> policy.expiration.endDate</span> und <span class="codeph"> policy.expiration.duration</span> kann nicht gleichzeitig angegeben werden. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Zeit, die eine Lizenz auf dem Client zwischengespeichert werden kann (in Minuten). Legen Sie diese Eigenschaft auf 0 fest, um die Lizenzzwischenspeicherung zu deaktivieren. Der Wert muss 0 oder höher sein. Beide <span class="codeph"> policy.licenseCaching.duration</span> und <span class="codeph"> policy.licenseCaching.endDate</span> darf nicht gleichzeitig verwendet werden. </p> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Hinweis</b>: Diese Richtlinieneinstellung wird nur auf das Lizenzzwischenspeichern auf der Festplatte angewendet. Die Dauer der im Speicher zwischengespeicherten Lizenz wird nicht gesteuert. Die Lizenz kann im Speicher zwischengespeichert werden, selbst wenn die angegebene Richtliniendauer null ist. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Datum, nach dem die Lizenzen nicht zwischengespeichert werden dürfen. Beide <span class="codeph"> policy.licenseCaching.duration</span> und <span class="codeph"> policy.licenseCaching.endDate</span> darf nicht gleichzeitig verwendet werden. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.anonymous</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, ob die anonyme Lizenzakquise zulässig ist. Die Standardeinstellung ist "false"(Benutzername/Passwort-Authentifizierung ist erforderlich), falls nicht angegeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.authNamespace</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn die Authentifizierung mit Benutzername/Kennwort erforderlich ist, gibt diese Eigenschaft einen optionalen Namensbezeichner für Benutzernamen an. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Benutzerdefinierte Name/Wert-Paare, die vom Server während der Lizenzakquise verwendet werden. Verwenden Sie das folgende Format, um Eigenschaften anzugeben: <span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.playWindow</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt das Wiedergabefenster (in Minuten) an, d. h. die Dauer, für die die Lizenz gültig ist, nachdem sie zum ersten Mal zum Abspielen geschützter Inhalte verwendet wird. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.digital</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Einschränkungen beim Output-Schutz. Die Werte müssen einer der folgenden sein: </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">NO_PROTECTION, USE_IF_AVAILABLE, REQUIRED, NO_PLAYBACK</i> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Für den Zugriff auf geschützte Inhalte muss das DRM-Modul über die angegebene Mindestsicherheitsstufe (oder höher) verfügen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Laufzeitmodul der Anwendung muss über die angegebene Mindestsicherheitsstufe (oder höher) verfügen, um auf geschützten Inhalt zugreifen zu können. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedAIRApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Eine Zulassungsliste von Adobe AIR- oder iOS-Anwendungen, die geschützte Inhalte wiedergeben dürfen. Die Eigenschaft muss das folgende Format verwenden: <span class="+ topic/ph pr-d/codeph codeph">pubId</span>[:<span class="+ topic/ph pr-d/codeph codeph">appId</span>[:[<span class="+ topic/ph pr-d/codeph codeph">min</span>]:[<span class="+ topic/ph pr-d/codeph codeph">max</span>]]] </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedSWFApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Eine Zulassungsliste von SWF-Applikationen, die geschützte Inhalte abspielen können. Verwenden Sie das folgende Format: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">URL</span> oder file=<span class="+ topic/ph pr-d/codeph codeph">swf_file</span>,time=<i class="+ topic/ph hi-d/i ">max_time_to_verify</i> <i class="+ topic/ph hi-d/i ">swf_file</i> ist die SWF-Datei, für die der Hash berechnet werden soll und <i class="+ topic/ph hi-d/i ">max_time_to_verify</i> ist die maximale Zeit, um den Download und die Verifizierung der SWF zu ermöglichen (in Sekunden). </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Benutzerdefinierte Name/Wert-Paare, die in Lizenzen für Benutzer enthalten sein sollen. Verwenden Sie das folgende Format: </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> <p class="- topic/p ">Diese Option kann mehrmals für mehrere benutzerdefinierte Eigenschaften definiert werden. </p> </td> 
  </tr> 
 </tbody> 
</table>
