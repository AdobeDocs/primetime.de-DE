---
title: Workflow "AAXS DRM External CEK"
description: Dieser Workflow unterscheidet sich von den meisten vorhandenen DRM-Systemen, da er keine Verwendung von zentralem Repository oder Content Key Management System (CKMS) erfordert
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Workflow &quot;AAXS DRM External CEK&quot;{#aaxs-drm-external-cek-workflow}

Dieser Workflow unterscheidet sich von den meisten vorhandenen DRM-Systemen, da hierfür kein zentrales Repository oder Content Key Management System (CKMS) erforderlich ist. Für Kunden, die AAXS wünschen, mit ihrem bestehenden CKMS zu arbeiten, bietet AAXS eine Funktion namens &quot;External CEK&quot;, in der das CEK extern bei der Verpackung und Lizenzausgabe bereitgestellt wird.

![](assets/ECEK_Workflow.PNG)

1. (Package) Das AXS Java SDK wird mit einem CEK und einer CEK ID bereitgestellt.
1. (Package) Das CEK wird zum Verschlüsseln von Inhalten verwendet.
1. (Package) Die CEK-ID wird in die DRM-Metadaten des Inhalts eingefügt.
1. Das Gerät versucht, Inhalte wiederzugeben, indem es eine Lizenz vom AXS-Server anfordert.
1. (Lizenzierung) Der AXS-Server extrahiert die CEK-ID aus den Inhaltsmetadaten.
1. Der AXS-Server ruft den CEK aus dem CKMS ab.
1. (Lizenzierung) Der AXS-Server gibt dem Gerät eine Lizenz aus, die das CEK enthält.
