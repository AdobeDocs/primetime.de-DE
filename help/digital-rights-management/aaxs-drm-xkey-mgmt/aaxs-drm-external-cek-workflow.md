---
title: AAXS DRM External CEK Workflow
description: Dieser Workflow unterscheidet sich von den meisten vorhandenen DRM-Systemen, da kein zentrales Repository oder Content Key Management System (CKMS) verwendet werden muss
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# AAXS DRM External CEK Workflow{#aaxs-drm-external-cek-workflow}

Dieser Arbeitsablauf unterscheidet sich von den meisten vorhandenen DRM-Systemen, da er nicht die Verwendung eines zentralen Repository oder Content Key Management System (CKMS) erfordert. Für Kunden, die AAXS möchten, mit ihren vorhandenen CKMS zu arbeiten, bietet AAXS eine Funktion namens &quot;External CEK&quot;, in der das CEK extern zur Zeit der Paketerstellung und Lizenzausgabe bereitgestellt wird.

![](assets/ECEK_Workflow.PNG)

1. (Paket) Das AAXS Java SDK wird mit einer CEK und einer CEK ID bereitgestellt.
1. (Paket) Das CEK wird zum Verschlüsseln von Inhalten verwendet.
1. (Paket) Die CEK-ID wird in die DRM-Metadaten des Inhalts eingefügt.
1. Das Gerät versucht, Inhalte wiederzugeben, indem es eine Lizenz vom AAXS-Server anfordert.
1. (Lizenzierung) Der AAXS-Server extrahiert die CEK-ID aus den Inhaltsmetadaten.
1. Der AAXS-Server ruft den CEK aus dem CKMS ab.
1. (Lizenzierung) Der AAXS-Server gibt dem Gerät eine Lizenz aus, die das CEK enthält.
