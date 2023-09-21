---
title: Best Practices für begleitende Banneranzeigen
description: Best Practices für begleitende Banneranzeigen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Best Practices für begleitende Banneranzeigen {#best-practices-for-companion-banner-ads}

TVSDK unterstützt begleitende Banneranzeigen, bei denen es sich um Anzeigen handelt, die eine lineare Anzeige begleiten und häufig nach dem Ende der linearen Anzeige auf der Seite bleiben. Ihre Anwendung ist für die Anzeige der begleitenden Banner verantwortlich, die mit einer linearen Anzeige bereitgestellt werden.

Befolgen Sie beim Anzeigen von begleitenden Anzeigen die folgenden Empfehlungen:

* Versuchen Sie, so viele begleitende Banneranzeigen einer Videoanzeige wie im Layout Ihres Players verfügbar zu machen.
* Zeigen Sie ein begleitendes Banner nur dann an, wenn Sie eine Position haben, die der angegebenen Höhe und Breite der Anzeige entspricht.

  >[!IMPORTANT]
  >
  >Ändern Sie die Größe der Anzeige nicht.

* Zeigen Sie die begleitenden Banner so bald wie möglich nach Beginn der Anzeige an.
* Überlagern Sie den Haupt-Anzeigen-/Video-Container nicht mit begleitenden Bannern.
* Sie können begleitende Banner nach dem Ende der Anzeige anzeigen.

Standardmäßig wird jedes begleitende Banner angezeigt, bis Sie einen Ersatz für die Anzeige haben.
