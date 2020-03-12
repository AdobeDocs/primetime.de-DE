---
description: In diesem Abschnitt werden die Funktionen beschrieben, die in verschiedenen Versionen von Flash Player und TVSDK verfügbar sind.
seo-description: In diesem Abschnitt werden die Funktionen beschrieben, die in verschiedenen Versionen von Flash Player und TVSDK verfügbar sind.
seo-title: RBOP-Client-Support
title: RBOP-Client-Support
uuid: d1d0f788-7bc1-488c-807e-be47f83725e9
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# RBOP-Client-Support {#rbop-client-support}

In diesem Abschnitt werden die Funktionen beschrieben, die in verschiedenen Versionen von Flash Player und TVSDK verfügbar sind.

**Fehler-Dispatch** - Die unten aufgeführten TVSDK-Plattformen lösen einen DRM-Laufzeitfehler aus, wenn die Auflösung des wiedergegebenen Inhalts die für die Gerätekonfiguration zulässige Auflösung überschreitet, die in der DRM-Richtlinie definiert ist:

* Flash Player-Versionen 18 bis 20
* Android - Versionen
* iOS - Versionen

>[!NOTE]
>
>* Alle Flash- und Mobilplattformen unterstützen &quot;Error Dispatch&quot;, aber nur die oben aufgeführten TVSDK-Clients verarbeiten RBOP-bezogene Fehler.
>* RBOP-bezogene [DRM-Client-Fehler](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages): >
   >    * **3371** - Fehlerhafte Auflösung basierend auf Ausgabeschutzbeschränkungen in der Lizenz.
   >    * **3372** - Die Auflösung des Inhalts ist größer als die in der Ausgabeschränkung angegebene maximale Auflösung. (Dies kann vorkommen, wenn jemand versucht hat, Inhalte für ein anderes Gerät einzuschleusen.)
   >    * **3373** - Die Auflösung des Inhalts ist größer als die Auflösung, die von der derzeit aktiven Ausgabeschränkung angegeben wird. (Das bedeutet, dass wir eine Herabstufung vornehmen müssen.)
>



**Automatische Neuskalierung** - Die Technik zum Downskalieren variiert je nach Plattform und Flash Player-Version:

* Flash Player Version 21: Unterstützt RBOP mit automatischer Downscaling (intelligentes Bitratenwechsel)
* Firefox Version 38 und höher unter Windows (mit Access CDM): Adobe stuft einen Stream mit höherer Bitrate automatisch auf einen Stream mit niedrigerer Bitrate herunter (anstatt einen Stream mit niedrigerer Qualität herunterzuladen).

>[!NOTE]
>
>Diese Plattformen führen automatisch Downscale-Videos durch und zeigen den Inhalt in einer Auflösung an, die kleiner oder gleich der von der DRM-Richtlinie festgelegten ist. Mit dieser Funktion werden Inhalte immer auf den Client zurückgegeben, solange ein verfügbarer Stream vorhanden ist, der die DRM-Richtlinienbeschränkungen erfüllt.

**Legacy Output Protection** - Clients, die Flash Player vor Version 18 verwenden, können nur ältere OP-Einschränkungen handhaben. Clients mit Flash Player Version 18 und höher können entweder Legacy- oder RBOP-Beschränkungen handhaben. Wenn Sie RBOP-Beschränkungen festlegen, sollten Sie auch ältere OP-Beschränkungen für ältere Clients festlegen. Bei Clients, die RBOP unterstützen, treten RBOP-Beschränkungen gegenüber bestehenden OP-Beschränkungen auf.
