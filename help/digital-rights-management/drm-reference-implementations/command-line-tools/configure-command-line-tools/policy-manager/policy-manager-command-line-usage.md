---
description: 'null'
seo-description: 'null'
seo-title: Befehlszeilenverwendung im Policy Manager
title: Befehlszeilenverwendung im Policy Manager
uuid: 9b17bc9a-0b1b-405f-a62b-0310c43c9255
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 0%

---


# Verwendung der Befehlszeile des Policy Manager {#policy-manager-command-line-usage}

```
java -jar AdobePolicyManager.jar  
<i class="+ topic ph hi-d="" i "="">
  command filename [options] 
</i class="+ topic>
```

**Tabelle 1: Befehle**

| Befehl | Beschreibung |
|---|---|
| `new` | Erstellt eine neue DRM-Richtlinie |
| `detail` | Beschreibt eine vorhandene DRM-Richtlinie |
| `update` | Aktualisiert eine vorhandene DRM-Richtlinie |

**Tabelle 2: Optionen**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_q5h_cpy_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Befehlszeilenoption </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Namen und den Speicherort der Konfigurationsdatei an. </p> <p class="- topic/p ">Wenn Sie keinen Namen oder einen Speicherort angeben, sucht der DRM Policy Manager im aktuellen Arbeitsverzeichnis nach <span class="filepath"> flashaccessStols.properties </span>. </p> <p>Hinweis:  Die Optionen, die Sie in der Befehlszeile angeben, haben Vorrang vor den Optionen, die Sie in der Konfigurationsdatei angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn die Zieldatei vorhanden ist, können Sie die Datei überschreiben, ohne dazu aufgefordert zu werden. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei vorhanden ist und <span class="codeph"> -o </span> nicht eingestellt ist, tritt ein Fehler auf. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -root  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, dass die DRM-Richtlinie über eine Stammlizenz verfügt. </p> <p class="- topic/p ">Diese Option steht nicht für Updates zur Verfügung. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e Datum  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Datum, an dem die Lizenzen gültig werden. </p> <p>Sie können das Datum im Format <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> oder <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:sec </span> angeben. Beispiel: 2008-12-1 oder 2008-12-1-00:00:00 Uhr für Mitternacht am 1. Dezember 2008. </p> <p> 
     <ul id="ul_D5DB5044756D4BD6A734813971598425"> 
      <li id="li_B6BD62A524384060A9DDA14FF50936FA">Der Wert muss größer als der Wert von <span class="codeph"> -s </span> sein, falls vorhanden. </li> 
      <li id="li_C3C5AD0231A240EC9AC57685B9206E8D">Sie können diese Option nicht mit <span class="codeph"> -r </span> anwenden. </li> 
      <li id="li_3790E2F829A149979BF44E0914CFF431">Um das Enddatum beim Aktualisieren einer DRM-Richtlinie zu entfernen, wenden Sie <span class="codeph"> -e </span> an, ohne ein Datum anzugeben. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r Minuten  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Dauer in Minuten, für die der geschützte Inhalt gültig ist. </p> <p class="- topic/p ">Die DRM-Richtlinie wird gültig, wenn der Inhalt mit dem Packager geschützt ist. </p> <p> 
     <ul id="ul_4690A0E4677A4DF6A006B7FCBD46F1BE"> 
      <li id="li_D1F098D44B494EE7A8647C0B62D5ACFA">Der Wert muss nicht negativ sein. </li> 
      <li id="li_ADFDCB01EEE04B37AFA42886AAEF47EB">Sie können diese Option nicht zusammen mit <span class="codeph"> -e </span> anwenden. </li> 
      <li id="li_E80563E68BEB43FC9E29A694594CAE01">Um die Dauer beim Aktualisieren einer DRM-Richtlinie zu entfernen oder zu löschen, wenden Sie <span class="codeph"> -r </span> an, ohne Minuten anzugeben. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s Datum  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Datum, an dem die Lizenzen gültig werden. </p> <p>Sie können das Datum im Format <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> oder <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:sec </span> angeben. Beispiel: <span class="codeph"> 2008-12-1 </span> oder <span class="codeph"> 2008-12-1-00:00:00 </span> für Mitternacht am 1. Dezember 2008. </p> <p> 
     <ul id="ul_D52B337F547F4E7AB87FE025236CA930"> 
      <li id="li_DBAE380972434DB1A4EF20D399038AB8">Der Wert muss kleiner als der Wert von <span class="codeph"> -e </span> sein, falls vorhanden. </li> 
      <li id="li_2899EC5559CF44319A4AC4ECD90A5B9A">Sie können diese Option nicht zusammen mit <span class="codeph"> -r </span> anwenden. </li> 
      <li id="li_19861B1A64E44B95B649948EAB3E4085">Um das Datum des Beginns beim Aktualisieren einer DRM-Richtlinie zu entfernen oder zu löschen, verwenden Sie <span class="codeph"> -s </span>, ohne ein Datum anzugeben. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w [&lt;minutes&gt;[,enableHS|disableHS]]  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wiedergabefenster, d. h. die Anzahl der Minuten, in denen der Inhalt ab der ersten Wiedergabe angezeigt werden kann. </p> <p>Wenn nicht angegeben oder <span class="codeph"> -w </span> ohne Angabe einer Anzahl von Minuten verwendet wird, gibt es keine Einschränkung des Wiedergabefensters. Der Wert muss nicht negativ sein. </p> <p>Das optionale <span class="codeph"> enableHS </span>- oder <span class="codeph">-Flag disableHS </span>-Signal, ob das Harthalten aktiviert oder deaktiviert werden soll. Das Flag gibt an, ob der Entschlüsselungskontext am Ende des Wiedergabefensters zerstört (aktiviert) oder nicht zerstört (deaktiviert) wird. </p> <p>Um beispielsweise anzugeben, dass der Inhalt nur für 60 Minuten angezeigt werden darf und eine feste Unterbrechung erforderlich ist, müssen Sie Folgendes angeben: 
     <codeblock>
       -w&amp;nbsp;60,enableHS 
     </codeblock> </p> <p>Hinweis:  <i>Hard stop</i> wird derzeit in Flash Player, Android und iOS nicht unterstützt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l Minuten  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Dauer der Lizenzzwischenspeicherung ist der Zeitraum in Minuten, in dem eine Lizenz im Lizenzspeicher des Kunden zwischengespeichert werden kann, nachdem die Lizenz vom Server ausgestellt wurde. Der Wert muss nicht negativ sein. </p> <p>Sie können <span class="codeph"> -l 0 </span> angeben, um anzugeben, dass die Lizenzzwischenspeicherung nicht zulässig ist. Geben Sie für eine unbegrenzte Lizenz-Caching <span class="codeph"> -l </span> ohne Minuten an. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -ldate  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Enddatum für die Lizenzzwischenspeicherung. </p> <p class="- topic/p ">Dies gibt das Enddatum an, ab dem der Client Lizenzen im Lizenzspeicher des Clients zwischenspeichern kann, nachdem der Primetime-DRM-Server die Lizenz erteilt hat. </p> <p>Sie können das Datum in den folgenden Formaten angeben: 
     <ul id="ul_112DE7248A9C48B19520A3AA9E5D1F03"> 
      <li id="li_01C5400E78B84A3B8955972FBA875AAC"> <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd  </span> </li> 
      <li id="li_AA13B1EFA07A4542A3DB41FA3320B143"> <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:sec  </span> </li> 
     </ul>Beispiel: <span class="codeph"> 2008-12-1 </span> oder <span class="codeph"> 2008-12-1-00:00:00 </span> für Mitternacht am 1. Dezember 2008. Sie müssen <span class="codeph"> -l </span> ohne Angabe von Minuten für die unbegrenzte Lizenzzwischenspeicherung anwenden. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Der Authentifizierungs-Namensraum. </p> <p class="- topic/p ">Wenn Sie diese Option aktivieren, muss der Kunde einen Benutzernamen und ein Kennwort eingeben, die von der angegebenen Behörde ausgegeben wurden. </p> <p>Sie können diese Option nicht zusammen mit <span class="codeph"> -x </span> anwenden. </p> <p>Diese Option ist für Aktualisierungen nicht zulässig. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Anonymen Zugriff zulassen. </p> <p class="- topic/p ">Sie können diese Option nicht zusammen mit <span class="codeph"> -authNS </span> anwenden. </p> <p class="- topic/p ">Diese Option ist für Aktualisierungen nicht zulässig. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId  </span>[:  <span class="+ topic/ph pr-d/codeph codeph"> appId  </span>[:[  <span class="+ topic/ph pr-d/codeph codeph"> min  </span>]:[  <span class="+ topic/ph pr-d/codeph codeph"> max  </span>]]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Eine Zulassungsliste von AIR-Anwendungen, die geschützten Inhalt abspielen können. </p> <p class="- topic/p ">Sie können diese Option anwenden, um einzuschränken, welche Herausgeber, Anwendungen und Versionen auf die Inhalte zugreifen können, die mit dieser DRM-Richtlinie geschützt sind. </p> <p class="- topic/p ">Wenn Sie <i class="+ topic/ph hi-d/i ">appId</i> nicht angeben, sind alle Anwendungen für den Herausgeber <i class="+ topic/ph hi-d/i ">pubId</i> zulässig. </p> <p>Hinweis:  <i class="+ topic/ph hi-d/i ">min</i> und <i class="+ topic/ph hi-d/i ">max</i> Versionsnummern sind optional. </p> <p class="- topic/p ">Sie können mehrere <span class="codeph"> -air </span>-Optionen angeben, um mehrere Anwendungen zuzulassen. Wenn Sie keine AIR- oder SWF-Anwendung angeben, können alle Anwendungen auf diesen Inhalt zugreifen. Wenn Sie während eines Updates alle Einträge aus der Liste entfernen oder löschen möchten, wenden Sie <span class="codeph"> -air </span> ohne die restlichen Argumente an. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmBlacklist name  </span> <i class="+ topic/ph hi-d/i ">/ </i> <span class="+ topic/ph pr-d/codeph codeph"> value  </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> paare  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die DRM-Clients, die keinen Zugriff auf geschützte Inhalte haben. </p> <p class="- topic/p ">Der Wert unterstützt kommagetrennte Paare aus name:value im folgenden Format: </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | release= stringValue  </span> </p> <p class="- topic/p ">Beispiel: <span class="codeph"> os=Win,release=2.0.1 </span>. Wenn Sie während eines Updates alle Einträge aus der Liste entfernen möchten, wenden Sie <span class="codeph"> -drmBlacklist </span> ohne die restlichen Argumente an. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmLevel int  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, dass DRM-Clients über eine zugewiesene Mindestsicherheitsstufe verfügen müssen, um Zugriff auf geschützte Inhalte zu erhalten. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opAnalog NO_PROTECTION | USE_IF_AVAILABLE | ERFORDERLICH | NO_PLAYBACK | REQUIRED_ACP | REQUIRED_CGMSA | USE_IF_AVAILABLE_ACP | USE_IF_AVAILABLE_CGMSA  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Analoge Ausgabeschutzeinschränkungen </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opDigital NO_PROTECTION | USE_IF_AVAILABLE | ERFORDERLICH | NO_PLAYBACK  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Einschränkungen beim digitalen Ausgabeschutz </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeBlacklist name  </span> <i class="+ topic/ph hi-d/i ">/ </i> <span class="+ topic/ph pr-d/codeph codeph"> value  </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> paare  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Anwendungslaufzeiten, die vom Zugriff auf geschützte Inhalte eingeschränkt sind. </p> <p class="- topic/p ">Der Wert unterstützt kommagetrennte Paare aus name:value im folgenden Format: </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | Antrag | release= stringValue  </span> </p> <p class="- topic/p ">Beispiel: <span class="codeph"> os=Win,release=2.0.1,application=AIR </span>. Wenn Sie während eines Updates alle Einträge aus der Liste entfernen möchten, wenden Sie <span class="codeph"> -runtimeBlacklist </span> ohne die restlichen Argumente an. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, dass die Anwendungs-Laufzeitumgebungen über ein angegebenes Mindestsicherheitsniveau verfügen müssen, um auf geschützten Inhalt zugreifen zu können. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url  </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file= swf_file  </span>,  <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify  </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Eine Zulassungsliste von SWF-Anwendungen, die geschützte Inhalte abspielen dürfen. </p> <p class="- topic/p ">Sie können mehrere <span class="codeph"> -swf </span>-Optionen angeben, um mehrere Anwendungen zuzulassen. Wenn Sie keine AIR- oder SWF-Anwendungen angeben, können alle Anwendungen auf diesen Inhalt zugreifen. </p> <p>Wenn Sie während eines Updates alle Einträge aus der Liste entfernen möchten, wenden Sie <span class="codeph"> -swf </span> ohne die restlichen Argumente an. Wenn Sie eine SWF anhand ihres Hashwerts identifizieren möchten, müssen Sie die SWF-Datei angeben, für die der Hash berechnet werden soll, sowie die maximale Zeit, die für den Abschluss der SWF-Überprüfung erforderlich ist (in Sekunden). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name= value  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt benutzerdefinierte Schlüssel/Werte an, die Sie einer DRM-Richtlinie hinzufügen möchten. </p> <p class="- topic/p ">Sie können mehrere <span class="codeph"> -k </span>-Optionen angeben. Während der Aktualisierung können Sie <span class="codeph"> -k </span> ohne die restlichen Argumente anwenden, wenn Sie alle Eigenschaften entfernen möchten. Die Interpretation oder Verarbeitung der Daten wird vom Primetime DRM-Lizenzserver verwaltet. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name= value  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fügt eine benutzerdefinierte Eigenschaft hinzu, die in der für jeden Client generierten Lizenz angezeigt wird. </p> <p class="- topic/p ">Sie können mehrere <span class="codeph"> -p </span>-Optionen angeben, um mehrere Eigenschaften hinzuzufügen. Bei einer Aktualisierung müssen Sie <span class="codeph"> -p </span> ohne die restlichen Argumente anwenden, wenn Sie alle Eigenschaften entfernen möchten. Die Interpretation oder Verarbeitung dieser Daten wird durch die Implementierung der Client-Anwendung verwaltet. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> <span class="codeph"> -opOTA whitelist=&lt;connection types=""&gt; </span> </span> </td> 
   <td colname="2" class="- topic/entry "> Über die Luft (OTA) Output Protection-Beschränkungen. Das Whitelist <span class="codeph">-Feld gibt an, welche Verbindungstypen zur Zulassungsliste und das Format <span class="codeph"> [type(,type)*] </span> verwendet werden, wobei Typ eines der folgenden sein kann: MIRACAST, AIRPLAY, WIDI, DLNA</span> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opResolution  &lt;filename&gt; </span> </td> 
   <td colname="2" class="- topic/entry "> <p>Auflösungsbasierte Ausgabenschutzbeschränkungen, wie in der angegebenen Datei definiert. </p> <p>Die Kodierung dieser Datei ist JSON. Die Grammatik für die Formatierung finden Sie unter <i>Über Auflösungsbasierter Ausgabeschutz</i>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Beispiele**

So erstellen Sie eine Richtlinie, die den anonymen Zugriff auf Ihren Inhalt ermöglicht, indem Sie Ihre eigene Konfigurationseigenschaftsdatei verwenden:

```
java -jar libs\AdobePolicyManager.jar new policy_test.pol -x -c my_configuration.properties
```
