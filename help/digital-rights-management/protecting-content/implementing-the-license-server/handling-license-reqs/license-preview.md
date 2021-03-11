---
title: Vorschau der Lizenz
description: Vorschau der Lizenz
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# Vorschau der Lizenz{#license-preview}

Der Client kann eine Lizenzanforderung senden, d. h., die Vorschau kann eine Vorschau durchführen, bevor der Benutzer aufgefordert wird, den  zu erwerben, um festzustellen, ob der Computer des Benutzers tatsächlich alle für die Wiedergabe erforderlichen Kriterien erfüllt.

*`License preview`* bezieht sich auf die Fähigkeit eines Kunden, die Lizenz zu Vorschau (um zu sehen, welche Rechte die Lizenz zulässt), im Gegensatz zur Vorschau des Inhalts (Anzeige eines kleinen Teils des Inhalts, bevor entschieden wird, zu kaufen). Einige der Parameter, die für die einzelnen Computer eindeutig sind, sind: verfügbare Ausgaben und deren Schutzstatus, die verfügbare Laufzeit-/DRM-Version und die DRM-Client-Sicherheitsstufe. Der Lizenzmodus ermöglicht es dem Laufzeit-/DRM-Vorschau-Client, die Geschäftslogik des Lizenzservers zu testen und dem Benutzer Informationen zurückzugeben, damit er eine fundierte Entscheidung treffen kann. So kann der Kunde sehen, wie eine gültige Lizenz aussieht, aber nicht tatsächlich den Schlüssel zum Entschlüsseln des Inhalts erhalten. Die Lizenzunterstützung ist optional und nur erforderlich, wenn Sie einen benutzerdefinierten Client implementieren, der diese Vorschau verwendet.

Rufen Sie `LicenseRequestMessage.getRequestPhase()`auf und vergleichen Sie diese mit `LicenseRequestMessage.RequestPhase.Acquire`, um festzustellen, ob der Client eine Anforderung zur Vorschau oder Lizenzerteilung gesendet hat.
