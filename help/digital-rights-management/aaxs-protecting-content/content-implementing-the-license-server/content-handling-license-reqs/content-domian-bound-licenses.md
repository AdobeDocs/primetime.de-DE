---
title: Erteilung von Domain-gebundenen Lizenzen
description: Erteilung von Domain-gebundenen Lizenzen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Erteilung von Domain-gebundenen Lizenzen{#issuing-domain-bound-licenses}

Um eine Lizenz mithilfe einer Richtlinie zu erteilen, die eine Domänenregistrierung erfordert, muss die Anfrage des Kunden ein gültiges Domain-Token enthalten, das von dem in der Richtlinie angegebenen Domain-Server ausgegeben wird. Wenn der Client eine Lizenz anfordert, enthält er automatisch seine Domänen-Token für jeden Domänen-Server, der in den Inhaltsmetadaten angegeben ist, wenn er sich bei diesen Domänenservern registriert hat. Wenn für die ausgewählte Richtlinie eine Domänenregistrierung erforderlich ist, wählt das SDK automatisch ein Domänen-Token aus der Anforderung aus, an das die Lizenz gebunden werden soll, oder gibt einen Fehler zurück, wenn kein entsprechendes Domänen-Token gefunden wurde.

Ein Domain-Token gilt als gültig, wenn es nicht abgelaufen ist und von einer autorisierten Domain CA ausgegeben wurde. Der Lizenzserver muss die Domänenbehörden angeben, von denen er Domain-Token akzeptiert, indem er `HandlerConfiguration.setDomainCAs()`. Wenn keine Domain-CAs konfiguriert sind, kann der Lizenzserver keine domänengebundenen Lizenzen ausstellen.

Wenn die Metadaten mehrere Richtlinien enthalten, kann die Geschäftslogik des Lizenzservers abhängig davon eine Richtlinie auswählen, ob der Client ein Domänen-Token angezeigt hat. Verwendung `LicenseRequestMessage.getDomainTokens()` , um die Domänen zu bestimmen, mit denen sich der Client registriert hat.
