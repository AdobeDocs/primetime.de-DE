---
description: Die meisten Anzeigenkunden benötigen detaillierte Informationen darüber, wann, wie lange und wie erfolgreich ihre Anzeigen angesehen wurden. Der effizienteste Ansatz besteht darin, dass der Client-Player während der Wiedergabe der Anzeigen Berichte sendet, der Manifestserver unterstützt jedoch auch die serverseitige und hybride Anzeigenverfolgung.
seo-description: Die meisten Anzeigenkunden benötigen detaillierte Informationen darüber, wann, wie lange und wie erfolgreich ihre Anzeigen angesehen wurden. Der effizienteste Ansatz besteht darin, dass der Client-Player während der Wiedergabe der Anzeigen Berichte sendet, der Manifestserver unterstützt jedoch auch die serverseitige und hybride Anzeigenverfolgung.
seo-title: Anzeigenverfolgung
title: Anzeigenverfolgung
uuid: 184b8c36-5e51-42a7-b905-53f2b7b15e49
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Anzeigenverfolgung {#ad-tracking}

Die meisten Anzeigenkunden benötigen detaillierte Informationen darüber, wann, wie lange und wie erfolgreich ihre Anzeigen angesehen wurden. Der effizienteste Ansatz besteht darin, dass der Client-Player während der Wiedergabe der Anzeigen Berichte sendet, der Manifestserver unterstützt jedoch auch die serverseitige und hybride Anzeigenverfolgung.

Bei Aktivierung der Anzeigenverfolgung gibt der Client einen der folgenden Ansätze an:

* **Client-Seite** Zusammen mit der anzeigengegebundenen Wiedergabeliste sendet der Server dem Client eine JSON-, VMAP- oder In-Manifest-Struktur, die Verfolgungs-Ereignis und URLs angibt. Diese Methode entspricht dem IAB-Standard (Interactive Advertising Bureau)

* **Serverseite** Der Client nimmt nicht an der Anzeigenverfolgung teil. Der Server sendet alle Informationen zur Anzeigenverfolgung. Verfolgungsdaten werden nur serverseitig berechnet und stimmen möglicherweise nicht mit der clientseitigen Wiedergabe-Aktivität überein. Wenn ein Endbenutzer z. B. die gesamte Anzeige nicht Ansicht, wird die Anzeige nach Auslieferung der Segmente weiterhin vom Server abgespielt.

* **Hybrid** Dies ist wie eine clientseitige Verfolgung, aber der Client sendet seine Berichte an den Manifestserver, der sie an die entsprechenden URLs weiterleitet. Werbetreibende erhalten dieselben Informationen wie bei der clientseitigen Verfolgung. Dieser Modus eignet sich für Kunden mit eingeschränktem Internetzugang.