---
title: Lizenzserver-Bereitstellungsoptionen
description: Lizenzserver-Bereitstellungsoptionen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Lizenzserver-Bereitstellungsoptionen{#license-server-deployment-options}

Sie können License Server mit einer der folgenden Optionen bereitstellen:

* Adobe Primetime DRM Server für geschütztes Streaming - Dieser Lizenzserver ist für Streaming optimiert. Sie können beispielsweise den Server für Adobe-HTTP Dynamic Streaming mit Primetime DRM einrichten. Dieser Server kann einfach mit sehr wenig Konfiguration bereitgestellt werden und unterstützt mehrere Mandanten. Es kann ein hohes Maß an Skalierbarkeit erreichen. Da diese Implementierung für Streaming optimiert ist, unterstützt sie nicht alle Primetime-DRM-Funktionen. Beispielsweise werden Benutzername/Kennwort-Authentifizierung, Domänen und Lizenzketten nicht unterstützt. Die Nutzungsregeln in von diesem Server ausgestellten Lizenzen werden über eine Server-Konfigurationsdatei gesteuert, die die beim Verpacken verwendete Richtlinie außer Kraft setzt.

  Siehe *Adobe Primetime DRM-Server für geschützte Streaming-Anleitung* Weitere Informationen zu den Nutzungsregeln, die vom Lizenzserver unterstützt werden.
* Referenz-Implementierungs-Lizenzserver - Sie können dieses Setup verwenden, um Ihre Serverimplementierung anzupassen. Dies ist eine Beispielimplementierung des Lizenzservers, einschließlich Quellcode, die zeigt, wie die APIs im Primetime DRM SDK verwendet werden, um alle Arten von Anfragen zu verwalten und wie benutzerdefinierte Geschäftslogik, die von einer Datenbank unterstützt wird, implementiert wird. Die Nutzungsregeln in von diesem Server ausgestellten Lizenzen werden durch die Richtlinie gesteuert, die zum Zeitpunkt der Verpackung mit dem Inhalt verknüpft ist.
* Benutzerdefinierte Serverimplementierung: Sie können auch Ihren eigenen Lizenzierungsserver mit dem SDK implementieren. In diesen Informationen wird beschrieben, wie die APIs zur Implementierung eines Lizenzservers verwendet werden.
