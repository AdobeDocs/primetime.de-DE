---
description: Überprüfen Sie die Einschränkungen und Anforderungen für Streams und Playlists (Manifeste), einschließlich DRM-Verschlüsselungsschlüssel.
title: Anforderungen an Inhalt und Manifest
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---


# Anforderungen an Inhalt und Manifest {#content-and-manifest-requirements}

Überprüfen Sie die Einschränkungen und Anforderungen für Streams und Playlists (Manifeste), einschließlich DRM-Verschlüsselungsschlüssel.

| Fügen Sie die `RESOLUTION`-Eigenschaft für jeden ABR-Stream in die Manifestdatei ein und legen Sie sie fest. Sie müssen Flash Player 14 oder höher verwenden. |
|---|
| Wenn der DRM-geschützte Stream eine Mehrfach-Bitrate (MBR) aufweist, sollte der DRM-Verschlüsselungsschlüssel, der für den MBR verwendet wird, mit dem in allen Bitratenströmen verwendeten Schlüssel übereinstimmen. |
| Muss die gleichen Bitratendarstellungen haben wie die Darstellungen des Hauptinhalts. |