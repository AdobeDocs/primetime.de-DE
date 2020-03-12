---
seo-title: Maschinenzahl bei Erteilung der Lizenzen
title: Maschinenzahl bei Erteilung der Lizenzen
uuid: d57f8b0b-0363-4b26-bd71-76f4abe5b68f
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Maschinenzahl bei Erteilung der Lizenzen{#machine-count-when-issuing-licenses}

Wenn die Geschäftsregeln erfordern, dass die Anzahl der Computer für einen Benutzer verfolgt wird, müssen der Lizenzserver oder der Domänenserver die mit dem Benutzer verknüpften Computer-IDs speichern. Die zuverlässigste Methode zur Verfolgung von Computer-IDs besteht darin, den von der `MachineId.getBytes()` Methode zurückgegebenen Wert in einer Datenbank zu speichern. Wenn eine neue Anforderung eingeht, vergleichen Sie die Computer-ID in der Anforderung mit den bekannten Computer-IDs, die `MachineId.matches()`verwenden.

`MachineId.matches()` führt einen Vergleich der IDs durch, um zu ermitteln, ob sie denselben Computer repräsentieren. Dieser Vergleich ist nur dann sinnvoll, wenn es eine kleine Anzahl von Computer-IDs gibt, mit denen verglichen werden kann. Wenn einem Benutzer beispielsweise fünf Computer in seiner Domäne zugewiesen sind, können Sie in der Datenbank nach den mit dem Benutzernamen verknüpften Computer-IDs suchen und einen kleinen Datensatz zum Vergleich abrufen.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Dieser Vergleich ist bei Bereitstellungen, die anonymen Zugriff ermöglichen, nicht praktikabel. In solchen Fällen `MachineId.getUniqueID()` kann diese ID jedoch nicht verwendet werden, wenn der Benutzer auf Inhalte aus Flash- und Adobe AIR®-Laufzeitumgebungen zugreift, und nicht überlebt, wenn der Benutzer die Festplatte neu formatiert.

Weitere Informationen `MachineToken.getMachineId()`und `MachineId.matches()`Informationen finden Sie in der *Adobe Access API-Referenz*.
