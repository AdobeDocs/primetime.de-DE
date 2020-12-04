---
seo-title: Vorschau der Lizenz
title: Vorschau der Lizenz
uuid: 3171647d-1437-48ab-9659-3eb363993618
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---


# Vorschau der Lizenz{#license-preview}

Der Client kann eine Lizenzanforderung senden, d. h., die Vorschau kann eine Vorschau durchführen, bevor der Benutzer aufgefordert wird, den  zu erwerben, um festzustellen, ob der Computer des Benutzers tatsächlich alle für die Wiedergabe erforderlichen Kriterien erfüllt. *Die Lizenzvorschau* bezieht sich auf die Fähigkeit des Kunden, die Lizenz Vorschau (um zu sehen, welche Rechte die Lizenz erlaubt), im Gegensatz zur Vorschau des Inhalts (Betrachten eines kleinen Teils des Inhalts, bevor der Kauf beschlossen wird). Einige der Parameter, die für die einzelnen Computer eindeutig sind, sind: verfügbare Ausgaben und deren Schutzstatus, die verfügbare Laufzeit-/DRM-Version und die DRM-Client-Sicherheitsstufe. Der Lizenzmodus ermöglicht es dem Laufzeit-/DRM-Vorschau-Client, die Geschäftslogik des Lizenzservers zu testen und dem Benutzer Informationen zurückzugeben, damit er eine fundierte Entscheidung treffen kann. So kann der Kunde sehen, wie eine gültige Lizenz aussieht, aber nicht tatsächlich den Schlüssel zum Entschlüsseln des Inhalts erhalten. Die Lizenzunterstützung ist optional und nur erforderlich, wenn Sie einen benutzerdefinierten Client implementieren, der diese Vorschau verwendet.

Rufen Sie `LicenseRequestMessage.getRequestPhase()`auf und vergleichen Sie diese mit `LicenseRequestMessage.RequestPhase.Acquire`, um festzustellen, ob der Client eine Anforderung zur Vorschau oder Lizenzerteilung gesendet hat.
