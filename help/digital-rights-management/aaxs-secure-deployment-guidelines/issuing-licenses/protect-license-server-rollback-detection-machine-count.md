---
title: Maschinenzahl bei Erteilung der Lizenzen
description: Maschinenzahl bei Erteilung der Lizenzen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---


# Anzahl der Computer bei der Lizenzerteilung{#machine-count-when-issuing-licenses}

Wenn die Geschäftsregeln erfordern, dass die Anzahl der Computer für einen Benutzer verfolgt wird, müssen der Lizenzserver oder der Domänenserver die mit dem Benutzer verknüpften Computer-IDs speichern. Die zuverlässigste Methode zur Verfolgung von Computer-IDs besteht darin, den von der `MachineId.getBytes()`-Methode zurückgegebenen Wert in einer Datenbank zu speichern. Wenn eine neue Anforderung eingeht, vergleichen Sie die Computer-ID in der Anforderung mit den bekannten Computer-IDs mit `MachineId.matches()`.

`MachineId.matches()` führt einen Vergleich der IDs durch, um zu ermitteln, ob sie denselben Computer repräsentieren. Dieser Vergleich ist nur dann sinnvoll, wenn es eine kleine Anzahl von Computer-IDs gibt, mit denen verglichen werden kann. Wenn einem Benutzer beispielsweise fünf Computer in seiner Domäne zugewiesen sind, können Sie in der Datenbank nach den mit dem Benutzernamen verknüpften Computer-IDs suchen und einen kleinen Datensatz zum Vergleich abrufen.

>[!NOTE]
>
>Dieser Vergleich ist bei Bereitstellungen, die anonymen Zugriff ermöglichen, nicht praktikabel. In solchen Fällen kann `MachineId.getUniqueID()` verwendet werden. Diese ID ist jedoch nicht identisch, wenn der Benutzer auf Inhalte von Flash- und Adobe AIR®-Laufzeitumgebungen zugreift, und überlebt nicht, wenn der Benutzer die Festplatte neu formatiert.

Weitere Informationen zu `MachineToken.getMachineId()`und `MachineId.matches()` finden Sie unter *API-Referenz für den Zugriff auf Adoben*.
