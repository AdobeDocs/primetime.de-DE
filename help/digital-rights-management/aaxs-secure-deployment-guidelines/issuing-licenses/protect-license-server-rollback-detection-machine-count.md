---
title: Maschinenzahl bei Erteilung der Lizenzen
description: Maschinenzahl bei Erteilung der Lizenzen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# Maschinenzahl bei Erteilung der Lizenzen{#machine-count-when-issuing-licenses}

Wenn die Geschäftsregeln erfordern, dass die Anzahl der Computer für einen Benutzer verfolgt wird, muss der Lizenzserver oder der Domänenserver die mit dem Benutzer verknüpften Computer-IDs speichern. Die zuverlässigste Methode zur Verfolgung von Computer-IDs besteht darin, den Wert zu speichern, der von der `MachineId.getBytes()` -Methode in einer Datenbank. Wenn eine neue Anforderung eingeht, vergleichen Sie die Computer-ID in der Anfrage mit den bekannten Computer-IDs mit `MachineId.matches()`.

`MachineId.matches()` führt einen Vergleich von IDs durch, um zu ermitteln, ob sie denselben Computer repräsentieren. Dieser Vergleich ist nur dann praktisch, wenn eine geringe Anzahl von Computer-IDs miteinander verglichen werden kann. Wenn einem Benutzer beispielsweise fünf Computer innerhalb seiner Domäne gestattet sind, können Sie in der Datenbank nach den mit dem Benutzernamen des Benutzers verknüpften Computer-IDs suchen und einen kleinen Datensatz abrufen, mit dem er vergleichen kann.

>[!NOTE]
>
>Dieser Vergleich ist bei Implementierungen, die einen anonymen Zugriff zulassen, nicht praktikabel. In diesen Fällen `MachineId.getUniqueID()` kann jedoch verwendet werden. Diese ID ist nicht identisch, wenn der Benutzer auf Inhalte von Flash und Adobe AIR®-Laufzeitumgebungen zugreift, und überlebt nicht, wenn der Benutzer seine Festplatte umformatiert.

Weitere Informationen zu `MachineToken.getMachineId()`und `MachineId.matches()`, siehe *Adobe Access API-Referenz*.
