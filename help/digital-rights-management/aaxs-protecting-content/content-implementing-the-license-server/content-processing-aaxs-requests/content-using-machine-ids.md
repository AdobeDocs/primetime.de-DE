---
seo-title: Verwenden der Maschinenkennungen
title: Verwenden der Maschinenkennungen
uuid: 2832c158-fade-4bbf-ae89-f95ce9dfc369
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# Verwenden der Maschinenkennungen{#using-machine-identifiers}

Alle Anfragen zum Zugriff auf Adoben (mit Ausnahme von Anfragen, die FMRMS-Kompatibilität unterstützen) enthalten Informationen über das Computertoken, das dem Client während der Individualisierung ausgegeben wird. Das Gerätetoken enthält eine Computer-ID, eine ID, die während der Individualisierung zugewiesen wird. Verwenden Sie diesen Bezeichner, um die Anzahl der Computer zu zählen, von denen aus ein Benutzer eine Lizenz beantragt oder einer Domäne beigetreten ist.

Es gibt zwei Möglichkeiten, den Bezeichner zu verwenden. Die `getUniqueId()`-Methode gibt eine Zeichenfolge zurück, die dem Gerät während der Individualisierung zugewiesen wurde. Sie können die Zeichenfolgen in einer Datenbank speichern und nach Bezeichner suchen. Dieser Bezeichner ändert sich jedoch, wenn der Benutzer die Festplatte neu formatiert und erneut individualisiert. Dieser Bezeichner hat auch einen anderen Wert zwischen Adobe® AIR® und Adobe® Flash® Player in verschiedenen Browsern auf demselben Computer.

Um Maschinen genauer zu zählen, können Sie `getBytes()` verwenden, um den gesamten Bezeichner zu speichern. Um festzustellen, ob der Computer zuvor gesehen wurde, rufen Sie alle Bezeichner für einen Benutzernamen ab und rufen Sie `matches()` auf, um zu prüfen, ob eine Übereinstimmung vorliegt. Da die `matches()`-Methode zum Vergleich der von `MachineId.getBytes` zurückgegebenen Werte verwendet werden muss, ist diese Option nur dann sinnvoll, wenn eine kleine Anzahl von Werten verglichen werden muss (z. B. die mit einem bestimmten Benutzer verknüpften Maschinen).
