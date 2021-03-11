---
title: Ausgabe von domänengebundenen Lizenzen
description: Ausgabe von domänengebundenen Lizenzen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# Ausgabe von domänengebundenen Lizenzen{#issuing-domain-bound-licenses}

Um eine Lizenz mithilfe einer DRM-Richtlinie auszustellen, die eine Domänenregistrierung erfordert, muss die Anforderung des Kunden ein gültiges Domänentoken enthalten, das vom in der Richtlinie angegebenen Domänenserver ausgegeben wird. Wenn der Client eine Lizenz anfordert, enthält er automatisch seine Domänen-Token für jeden Domänenserver, der in den Inhaltsmetadaten angegeben ist, sofern er sich bei diesen Domänenservern registriert hat. Wenn für die ausgewählte DRM-Richtlinie eine Domänenregistrierung erforderlich ist, wählt das SDK dann automatisch ein Domänentoken aus der Anforderung aus, an das die Lizenz gebunden werden soll, oder gibt einen Fehler zurück, wenn kein entsprechendes Domänentoken gefunden wurde.

Ein Domain-Token gilt als gültig, wenn es nicht abgelaufen ist und von einer autorisierten Domäne CA ausgegeben wurde. Der Lizenzserver muss die Domänenbehörden angeben, von denen er dann Domänentoken akzeptiert, indem er `HandlerConfiguration.setDomainCAs()` konfiguriert. Wenn keine Domänen-CAs konfiguriert sind, kann der Lizenzserver keine domänengebundenen Lizenzen ausstellen.

Wenn die Metadaten mehrere DRM-Richtlinien enthalten, kann die Geschäftslogik des Lizenzservers eine DRM-Richtlinie auswählen, die darauf basiert, ob der Client ein Domänentoken angezeigt hat. Sie können `LicenseRequestMessage.getDomainTokens()` verwenden, um die Domänen zu ermitteln, mit denen sich der Client registriert hat.
