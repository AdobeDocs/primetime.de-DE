---
seo-title: Domänenregistrierung des Geräts
title: Domänenregistrierung des Geräts
uuid: fd559175-2c3c-4d71-bfa1-8de9907d2b7c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Gerätegruppendomänenregistrierung{#device-group-domain-registration}

Alternativ zur Bindung einer Lizenz an ein bestimmtes Gerät unterstützt Adobe Access 3.0 und höher die Bindung von Lizenzen an eine Gerätedomäne. Mehrere Geräte können einer Domäne beitreten und Domänentoken empfangen. Nachdem ein Gerät in der Domäne eine Lizenz erworben hat, kann die Lizenz auf ein anderes Gerät in der Domäne übertragen werden, und diese Geräte können den Inhalt abspielen, ohne eine Lizenz direkt vom Lizenzserver zu erwerben.

Zur Unterstützung der domänengebundenen Lizenzen muss die Richtlinie den Domänenserver angeben, bei dem sich der Client registrieren muss. Die Richtlinie legt außerdem die Authentifizierungsanforderungen für den Domänenserver fest (ob anonymer Zugriff zulässig ist oder ob der Server Benutzername/Kennwort oder benutzerdefinierte Authentifizierung erfordert).

Domänenregistrierungs- und domänengebundene Lizenzen werden von Adobe Access Clients ab Version 3.0 unterstützt. Wenn ein älterer Client oder ein Adobe Access 3.0-Client in Flash Player eine Lizenz für Inhalte anfordert, die die Domänenregistrierung unterstützen, kann der Lizenzserver eine Lizenz mit einer anderen Richtlinie ausstellen, die die Bindung an ein bestimmtes Gerät unterstützt.
