---
title: Vorbereiten von Kennwörtern für die Dateien mit den Servereigenschaften
description: Vorbereiten von Kennwörtern für die Dateien mit den Servereigenschaften
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---


# Vorbereiten von Kennwörtern für die Dateien mit den Servereigenschaften{#prepare-passwords-for-the-server-properties-files}

Die Referenz-Implementierung stellt `ScrambleUtil.class` bereit, eine Klasse, die die Sicherheit des Kennworts Ihrer Berechtigung gewährleistet.

Verwenden Sie dieses Tool, um das Kennwort zu verschlüsseln, bevor Sie es in die Datei [!DNL flashaccess-refimpl.properties] einschließen.

Zum Ausführen des Tools können Sie entweder ein Ant-Skript oder Java verwenden.

Das Dienstprogramm generiert das verschlüsselte Kennwort, das Sie in die Datei [!DNL flashaccess-refimpl.properties] kopieren müssen.

>[!NOTE]
>
>Kennwörter, die mit der Referenzimplementierung von `ScrambleUtil.class` kodiert wurden, funktionieren nicht mit dem Primetime DRM-Server für geschütztes Streaming.
