---
description: 'null'
seo-description: 'null'
seo-title: Vorbereiten von Kennwörtern für die Dateien mit den Servereigenschaften
title: Vorbereiten von Kennwörtern für die Dateien mit den Servereigenschaften
uuid: 3e00ba9b-b692-4713-8306-5ab896461f2a
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Vorbereiten von Kennwörtern für die Dateien mit den Servereigenschaften{#prepare-passwords-for-the-server-properties-files}

Die Referenz-Implementierung bietet `ScrambleUtil.class`eine Klasse, die die Sicherheit des Kennworts Ihrer Berechtigung gewährleistet.

Verwenden Sie dieses Tool, um das Kennwort zu verschlüsseln, bevor Sie es in die [!DNL flashaccess-refimpl.properties] Datei aufnehmen.

Zum Ausführen des Tools können Sie entweder ein Ant-Skript oder Java verwenden.

Das Dienstprogramm generiert das verschlüsselte Kennwort, das Sie in die [!DNL flashaccess-refimpl.properties] Datei kopieren müssen.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Kennwörter, die mit der `ScrambleUtil.class` , die mit der Referenz-Implementierung bereitgestellt wurde, kodiert wurden, funktionieren nicht mit dem Primetime DRM-Server für geschütztes Streaming.
