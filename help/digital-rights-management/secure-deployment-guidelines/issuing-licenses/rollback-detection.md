---
description: Wenn Ihre Implementierung von Adobe Primetime DRM Geschäftsregeln verwendet, bei denen der Client den Status beibehalten muss (z. B. das Zeitintervall des Wiedergabefensters), empfiehlt Adobe, dass der Server den Rollback-Zähler verfolgt und die Verwendung von AIR oder SWF-Listen zulässt.
title: Rollenerkennung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---


# Rollenerkennung {#rollback-detection}

Wenn Ihre Implementierung von Adobe Primetime DRM Geschäftsregeln verwendet, bei denen der Client den Status beibehalten muss (z. B. das Zeitintervall des Wiedergabefensters), empfiehlt Adobe, dass der Server den Rollback-Zähler verfolgt und die Verwendung von AIR oder SWF-Listen zulässt.

Der Rollback-Zähler wird in den meisten Anforderungen des Clients an den Server gesendet. Wenn für Ihre Implementierung von Primetime DRM der Rollback-Zähler nicht erforderlich ist, kann er ignoriert werden. Andernfalls empfiehlt Adobe, dass der Server die zufällige Computer-ID, die mit [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) abgerufen wird, und den aktuellen Zählerwert in einer Datenbank speichert.

Weitere Informationen zum Inkrementieren und Verfolgen des Rollback-Zählers finden Sie unter [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html)- und Rollback-Erkennung.