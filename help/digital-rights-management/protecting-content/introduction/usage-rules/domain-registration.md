---
title: Registrierung der Gerätegruppendomäne
description: Registrierung der Gerätegruppendomäne
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---

# Registrierung der Gerätegruppendomäne{#device-group-domain-registration}

Als Alternative zur Bindung einer Lizenz an ein bestimmtes Gerät unterstützt Primetime DRM 3.0 oder höher die Bindung von Lizenzen an eine Gerätedomäne.

Mehrere Geräte können einer Domäne beitreten und Domänen-Token empfangen. Nachdem ein Gerät in der Domäne eine Lizenz erworben hat, kann die Lizenz auf ein anderes Gerät in der Domäne übertragen werden. Diese Geräte können den Inhalt wiedergeben, ohne eine Lizenz direkt vom Lizenzserver zu erwerben.

Wenn Sie domänengebundene Lizenzen unterstützen möchten, muss die Primetime-DRM-Richtlinie den Domänenserver angeben, bei dem sich der Client registrieren muss. Die Primetime-DRM-Richtlinie muss außerdem die Authentifizierungsanforderungen für den Domänenserver angeben, ob der anonyme Zugriff aktiviert ist oder ob der Server Benutzername/Kennwort oder benutzerdefinierte Authentifizierung erfordert.

Domain-Registrierung und domänengebundene Lizenzen werden von den Primetime DRM-Clients Version 3.0 oder höher unterstützt. Wenn ein älterer Client oder ein Adobe Primetime 3.0-Client unter Flash Player eine Lizenz für Inhalte anfordert, die die Domänenregistrierung unterstützen, kann der Lizenzserver eine Lizenz ausstellen, die eine alternative Primetime-DRM-Richtlinie verwendet, um die Bindung an ein bestimmtes Gerät zu unterstützen.
