---
seo-title: Übersicht über zeitbasierte Regeln
title: Übersicht über zeitbasierte Regeln
uuid: 10b7766e-3b1a-4d8a-ba15-46976aa0847d
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Zeitbasierte Regeln {#time-based-rules}

Primetime DRM verwendet die &quot;weiche Durchsetzung&quot;zeitbasierter Lizenzbeschränkungen. Wenn während der Wiedergabe eines Videos ein Zeitrecht abläuft, schränkt Primetime DRM standardmäßig die Wiedergabe erst ein, wenn der Videostream das nächste Mal neu erstellt wird (durch Aufruf von `Netstream.stop()` und `Netstream.play()`).

Während die weiche Durchsetzung das Standardverhalten ist, können Sie auch eine harte Durchsetzung aktivieren, indem Sie eine der folgenden Aufgaben ausführen:

* Lassen Sie Ihren Videoplayer regelmäßig die Lizenz abfragen, um sicherzustellen, dass keine der Zeitbeschränkungen abgelaufen ist. Dies kann durch Aufruf von `DRMManager.loadVoucher(LOCAL_ONLY).` erreicht werden. Ein Fehlercode gibt an, dass die lokal gespeicherte Lizenz nicht mehr gültig ist.
* Wenn der Benutzer auf **[!UICONTROL Pause]** klickt, können Sie den aktuellen Video-Zeitstempel aufzeichnen und dann `Netstream.stop()` aufrufen. Wenn der Benutzer auf die Schaltfläche &quot;Abspielen&quot;klickt, können Sie zum aufgezeichneten Speicherort suchen und `Netstream.play()` aufrufen.