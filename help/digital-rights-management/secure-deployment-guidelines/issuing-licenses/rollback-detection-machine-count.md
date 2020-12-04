---
description: Wenn die Geschäftsregeln erfordern, dass die Anzahl der Computer für einen Benutzer verfolgt wird, müssen der Lizenzserver oder der Domänenserver die mit dem Benutzer verknüpften Computer-IDs speichern.
seo-description: Wenn die Geschäftsregeln erfordern, dass die Anzahl der Computer für einen Benutzer verfolgt wird, müssen der Lizenzserver oder der Domänenserver die mit dem Benutzer verknüpften Computer-IDs speichern.
seo-title: Maschinenzahl bei Erteilung der Lizenzen
title: Maschinenzahl bei Erteilung der Lizenzen
uuid: 7ba8a8d4-a31f-4f37-82a7-755cfa443544
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---


# Maschinenanzahl bei der Erteilung von Lizenzen {#machine-count-when-issuing-licenses}

Wenn die Geschäftsregeln erfordern, dass die Anzahl der Computer für einen Benutzer verfolgt wird, müssen der Lizenzserver oder der Domänenserver die mit dem Benutzer verknüpften Computer-IDs speichern.

Die zuverlässigste Methode zur Verfolgung von Computer-IDs besteht darin, den von der [MachineId.getBytes()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes())-Methode zurückgegebenen Wert in einer Datenbank zu speichern. Wenn eine neue Anforderung empfangen wird, vergleichen Sie die Computer-ID in der Anforderung mit den bekannten Computer-IDs, indem Sie [MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) verwenden.

[MachineId.match() ](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) führt einen ID-Vergleich durch, um zu ermitteln, ob die IDs für denselben Computer stehen. Dieser Vergleich ist nur sinnvoll, wenn eine kleine Anzahl von Computer-IDs vorhanden ist. Wenn Benutzer beispielsweise fünf Computer in ihrer Domäne zulassen, können Sie in der Datenbank nach den Computer-IDs suchen, die mit dem Benutzernamen des Benutzers verknüpft sind, und einen kleinen Datensatz zum Vergleich abrufen.

Dieser Vergleich ist bei Bereitstellungen, die anonymen Zugriff zulassen, nicht praktikabel. In diesem Fall kann [MachineId.getUniqueID()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) verwendet werden. Diese ID kann jedoch nicht identisch sein, wenn der Benutzer über Flash und Adobe AIR®-Laufzeitumgebungen auf Inhalte zugreift.

>[!NOTE]
>
>Die ID überlebt nicht, wenn der Benutzer die Festplatte neu formatiert.