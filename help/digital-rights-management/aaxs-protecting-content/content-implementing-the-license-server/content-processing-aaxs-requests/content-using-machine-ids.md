---
title: Verwenden von Maschinenkennungen
description: Verwenden von Maschinenkennungen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Verwenden von Maschinenkennungen{#using-machine-identifiers}

Alle Adobe Access-Anfragen (mit Ausnahme von Anfragen, die die FMRMS-Kompatibilität unterstützen) enthalten Informationen über das Computer-Token, das dem Client während der Individualisierung zugewiesen wurde. Das Machine-Token enthält eine Machine Id, eine Kennung, die während der Individualisierung zugewiesen wird. Verwenden Sie diese Kennung, um die Anzahl der Computer zu zählen, von denen aus ein Benutzer eine Lizenz angefordert oder einer Domäne beigetreten ist.

Es gibt zwei Möglichkeiten, die Kennung zu verwenden. Die `getUniqueId()` -Methode gibt eine Zeichenfolge zurück, die dem Gerät während der Individualisierung zugewiesen wurde. Sie können die Zeichenfolgen in einer Datenbank speichern und nach Kennung suchen. Diese Kennung ändert sich jedoch, wenn der Benutzer die Festplatte neu formatiert und erneut individualisiert. Dieser Bezeichner hat auch einen anderen Wert zwischen Adobe® AIR® und Adobe® Flash® Player in verschiedenen Browsern auf demselben Computer.

Um Maschinen genauer zu zählen, können Sie `getBytes()` zum Speichern der gesamten Kennung. Um festzustellen, ob der Computer zuvor gesehen wurde, rufen Sie alle Kennungen für einen Benutzernamen ab und rufen Sie auf `matches()` , um zu überprüfen, ob eine Übereinstimmung vorliegt. Da die `matches()` -Methode verwendet werden, um die von `MachineId.getBytes`, ist diese Option nur praktisch, wenn eine kleine Anzahl von Werten zu vergleichen ist (z. B. die mit einem bestimmten Benutzer verbundenen Maschinen).
