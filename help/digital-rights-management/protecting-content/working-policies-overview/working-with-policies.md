---
title: Übersicht über DRM-Richtlinien verwenden
description: Übersicht über DRM-Richtlinien verwenden
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Übersicht {#working-with-drm-policies-overview}

Inhaltsanbieter können DRM-Richtlinien mithilfe des Primetime DRM SDK auf Mediendateien anwenden. Administratoren können dann DRM-Richtlinien mithilfe von Policy Management-APIs erstellen, Details dazu anzeigen und aktualisieren.

A *`DRM policy`* ist eine Sammlung von Informationen, die Sicherheitseinstellungen, Authentifizierungsanforderungen und Verwendungsrechte enthalten. Die Richtlinie definiert, wie Benutzer Inhalte anzeigen können. DRM-Richtlinien, Verschlüsselung und Signatur ermöglichen es Inhaltsanbietern, die Kontrolle über ihren Inhalt zu behalten, unabhängig davon, wie weit der Inhalt verteilt ist.

Eine DRM-Richtlinie dient als Vorlage, die der Lizenzserver bei der Erstellung einer Lizenz verwendet. Ein Client kann auch auf die DRM-Richtlinie verweisen, bevor er eine Lizenz anfordert, um festzustellen, ob der Client den Benutzer zur Authentifizierung auffordern muss, bevor er eine Lizenzanfrage an den Server sendet.

Sie können geschützte Inhalte über einen Adobe-Flash Media Server oder einen HTTP-Server bereitstellen. Benutzer können geschützte Inhalte in benutzerdefinierten Playern herunterladen und abspielen, die mit dem Primetime DRM SDK erstellt wurden.

Eine DRM-Richtlinie gibt eine oder mehrere Rechte an, die dem Kunden gewährt werden. Normalerweise umfasst eine DRM-Richtlinie mindestens die *`Play Right`*. Sie können auch mehrere Wiedergabeberechtigungen mit jeweils unterschiedlichen Einschränkungen angeben. Wenn der Client eine Lizenz mit mehreren Wiedergabedokumenten erhält, verwendet er die erste Lizenz, die alle Einschränkungen erfüllt. Sie können beispielsweise verschiedene Einstellungen für den Ausgabeschutz auf verschiedenen Plattformen erzwingen.

Siehe `CreatePolicyWithOutputProtection.java` in den Befehlszeilenwerkzeugen für die Referenzimplementierung [!DNL samples] -Verzeichnis für Beispielcode, das dieses Beispiel veranschaulicht.

Sie können die folgenden Aufgaben mit den Primetime DRM-Richtlinienmanagement-APIs ausführen:

* Richtlinien erstellen und aktualisieren
* Details zur DRM-Richtlinie anzeigen
* Listen zur Aktualisierung von DRM-Richtlinien verwalten

Siehe *Primetime-DRM-API-Referenz* für Details zur Java-API.

Siehe *Verwenden der Primetime-DRM-Referenzimplementierungen* Handbuch für Informationen zum Primetime DRM Policy Manager.
