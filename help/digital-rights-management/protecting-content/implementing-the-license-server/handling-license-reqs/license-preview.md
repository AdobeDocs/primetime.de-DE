---
title: Lizenzvorschau
description: Lizenzvorschau
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Lizenzvorschau{#license-preview}

Der Client kann eine Lizenzvorschau-Anfrage senden. Das bedeutet, dass die Anwendung einen Vorschauvorgang durchführen kann, bevor der Benutzer aufgefordert wird, den Inhalt zu kaufen, um festzustellen, ob der Computer des Benutzers tatsächlich alle für die Wiedergabe erforderlichen Kriterien erfüllt.

*`License preview`* bezieht sich auf die Fähigkeit eines Kunden, eine Vorschau der Lizenz anzuzeigen (um zu sehen, welche Rechte die Lizenz zulässt), anstatt den Inhalt in der Vorschau anzuzeigen (einen kleinen Teil des Inhalts anzuzeigen, bevor er sich für den Kauf entscheidet). Einige der Parameter, die für jeden Computer eindeutig sind, sind: verfügbare Ausgaben und ihr Schutzstatus, die verfügbare Laufzeit-/DRM-Version und die DRM-Client-Sicherheitsstufe. Der Lizenzvorschau-Modus ermöglicht es dem Laufzeit-/DRM-Client, die Geschäftslogik des Lizenzservers zu testen und dem Benutzer Informationen zurückzugeben, damit er eine fundierte Entscheidung treffen kann. So kann der Client sehen, wie eine gültige Lizenz aussieht, aber nicht den Schlüssel zum Entschlüsseln des Inhalts erhalten. Die Unterstützung für die Lizenzvorschau ist optional und nur erforderlich, wenn Sie einen benutzerdefinierten Client implementieren, der diese Funktion verwendet.

Rufen Sie auf, um festzustellen, ob der Client eine Vorschau-Anfrage oder eine Lizenzakquise-Anfrage gesendet hat `LicenseRequestMessage.getRequestPhase()`und vergleichen Sie sie mit `LicenseRequestMessage.RequestPhase.Acquire`
