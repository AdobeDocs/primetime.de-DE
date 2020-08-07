---
seo-title: Anforderungen für die Synchronisierung
title: Anforderungen für die Synchronisierung
uuid: 976a0ae1-bece-437e-b95b-6cd222525d13
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Anforderungen für die Synchronisierung{#requirements-for-synchronization}

Gibt die Häufigkeit an, mit der der Client seinen Status mit dem Server synchronisiert. If the client has been issued an out-of-band license (without a license server being contacted), usage rules may specify that the client must send synchronization messages to the server in order to synchronize the client&#39;s secure time and report client state to the server.

Das Synchronisierungsverhalten wird mithilfe der folgenden Parameter definiert:

* Beginn-Intervall — Gibt an, wie lange nach der letzten erfolgreichen Synchronisierung gewartet wird, bis eine weitere Synchronisierungsanforderung Beginn wird.
* Hartes Stoppintervall — (Optional). Die Wiedergabe ist nicht zulässig, wenn innerhalb der angegebenen Zeitspanne keine erfolgreiche Synchronisierung stattgefunden hat.
* Synchronisierungswahrscheinlichkeit erzwingen — (Optional). Probability with which the client should send a synchronize message before the next start interval.

>[!NOTE]
>
>This usage rule is supported by Adobe Access clients version 3.0 and higher. The behavior on older clients depends on the minimum client version supported by the license server. See, [Minimum Client Version](../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md).

