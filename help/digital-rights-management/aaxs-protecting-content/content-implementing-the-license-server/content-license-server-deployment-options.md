---
title: Lizenzserver-Bereitstellungsoptionen
description: Lizenzserver-Bereitstellungsoptionen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Lizenzserver-Bereitstellungsoptionen{#license-server-deployment-options}

Der Lizenzserver kann mit einer der folgenden Optionen bereitgestellt werden:

* **Adobe Access Server für geschütztes Streaming** — Dieser Lizenzserver ist für Streaming optimiert. Sie können beispielsweise den Server für Adobe-HTTP Dynamic Streaming mit Adobe-Zugriff einrichten. Dieser Server kann einfach mit sehr wenig Konfiguration bereitgestellt werden und unterstützt mehrere Mandanten und kann eine hohe Skalierbarkeit erreichen. Da diese Implementierung jedoch für Streaming optimiert ist, unterstützt sie nicht alle Adobe Access-Funktionen. Beispielsweise werden Benutzername/Kennwort-Authentifizierung, Domänen und Lizenzketten nicht unterstützt. Die Nutzungsregeln in von diesem Server ausgestellten Lizenzen werden über eine Server-Konfigurationsdatei gesteuert, die die beim Verpacken verwendete Richtlinie außer Kraft setzt. Siehe *Handbuch zu Adobe Access Server für geschütztes Streaming* für weitere Informationen zu den von diesem Server unterstützten Nutzungsregeln.
* **Referenz-Implementierungslizenzserver** — Verwenden Sie dieses Setup als Ausgangspunkt für eine benutzerdefinierte Serverimplementierung. Dies ist eine Beispielimplementierung des Lizenzservers, einschließlich Quellcode, die zeigt, wie die APIs im Adobe Access-SDK zur Verarbeitung aller Anfragetypen verwendet werden und wie benutzerdefinierte, von einer Datenbank unterstützte Geschäftslogik implementiert wird. Die Nutzungsregeln in von diesem Server ausgestellten Lizenzen werden durch die Richtlinie gesteuert, die zum Zeitpunkt der Verpackung mit dem Inhalt verknüpft ist.
* **Benutzerdefinierte Serverimplementierung** — Sie können auch Ihren eigenen Lizenzserver mithilfe des SDK implementieren. Die Informationen in diesem Kapitel beschreiben die APIs, die zur Implementierung eines Lizenzservers verwendet werden.
