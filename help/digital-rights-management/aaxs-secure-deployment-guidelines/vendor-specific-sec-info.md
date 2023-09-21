---
title: Anbieterspezifische Sicherheitsinformationen
description: Anbieterspezifische Sicherheitsinformationen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Anbieterspezifische Sicherheitsinformationen{#vendor-specific-security-information}

Dieser Abschnitt enthält sicherheitsbezogene Informationen zu Betriebssystemen und Anwendungsservern, die in Ihre Adobe Access-Lösung integriert sind.

Verwenden Sie die in diesem Abschnitt angegebenen Links, um herstellerspezifische Sicherheitsinformationen für Ihr Betriebssystem und Ihren Anwendungsserver zu finden.

## Informationen zur Betriebssystemsicherheit {#section-B6D9D6CEA7CC42A8A20346600EFB5E4E}

Führen Sie beim Schützen Ihres Betriebssystems die von Ihrem Betriebssystemanbieter beschriebenen Maßnahmen sorgfältig durch, einschließlich der folgenden:

* Definieren und Steuern von Benutzern, Rollen und Berechtigungen
* Überwachungsprotokolle und Prüfprotokolle
* Entfernen unnötiger Dienste und Anwendungen
* Sichern von Dateien

Sicherheitsinformationen zu von Adobe Access unterstützten Betriebssystemen finden Sie in den nachfolgend aufgeführten Ressourcen.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-ugl-kjz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Betriebssystem </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Sicherheitsressource </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Microsoft® Windows Server® 2008 Enterprise oder Standard Edition </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Windows Server 2008 Security Guide</i> </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Red Hat® Enterprise Linux® 5.4, 5.5 und 5.6. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Red Hat Enterprise Linux 5 Security Guide</i> </p> </td> 
  </tr> 
 </tbody> 
</table>

In der folgenden Tabelle werden einige potenzielle Ansätze zum Minimieren von Sicherheitslücken im Betriebssystem beschrieben.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-whl-kjz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Posten </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Sicherheitspatches </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Es besteht ein erhöhtes Risiko, dass ein nicht autorisierter Benutzer Zugriff auf den Anwendungsserver erhält, wenn Sicherheits-Patches und -Upgrades des des Anbieters nicht zeitnah angewendet werden. Testen Sie Sicherheits-Patches, bevor Sie sie auf Produktionsserver anwenden. </p> <p class="- topic/p ">Erstellen Sie außerdem Richtlinien und Verfahren, um regelmäßig nach Patches zu suchen und diese zu installieren. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Virenschutzsoftware </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Virenscanner können infizierte Dateien identifizieren, indem sie nach einer Signatur suchen oder auf ungewöhnliches Verhalten achten. Scanner speichern ihre Virensignaturen in einer Datei, die normalerweise auf der lokalen Festplatte gespeichert wird. Da häufig neue Viren entdeckt werden, müssen Sie diese Datei häufig aktualisieren, damit der Virenscanner alle aktuellen Viren erkennt. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Network Time Protocol (NTP) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Halten Sie sowohl für den ordnungsgemäßen Betrieb als auch für die forensische Analyse genaue Zeit auf Adobe Access-Servern und Adobe Access-Packagern bereit. Verwenden Sie eine sichere Version von NTP, um die Zeit auf allen mit dem Internet verbundenen Systemen zu synchronisieren. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Sicherheitsinformationen für den Anwendungsserver {#section-EBB4EF371CFF4A848694CC240B23D404}

Beim Schützen des Anwendungsservers müssen Sie die vom Serveranbieter beschriebenen Maßnahmen implementieren, einschließlich der folgenden:

* Verwenden eines nicht offensichtlichen Benutzernamens für Administratoren
* Deaktivieren unnötiger Dienste
* Schützen des Konsolenmanagers
* Sichere Cookies aktivieren
* Schließen nicht benötigter Ports
* Grenzen von Verwaltungsschnittstellen nach IP-Adressen oder Domänen
* Verwenden von Java™ Security Manager
