---
seo-title: Verwenden Sie die Maschinenkennungen
title: Verwenden Sie die Maschinenkennungen
uuid: 14eee414-62f1-4a9d-84bd-689ca2271d19
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verwenden Sie die Maschinenkennungen{#use-machine-identifiers}

Alle DRM-Anforderungen von Adobe Primetime (mit Ausnahme von Anforderungen, die FMRMS-Kompatibilität unterstützen) enthalten Informationen über das Computertoken, das dem Client während der Individualisierung ausgegeben wurde. Das Gerätetoken enthält eine Computer-ID, eine ID, die während der Individualisierung zugewiesen wurde. Mit diesem Bezeichner können Sie die Anzahl der Computer zählen, auf denen ein Benutzer eine Lizenz beantragt oder einer Domäne beigetreten ist.

Sie können einen Bezeichner wie folgt verwenden:

* Die `getUniqueId()` Methode gibt eine Zeichenfolge zurück, die einem Gerät während der Individualisierung zugewiesen wurde. Sie können die Zeichenfolgen in einer Datenbank speichern und nach Bezeichner suchen. Dieser Bezeichner ändert sich jedoch, wenn der Benutzer die Festplatte neu formatiert und erneut individualisiert. Dieser Bezeichner hat auch einen anderen Wert zwischen Adobe AIR und Adobe Flash Player in verschiedenen Browsern auf demselben Computer.
* Wenn Sie Maschinen genauer zählen möchten, können Sie den gesamten Bezeichner `getBytes()` speichern. Um festzustellen, ob der Computer zuvor gesehen wurde, rufen Sie alle Bezeichner für einen Benutzernamen ab und prüfen Sie, ob eine Übereinstimmung vorliegt. `matches()` Da die `matches()` `MachineId.getBytes`Methode zum Vergleich der zurückgegebenen Werte verwendet werden muss, ist diese Option nur dann praktisch, wenn eine kleine Anzahl von Werten miteinander verglichen werden kann. zum Beispiel die mit einem bestimmten Benutzer verbundenen Computer.

