---
seo-title: Vorgenerieren von Lizenzen
title: Vorgenerieren von Lizenzen
uuid: 0207abdf-52bb-4bd0-a4f2-fe740b89fa83
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Vorgenerieren von Lizenzen{#pre-generating-licenses}

Wenn Sie Lizenzen vorgenerieren, die zeitbasierte Nutzungsregeln enthalten, wird dringend empfohlen, dass die Lizenz Synchronisierungsanforderungen enthält (siehe Handbuch *Verwenden des Adobe Access SDK zum Schutz von Inhalten* ), damit der Lizenzablauf sicher erzwungen werden kann. Es wird dringend empfohlen, einen &quot;Herzschlag&quot;-Mechanismus zwischen dem Client und dem Server zu implementieren, wenn die Lizenz zeitbasierte Einschränkungen enthält, da der Herzschlag die Clientzeit mit der Serverzeit synchronisiert.
