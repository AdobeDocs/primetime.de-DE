---
title: Vorausgenerierung von Lizenzen
description: Vorausgenerierung von Lizenzen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 0%

---

# Vorausgenerierung von Lizenzen{#pre-generating-licenses}

Wenn Sie Lizenzen vorgenerieren, die zeitbasierte Nutzungsregeln enthalten, wird dringend empfohlen, die Lizenz mit Synchronisierungsanforderungen zu versehen (siehe *Verwenden des Adobe Access SDK zum Schutz von Inhalten* ), damit der Lizenzablauf sicher erzwungen werden kann. Es wird dringend empfohlen, einen &quot;Herzschlag&quot;-Mechanismus zwischen dem Client und dem Server zu implementieren, wenn die Lizenz zeitbasierte Beschränkungen aufweist, da der Herzschlag die Client-Zeit mit der Server-Zeit synchronisiert.
