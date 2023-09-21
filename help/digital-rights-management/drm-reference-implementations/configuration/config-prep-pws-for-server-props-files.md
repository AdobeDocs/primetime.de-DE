---
title: Vorbereiten von Kennwörtern für die Servereigenschaftsdateien
description: Vorbereiten von Kennwörtern für die Servereigenschaftsdateien
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# Vorbereiten von Kennwörtern für die Servereigenschaftsdateien{#prepare-passwords-for-the-server-properties-files}

Die Referenzimplementierung bietet `ScrambleUtil.class`: eine Klasse, die die Sicherheit des Kennworts Ihrer Berechtigung gewährleistet.

Verwenden Sie dieses Tool, um das Kennwort zu verschlüsseln, bevor Sie es in die [!DNL flashaccess-refimpl.properties] -Datei.

Um das Tool auszuführen, können Sie entweder ein Ant-Skript oder Java verwenden.

Das Dienstprogramm generiert das verschlüsselte Kennwort, das Sie in die [!DNL flashaccess-refimpl.properties] -Datei.

>[!NOTE]
>
>Mit der Variablen `ScrambleUtil.class` die mit der Referenzimplementierung bereitgestellt wurden, funktionieren nicht mit dem Primetime-DRM-Server für geschütztes Streaming.
