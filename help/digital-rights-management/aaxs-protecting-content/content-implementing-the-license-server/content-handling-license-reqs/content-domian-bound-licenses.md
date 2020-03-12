---
seo-title: Erteilung von domänengebundenen Lizenzen
title: Erteilung von domänengebundenen Lizenzen
uuid: 175d3b7d-d1df-44ee-85ad-a0db4a1bdb9d
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Erteilung von domänengebundenen Lizenzen{#issuing-domain-bound-licenses}

Um eine Lizenz mithilfe einer Richtlinie auszustellen, die eine Domänenregistrierung erfordert, muss die Anforderung des Kunden ein gültiges Domänentoken enthalten, das vom in der Richtlinie angegebenen Domänenserver ausgegeben wird. Wenn der Client eine Lizenz anfordert, enthält er automatisch seine Domänen-Token für jeden Domänenserver, der in den Inhaltsmetadaten angegeben ist, sofern er sich bei diesen Domänenservern registriert hat. Wenn für die ausgewählte Richtlinie eine Domänenregistrierung erforderlich ist, wählt das SDK automatisch ein Domänentoken aus der Anforderung aus, an das die Lizenz gebunden werden soll, oder gibt einen Fehler zurück, wenn kein entsprechendes Domänentoken gefunden wurde.

Ein Domain-Token gilt als gültig, wenn es nicht abgelaufen ist und von einer autorisierten Domäne CA ausgegeben wurde. Der Lizenzserver muss die Domänenbehörden angeben, von denen er Domänentoken durch Konfiguration akzeptiert `HandlerConfiguration.setDomainCAs()`. Wenn keine Domänen-CAs konfiguriert sind, kann der Lizenzserver keine domänengebundenen Lizenzen ausstellen.

Wenn die Metadaten mehrere Richtlinien enthalten, kann die Geschäftslogik des Lizenzservers eine Richtlinie auswählen, die darauf basiert, ob der Client ein Domänentoken angezeigt hat. Ermitteln Sie `LicenseRequestMessage.getDomainTokens()` die Domänen, mit denen sich der Client registriert hat.
