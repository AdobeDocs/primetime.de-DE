---
seo-title: Lizenzserver-Bereitstellungsoptionen
title: Lizenzserver-Bereitstellungsoptionen
uuid: 297c587f-23e2-4bb5-911b-72d7b82370f4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---


# Lizenzserver-Bereitstellungsoptionen{#license-server-deployment-options}

Der Lizenzserver kann mit einer der folgenden Optionen bereitgestellt werden:

* **Adobe Access Server für geschütztes Streaming**  - Dieser Lizenzserver ist für Streaming optimiert. Sie können beispielsweise den Server für Adobe HTTP Dynamic Streaming mit Adobe Access einrichten. Dieser Server kann problemlos mit sehr wenig benötigter Konfiguration bereitgestellt werden und unterstützt mehrere Mandanten und kann eine hohe Skalierbarkeit erreichen. Da diese Implementierung jedoch für das Streaming optimiert ist, werden nicht alle Adobe Access-Funktionen unterstützt. Beispielsweise werden die Authentifizierung von Benutzername/Kennwort, Domänen und Lizenzverkettung nicht unterstützt. Die Nutzungsregeln in von diesem Server ausgegebenen Lizenzen werden über eine Serverkonfigurationsdatei gesteuert, wodurch die beim Verpacken verwendete Richtlinie außer Kraft gesetzt wird. Weitere Informationen zu den von diesem Server unterstützten Nutzungsregeln finden Sie im Handbuch *Adobe Access Server für geschütztes Streaming*.
* **Referenz-Implementierungslizenzserver**  - Verwenden Sie dieses Setup als Ausgangspunkt für eine benutzerdefinierte Serverimplementierung. Dies ist eine Beispielimplementierung des Lizenzservers, einschließlich Quellcode, die zeigt, wie die APIs im Adobe Access SDK zur Verarbeitung aller Anforderungstypen verwendet werden und wie benutzerdefinierte, durch eine Datenbank gesicherte Geschäftslogik implementiert wird. Die Nutzungsregeln in von diesem Server ausgestellten Lizenzen werden durch die Richtlinie gesteuert, die zum Zeitpunkt der Verpackung mit dem Inhalt verknüpft ist.
* **Benutzerdefinierte Serverimplementierung** : Sie können auch Ihren eigenen Lizenzserver mithilfe des SDK implementieren. Die Informationen in diesem Kapitel beschreiben die APIs, mit denen ein Lizenzserver implementiert wird.

