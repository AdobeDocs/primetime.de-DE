---
description: Überprüfen Sie die Einschränkungen und Anforderungen für Streams und Wiedergabelisten (Manifeste), einschließlich DRM-Verschlüsselungsschlüssel.
title: Anforderungen an Inhalt und Manifest
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---

# Anforderungen an Inhalt und Manifest {#content-and-manifest-requirements}

Überprüfen Sie die Einschränkungen und Anforderungen für Streams und Wiedergabelisten (Manifeste), einschließlich DRM-Verschlüsselungsschlüssel.

| Fügen Sie ein und legen Sie die `RESOLUTION` -Eigenschaft für jeden ABR-Stream in der Manifestdatei. Sie müssen Flash Player 14 oder höher verwenden. |
|---|
| Wenn der DRM-geschützte Stream eine Mehrfach-Bitrate (MBR) aufweist, sollte der für den MBR verwendete DRM-Verschlüsselungsschlüssel mit dem Schlüssel übereinstimmen, der in allen Bitratenströmen verwendet wird. |
| Muss über dieselbe Bitrate wie die Ausgabeformate des Hauptinhalts verfügen. |
