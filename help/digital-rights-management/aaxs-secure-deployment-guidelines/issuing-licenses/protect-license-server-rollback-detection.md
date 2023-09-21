---
title: Rollenerkennung
description: Rollenerkennung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# Rollenerkennung {#rollback-detection}

Wenn Ihre Implementierung von Adobe Access Geschäftsregeln nutzt, bei denen der Client den Status beibehalten muss (z. B. das Wiedergabefenster), empfiehlt Adobe dringend, dass der Server den Rollback-Zähler verfolgt und AIR- oder SWF-Zulassungsauflistungen verwendet.

Der Rollback-Zähler wird in den meisten Anforderungen des Clients an den Server gesendet. Wenn für Ihre Implementierung von Adobe Access der Rollback-Zähler nicht erforderlich ist, kann er ignoriert werden. Andernfalls empfiehlt Adobe, dass der Server die zufällige Computer-ID speichert, die mithilfe von abgerufen wurde. `MachineToken.getMachineId().getUniqueId()`- und den aktuellen Zählerwert in einer Datenbank. Weitere Informationen zum Inkrementieren und Tracking des Rollback-Zählers finden Sie unter ClientState in *Adobe Access API-Referenz* und *Rollenerkennung* in *Verwenden des Adobe Access SDK zum Schutz von Inhalten*.
