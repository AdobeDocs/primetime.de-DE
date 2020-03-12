---
seo-title: Rollenerkennung
title: Rollenerkennung
uuid: fc80c98f-7ee5-414b-87fe-0dbb8d4f6019
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Rollenerkennung{#rollback-detection}

Wenn Ihre Implementierung von Adobe Access Geschäftsregeln verwendet, bei denen der Client den Status beibehalten muss (z. B. das Wiedergabefenster), empfiehlt Adobe dringend, dass der Server den Rollback-Zähler verfolgt und die AIR- oder SWF-Whitelisting verwendet.

Der Rollback-Zähler wird in den meisten Anforderungen des Clients an den Server gesendet. Wenn für Ihre Implementierung von Adobe Access der Rollback-Zähler nicht erforderlich ist, kann er ignoriert werden. Andernfalls empfiehlt Adobe, dass der Server die zufällige Computer-ID (abgerufen unter `MachineToken.getMachineId().getUniqueId()`) und den aktuellen Zählerwert in einer Datenbank speichert. Weitere Informationen zum Inkrementieren und Verfolgen des Rollback-Zählers finden Sie unter ClientState in der *Adobe Access API-Referenz* und *Rollback-Erkennung* in *Verwenden des Adobe Access SDK zum Schutz von Inhalten*.
