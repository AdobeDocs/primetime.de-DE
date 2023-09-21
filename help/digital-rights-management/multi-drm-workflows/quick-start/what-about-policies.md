---
description: Beim Festlegen von Richtlinien werden Bedingungen festgelegt, unter denen Benutzer geschützte Videoinhalte wiedergeben können.
title: Festlegen von Richtlinien
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Festlegen von Richtlinien{#setting-policies}

Beim Festlegen von Richtlinien werden Bedingungen festgelegt, unter denen Benutzer geschützte Videoinhalte wiedergeben können.

Die Erstellung von Richtlinien erfolgt im Rahmen Ihrer Lizenztoken-Anfrage. (Siehe [https://www.expressplay.com/developer/restapi/#widevine-license-token-request](https://www.expressplay.com/developer/restapi/#widevine-license-token-request) für ein Beispiel mit Widevine).

Sobald der serverseitige Code eines Kunden festgestellt hat, dass er eine Lizenz ausstellt (basierend auf Berechtigungsprüfungen, Geolocation oder anderen erforderlichen Informationen), fordert er ein Token an und *im Token* Gibt die erforderliche `securityLevel`, `hdcpOutputControl`, und `licenseDuration`. Dies sind die clientseitigen Optionen für eine umfassende Richtlinie. Andere DRM-Lösungen bieten ähnliche Ansätze, aber die Details unterscheiden sich in jedem Fall und werden in den einzelnen Workflows erläutert.

>[!NOTE]
>
>Adobe stellt einen Beispiel-Referenz-Server bereit, der zeigt, wie Sie Ihren eigenen Berechtigungsserver/Ihre Storefront implementieren: [Referenz-Server: Beispiel für ExpressPlay Entitlement Server (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)
