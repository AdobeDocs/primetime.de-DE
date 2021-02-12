---
description: Multi-CDN ermöglicht die Einstellung einer oder mehrerer CDN-Standorte, um transkodierte Anzeigen bereitzustellen.
seo-description: Multi-CDN ermöglicht die Einstellung einer oder mehrerer CDN-Standorte, um transkodierte Anzeigen bereitzustellen.
seo-title: Multi-CDN-Unterstützung
title: Multi-CDN-Unterstützung
uuid: 2b6d71f0-61c8-486b-a35a-f7ef3a9519d2
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---


# Multi-CDN-Unterstützung {#multi-cdn-support}

Multi-CDN ermöglicht die Einstellung einer oder mehrerer CDN-Standorte, um transkodierte Anzeigen bereitzustellen.

Standardmäßig werden alle transkodierten Assets auf dem im Besitz der Adobe befindlichen Akamai CDN gehostet. Sie können jedoch keine oder mehrere zusätzliche CDN-Positionen Ihrer eigenen auswählen, an denen CRS das transkodierte Asset hosten soll. In diesem Fall können Ihre transkodierten Assets und Inhalte von demselben CDN bereitgestellt werden.

Wenn der Manifestserver nach transkodierten Anforderungen sucht, verwendet er eine Bootstrap-URL, die eine Reihe von Abfragen-Parametern enthält. Wenn Sie eine Multi-CDN-Umgebung eingerichtet haben, muss die Bootstrap-URL auch den Parameter `ptcdn` enthalten. Der Manifestserver verwendet diesen Parameter, um den CDN-Server zu identifizieren, von dem die transkodierte Version der Anzeige abgerufen werden soll.

Multi-CDN-Unterstützung ist auch für die folgenden Primetime-Lösungen verfügbar:

1. TVSDK für Android
1. TVSDK für Desktop-HLS
1. TVSDK für iOS

## CDN-Unterstützung {#section_1BA344F2300B49F291865A7461EDFEAE} aktivieren

CRS ist standardmäßig für alle Kunden deaktiviert

Wenden Sie sich an Ihren Kundenbetreuer, um Ihr CRS-Konto zu konfigurieren und andere CDNs zum Hosten der transkodierten Anzeigenelemente zu verwenden.Sie müssen die folgenden Informationen angeben, die CRS zum Hochladen der transkodierten Anzeigenelemente in das CDN benötigt

1. CDN-URL
1. Authentifizierungsdetails
1. Ausgabe-URL-Format

Ihr Kundenbetreuer für Adobe stellt Ihnen außerdem einen Spitznamen für dieses CDN zur Verfügung. Sie müssen diesen als Wert des Parameters `ptcdn` in der Bootstrap-URL übergeben.

Sie können mehrere CDNs über die Adobe-Unterstützung auf CRS-End konfigurieren. Das CDN, mit dem Anzeigen-Assets ausgewählt werden, die über den Manifestserver verknüpft werden sollen, muss jedoch das CDN sein, das als Wert des Parameters `ptcdn` in der Bootstrap-URL übergeben wird.
