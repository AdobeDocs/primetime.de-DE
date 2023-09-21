---
description: In diesem Abschnitt werden die Funktionen beschrieben, die in verschiedenen Versionen von Flash Player und TVSDK verfügbar sind.
title: RBOP-Client-Support
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# RBOP-Client-Support {#rbop-client-support}

In diesem Abschnitt werden die Funktionen beschrieben, die in verschiedenen Versionen von Flash Player und TVSDK verfügbar sind.

**Fehler-Dispatch** - Die unten aufgeführten TVSDK-Plattformen senden einen DRM Runtime-Fehler, wenn die Auflösung des wiedergegebenen Inhalts die für die Gerätekonfiguration zulässige Auflösung überschreitet, die in der DRM-Richtlinie definiert ist:

* Flash Player Versionen 18 bis 20
* Android - Versionen
* iOS - Versionen

>[!NOTE]
>
>* Alle Flash- und Mobilplattformen unterstützen &quot;Error Dispatch&quot;, aber nur die oben aufgeführten TVSDK-Clients verarbeiten RBOP-bezogene Fehler.
>* RBOP-bezogen [DRM-Client-Fehler](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages):
>    * **3371** - Fehlerhafte Auflösung basierend auf Ausgabeschutzbegrenzungen in der Lizenz.
>    * **3372** - Die Auflösung des Inhalts ist größer als die maximale Auflösung, die in der Ausgabeschutzbegrenzung angegeben ist. (Dies kann vorkommen, wenn jemand versucht hat, Inhalte für ein anderes Gerät einzufügen.)
>    * **3373** - Die Auflösung des Inhalts ist größer als die Auflösung, die durch die derzeit aktive Ausgabeschränkung angegeben wird. (Das bedeutet, dass wir das Upgrade durchführen müssen.)
>

**Automatische Downskalierung** - Die zum Downskalieren verwendete Technik variiert je nach Plattform- und Flash Player-Version:

* Flash Player Version 21: Unterstützt RBOP mit automatischer Downskalierung (intelligenter Bitratenwechsel)
* Firefox Version 38 und höher unter Windows (mit Access CDM): Adobe lädt automatisch einen höheren Bitratenstream auf einen niedrigeren herunter (anstatt einen Stream mit niedrigerer Bitrate herunterzuladen).

>[!NOTE]
>
>Diese Plattformen skalieren automatisch Videos herunter und zeigen den Inhalt in einer Auflösung an, die kleiner oder gleich der in der DRM-Richtlinie festgelegten Auflösung ist. Mit dieser Funktion werden Inhalte immer an den Client zurückgegeben, sofern ein verfügbarer Stream vorhanden ist, der die DRM-Richtlinienbeschränkungen erfüllt.

**Legacy Output Protection** - Clients, die Flash Player vor Version 18 verwenden, können nur ältere OP-Beschränkungen handhaben. Clients mit Flash Player Version 18 und höher können Legacy- oder RBOP-Einschränkungen handhaben. Wenn Sie RBOP-Einschränkungen festlegen, sollten Sie auch ältere OP-Einschränkungen für ältere Clients festlegen. Für Clients, die RBOP unterstützen, übertreffen RBOP-Einschränkungen bestehende OP-Beschränkungen.
