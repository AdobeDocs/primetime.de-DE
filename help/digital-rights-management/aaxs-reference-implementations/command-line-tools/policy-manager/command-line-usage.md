---
title: Befehlszeilenverwendung
description: Befehlszeilenverwendung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# Befehlszeilenverwendung {#command-line-usage}

Bevor Sie Policy Manager verwenden, stellen Sie sicher, dass Sie die unter Anforderungen aufgelisteten Anforderungen erfüllen.

Der Richtlinien-Manager befindet sich im [!DNL \Reference Implementation\Command Line Tools] auf der DVD. Verwenden Sie die folgende Syntax, um das Tool auszuführen:

```
java -jar AdobePolicyManager.jar  
<i class="+ topic ph hi-d="" i "="">
  command filename [options] 
</i class="+ topic>
```

Die folgende Tabelle enthält Beschreibungen der Befehlszeilenaktionen, die in der obigen Syntax angezeigt werden:

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt den Speicherort der Konfigurationsdatei an. Wenn diese Option nicht verwendet wird, sucht der Policy Manager nach <span class="filepath"> flashaccessHools.properties </span> im Arbeitsverzeichnis. Die in der Befehlszeile angegebenen Optionen haben Vorrang vor den Optionen in der Konfigurationsdatei. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Wenn die Zieldatei bereits vorhanden ist, überschreiben Sie sie ohne Eingabeaufforderung. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noconsole </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fragen Sie nicht, ob die Zieldatei überschrieben werden soll. Wenn die Zieldatei bereits vorhanden ist und <span class="codeph"> -o </span> nicht festgelegt ist, wird ein Fehler zurückgegeben. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -root </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, dass die Richtlinie über eine Stammlizenz verfügt. Für Aktualisierungen nicht zulässig. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e date </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Datum, vor dem die Lizenzen gültig sein werden. Angeben als <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> oder <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:Sek </span>. Beispiel: 12.1.2008 oder 2008-12-1-00:00:00 für Mitternacht am 1. Dezember 2008. Der Wert muss größer sein als der Wert von <span class="codeph"> -s </span>, falls vorhanden. Diese Option kann nicht mit <span class="codeph"> -r </span>. Um das Enddatum beim Aktualisieren einer Richtlinie zu entfernen, verwenden Sie <span class="codeph"> -e </span> ohne Angabe eines Datums. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r Minuten </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Dauer (Minuten), in der durch diese Richtlinie geschützte Inhalte gültig sind, beginnend mit dem Schutz des Inhalts mit dem Packager. Der Wert darf nicht negativ sein. Diese Option kann nicht mit <span class="codeph"> -e </span>. Verwenden Sie zum Entfernen der Dauer beim Aktualisieren einer Richtlinie <span class="codeph"> -r </span> ohne Angabe einer Anzahl von Minuten. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s date </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Datum, nach dem die Lizenzen gültig sind. Angeben als <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> oder <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:Sek </span>. Beispiel: 12.1.2008 oder 2008-12-1-00:00:00 für Mitternacht am 1. Dezember 2008. Der Wert muss kleiner sein als der Wert von <span class="codeph"> -e </span>, falls vorhanden. Diese Option kann nicht mit <span class="codeph"> -r </span>. Um das Startdatum beim Aktualisieren einer Richtlinie zu entfernen, verwenden Sie <span class="codeph"> -s </span> ohne Angabe eines Datums. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w Minuten </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Wiedergabefenster (die Anzahl der Minuten, in denen der Inhalt angezeigt werden kann, beginnend mit der ersten Wiedergabe). Wenn diese Option nicht angegeben ist oder wenn <span class="codeph"> -w </span> verwendet wird, ohne die Anzahl der Minuten anzugeben, gibt es keine Beschränkung für das Wiedergabefenster. Der Wert darf nicht negativ sein. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l Minuten </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Lizenz-Caching-Dauer in Minuten. Dies ist der Zeitpunkt, zu dem eine Lizenz im Lizenzspeicher des Kunden zwischengespeichert werden darf, nachdem die Lizenz vom Server ausgestellt wurde. Der Wert darf nicht negativ sein. Angeben <span class="codeph"> -l 0 </span> um anzugeben, dass Lizenzzwischenspeicherung nicht zulässig ist. Verwendung <span class="codeph"> -l </span> ohne Angabe einer Anzahl von Minuten für unbegrenzte Lizenzzwischenspeicherung. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -ldate </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Das Enddatum der Lizenzzwischenspeicherung (das Datum, nach dem Lizenzen nicht im Lizenzspeicher des Kunden zwischengespeichert werden dürfen, nachdem die Lizenz vom Server erteilt wurde). Angeben als <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span><i class="+ topic/ph hi-d/i "> </i>oder<i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:Sek </span>. Beispiel: 12.1.2008 oder 2008-12-1-00:00:00 für Mitternacht am 1. Dezember 2008. Verwendung <span class="codeph"> -l </span> ohne Angabe einer Anzahl von Minuten für unbegrenzte Lizenzzwischenspeicherung. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Der Authentifizierungs-Namespace. Falls angegeben, sollte sich der Client mit einem Benutzernamen und einem Kennwort authentifizieren, das von der angegebenen Behörde ausgegeben wurde. Diese Option kann nicht mit <span class="codeph"> -x </span>. Es ist nicht für Aktualisierungen zulässig. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Anonymen Zugriff zulassen. Diese Option kann nicht mit <span class="codeph"> -authNS </span>. Es ist nicht für Aktualisierungen zulässig. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId </span>[: <span class="+ topic/ph pr-d/codeph codeph"> appId </span>[:[ <span class="+ topic/ph pr-d/codeph codeph"> min </span>]:[ <span class="+ topic/ph pr-d/codeph codeph"> max </span>]]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Eine Zulassungsliste von AIR-Anwendungen, die geschützte Inhalte abspielen dürfen. Verwenden Sie dies, um zu beschränken, welche Herausgeber, Anwendungen und Versionen auf Inhalte zugreifen können, die mit dieser Richtlinie geschützt sind. </p> <p class="- topic/p ">Wenn <i class="+ topic/ph hi-d/i ">appId</i> nicht angegeben ist, werden alle Anwendungen für Herausgeber <i class="+ topic/ph hi-d/i ">pubId</i> sind erlaubt. </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">min</i> und <i class="+ topic/ph hi-d/i ">max</i> Versionsnummern sind optional. </p> <p class="- topic/p ">Mehrere <span class="codeph"> - Luft </span> -Optionen angegeben werden, um mehrere Anwendungen zuzulassen. Wenn keine AIR- oder SWF-Anwendungen angegeben sind, können alle Anwendungen auf diesen Inhalt zugreifen. Verwenden Sie während einer Aktualisierung -air ohne die verbleibenden Argumente, um alle Einträge aus der Liste zu entfernen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmBlacklist name </span> <i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> value </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> Paare </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die DRM-Clients haben den Zugriff auf geschützte Inhalte eingeschränkt. Der Wert besteht aus kommagetrennten Name-Wert-Paaren mit folgendem Format: </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | release= stringValue </span> </p> <p class="- topic/p ">Beispiel: <span class="codeph"> os=Win,release=2.0.1 </span>. Verwenden Sie während einer Aktualisierung <span class="codeph"> -drmBlacklist </span> ohne die verbleibenden Argumente, um alle Einträge aus der Liste zu entfernen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, dass DRM-Clients über die angegebene Mindestsicherheitsstufe verfügen müssen, um auf geschützte Inhalte zugreifen zu können. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opAnalog NO_PROTECTION | USE_IF_AVAILABLE | ERFORDERLICH | NO_PLAYBACK | AKP_REQUIRED | CGMS-A_REQUIRED | USE_ACP_IF_AVAILABLE | USE_CGMS-A_IF_AVAILABLE </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Analog-Ausgabeschutzeinschränkungen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opDigital NO_PROTECTION | USE_IF_AVAILABLE | ERFORDERLICH | NO_PLAYBACK </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Einschränkungen hinsichtlich des digitalen Ausgabeschutzes. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeBlacklist-Name </span> <i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> value </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> Paare </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Anwendungslaufzeiten sind vom Zugriff auf geschützte Inhalte eingeschränkt. Der Wert besteht aus kommagetrennten Name-Wert-Paaren mit folgendem Format: </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | Anwendung | release= stringValue </span> </p> <p class="- topic/p ">Beispiel: <span class="codeph"> os=Win,release=2.0.1,application=AIR </span>. Verwenden Sie während einer Aktualisierung <span class="codeph"> -runtimeBlacklist </span> ohne die verbleibenden Argumente, um alle Einträge aus der Liste zu entfernen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt an, dass die Anwendungslaufzeiten über die angegebene Mindestsicherheitsstufe verfügen müssen, um auf geschützten Inhalt zugreifen zu können. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file= swf_file </span>, <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Eine Zulassungsliste von SWF-Applikationen, die geschützte Inhalte abspielen können. Es können mehrere -swf-Optionen angegeben werden, um mehrere Anwendungen zuzulassen. Wenn keine AIR- oder SWF-Anwendungen angegeben sind, können alle Anwendungen auf diesen Inhalt zugreifen. Verwenden Sie während einer Aktualisierung -swf ohne die verbleibenden Argumente, um alle Einträge aus der Liste zu entfernen. Um eine SWF anhand ihres Hash-Werts zu identifizieren, geben Sie die SWF-Datei an, für die der Hash berechnet werden soll, und geben Sie die maximale Zeit an, um die SWF-Verifizierung abzuschließen (in Sekunden). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name= value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gibt benutzerdefinierte Schlüssel/Werte an, die der Richtlinie hinzugefügt werden sollen. Mehrere <span class="codeph"> -k </span> -Optionen angegeben werden. Verwenden Sie während der Aktualisierung <span class="codeph"> -k </span> ohne die verbleibenden Argumente, um alle Eigenschaften zu entfernen. Die Interpretation oder Handhabung dieser Daten obliegt der Implementierung des Adobe Access License Servers. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name= value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fügt eine benutzerdefinierte Eigenschaft hinzu, die in der für jeden Client generierten Lizenz angezeigt wird. Mehrere <span class="codeph"> -p </span> -Optionen angegeben werden, um mehrere Eigenschaften hinzuzufügen. Verwenden Sie während einer Aktualisierung <span class="codeph"> -p </span> ohne die verbleibenden Argumente, um alle Eigenschaften zu entfernen. Die Interpretation oder Handhabung dieser Daten obliegt der Implementierung der Client-Anwendung. </p> </td> 
  </tr> 
 </tbody> 
</table>
