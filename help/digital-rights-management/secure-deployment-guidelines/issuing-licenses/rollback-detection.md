---
description: Wenn Ihre Implementierung von Adobe Primetime DRM Geschäftsregeln verwendet, bei denen der Client den Status beibehalten muss (z. B. das Zeitintervall des Wiedergabefensters), empfiehlt Adobe, dass der Server den Rollback-Zähler verfolgt und die AIR- oder SWF-Whitelist verwendet.
seo-description: Wenn Ihre Implementierung von Adobe Primetime DRM Geschäftsregeln verwendet, bei denen der Client den Status beibehalten muss (z. B. das Zeitintervall des Wiedergabefensters), empfiehlt Adobe, dass der Server den Rollback-Zähler verfolgt und die AIR- oder SWF-Whitelist verwendet.
seo-title: Rollenerkennung
title: Rollenerkennung
uuid: f161ed41-488a-478a-b6a8-468cf6d11e89
translation-type: tm+mt
source-git-commit: 3fdef12b717bb6f70ca27d9278de61d709f8349c

---


# Rollenerkennung {#rollback-detection}

Wenn Ihre Implementierung von Adobe Primetime DRM Geschäftsregeln verwendet, bei denen der Client den Status beibehalten muss (z. B. das Zeitintervall des Wiedergabefensters), empfiehlt Adobe, dass der Server den Rollback-Zähler verfolgt und die AIR- oder SWF-Whitelist verwendet.

Der Rollback-Zähler wird in den meisten Anforderungen des Clients an den Server gesendet. Wenn für Ihre Implementierung von Primetime DRM der Rollback-Zähler nicht erforderlich ist, kann er ignoriert werden. Andernfalls empfiehlt Adobe, dass der Server die zufällige Computer-ID, die mit [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId())abgerufen wird, und den aktuellen Zählerwert in einer Datenbank speichert.

Weitere Informationen zum Inkrementieren und Verfolgen des Rollback-Zählers finden Sie unter [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) - und Rollback-Erkennung.