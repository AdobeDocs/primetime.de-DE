---
seo-title: Vorschau der Lizenz
title: Vorschau der Lizenz
uuid: 3069aa16-5bf3-4af6-801c-ad823530d7eb
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Vorschau der Lizenz{#license-preview}

Der Client kann eine Lizenzanforderung senden, d. h., die Vorschau kann eine Vorschau durchführen, bevor der Benutzer aufgefordert wird, den  zu erwerben, um festzustellen, ob der Computer des Benutzers tatsächlich alle für die Wiedergabe erforderlichen Kriterien erfüllt.

*`License preview`* bezieht sich auf die Fähigkeit eines Kunden, die Lizenz zu Vorschau (um zu sehen, welche Rechte die Lizenz zulässt), im Gegensatz zur Vorschau des Inhalts (Anzeige eines kleinen Teils des Inhalts, bevor entschieden wird, zu kaufen). Einige der Parameter, die für die einzelnen Computer eindeutig sind, sind: verfügbare Ausgaben und deren Schutzstatus, die verfügbare Laufzeit-/DRM-Version und die DRM-Client-Sicherheitsstufe. Der Lizenzmodus ermöglicht es dem Laufzeit-/DRM-Vorschau-Client, die Geschäftslogik des Lizenzservers zu testen und dem Benutzer Informationen zurückzugeben, damit er eine fundierte Entscheidung treffen kann. So kann der Kunde sehen, wie eine gültige Lizenz aussieht, aber nicht tatsächlich den Schlüssel zum Entschlüsseln des Inhalts erhalten. Die Lizenzunterstützung ist optional und nur erforderlich, wenn Sie einen benutzerdefinierten Client implementieren, der diese Vorschau verwendet.

Rufen Sie zum Bestimmen, ob der Client eine Lizenzanforderung oder eine Lizenzersatzanforderung gesendet hat, an `LicenseRequestMessage.getRequestPhase()`und vergleichen Sie diese mit `LicenseRequestMessage.RequestPhase.Acquire`
