---
seo-title: Umgang mit Synchronisierungsanforderungen
title: Umgang mit Synchronisierungsanforderungen
uuid: e2623afb-7a57-402d-a8a1-07bcf6324d41
translation-type: tm+mt
source-git-commit: eed2ed2512c2c462cd43637d83d80bf9a5c0d490
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---


# Verarbeiten von Synchronisierungsanforderungen {#handle-synchronization-requests}

Wenn eine Lizenz die Synchronisierungsanforderungen [Anforderungen für die Synchronisierung festlegt, sendet der Client regelmäßig Synchronisierungsanfragen an den Server, basierend auf der in der Lizenz angegebenen Häufigkeit. ](../../protecting-content/introduction/usage-rules/authentication/synchronization.md) Um Synchronisierungsmeldungen zu aktivieren, legen Sie `SyncFrequencyRequirements` in PlayRight fest.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* Die Anforderungsmeldungsklasse ist `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* Wenn Client und Server das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;URL des Lizenzservers in Metadaten: + &quot; [!DNL /flashaccess/sync/v4]&quot;. Andernfalls lautet die Anforderungs-URL &quot;URL des Lizenzservers in Metadaten&quot; + &quot; [!DNL /flashaccess/sync/v3]&quot;

Synchronisierungsmeldungen werden verwendet, um die Zeit des Clients mit der Zeit des Servers zu synchronisieren. Wenn Lizenzen in den Inhalt eingebettet sind und nicht von einem Lizenzserver abgerufen werden müssen, ist eine Synchronisierung der Zeit des Clients wichtig, um zu verhindern, dass der Client seine Uhr ändert, um den Ablauf der Lizenz zu umgehen.

Synchronisierungsmeldungen können auch verwendet werden, um die Clientstatusinformationen zur Rollback-Erkennung an den Server ( `getClientState()`) zu übermitteln.

Siehe [Rollback-Schutz](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#rollback-detection).
