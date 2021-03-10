---
description: In diesem Abschnitt werden die Funktionen beschrieben, die mit verschiedenen Versionen von Flash Player und TVSDK verfügbar sind.
title: RBOP-Client-Support
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# RBOP-Client-Unterstützung {#rbop-client-support}

In diesem Abschnitt werden die Funktionen beschrieben, die mit verschiedenen Versionen von Flash Player und TVSDK verfügbar sind.

**Fehler-Dispatch** : Die unten aufgeführten TVSDK-Plattformen lösen einen DRM-Laufzeitfehler aus, wenn die Auflösung des wiedergegebenen Inhalts die für die Gerätekonfiguration zulässige Auflösung überschreitet, die in der DRM-Richtlinie definiert ist:

* Flash Player Versionen 18 bis 20
* Android - Versionen
* iOS - Versionen

>[!NOTE]
>
>* Alle Flash- und Mobilplattformen unterstützen &quot;Error Dispatch&quot;, aber nur die oben aufgeführten TVSDK-Clients verarbeiten RBOP-bezogene Fehler.
>* RBOP-bezogene [DRM-Clientfehler](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages):
   >    * **3371** - Fehlerhafte Auflösung basierend auf Ausgabeschutzbeschränkungen in der Lizenz.
   >    * **3372**  - Die Auflösung des Inhalts ist größer als die in der Ausgabeschränkung angegebene maximale Auflösung. (Dies kann vorkommen, wenn jemand versucht hat, Inhalte für ein anderes Gerät einzuschleusen.)
   >    * **3373**  - Die Auflösung des Inhalts ist größer als die Auflösung, die durch die derzeit aktive Ausgabeschränkung angegeben wird. (Das bedeutet, dass wir eine Herabstufung vornehmen müssen.)

>



**Automatische Neuskalierung**  - Die Vorgehensweise zum Downskalieren variiert je nach Plattform- und Flash Player-Version:

* Flash Player Version 21: Unterstützt RBOP mit automatischer Downscaling (intelligentes Bitratenwechsel)
* Firefox Version 38 und höher unter Windows (mit Access CDM): Bei der Adobe wird ein Stream mit höherer Bitrate automatisch auf einen Stream mit niedrigerer Bitrate herabgestuft (im Gegensatz zum Herunterladen eines Streams mit niedrigerer Qualität).

>[!NOTE]
>
>Diese Plattformen führen automatisch Downscale-Videos durch und zeigen den Inhalt in einer Auflösung an, die kleiner oder gleich der von der DRM-Richtlinie festgelegten ist. Mit dieser Funktion werden Inhalte immer auf den Client zurückgegeben, solange ein verfügbarer Stream vorhanden ist, der die DRM-Richtlinienbeschränkungen erfüllt.

**Älterer Output Protection**  - Clients, die Flash Player vor Version 18 verwenden, können nur ältere OP-Einschränkungen handhaben. Clients mit Flash Player Version 18 und höher können entweder Legacy- oder RBOP-Beschränkungen handhaben. Wenn Sie RBOP-Beschränkungen festlegen, sollten Sie auch ältere OP-Beschränkungen für ältere Clients festlegen. Bei Clients, die RBOP unterstützen, treten RBOP-Beschränkungen gegenüber bestehenden OP-Beschränkungen auf.
