---
description: Die meisten Anzeigenkunden benötigen detaillierte Informationen darüber, wann, wie lange und wie erfolgreich ihre Anzeigen angesehen wurden. Der effizienteste Ansatz besteht darin, dass der Client-Player während der Wiedergabe der Anzeigen Berichte sendet, der Manifestserver unterstützt jedoch auch die serverseitige und hybride Anzeigenverfolgung.
title: Anzeigenverfolgung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# Anzeigenverfolgung {#ad-tracking}

Die meisten Anzeigenkunden benötigen detaillierte Informationen darüber, wann, wie lange und wie erfolgreich ihre Anzeigen angesehen wurden. Der effizienteste Ansatz besteht darin, dass der Client-Player während der Wiedergabe der Anzeigen Berichte sendet, der Manifestserver unterstützt jedoch auch die serverseitige und hybride Anzeigenverfolgung.

Bei Aktivierung der Anzeigenverfolgung gibt der Client einen der folgenden Ansätze an:

* **Client-** SeiteZusammen mit der Anzeigenliste sendet der Server dem Client eine JSON-, VMAP- oder In-Manifest-Struktur, die Tracking-Ereignis und URLs angibt. Diese Methode entspricht dem IAB-Standard (Interactive Advertising Bureau)

* **Server-** SeiteDer Client nimmt nicht an der Anzeigenverfolgung teil. Der Server sendet alle Informationen zur Anzeigenverfolgung. Verfolgungsdaten werden nur serverseitig berechnet und stimmen möglicherweise nicht mit der clientseitigen Wiedergabe-Aktivität überein. Wenn ein Endbenutzer z. B. die gesamte Anzeige nicht Ansicht, wird die Anzeige nach Auslieferung der Segmente weiterhin vom Server abgespielt.

* **** HybridDies ist wie eine clientseitige Verfolgung, aber der Client sendet seine Berichte an den Manifestserver, der sie an die entsprechenden URLs weiterleitet. Werbetreibende erhalten dieselben Informationen wie bei der clientseitigen Verfolgung. Dieser Modus eignet sich für Kunden mit eingeschränktem Internetzugang.