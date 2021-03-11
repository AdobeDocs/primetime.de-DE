---
title: Rollenerkennung
description: Rollenerkennung
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---


# Rollenerkennung {#rollback-detection}

Wenn Ihre Implementierung von Adobe Access Geschäftsregeln verwendet, bei denen der Client den Status beibehalten muss (z. B. das Wiedergabefenster), empfiehlt Adobe dringend, dass der Server den Rollback-Zähler verfolgt und AIR oder SWF die Auflistung zulässt.

Der Rollback-Zähler wird in den meisten Anforderungen des Clients an den Server gesendet. Wenn für Ihre Implementierung von Adobe Access der Rollback-Zähler nicht erforderlich ist, kann er ignoriert werden. Andernfalls empfiehlt Adobe, dass der Server die zufällige Computer-ID (abgerufen mit `MachineToken.getMachineId().getUniqueId()`) und den aktuellen Zählerwert in einer Datenbank speichert. Weitere Informationen zum Inkrementieren und Verfolgen des Rollback-Zählers finden Sie unter ClientState in *Adobe Access API Reference* und *Rollback Detection* in *Verwenden des Adobe Access SDK zum Schützen von Inhalten*.
