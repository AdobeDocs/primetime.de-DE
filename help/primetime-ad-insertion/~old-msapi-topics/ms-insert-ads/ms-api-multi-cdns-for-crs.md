---
description: Während das Standard-Szenario für den Kreativumverpackungsdienst (CRS) darin besteht, ein Content Versand Network (CDN) zu verwenden, können Sie CRS-Elemente auf mehr als einem CDN bereitstellen.
title: Mehrere CDN-Unterstützung für CRS und Versand
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Mehrere CDN-Unterstützung für CRS und Versand {#multiple-cdn-support-for-crs-ad-delivery}

Während das Standard-Szenario für den Kreativumverpackungsdienst (CRS) darin besteht, ein Content Versand Network (CDN) zu verwenden, können Sie CRS-Elemente auf mehr als einem CDN bereitstellen.

## Anforderungen

Sie können aus den folgenden Gründen mehrere CDNs verwenden:

* Erfordernis, die Größe für große Ereignisse zu erhöhen
* Eine Anforderung, die CDN-Quelle des CRS-Assets mit der CDN-Quelle des Hauptinhalts abzugleichen.
* Eine Anforderung, ein anderes CDN als das CRS-Standard-CDN (Akamai) zu verwenden.

Wenn der Manifestserver nach transkodierten Anforderungen sucht, verwendet er eine Bootstrap-URL, die eine Reihe von Abfragen-Parametern enthält. Wenn Sie eine Multi-CDN-Umgebung eingerichtet haben, muss die Bootstrap-URL auch den Parameter `ptcdn` enthalten. Der Manifestserver verwendet diesen Parameter, um den CDN-Server zu identifizieren, von dem die transkodierte Version der Anzeige abgerufen wird.

Weitere Informationen finden Sie unter [Multi CDN Support](../../~old-creative-repackaging-service/multi-cdn-supportt.md) in der CRS-Dokumentation.
