---
description: Browser TVSDK stellt Ihre Video-App mit Informationen zur Verfügung, die erforderlich sind, um auf den Klick eines Benutzers auf eine anklickbare Anzeige zu reagieren.
seo-description: Browser TVSDK stellt Ihre Video-App mit Informationen zur Verfügung, die erforderlich sind, um auf den Klick eines Benutzers auf eine anklickbare Anzeige zu reagieren.
seo-title: Klickbare Anzeigen
title: Klickbare Anzeigen
uuid: 493c3199-b5ba-4809-86eb-e80f10eb957b
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Übersicht {#clickable-ads-overview}

Browser TVSDK stellt Ihre Video-App mit Informationen zur Verfügung, die erforderlich sind, um auf den Klick eines Benutzers auf eine anklickbare Anzeige zu reagieren.

Wenn ein Benutzer auf eine anklickbare Anzeige klickt, besteht eine typische Antwort aus einer Video-App darin, ein neues Browserfenster zu öffnen und zu der mit der Anzeige verknüpften URL zu navigieren. Um dies zu erleichtern, löst Browser TVSDK Anzeigenbenachrichtigungen aus, die Ihre App zur Verwaltung des Clickthrough-Prozesses verwenden kann.

In Ihrer App können Sie dem Benutzer ein Steuerelement zum Klicken (z. B. eine Schaltfläche) bereitstellen, während die anklickbare Anzeige abgespielt wird. Sie müssen Handler für von Browser TVSDK ausgelöste Ereignis erstellen, die mit der Anzeige verknüpft sind (z. B. Anzeigen-Beginn, Anklicken und Abschließen). Schließlich müssen Sie die spezifischen Verhaltensweisen implementieren, die Ihre App nach dem Klick eines Benutzers hat (z. B. ob die Anzeige angehalten werden soll oder nicht, ob die Clickthrough-URL angezeigt werden soll usw.).

>[!NOTE]
>
>Der im Lieferumfang von Browser TVSDK enthaltene Referenz-Player enthält eine mögliche Arbeitslösung zur Verarbeitung von Clickthrough-Anzeigen.