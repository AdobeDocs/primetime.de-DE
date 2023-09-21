---
title: Erteilung von domänengebundenen Lizenzen
description: Erteilung von domänengebundenen Lizenzen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Erteilung von domänengebundenen Lizenzen{#issuing-domain-bound-licenses}

Um eine Lizenz mithilfe einer DRM-Richtlinie zu erteilen, für die eine Domänenregistrierung erforderlich ist, muss die Anfrage des Kunden ein gültiges Domain-Token enthalten, das vom in der Richtlinie angegebenen Domänenserver ausgestellt wurde. Wenn der Client eine Lizenz anfordert, enthält er automatisch seine Domänen-Token für jeden Domänenserver, der in den Inhaltsmetadaten angegeben ist, sofern er sich bei diesen Domänenservern registriert hat. Wenn für die ausgewählte DRM-Richtlinie eine Domänenregistrierung erforderlich ist, wählt das SDK dann automatisch ein Domänen-Token aus der Anforderung aus, an das die Lizenz gebunden werden soll, oder gibt einen Fehler zurück, wenn kein geeignetes Domänen-Token gefunden wurde.

Ein Domain-Token gilt als gültig, wenn es nicht abgelaufen ist und von einer autorisierten Domain CA ausgegeben wurde. Der Lizenzserver muss die Domänenbehörden angeben, von denen er dann Domain-Token akzeptiert, indem er `HandlerConfiguration.setDomainCAs()`. Wenn keine Domain-CAs konfiguriert sind, kann der Lizenzserver keine domänengebundenen Lizenzen ausstellen.

Wenn die Metadaten mehrere DRM-Richtlinien enthalten, kann die Geschäftslogik des Lizenzservers eine DRM-Richtlinie auswählen, die darauf basiert, ob der Client ein Domänen-Token angezeigt hat. Sie können `LicenseRequestMessage.getDomainTokens()` , um die Domänen zu bestimmen, mit denen sich der Client registriert hat.
