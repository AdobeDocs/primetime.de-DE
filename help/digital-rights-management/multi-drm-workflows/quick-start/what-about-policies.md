---
description: Beim Festlegen von Richtlinien werden Bedingungen festgelegt, unter denen ein Benutzer geschützten Videoinhalt wiedergeben darf.
title: Richtlinien festlegen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Richtlinien{#setting-policies} festlegen

Beim Festlegen von Richtlinien werden Bedingungen festgelegt, unter denen ein Benutzer geschützten Videoinhalt wiedergeben darf.

Die Erstellung von Richtlinien erfolgt im Rahmen Ihrer Lizenztoken-Anforderung. (Ein Beispiel mit Widevine finden Sie unter [https://www.expressplay.com/developer/restapi/#widevine-license-token-request](https://www.expressplay.com/developer/restapi/#widevine-license-token-request).)

Sobald der serverseitige Code eines Kunden festgestellt hat, dass er eine Lizenz ausstellt (basierend auf Berechtigungsprüfungen, Geolocation oder anderen erforderlichen Informationen), fordert er ein Token an und *im Token* gibt es die erforderlichen `securityLevel`, `hdcpOutputControl` und `licenseDuration` an. Dies sind die clientseitigen Optionen für eine Widevine-Richtlinie. Andere DRM-Lösungen bieten ähnliche Ansätze, aber die Details unterscheiden sich in jedem Fall und werden in der Workflows detailliert beschrieben.

>[!NOTE]
>
>Adobe bietet einen Beispiel-Referenzserver, der zeigt, wie Sie Ihren eigenen Berechtigungsserver/Store implementieren: [Referenz-Server: Beispiel für einen ExpressPlay-Berechtigungsserver (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

