---
seo-title: Befehlszeilenverwendung
title: Befehlszeilenverwendung
uuid: e549a98e-b027-4472-8860-6aa1d56d4a8b
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 0%

---


# Befehlszeilenverwendung {#command-line-usage}

Bevor Sie den Policy Manager verwenden, stellen Sie sicher, dass Sie die unter Anforderungen aufgelisteten Anforderungen erfüllen.

Der Policy Manager befindet sich im Ordner [!DNL \Reference Implementation\Command Line Tools] auf der DVD. Verwenden Sie zum Ausführen des Tools die folgende Syntax:

```
java -jar AdobePolicyManager.jar  
<i class="+ topic ph hi-d="" i "="">
  command filename [options] 
</i class="+ topic>
```

Die folgende Tabelle enthält Beschreibungen der Befehlszeilenaktionen, die in der obigen Syntax aufgeführt sind:

| Befehlszeilenaktion | Beschreibung |
|---|---|
| `new` | Erstellt eine neue Richtlinie. |
| `detail` | Beschreibt eine vorhandene Richtlinie. |
| `update` | Aktualisiert eine vorhandene Richtlinie. |

In der folgenden Tabelle werden die Befehlszeilenoptionen beschrieben, die zusammen mit der obigen Syntax angegeben werden können:

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Speicherort der Konfigurationsdatei an. Wenn diese Option nicht verwendet wird, sucht der Policy Manager im Arbeitsverzeichnis nach " <span class="filepath"> flashaccessStols.properties" </span> . Die in der Befehlszeile angegebenen Optionen haben Vorrang vor den Optionen in der Konfigurationsdatei. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn die Zieldatei bereits vorhanden ist, überschreiben Sie sie ohne Eingabeaufforderung. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und <span class="codeph"> -o nicht festgelegt </span> ist, wird ein Fehler zurückgegeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -root </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, dass die Richtlinie über eine Stammlizenz verfügt. Für Updates nicht zulässig. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e Datum </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Datum, vor dem die Lizenzen gültig sein werden. Geben Sie als <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> oder <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:sec </span>. Beispiel: 2008-12-1 oder 2008-12-1-00:00:00 Uhr für Mitternacht am 1. Dezember 2008. Der Wert muss größer als der Wert von <span class="codeph"> -s sein, </span>(sofern vorhanden). Diese Option kann nicht mit <span class="codeph"> -r verwendet werden </span>. Um das Enddatum beim Aktualisieren einer Richtlinie zu entfernen, verwenden Sie <span class="codeph"> -e, </span> ohne ein Datum anzugeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r Minuten </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Dauer (Minuten), die der mit dieser Richtlinie geschützte Inhalt hat, ist gültig, beginnend mit dem Schutz des Inhalts mit dem Packager. Der Wert muss nicht negativ sein. Diese Option kann nicht mit <span class="codeph"> -e verwendet werden </span>. Um die Dauer beim Aktualisieren einer Richtlinie zu entfernen, verwenden Sie <span class="codeph"> -r, </span> ohne eine Anzahl von Minuten anzugeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s Datum </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Datum, nach dem die Lizenzen gültig sind. Geben Sie als <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> oder <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:sec </span>. Beispiel: 2008-12-1 oder 2008-12-1-00:00:00 Uhr für Mitternacht am 1. Dezember 2008. Der Wert muss kleiner als der Wert von <span class="codeph"> -e sein, </span>(sofern vorhanden). Diese Option kann nicht mit <span class="codeph"> -r verwendet werden </span>. Um das Datum des Beginns beim Aktualisieren einer Richtlinie zu entfernen, verwenden Sie <span class="codeph"> -s, </span> ohne ein Datum anzugeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w Minuten </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Wiedergabefenster (die Anzahl der Minuten, in denen der Inhalt angezeigt werden kann, beginnend mit der ersten Wiedergabe). Wenn diese Option nicht angegeben ist oder wenn <span class="codeph"> -w ohne Angabe der Minutenanzahl verwendet </span> wird, gibt es keine Einschränkung des Wiedergabefensters. Der Wert muss nicht negativ sein. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l Minuten </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Dauer der Lizenzzwischenspeicherung in Minuten, d. h. der Zeitpunkt, zu dem eine Lizenz im Lizenzspeicher des Kunden zwischengespeichert werden kann, nachdem die Lizenz vom Server ausgestellt wurde. Der Wert muss nicht negativ sein. Geben Sie <span class="codeph"> -l 0 </span> an, um anzugeben, dass Lizenzzwischenspeicherung nicht zulässig ist. Verwenden Sie <span class="codeph"> -l </span> ohne Angabe einer Anzahl von Minuten für die unbegrenzte Lizenzzwischenspeicherung. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -ldate </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Enddatum der Lizenzzwischenspeicherung (das Datum, nach dem Lizenzen nicht im Lizenzspeicher des Kunden zwischengespeichert werden können, nachdem die Lizenz vom Server erteilt wurde). Geben Sie als <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span><i class="+ topic/ph hi-d/i "> oder </i>als<i class="+ topic/ph hi-d/i "> yyyy-mm-dd-h24:min:sec </i> <span class="+ topic/ph pr-d/codeph codeph"> </span>. Beispiel: 2008-12-1 oder 2008-12-1-00:00:00 Uhr für Mitternacht am 1. Dezember 2008. Verwenden Sie <span class="codeph"> -l </span> ohne Angabe einer Anzahl von Minuten für die unbegrenzte Lizenzzwischenspeicherung. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Der Authentifizierungs-Namensraum. Falls angegeben, muss sich der Client mit einem Benutzernamen und einem Kennwort authentifizieren, das von der angegebenen Behörde ausgegeben wird. Diese Option kann nicht mit <span class="codeph"> -x verwendet werden </span>. Updates sind nicht zulässig. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Anonymen Zugriff zulassen. Diese Option kann nicht mit <span class="codeph"> -authNS verwendet werden </span>. Updates sind nicht zulässig. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId </span>[: <span class="+ topic/ph pr-d/codeph codeph"> appId </span>[:[ <span class="+ topic/ph pr-d/codeph codeph"> min </span>]:[ <span class="+ topic/ph pr-d/codeph codeph"> max </span>]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Eine Zulassungsliste von AIR-Anwendungen, die geschützte Inhalte abspielen dürfen. Verwenden Sie diese Option, um einzuschränken, welche Herausgeber, Anwendungen und Versionen auf Inhalte zugreifen dürfen, die mit dieser Richtlinie geschützt sind. </p> <p class="- topic/p ">Wenn <i class="+ topic/ph hi-d/i ">appId</i> nicht angegeben ist, sind alle Anwendungen für <i class="+ topic/ph hi-d/i ">pubId</i> des Herausgebers zulässig. </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Min</i> - und <i class="+ topic/ph hi-d/i ">Max</i> -Versionsnummern sind optional. </p> <p class="- topic/p ">Es können mehrere <span class="codeph"> - air- </span> Optionen angegeben werden, um mehrere Anwendungen zuzulassen. Wenn keine AIR- oder SWF-Anwendungen angegeben sind, können alle Anwendungen auf diesen Inhalt zugreifen. Verwenden Sie während einer Aktualisierung -air ohne die restlichen Argumente, um alle Einträge aus der Liste zu entfernen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmBlacklist name </span> / <i class="+ topic/ph hi-d/i ">value</i><span class="+ topic/ph pr-d/codeph codeph"> - </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> Paare </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die DRM-Clients haben den Zugriff auf geschützte Inhalte eingeschränkt. Der Wert besteht aus durch Kommas getrennten Paaren "name:value"mit folgendem Format: </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | release= stringValue </span> </p> <p class="- topic/p ">Beispiel: <span class="codeph"> os=Win,release=2.0.1 </span>. Verwenden Sie während eines Updates <span class="codeph"> -drmBlacklist </span> ohne die restlichen Argumente, um alle Einträge aus der Liste zu entfernen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, dass DRM-Clients über das angegebene Mindestsicherheitsniveau verfügen müssen, um auf geschützte Inhalte zugreifen zu können. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opAnalog NO_PROTECTION | USE_IF_AVAILABLE | ERFORDERLICH | NO_PLAYBACK | ACP_REQUIRED | CGMS-A_REQUIRED | USE_ACP_IF_AVAILABLE | USE_CGMS-A_IF_AVAILABLE </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Analoge Ausgabeschutzeinschränkungen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opDigital NO_PROTECTION | USE_IF_AVAILABLE | ERFORDERLICH | NO_PLAYBACK </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Einschränkungen des digitalen Ausgabeschutzes. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeBlacklist name </span> / <i class="+ topic/ph hi-d/i ">value</i><span class="+ topic/ph pr-d/codeph codeph"> - </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> Paare </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Anwendungslaufzeiten beschränkten sich auf den Zugriff auf geschützten Inhalt. Der Wert besteht aus durch Kommas getrennten Paaren "name:value"mit folgendem Format: </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | Antrag | release= stringValue </span> </p> <p class="- topic/p ">Beispiel: <span class="codeph"> os=Win,release=2.0.1,application=AIR </span>. Verwenden Sie während eines Updates <span class="codeph"> -runtimeBlacklist </span> ohne die restlichen Argumente, um alle Einträge aus der Liste zu entfernen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, dass die Anwendungs-Laufzeitumgebungen über das angegebene Mindestsicherheitsniveau verfügen müssen, um auf geschützten Inhalt zugreifen zu können. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file= swf_file </span>, <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Eine Zulassungsliste von SWF-Anwendungen, die geschützte Inhalte abspielen dürfen. Es können mehrere SWF-Optionen angegeben werden, um mehrere Anwendungen zuzulassen. Wenn keine AIR- oder SWF-Anwendungen angegeben sind, können alle Anwendungen auf diesen Inhalt zugreifen. Verwenden Sie während einer Aktualisierung -swf ohne die restlichen Argumente, um alle Einträge aus der Liste zu entfernen. Um eine SWF nach ihrem Hashwert zu identifizieren, geben Sie die SWF-Datei an, für die der Hash berechnet werden soll, und geben Sie die maximale Zeit an, die für den Abschluss der SWF-Überprüfung zulässig ist (in Sekunden). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name= value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt benutzerdefinierte Schlüssel/Werte an, die der Richtlinie hinzugefügt werden sollen. Es können mehrere <span class="codeph"> -k- </span> Optionen angegeben werden. Verwenden Sie während der Aktualisierung <span class="codeph"> -k </span> ohne die restlichen Argumente, um alle Eigenschaften zu entfernen. Die Interpretation oder Verarbeitung dieser Daten hängt vollständig von der Implementierung des Adobe Access-Lizenzservers ab. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name= value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fügt eine benutzerdefinierte Eigenschaft hinzu, die in der für jeden Client generierten Lizenz angezeigt wird. Es können mehrere <span class="codeph"> -p- </span> Optionen angegeben werden, um mehrere Eigenschaften hinzuzufügen. Verwenden Sie während einer Aktualisierung <span class="codeph"> -p </span> ohne die restlichen Argumente, um alle Eigenschaften zu entfernen. Die Interpretation oder Verarbeitung dieser Daten liegt vollständig bei der Implementierung der Client-Anwendung. </p> </td> 
  </tr> 
 </tbody> 
</table>

