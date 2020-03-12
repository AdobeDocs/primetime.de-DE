---
seo-title: Arbeiten mit DRM-Richtlinien - Übersicht
title: Arbeiten mit DRM-Richtlinien - Übersicht
uuid: 32423448-013c-4183-bea8-e14b6690abdb
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Übersicht {#working-with-drm-policies-overview}

Content Provider können DRM-Richtlinien mit dem Primetime DRM SDK auf Mediendateien anwenden. Administratoren können dann DRM-Richtlinien mithilfe von Richtlinien-Management-APIs erstellen, Ansichten erstellen und aktualisieren.

Eine *`DRM policy`* Sammlung von Informationen, die Sicherheitseinstellungen, Authentifizierungsanforderungen und Verwendungsrechte enthalten. Die Richtlinie definiert, wie Ansichten von Inhalten für Benutzer möglich sind. DRM-Richtlinien, Verschlüsselung und Unterzeichnung ermöglichen es Inhaltsanbietern, die Kontrolle über ihre Inhalte unabhängig von der Verteilung der Inhalte zu behalten.

Eine DRM-Richtlinie dient als Vorlage, die der Lizenzserver beim Generieren einer Lizenz verwendet. Ein Client kann auch auf die DRM-Richtlinie verweisen, bevor er eine Lizenz anfordert, um festzustellen, ob der Client den Benutzer zur Authentifizierung auffordern muss, bevor er eine Lizenzanforderung an den Server sendet.

Sie können geschützte Inhalte mit Adobe Flash Media Server oder einem HTTP-Server bereitstellen. Benutzer können geschützte Inhalte in benutzerdefinierten Playern herunterladen und abspielen, die mit dem Primetime DRM SDK erstellt wurden.

Eine DRM-Richtlinie gibt eine oder mehrere Rechte an, die dem Kunden gewährt werden. Normalerweise enthält eine DRM-Richtlinie mindestens die *`Play Right`*. Sie können auch mehrere Wiedergaberechte mit jeweils unterschiedlichen Einschränkungen angeben. Wenn der Client eine Lizenz mit mehreren Abspielrechten erhält, verwendet er die erste Lizenz, die alle Einschränkungen erfüllt. Sie können beispielsweise verschiedene Ausgabeschutzeinstellungen auf verschiedenen Plattformen erzwingen.

Beispielcode, der dieses Beispiel illustriert, finden Sie `CreatePolicyWithOutputProtection.java` im [!DNL samples] Verzeichnis der Referenzimplementierungs-Befehlszeilenwerkzeuge.

Sie können die folgenden Aufgaben mit den Primetime DRM Policy Management APIs durchführen:

* Richtlinien erstellen und aktualisieren
* Informationen zur DRM-Politik der Ansicht
* Listen zur Aktualisierung von DRM-Richtlinien verwalten

Einzelheiten zur Java-API finden Sie in der *Primetime DRM API-Referenz* .

Informationen zum DRM-Policy-Manager von Primetime finden Sie im Handbuch *Verwenden der Primetime-DRM-Referenzimplementierungen* .
