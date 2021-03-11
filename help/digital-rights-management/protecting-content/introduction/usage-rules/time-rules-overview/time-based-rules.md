---
title: Übersicht über zeitbasierte Regeln
description: Übersicht über zeitbasierte Regeln
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Zeitbasierte Regeln {#time-based-rules}

Primetime DRM verwendet die &quot;weiche Durchsetzung&quot;zeitbasierter Lizenzbeschränkungen. Wenn während der Wiedergabe eines Videos ein Zeitrecht abläuft, schränkt Primetime DRM standardmäßig die Wiedergabe erst ein, wenn der Videostream das nächste Mal neu erstellt wird (durch Aufruf von `Netstream.stop()` und `Netstream.play()`).

Während die weiche Durchsetzung das Standardverhalten ist, können Sie auch eine harte Durchsetzung aktivieren, indem Sie eine der folgenden Aufgaben ausführen:

* Lassen Sie Ihren Videoplayer regelmäßig die Lizenz abfragen, um sicherzustellen, dass keine der Zeitbeschränkungen abgelaufen ist. Dies kann durch Aufruf von `DRMManager.loadVoucher(LOCAL_ONLY).` erreicht werden. Ein Fehlercode gibt an, dass die lokal gespeicherte Lizenz nicht mehr gültig ist.
* Wenn der Benutzer auf **[!UICONTROL Pause]** klickt, können Sie den aktuellen Video-Zeitstempel aufzeichnen und dann `Netstream.stop()` aufrufen. Wenn der Benutzer auf die Schaltfläche &quot;Abspielen&quot;klickt, können Sie zum aufgezeichneten Speicherort suchen und `Netstream.play()` aufrufen.