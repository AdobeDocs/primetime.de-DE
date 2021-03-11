---
title: Domänenregistrierung des Geräts
description: Domänenregistrierung des Geräts
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Gerätegruppendomänenregistrierung{#device-group-domain-registration}

Alternativ zur Bindung einer Lizenz an ein bestimmtes Gerät unterstützt Adobe Access 3.0 und höher die Bindung von Lizenzen an eine Gerätedomäne. Mehrere Geräte können einer Domäne beitreten und Domänentoken empfangen. Nachdem ein Gerät in der Domäne eine Lizenz erworben hat, kann die Lizenz auf ein anderes Gerät in der Domäne übertragen werden, und diese Geräte können den Inhalt abspielen, ohne eine Lizenz direkt vom Lizenzserver zu erwerben.

Zur Unterstützung der domänengebundenen Lizenzen muss die Richtlinie den Domänenserver angeben, bei dem sich der Client registrieren muss. Die Richtlinie legt außerdem die Authentifizierungsanforderungen für den Domänenserver fest (ob anonymer Zugriff zulässig ist oder ob der Server Benutzername/Kennwort oder benutzerdefinierte Authentifizierung erfordert).

Domänenregistrierungs- und domänengebundene Lizenzen werden von Adobe Access Clients ab Version 3.0 unterstützt. Wenn ein älterer Client oder ein Adobe Access 3.0-Client in Flash Player eine Lizenz für Inhalte anfordert, die die Domänenregistrierung unterstützen, kann der Lizenzserver eine Lizenz mit einer anderen Richtlinie ausstellen, die die Bindung an ein bestimmtes Gerät unterstützt.
