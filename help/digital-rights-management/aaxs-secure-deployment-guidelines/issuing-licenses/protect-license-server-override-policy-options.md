---
title: Überschreiben von Richtlinienoptionen
description: Überschreiben von Richtlinienoptionen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Überschreiben von Richtlinienoptionen{#overriding-policy-options}

Bei der Lizenzerteilung ist es möglich, dass der Lizenzserver die in der Richtlinie angegebenen Nutzungsregeln außer Kraft setzt. Wenn die Richtlinie ein Startdatum angibt, wird vor diesem Startdatum keine Lizenz generiert. Es ist jedoch möglich, ein künftiges Startdatum in der Lizenz festzulegen, nachdem die Lizenz generiert wurde. Diese Option sollte mit Vorsicht verwendet werden, da der Client den Benutzer nicht daran hindert, die Systemzeit vorwärts zu verschieben, um das Startdatum zu umgehen.
