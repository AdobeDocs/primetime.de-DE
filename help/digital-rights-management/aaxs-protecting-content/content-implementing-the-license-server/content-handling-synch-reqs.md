---
title: Bearbeitung von Synchronisierungsanforderungen
description: Bearbeitung von Synchronisierungsanforderungen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# Bearbeitung von Synchronisierungsanforderungen{#handling-synchronization-requests}

. Wenn in einer Lizenz die Synchronisierungsanforderungen ([Anforderungen für die Synchronisierung](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-time-based-rules/content-time-based-rules-defining.md#requirements-for-synchronization)) angegeben sind, sendet der Client in regelmäßigen Abständen Synchronisierungsanfragen an den Server, basierend auf der in der Lizenz angegebenen Häufigkeit. Um Synchronisierungsmeldungen zu aktivieren, legen Sie SyncFrequencyRequirements in PlayRight fest.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* Die Anforderungsmeldungsklasse ist `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* Wenn Client und Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;URL des Lizenzservers in Metadaten: + &quot;/flashaccess/sync/v4&quot;. Andernfalls lautet die Anforderungs-URL &quot;URL des Lizenzservers in Metadaten&quot; + &quot;/flashaccess/sync/v3&quot;

Synchronisierungsmeldungen werden verwendet, um die Zeit des Clients mit der Zeit des Servers zu synchronisieren. Wenn Lizenzen in den Inhalt eingebettet sind und nicht von einem Lizenzserver abgerufen werden müssen, ist eine Synchronisierung der Zeit des Clients wichtig, um zu verhindern, dass der Client seine Uhr ändert, um den Ablauf der Lizenz zu umgehen.

Synchronisierungsmeldungen können auch verwendet werden, um die Clientstatusinformationen zur Rollback-Erkennung an den Server ( `getClientState()`) zu übermitteln. Siehe [Rollback-Schutz](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-rollback-detection.md).