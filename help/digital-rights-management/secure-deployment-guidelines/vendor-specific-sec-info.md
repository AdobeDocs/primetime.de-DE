---
description: Betriebssysteme und Anwendungsserver sind in Ihrer Adobe Primetime DRM-Lösung enthalten.
title: Anbieterspezifische Sicherheitsinformationen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# Anbieterspezifische Sicherheitsinformationen{#vendor-specific-security-information}

Betriebssysteme und Anwendungsserver sind in Ihrer Adobe Primetime DRM-Lösung enthalten.

Informationen zu herstellerspezifischen Sicherheitsinformationen für Ihr Betriebssystem und Ihren Anwendungsserver finden Sie unter Verwenden des Adobe Primetime DRM Key Servers .

## Informationen zur Betriebssystemsicherheit {#section_53CAD802FCA54C4D8CE0C4E1B3045E52}

Beim Schützen Ihres Betriebssystems müssen Sie die von Ihrem Betriebssystemanbieter beschriebenen Maßnahmen implementieren.

Im Folgenden finden Sie einige der Kennzahlen:

* Definieren und Steuern von Benutzern, Rollen und Berechtigungen
* Überwachungsprotokolle und Prüfprotokolle
* Entfernen unnötiger Dienste und Anwendungen
* Sichern von Dateien

Im Folgenden finden Sie einige Informationen zu den Betriebssystemen, die von Adobe Primetime DRM unterstützt werden:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_ugl_kjz_n4"> 
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

Im Folgenden finden Sie einige Informationen zu Ansätzen zur Minimierung von Sicherheitslücken im Betriebssystem:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_whl_kjz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Posten </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Sicherheitspatches </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Es besteht ein erhöhtes Risiko, dass ein nicht autorisierter Benutzer Zugriff auf den Anwendungsserver erhält, wenn Sicherheits-Patches und -Upgrades des des Anbieters nicht zeitnah angewendet werden. </p> <p>Hinweis: Stellen Sie sicher, dass Sie Sicherheits-Patches testen, bevor Sie sie auf Produktionsserver anwenden. </p> <p class="- topic/p ">Sie müssen Richtlinien und Verfahren erstellen, um regelmäßig nach Patches zu suchen und diese zu installieren. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Virenschutzsoftware </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Virenscanner können infizierte Dateien identifizieren, indem sie nach einer Signatur oder einem ungewöhnlichen Verhalten suchen. </p> <p>Scanner speichern ihre Virensignaturen in einer Datei, die normalerweise auf der lokalen Festplatte gespeichert wird. Neue Viren werden häufig entdeckt, daher müssen Sie sicherstellen, dass diese Datei regelmäßig aktualisiert wird. Auf diese Weise können Virenscanner immer alle aktuellen Viren identifizieren. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Network Time Protocol (NTP) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Für einen ordnungsgemäßen Betrieb und eine forensische Analyse sollten Sie auf Primetime-DRM-Servern und -Packagern eine genaue Zeit haben. Verwenden Sie eine sichere Version von NTP, um die Primetime DRM-Zeit auf allen mit dem Internet verbundenen Systemen zu synchronisieren. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Sicherheitsinformationen für den Anwendungsserver {#section_22986936F1A547CEAB2D97E9E9D4825C}

Beim Schützen des Anwendungsservers müssen Sie die von Ihrem Serveranbieter beschriebenen Maßnahmen implementieren.

Im Folgenden finden Sie einige dieser Kennzahlen:

* Verwenden eines nicht offensichtlichen Benutzernamens für Administratoren
* Deaktivieren unnötiger Dienste
* Schützen des Konsolenmanagers
* Sichere Cookies aktivieren
* Schließen nicht benötigter Ports
* Grenzen von Verwaltungsschnittstellen nach IP-Adressen oder Domänen
* Verwenden von Java™ Security Manager
