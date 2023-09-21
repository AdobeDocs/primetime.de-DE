---
title: Registrierung der Gerätegruppendomäne
description: Registrierung der Gerätegruppendomäne
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Registrierung der Gerätegruppendomäne{#device-group-domain-registration}

Als Alternative zum Binden einer Lizenz an ein bestimmtes Gerät unterstützt Adobe Access 3.0 und höher das Binden von Lizenzen an eine Gerätedomäne. Mehrere Geräte können einer Domäne beitreten und Domänen-Token empfangen. Nachdem ein Gerät in der Domäne eine Lizenz erworben hat, kann die Lizenz auf ein anderes Gerät in der Domäne übertragen werden. Diese Geräte können den Inhalt wiedergeben, ohne eine Lizenz direkt vom Lizenzserver zu erwerben.

Um die domänengebundenen Lizenzen zu unterstützen, muss die Richtlinie den Domänenserver angeben, bei dem sich der Client registrieren muss. Die Richtlinie legt außerdem die Authentifizierungsanforderungen für den Domänenserver fest (ob anonymer Zugriff zulässig ist oder ob der Server Benutzernamen/Kennwort oder benutzerdefinierte Authentifizierung erfordert).

Domain-Registrierung und domänengebundene Lizenzen werden von Adobe Access-Clients ab Version 3.0 unterstützt. Wenn ein älterer Client oder ein Adobe Access 3.0-Client unter Flash Player eine Lizenz für Inhalte anfordert, die die Domänenregistrierung unterstützen, kann der Lizenzserver eine Lizenz unter Verwendung einer alternativen Richtlinie ausstellen, die die Bindung an ein bestimmtes Gerät unterstützt.
