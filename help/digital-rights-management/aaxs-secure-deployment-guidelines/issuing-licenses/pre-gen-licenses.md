---
title: Vorgenerieren von Lizenzen
description: Vorgenerieren von Lizenzen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 0%

---


# Vorgenerierende Lizenzen{#pre-generating-licenses}

Wenn Sie Lizenzen vorgenerieren, die zeitbasierte Nutzungsregeln enthalten, wird dringend empfohlen, dass die Lizenz Synchronisierungsanforderungen enthält (siehe Handbuch *Verwenden des Adobe Access SDK for Protecting Content*), damit der Lizenzablauf sicher erzwungen werden kann. Es wird dringend empfohlen, einen &quot;Herzschlag&quot;-Mechanismus zwischen dem Client und dem Server zu implementieren, wenn die Lizenz zeitbasierte Einschränkungen enthält, da der Herzschlag die Clientzeit mit der Serverzeit synchronisiert.
