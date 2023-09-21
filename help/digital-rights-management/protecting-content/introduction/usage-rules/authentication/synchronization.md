---
title: Anforderungen an die Synchronisierung
description: Anforderungen an die Synchronisierung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Anforderungen für die Synchronisierung {#requirements-for-synchronization}

Die Anforderungen für die Synchronisierung geben an, mit welcher Häufigkeit der Client seinen Status mit dem Server synchronisiert. Wenn dem Client eine Out-of-Band-Lizenz erteilt wurde (ohne dass ein Lizenzserver kontaktiert wird), können Nutzungsregeln festlegen, dass der Client Synchronisierungsmeldungen an den Server senden muss, um die sichere Zeit des Clients zu synchronisieren, und den Clientstatus an den Server melden.

Das Synchronisierungsverhalten wird mithilfe der folgenden Parameter definiert:

* **Startintervall** - Gibt an, wie lange es nach der letzten erfolgreichen Synchronisation warten muss, um eine weitere Synchronisierungsanforderung zu starten.
* **Hard Stopp Interval** - (Optional). Die Wiedergabe verweigern, wenn innerhalb der angegebenen Zeit keine erfolgreiche Synchronisierung stattgefunden hat.
* **Wahrscheinlichkeit der erzwungenen Synchronisierung** - (Optional). Wahrscheinlichkeit, mit der der Client eine Synchronisierungsmeldung vor dem nächsten Startintervall senden soll.

>[!NOTE]
>
>Diese Nutzungsregel wird von Primetime DRM-Clients Version 3.0 oder höher unterstützt. Das Verhalten bei älteren Clients hängt von der vom Lizenzserver unterstützten Mindestversion des Clients ab.
