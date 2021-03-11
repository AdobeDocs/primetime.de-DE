---
title: Anforderungen für die Synchronisierung
description: Anforderungen für die Synchronisierung
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Anforderungen für die Synchronisierung{#requirements-for-synchronization}

Gibt die Häufigkeit an, mit der der Client seinen Status mit dem Server synchronisiert. Wenn dem Client eine Out-of-Band-Lizenz erteilt wurde (ohne dass ein Lizenzserver kontaktiert wird), können Nutzungsregeln festlegen, dass der Client Synchronisierungsmeldungen an den Server senden muss, um die sichere Zeit des Clients zu synchronisieren und den Clientstatus mit dem Server zu melden.

Das Synchronisierungsverhalten wird mithilfe der folgenden Parameter definiert:

* Beginn-Intervall — Gibt an, wie lange nach der letzten erfolgreichen Synchronisierung gewartet wird, bis eine weitere Synchronisierungsanforderung Beginn wird.
* Hartes Stoppintervall — (Optional). Die Wiedergabe ist nicht zulässig, wenn innerhalb der angegebenen Zeitspanne keine erfolgreiche Synchronisierung stattgefunden hat.
* Synchronisierungswahrscheinlichkeit erzwingen — (Optional). Möglichkeit, mit der der Client vor dem nächsten Beginn eine Synchronisierungsmeldung senden soll.

>[!NOTE]
>
>Diese Nutzungsregel wird von Adobe Access Clients ab Version 3.0 unterstützt. Das Verhalten älterer Clients hängt von der vom Lizenzserver unterstützten Clientversion ab. Siehe [Minimale Client-Version](../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md).

