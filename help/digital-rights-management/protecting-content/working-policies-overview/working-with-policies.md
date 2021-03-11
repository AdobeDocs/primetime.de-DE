---
title: Arbeiten mit DRM-Richtlinien - Übersicht
description: Arbeiten mit DRM-Richtlinien - Übersicht
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Übersicht {#working-with-drm-policies-overview}

Content Provider können DRM-Richtlinien mit dem Primetime DRM SDK auf Mediendateien anwenden. Administratoren können dann DRM-Richtlinien mithilfe von Richtlinien-Management-APIs erstellen, Ansichten erstellen und aktualisieren.

Ein *`DRM policy`* ist eine Sammlung von Informationen mit Sicherheitseinstellungen, Authentifizierungsanforderungen und Verwendungsrechten. Die Richtlinie definiert, wie Ansichten von Inhalten für Benutzer möglich sind. DRM-Richtlinien, Verschlüsselung und Unterzeichnung ermöglichen es Inhaltsanbietern, die Kontrolle über ihre Inhalte unabhängig von der Verteilung der Inhalte zu behalten.

Eine DRM-Richtlinie dient als Vorlage, die der Lizenzserver beim Generieren einer Lizenz verwendet. Ein Client kann auch auf die DRM-Richtlinie verweisen, bevor er eine Lizenz anfordert, um festzustellen, ob der Client den Benutzer zur Authentifizierung auffordern muss, bevor er eine Lizenzanforderung an den Server sendet.

Sie können geschützte Inhalte mit Adobe Flash Media Server oder einem HTTP-Server bereitstellen. Benutzer können geschützte Inhalte in benutzerdefinierten Playern herunterladen und abspielen, die mit dem Primetime DRM SDK erstellt wurden.

Eine DRM-Richtlinie gibt eine oder mehrere Rechte an, die dem Kunden gewährt werden. Normalerweise enthält eine DRM-Richtlinie mindestens das *`Play Right`*. Sie können auch mehrere Wiedergaberechte mit jeweils unterschiedlichen Einschränkungen angeben. Wenn der Client eine Lizenz mit mehreren Abspielrechten erhält, verwendet er die erste Lizenz, die alle Einschränkungen erfüllt. Sie können beispielsweise verschiedene Ausgabeschutzeinstellungen auf verschiedenen Plattformen erzwingen.

Beispielcode, der dieses Beispiel illustriert, finden Sie unter `CreatePolicyWithOutputProtection.java` im Verzeichnis der Referenzimplementierungs-Befehlszeilenwerkzeuge [!DNL samples].

Sie können die folgenden Aufgaben mit den Primetime DRM Policy Management APIs durchführen:

* Richtlinien erstellen und aktualisieren
* Informationen zur DRM-Politik der Ansicht
* Listen zur Aktualisierung von DRM-Richtlinien verwalten

Weitere Informationen zur Java-API finden Sie unter *Primetime DRM-API-Referenz*.

Informationen zum DRM Policy Manager von Primetime finden Sie im Handbuch *Verwenden der Primetime-DRM-Referenzimplementierungen*.
