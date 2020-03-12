---
seo-title: AAXS DRM External CEK Workflow
title: AAXS DRM External CEK Workflow
description: Dieser Workflow unterscheidet sich von den meisten vorhandenen DRM-Systemen, da kein zentrales Repository oder Content Key Management System (CKMS) verwendet werden muss
seo-description: Dieser Workflow unterscheidet sich von den meisten vorhandenen DRM-Systemen, da kein zentrales Repository oder Content Key Management System (CKMS) verwendet werden muss
uuid: b313594b-0feb-4f27-bf02-f04b955e2140
translation-type: tm+mt
source-git-commit: 17a492d30c65b1b5e12419f04afa0116654b99fc

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
