---
description: Überprüfen Sie die Einschränkungen und Anforderungen für Streams und Playlists (Manifeste), einschließlich DRM-Verschlüsselungsschlüssel.
seo-description: Überprüfen Sie die Einschränkungen und Anforderungen für Streams und Playlists (Manifeste), einschließlich DRM-Verschlüsselungsschlüssel.
seo-title: Anforderungen an Inhalt und Manifest
title: Anforderungen an Inhalt und Manifest
uuid: 53cc570a-be33-4488-95e8-43f91b559b13
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Anforderungen an Inhalt und Manifest {#content-and-manifest-requirements}

Überprüfen Sie die Einschränkungen und Anforderungen für Streams und Playlists (Manifeste), einschließlich DRM-Verschlüsselungsschlüssel.

| Schließen Sie die `RESOLUTION` Eigenschaft für jeden ABR-Stream in die Manifestdatei ein und legen Sie sie fest. Sie müssen Flash Player 14 oder höher verwenden. |
|---|
| Wenn der DRM-geschützte Stream eine Mehrfach-Bitrate (MBR) aufweist, sollte der DRM-Verschlüsselungsschlüssel, der für den MBR verwendet wird, mit dem in allen Bitratenströmen verwendeten Schlüssel übereinstimmen. |
| Muss die gleichen Bitratendarstellungen haben wie die Darstellungen des Hauptinhalts. |