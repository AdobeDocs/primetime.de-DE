---
description: Browser TVSDK stellt Ihrer Video-App Informationen bereit, die erforderlich sind, um auf den Klick eines Benutzers auf eine anklickbare Anzeige zu reagieren.
title: Klickbare Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Übersicht {#clickable-ads-overview}

Browser TVSDK stellt Ihrer Video-App Informationen bereit, die erforderlich sind, um auf den Klick eines Benutzers auf eine anklickbare Anzeige zu reagieren.

Wenn ein Benutzer auf eine anklickbare Anzeige klickt, besteht eine typische Antwort von einer Video-App darin, ein neues Browser-Fenster zu öffnen und zu der mit der Anzeige verknüpften URL zu navigieren. Um dies zu erleichtern, löst Browser TVSDK Anzeigenbenachrichtigungen aus, die Ihre App zum Verwalten des Clickthrough-Prozesses verwenden kann.

In Ihrer App können Sie dem Benutzer ein Steuerelement bereitstellen, auf das er klicken kann (z. B. eine Schaltfläche), während die anklickbare Anzeige wiedergegeben wird. Sie müssen Handler für Ereignisse erstellen, die von Browser TVSDK ausgelöst werden und mit der Anzeige verknüpft sind (z. B. Anzeigenstart, Anzeigenklick, Anzeigenbeendigung). Schließlich müssen Sie die spezifischen Verhaltensweisen implementieren, die Ihre App nach dem Anzeigenklick eines Benutzers hat (z. B. ob Sie die Anzeige anhalten oder nicht, die Clickthrough-URL anzeigen usw.).

>[!NOTE]
>
>Der im Browser TVSDK enthaltene Referenz-Player enthält eine mögliche Arbeitslösung zur Verarbeitung von Clickthrough-Anzeigen.
