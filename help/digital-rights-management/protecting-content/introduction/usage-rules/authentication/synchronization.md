---
seo-title: Anforderungen für die Synchronisierung
title: Anforderungen für die Synchronisierung
uuid: 19a6ee7e-9580-48bb-a3a6-ff2cedcc796a
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Anforderungen für die Synchronisierung {#requirements-for-synchronization}

Die Anforderungen für die Synchronisierung geben die Häufigkeit an, mit der der Client seinen Status mit dem Server synchronisiert. Wenn dem Client eine Out-of-Band-Lizenz erteilt wurde (ohne dass ein Lizenzserver kontaktiert wird), können Nutzungsregeln festlegen, dass der Client Synchronisierungsmeldungen an den Server senden muss, um die sichere Zeit des Clients zu synchronisieren, und den Clientstatus an den Server melden.

Das Synchronisierungsverhalten wird mithilfe der folgenden Parameter definiert:

* **Beginn-Intervall** - Gibt an, wie lange nach der letzten erfolgreichen Synchronisierung gewartet wird, bis eine weitere Synchronisierungsanforderung Beginn wird.
* **Hartes Stoppintervall** - (Optional). Die Wiedergabe ist nicht zulässig, wenn innerhalb der angegebenen Zeitspanne keine erfolgreiche Synchronisierung stattgefunden hat.
* **Synchronisierungswahrscheinlichkeit erzwingen** - (Optional). Möglichkeit, mit der der Client vor dem nächsten Beginn eine Synchronisierungsmeldung senden soll.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Diese Nutzungsregel wird von Primetime DRM-Clients Version 3.0 oder höher unterstützt. Das Verhalten älterer Clients hängt von der vom Lizenzserver unterstützten Clientversion ab.
