---
seo-title: Domänenregistrierung des Geräts
title: Domänenregistrierung des Geräts
uuid: 221bf6c3-0568-443d-b761-64715a57ada6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Domänenregistrierung des Geräts{#device-group-domain-registration}

Als Alternative zur Bindung einer Lizenz an ein bestimmtes Gerät unterstützt Primetime DRM 3.0 oder höher die Bindung von Lizenzen an eine Gerätedomäne.

Mehrere Geräte können einer Domäne beitreten und Domänentoken empfangen. Nachdem ein Gerät in der Domäne eine Lizenz erworben hat, kann die Lizenz auf ein anderes Gerät in der Domäne übertragen werden, und diese Geräte können den Inhalt abspielen, ohne eine Lizenz direkt vom Lizenzserver zu erwerben.

Wenn Sie domänengebundene Lizenzen unterstützen möchten, muss die Primetime-DRM-Richtlinie den Domänenserver angeben, bei dem sich der Client registrieren muss. Die Primetime-DRM-Richtlinie muss außerdem die Authentifizierungsanforderungen für den Domänenserver angeben, ob der anonyme Zugriff aktiviert ist oder ob der Server Benutzername/Kennwort oder benutzerdefinierte Authentifizierung erfordert.

Domänenregistrierung und domänengebundene Lizenzen werden von Primetime DRM-Clients Version 3.0 oder höher unterstützt. Wenn ein älterer Client oder ein Adobe Primetime 3.0-Client in Flash Player eine Lizenz für Inhalte anfordert, die die Domänenregistrierung unterstützen, kann der Lizenzserver eine Lizenz ausstellen, die eine alternative Primetime DRM-Richtlinie verwendet, um die Bindung an ein bestimmtes Gerät zu unterstützen.
