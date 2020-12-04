---
seo-title: Rollenerkennung
title: Rollenerkennung
uuid: fc80c98f-7ee5-414b-87fe-0dbb8d4f6019
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---


# Rollenerkennung {#rollback-detection}

Wenn Ihre Implementierung von Adobe Access Geschäftsregeln verwendet, bei denen der Client den Status beibehalten muss (z. B. das Wiedergabefenster), empfiehlt Adobe dringend, dass der Server den Rollback-Zähler verfolgt und AIR oder SWF die Auflistung zulässt.

Der Rollback-Zähler wird in den meisten Anforderungen des Clients an den Server gesendet. Wenn für Ihre Implementierung von Adobe Access der Rollback-Zähler nicht erforderlich ist, kann er ignoriert werden. Andernfalls empfiehlt Adobe, dass der Server die zufällige Computer-ID (abgerufen mit `MachineToken.getMachineId().getUniqueId()`) und den aktuellen Zählerwert in einer Datenbank speichert. Weitere Informationen zum Inkrementieren und Verfolgen des Rollback-Zählers finden Sie unter ClientState in *Adobe Access API Reference* und *Rollback Detection* in *Verwenden des Adobe Access SDK zum Schützen von Inhalten*.
