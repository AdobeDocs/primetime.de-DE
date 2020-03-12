---
seo-title: Verwenden der Maschinenkennungen
title: Verwenden der Maschinenkennungen
uuid: 2832c158-fade-4bbf-ae89-f95ce9dfc369
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verwenden der Maschinenkennungen{#using-machine-identifiers}

Alle Adobe Access-Anfragen (mit Ausnahme von Anfragen, die FMRMS-Kompatibilität unterstützen) enthalten Informationen über das Computertoken, das dem Client während der Individualisierung ausgegeben wird. Das Gerätetoken enthält eine Computer-ID, eine ID, die während der Individualisierung zugewiesen wird. Verwenden Sie diesen Bezeichner, um die Anzahl der Computer zu zählen, von denen aus ein Benutzer eine Lizenz beantragt oder einer Domäne beigetreten ist.

Es gibt zwei Möglichkeiten, den Bezeichner zu verwenden. Die `getUniqueId()` Methode gibt eine Zeichenfolge zurück, die dem Gerät während der Individualisierung zugewiesen wurde. Sie können die Zeichenfolgen in einer Datenbank speichern und nach Bezeichner suchen. Dieser Bezeichner ändert sich jedoch, wenn der Benutzer die Festplatte neu formatiert und erneut individualisiert. Dieser Bezeichner hat auch einen anderen Wert zwischen Adobe® AIR® und Adobe® Flash® Player in verschiedenen Browsern auf demselben Computer.

Um Maschinen genauer zu zählen, können Sie den gesamten Bezeichner `getBytes()` speichern. Um festzustellen, ob der Computer zuvor gesehen wurde, rufen Sie alle Bezeichner für einen Benutzernamen ab und prüfen Sie, ob eine Übereinstimmung vorliegt. `matches()` Da die `matches()` `MachineId.getBytes`Methode zum Vergleich der zurückgegebenen Werte verwendet werden muss, ist diese Option nur dann sinnvoll, wenn eine kleine Anzahl von Werten miteinander verglichen werden kann (z. B. die mit einem bestimmten Benutzer verbundenen Computer).
