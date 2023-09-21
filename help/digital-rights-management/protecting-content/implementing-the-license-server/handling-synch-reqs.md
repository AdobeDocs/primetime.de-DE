---
title: Verarbeitung von Synchronisierungsanfragen
description: Verarbeitung von Synchronisierungsanfragen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# Verarbeitung von Synchronisierungsanfragen {#handle-synchronization-requests}

Wenn eine Lizenz Synchronisierungsanforderungen angibt  [Anforderungen an die Synchronisierung,](../../protecting-content/introduction/usage-rules/authentication/synchronization.md) Der Client sendet regelmäßig Synchronisierungsanfragen an den Server, basierend auf der in der Lizenz angegebenen Häufigkeit. Um Synchronisierungsmeldungen zu aktivieren, legen Sie `SyncFrequencyRequirements` in einem PlayRight.

* Die Anfrage-Handler-Klasse lautet `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* Wenn sowohl der Client als auch der Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;Lizenzserver-URL in Metadaten: + &quot;. [!DNL /flashaccess/sync/v4]&quot;. Andernfalls lautet die Anforderungs-URL &quot;Lizenzserver-URL in Metadaten&quot; + &quot; [!DNL /flashaccess/sync/v3]&quot;

Synchronisierungsmeldungen werden verwendet, um die Zeit des Clients mit der Zeit des Servers zu synchronisieren. Wenn Lizenzen in den Inhalt eingebettet sind und nicht von einem Lizenzserver abgerufen werden müssen, ist eine Synchronisierung der Zeit des Kunden wichtig, um zu verhindern, dass der Client seine Uhr ändert, um den Lizenzablauf zu umgehen.

Synchronisierungsmeldungen können auch verwendet werden, um die Client-Statusinformationen an den Server zu übermitteln ( `getClientState()`) für die Rollback-Erkennung.

Siehe [Rollschutz](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#rollback-detection).
