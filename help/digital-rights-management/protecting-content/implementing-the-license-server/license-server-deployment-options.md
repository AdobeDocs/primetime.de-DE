---
seo-title: Lizenzserver-Bereitstellungsoptionen
title: Lizenzserver-Bereitstellungsoptionen
uuid: 732b948f-8037-423e-9f85-770d6316cbae
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Lizenzserver-Bereitstellungsoptionen{#license-server-deployment-options}

Sie können License Server mit einer der folgenden Optionen bereitstellen:

* Adobe Primetime DRM Server for Protected Streaming - Dieser Lizenzserver ist für das Streaming optimiert. Sie können beispielsweise den Server für Adobe HTTP Dynamic Streaming mit Primetime DRM einrichten. Dieser Server kann problemlos mit sehr wenig benötigter Konfiguration bereitgestellt werden und unterstützt mehrere Mandanten. Es kann ein hohes Maß an Skalierbarkeit erreichen. Da diese Implementierung für das Streaming optimiert ist, werden nicht alle Primetime-DRM-Funktionen unterstützt. Beispielsweise werden die Authentifizierung von Benutzername/Kennwort, Domänen und Lizenzverkettung nicht unterstützt. Die Nutzungsregeln in von diesem Server ausgegebenen Lizenzen werden über eine Serverkonfigurationsdatei gesteuert, wodurch die beim Verpacken verwendete Richtlinie außer Kraft gesetzt wird.

   Weitere Informationen zu den vom Lizenzserver unterstützten Nutzungsregeln finden Sie im Leitfaden *zum geschützten Streaming für* Adobe Primetime DRM Server.
* Referenz-Implementierungslizenzserver - Mit diesem Setup können Sie Ihre Serverimplementierung anpassen. Dies ist eine Beispielimplementierung des Lizenzservers, einschließlich Quellcode, die zeigt, wie die APIs im Primetime DRM SDK zum Verwalten aller Anforderungstypen verwendet werden und wie benutzerdefinierte Geschäftslogik, die von einer Datenbank unterstützt wird, implementiert wird. Die Nutzungsregeln in von diesem Server ausgestellten Lizenzen werden durch die Richtlinie gesteuert, die zum Zeitpunkt der Verpackung mit dem Inhalt verknüpft ist.
* Benutzerdefinierte Serverimplementierung - Sie können auch Ihren eigenen Lizenzserver mit dem SDK implementieren. Die Informationen beschreiben, wie die APIs zum Implementieren eines Lizenzservers verwendet werden.

