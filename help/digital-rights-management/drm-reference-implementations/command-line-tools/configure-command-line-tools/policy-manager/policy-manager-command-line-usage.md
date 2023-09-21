---
title: Befehlszeilenverwendung in Policy Manager
description: Befehlszeilenverwendung in Policy Manager
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1223'
ht-degree: 0%

---

# Befehlszeilenverwendung in Policy Manager {#policy-manager-command-line-usage}

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
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Namen und Speicherort der Konfigurationsdatei an. </p> <p class="- topic/p ">Wenn Sie keinen Namen oder Speicherort angeben, sucht der DRM Policy Manager nach <span class="filepath"> flashaccessHools.properties </span> im aktuellen Arbeitsverzeichnis. </p> <p>Hinweis: Die Optionen, die Sie in der Befehlszeile angeben, haben Vorrang vor den Optionen, die Sie in der Konfigurationsdatei angeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn die Zieldatei vorhanden ist, können Sie die Datei überschreiben, ohne dazu aufgefordert zu werden. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noconsole </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei vorhanden ist und <span class="codeph"> -o </span> nicht festgelegt ist, tritt ein Fehler auf. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -root </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, dass die DRM-Richtlinie über eine Stammlizenz verfügt. </p> <p class="- topic/p ">Diese Option steht nicht für Aktualisierungen zur Verfügung. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e date </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Datum, an dem die Lizenzen gültig werden. </p> <p>Sie können das Datum unter <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> oder <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:Sek </span> Format. Beispiel: 12.1.2008 oder 2008-12-1-00:00:00 für Mitternacht am 1. Dezember 2008. </p> <p> 
     <ul id="ul_D5DB5044756D4BD6A734813971598425"> 
      <li id="li_B6BD62A524384060A9DDA14FF50936FA">Der Wert muss größer sein als der Wert von <span class="codeph"> -s </span> sofern vorhanden. </li> 
      <li id="li_C3C5AD0231A240EC9AC57685B9206E8D">Diese Option kann nicht angewendet werden mit <span class="codeph"> -r </span>. </li> 
      <li id="li_3790E2F829A149979BF44E0914CFF431">Um das Enddatum beim Aktualisieren einer DRM-Richtlinie zu entfernen, wenden Sie <span class="codeph"> -e </span> ohne Angabe eines Datums. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r Minuten </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Gültigkeitsdauer des geschützten Inhalts in Minuten. </p> <p class="- topic/p ">Die DRM-Richtlinie wird gültig, wenn der Inhalt mit dem Packager geschützt ist. </p> <p> 
     <ul id="ul_4690A0E4677A4DF6A006B7FCBD46F1BE"> 
      <li id="li_D1F098D44B494EE7A8647C0B62D5ACFA">Der Wert darf nicht negativ sein. </li> 
      <li id="li_ADFDCB01EEE04B37AFA42886AAEF47EB">Diese Option kann nicht zusammen mit <span class="codeph"> -e </span>. </li> 
      <li id="li_E80563E68BEB43FC9E29A694594CAE01">Um die Dauer beim Aktualisieren einer DRM-Richtlinie zu entfernen oder zu löschen, wenden Sie <span class="codeph"> -r </span> ohne Angabe von Minuten. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s date </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Datum, an dem die Lizenzen gültig werden. </p> <p>Sie können das Datum im <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> oder <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:Sek </span> Format. Beispiel: <span class="codeph"> 12.1.2008 </span> oder <span class="codeph"> 12.1.2008:00:00 </span> für Mitternacht am 1. Dezember 2008. </p> <p> 
     <ul id="ul_D52B337F547F4E7AB87FE025236CA930"> 
      <li id="li_DBAE380972434DB1A4EF20D399038AB8">Der Wert muss kleiner sein als der Wert von <span class="codeph"> -e </span>, falls vorhanden. </li> 
      <li id="li_2899EC5559CF44319A4AC4ECD90A5B9A">Diese Option kann nicht zusammen mit <span class="codeph"> -r </span>. </li> 
      <li id="li_19861B1A64E44B95B649948EAB3E4085">Verwenden Sie zum Entfernen oder Löschen des Startdatums beim Aktualisieren einer DRM-Richtlinie <span class="codeph"> -s </span> ohne Angabe eines Datums. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w [&lt;minutes&gt;[,enableHS|disableHS]] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wiedergabefenster, d. h. die Anzahl der Minuten, in denen der Inhalt ab der ersten Wiedergabe angezeigt werden kann. </p> <p>Wenn nicht angegeben, oder wenn <span class="codeph"> -w </span> verwendet wird, ohne eine Anzahl von Minuten anzugeben, gibt es keine Beschränkung für das Wiedergabefenster. Der Wert darf nicht negativ sein. </p> <p>Das optionale <span class="codeph"> enableHS </span> oder <span class="codeph"> disableHS </span> Markierung signalisiert, ob der harte Stopp aktiviert oder deaktiviert werden soll. Das Flag gibt an, ob der Entschlüsselungskontext am Ende des Wiedergabefensters zerstört (aktiviert) oder nicht zerstört (deaktiviert) wird. </p> <p>Um beispielsweise anzugeben, dass der Inhalt nur 60 Minuten lang angezeigt werden darf und einen harten Stopp erfordert: 
     <codeblock>
       -w&amp;nbsp;60,enableHS 
     </codeblock> </p> <p>Hinweis:  <i>Hardstop</i> wird derzeit nicht in Flash Player, Android und iOS unterstützt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l Minuten </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Lizenzzwischenspeicherungsdauer ist die Zeit in Minuten, zu der eine Lizenz im Lizenzspeicher des Kunden zwischengespeichert werden kann, nachdem die Lizenz vom Server ausgestellt wurde. Der Wert darf nicht negativ sein. </p> <p>Sie können <span class="codeph"> -l 0 </span> , um anzugeben, dass die Zwischenspeicherung von Lizenzen nicht zulässig ist. Für unbegrenzte Lizenzzwischenspeicherung geben Sie <span class="codeph"> -l </span> ohne Minuten. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -ldate </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Enddatum für die Lizenzzwischenspeicherung. </p> <p class="- topic/p ">Dies gibt das Enddatum an, an dem der Client Lizenzen im Lizenzspeicher des Clients zwischenspeichern kann, nachdem der Primetime DRM-Server die Lizenz erteilt hat. </p> <p>Sie können das Datum in den folgenden Formaten angeben: 
     <ul id="ul_112DE7248A9C48B19520A3AA9E5D1F03"> 
      <li id="li_01C5400E78B84A3B8955972FBA875AAC"> <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> </li> 
      <li id="li_AA13B1EFA07A4542A3DB41FA3320B143"> <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:Sek </span> </li> 
     </ul>Beispiel: <span class="codeph"> 12.1.2008 </span> oder <span class="codeph"> 12.1.2008:00:00 </span> für Mitternacht am 1. Dezember 2008. Sie müssen <span class="codeph"> -l </span> ohne Angabe von Minuten für unbegrenzte Lizenzzwischenspeicherung. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Der Authentifizierungs-Namespace. </p> <p class="- topic/p ">Wenn Sie diese Option anwenden, muss der Kunde einen Benutzernamen und ein Kennwort eingeben, die von der angegebenen Behörde ausgegeben wurden. </p> <p>Diese Option kann nicht zusammen mit <span class="codeph"> -x </span>. </p> <p>Diese Option ist für Aktualisierungen nicht zulässig. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Anonymen Zugriff zulassen. </p> <p class="- topic/p ">Diese Option kann nicht zusammen mit <span class="codeph"> -authNS </span>. </p> <p class="- topic/p ">Diese Option ist für Aktualisierungen nicht zulässig. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId </span>[: <span class="+ topic/ph pr-d/codeph codeph"> appId </span>[:[ <span class="+ topic/ph pr-d/codeph codeph"> min </span>]:[ <span class="+ topic/ph pr-d/codeph codeph"> max </span>]]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Eine Zulassungsliste von AIR-Anwendungen, die geschützten Inhalt abspielen können. </p> <p class="- topic/p ">Sie können diese Option anwenden, um zu beschränken, welche Herausgeber, Anwendungen und Versionen auf den Inhalt zugreifen können, der mit dieser DRM-Richtlinie geschützt ist. </p> <p class="- topic/p ">Wenn Sie <i class="+ topic/ph hi-d/i ">appId</i>, alle Anwendungen für Publisher <i class="+ topic/ph hi-d/i ">pubId</i> sind erlaubt. </p> <p>Hinweis:  <i class="+ topic/ph hi-d/i ">min</i> und <i class="+ topic/ph hi-d/i ">max</i> Versionsnummern sind optional. </p> <p class="- topic/p ">Sie können mehrere <span class="codeph"> - Luft </span> Optionen, um mehrere Anwendungen zuzulassen. Wenn Sie keine AIR- oder SWF-Anwendung angeben, können alle Anwendungen auf diesen Inhalt zugreifen. Wenn Sie während einer Aktualisierung alle Einträge aus der Liste entfernen oder löschen möchten, wenden Sie <span class="codeph"> - Luft </span> ohne die verbleibenden Argumente . </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmBlacklist name </span> <i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> value </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> Paare </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die DRM-Clients, die keinen Zugriff auf geschützte Inhalte haben. </p> <p class="- topic/p ">Der Wert unterstützt kommagetrennte Name-Wert-Paare im folgenden Format: </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | release= stringValue </span> </p> <p class="- topic/p ">Beispiel: <span class="codeph"> os=Win,release=2.0.1 </span>. Während einer Aktualisierung müssen Sie alle Einträge aus der Liste entfernen. <span class="codeph"> -drmBlacklist </span> ohne die übrigen Argumente. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, dass DRM-Clients über eine zugewiesene Mindestsicherheitsstufe verfügen müssen, um Zugriff auf geschützte Inhalte zu erhalten. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opAnalog NO_PROTECTION | USE_IF_AVAILABLE | ERFORDERLICH | NO_PLAYBACK | REQUIRED_AKP | REQUIRED_CGMSA | USE_IF_AVAILABLE_AKP | USE_IF_AVAILABLE_CGMSA </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Analog-Ausgabeschutzeinschränkungen </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opDigital NO_PROTECTION | USE_IF_AVAILABLE | ERFORDERLICH | NO_PLAYBACK </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Digital Output Protection-Einschränkungen </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeBlacklist-Name </span> <i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> value </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> Paare </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Anwendungslaufzeiten, die vom Zugriff auf geschützte Inhalte ausgeschlossen sind. </p> <p class="- topic/p ">Der Wert unterstützt kommagetrennte Name-Wert-Paare im folgenden Format: </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | Anwendung | release= stringValue </span> </p> <p class="- topic/p ">Beispiel: <span class="codeph"> os=Win,release=2.0.1,application=AIR </span>. Während einer Aktualisierung müssen Sie alle Einträge aus der Liste entfernen. <span class="codeph"> -runtimeBlacklist </span> ohne die verbleibenden Argumente . </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, dass die Anwendungslaufzeiten über ein bestimmtes Mindestsicherheitsniveau verfügen müssen, um auf geschützten Inhalt zugreifen zu können. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file= swf_file </span>, <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Eine Zulassungsliste von SWF-Applikationen, die geschützten Inhalt abspielen dürfen. </p> <p class="- topic/p ">Sie können mehrere <span class="codeph"> -swf </span> Optionen, um mehrere Anwendungen zuzulassen. Wenn Sie keine AIR- oder SWF-Anwendungen angeben, können alle Anwendungen auf diesen Inhalt zugreifen. </p> <p>Während einer Aktualisierung müssen Sie alle Einträge aus der Liste entfernen. <span class="codeph"> -swf </span> ohne die verbleibenden Argumente . Wenn Sie eine SWF anhand ihres Hash-Werts identifizieren möchten, müssen Sie die SWF-Datei angeben, für die der Hash berechnet werden soll, und die maximale Zeit, um die SWF-Verifizierung abzuschließen (in Sekunden). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name= value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt benutzerdefinierte Schlüssel/Werte an, die Sie einer DRM-Richtlinie hinzufügen möchten. </p> <p class="- topic/p ">Sie können mehrere <span class="codeph"> -k </span> Optionen. Während der Aktualisierung können Sie <span class="codeph"> -k </span> ohne die restlichen Argumente, wenn Sie alle Eigenschaften entfernen möchten. Die Interpretation oder Handhabung der Daten wird vom Primetime DRM-Lizenzserver verwaltet. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name= value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fügt eine benutzerdefinierte Eigenschaft hinzu, die in der für jeden Client generierten Lizenz angezeigt wird. </p> <p class="- topic/p ">Sie können mehrere <span class="codeph"> -p </span> Optionen zum Hinzufügen mehrerer Eigenschaften. Bei einer Aktualisierung müssen Sie <span class="codeph"> -p </span> ohne die restlichen Argumente, wenn Sie alle Eigenschaften entfernen möchten. Die Interpretation oder Handhabung dieser Daten wird durch die Implementierung der Clientanwendung verwaltet. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> <span class="codeph"> -opOTA whitelist=&lt;connection types=""&gt; </span> </span> </td> 
   <td colname="2" class="- topic/entry "> Über die Luft (OTA) Einschränkungen des Output Protection. Die <span class="codeph"> Whitelist </span> field gibt an, welche Verbindungstypen zur Zulassungsliste und das Format von &lt;connection types=""&gt; is <span class="codeph"> [type(,type)*] </span>, wobei der Typ einer der folgenden sein kann: MIRACAST, AIRPLAY, WIDI, DLNA </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opResolution &lt;filename&gt; </span> </td> 
   <td colname="2" class="- topic/entry "> <p>Auflösungsbasierte Ausgabeschutzbegrenzungen, wie in der angegebenen Datei definiert. </p> <p>Die Kodierung dieser Datei ist JSON. Die Grammatik für die Formatierung finden Sie unter <i>Über den auflösungsbasierten Output Protection</i>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Beispiele**

So erstellen Sie eine Richtlinie, die anonymen Zugriff auf Ihren Inhalt ermöglicht, indem Sie Ihre eigene Konfigurationseigenschaftsdatei verwenden:

```
java -jar libs\AdobePolicyManager.jar new policy_test.pol -x -c my_configuration.properties
```
