---
description: Die meisten Anzeigenkunden benötigen detaillierte Informationen darüber, wann, wie lange und wie erfolgreich ihre Anzeigen angesehen wurden. Der effizienteste Ansatz besteht darin, dass der Client-Player während der Wiedergabe der Anzeigen Berichte sendet, der Manifestserver unterstützt jedoch auch die serverseitige und hybride Anzeigenverfolgung.
seo-description: Die meisten Anzeigenkunden benötigen detaillierte Informationen darüber, wann, wie lange und wie erfolgreich ihre Anzeigen angesehen wurden. Der effizienteste Ansatz besteht darin, dass der Client-Player während der Wiedergabe der Anzeigen Berichte sendet, der Manifestserver unterstützt jedoch auch die serverseitige und hybride Anzeigenverfolgung.
seo-title: Anzeigenverfolgung
title: Anzeigenverfolgung
uuid: 184b8c36-5e51-42a7-b905-53f2b7b15e49
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---


# Anzeigenverfolgung {#ad-tracking}

Die meisten Anzeigenkunden benötigen detaillierte Informationen darüber, wann, wie lange und wie erfolgreich ihre Anzeigen angesehen wurden. Der effizienteste Ansatz besteht darin, dass der Client-Player während der Wiedergabe der Anzeigen Berichte sendet, der Manifestserver unterstützt jedoch auch die serverseitige und hybride Anzeigenverfolgung.

Bei Aktivierung der Anzeigenverfolgung gibt der Client einen der folgenden Ansätze an:

* **Client-** SeiteZusammen mit der Anzeigenliste sendet der Server dem Client eine JSON-, VMAP- oder In-Manifest-Struktur, die Tracking-Ereignis und URLs angibt. Diese Methode entspricht dem IAB-Standard (Interactive Advertising Bureau)

* **Server-** SeiteDer Client nimmt nicht an der Anzeigenverfolgung teil. Der Server sendet alle Informationen zur Anzeigenverfolgung. Verfolgungsdaten werden nur serverseitig berechnet und stimmen möglicherweise nicht mit der clientseitigen Wiedergabe-Aktivität überein. Wenn ein Endbenutzer z. B. die gesamte Anzeige nicht Ansicht, wird die Anzeige nach Auslieferung der Segmente weiterhin vom Server abgespielt.

* **** HybridDies ist wie eine clientseitige Verfolgung, aber der Client sendet seine Berichte an den Manifestserver, der sie an die entsprechenden URLs weiterleitet. Werbetreibende erhalten dieselben Informationen wie bei der clientseitigen Verfolgung. Dieser Modus eignet sich für Kunden mit eingeschränktem Internetzugang.