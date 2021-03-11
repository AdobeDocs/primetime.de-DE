---
description: Betriebssysteme und Anwendungsserver sind in Ihrer Adobe Primetime DRM-Lösung enthalten.
title: Herstellerspezifische Sicherheitsinformationen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# Herstellerspezifische Sicherheitsinformationen{#vendor-specific-security-information}

Betriebssysteme und Anwendungsserver sind in Ihrer Adobe Primetime DRM-Lösung enthalten.

Informationen zur herstellerspezifischen Sicherheit für Ihr Betriebssystem und Ihren Anwendungsserver finden Sie unter Verwenden des Adobe Primetime DRM-Schlüsselservers.

## Informationen zur Betriebssystemsicherheit {#section_53CAD802FCA54C4D8CE0C4E1B3045E52}

Beim Schützen des Betriebssystems müssen Sie die vom Betriebssystemhersteller beschriebenen Maßnahmen implementieren.

Hier einige der Maßnahmen:

* Definieren und Steuern von Benutzern, Rollen und Berechtigungen
* Überwachungsprotokolle und Prüfpfade
* Entfernen unnötiger Dienste und Anwendungen
* Sichern von Dateien

Im Folgenden finden Sie einige Informationen zu den von Adobe Primetime DRM unterstützten Betriebssystemen:

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
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Sicherheits-Patches </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Es besteht ein erhöhtes Risiko, dass ein nicht autorisierter Benutzer Zugriff auf den Anwendungsserver erhält, wenn vom Anbieter bereitgestellte Sicherheits-Patches und -Aktualisierungen nicht zeitnah angewendet werden. </p> <p>Hinweis:  Stellen Sie sicher, dass Sie Sicherheits-Patches testen, bevor Sie sie auf Produktionsserver anwenden. </p> <p class="- topic/p ">Sie müssen Richtlinien und Verfahren erstellen, um Patches regelmäßig zu suchen und zu installieren. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Virenschutzsoftware </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Virenscanner können infizierte Dateien identifizieren, indem sie nach einer Signatur oder einem ungewöhnlichen Verhalten suchen. </p> <p>Scanner speichern ihre Virensignaturen in einer Datei, die normalerweise auf der lokalen Festplatte gespeichert wird. Neue Viren werden häufig entdeckt, daher müssen Sie sicherstellen, dass diese Datei regelmäßig aktualisiert wird. Auf diese Weise können Virenscanner immer alle aktuellen Viren identifizieren. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Network Time Protocol (NTP) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Für einen ordnungsgemäßen Betrieb und eine forensische Analyse sollten Sie auf den Primetime DRM-Servern und -Packagern die richtige Zeit behalten. Verwenden Sie eine sichere Version von NTP, um die Primetime DRM-Zeit auf allen Systemen zu synchronisieren, die mit dem Internet verbunden sind. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Informationen zur Sicherheit des Anwendungsservers {#section_22986936F1A547CEAB2D97E9E9D4825C}

Beim Schützen des Anwendungsservers müssen Sie die vom Serverhersteller beschriebenen Maßnahmen implementieren.

Hier einige dieser Maßnahmen:

* Verwenden eines nicht offensichtlichen Benutzernamens des Administrators
* Deaktivieren unnötiger Dienste
* Schützen des Konsolenmanagers
* Aktivieren sicherer Cookies
* Schließen nicht benötigter Anschlüsse
* Eingrenzen von Verwaltungsschnittstellen nach IP-Adressen oder Domänen
* Verwenden des Java™ Security Managers

