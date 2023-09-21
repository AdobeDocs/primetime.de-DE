---
description: Im Folgenden finden Sie einige Informationen und Beispiele dazu, wie das Browser TVSDK aktualisierte Master-Manifeste unterstützt.
title: Aktualisierungsarchitektur des Live-Master-Manifests
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 1%

---

# Aktualisierungsarchitektur des Live-Master-Manifests{#live-master-manifest-update-architecture}

Im Folgenden finden Sie einige Informationen und Beispiele dazu, wie das Browser TVSDK aktualisierte Master-Manifeste unterstützt.

Standardmäßig ist diese Funktion deaktiviert. Wenn Ihre Anwendung dies durch Festlegen einer Aktualisierungshäufigkeit in Minuten aktiviert, werden nach jedem Aktualisierungsintervall die folgenden Schritte ausgeführt:

1. Das Browser TVSDK überprüft die Zeit der letzten Änderung des Master-Manifests und gibt an, ob die Datei aktualisiert wurde.

   Wenn sich sowohl die Zeit als auch das Tag geändert haben, gilt die Datei als geändert.
1. Das Browser TVSDK analysiert und analysiert das neue Manifest und ergreift je nach Art der Aktualisierung geeignete Maßnahmen.
1. Wenn die aktuelle Wiedergabe-Bitrate mit der Bitrate des modifizierten Manifests übereinstimmt, wechselt das Browser TVSDK zum neuen Profil.

   Das neue Profil kann von einem anderen Server oder vom selben Server stammen und dieselbe Bitrate aufweisen. In diesem Fall ist die Transition glatt.
1. Wenn die aktuelle Wiedergabe-Bitrate nicht mehr im neuen Manifest vorhanden ist, versucht das Browser TVSDK, eine Bitrate im aktuellen Profil zu finden, die auch im neuen Manifest vorhanden ist.

   * Wenn eine Übereinstimmung gefunden wird, wechselt der Player zunächst zum entsprechenden Bitratenprofil im vorhandenen Manifest und wechselt zum entsprechenden Bitratenprofil im aktualisierten Manifest. Dadurch wird sichergestellt, dass der Übergang reibungslos verläuft.
   * Wenn zwischen dem vorherigen Manifest und dem neuen Manifest keine Bitrate vorhanden ist oder das Browser TVSDK nicht zu der passenden Bitrate wechseln kann, wechselt das Browser TVSDK direkt zum niedrigsten Bitratenprofil des neuen Manifests und verwendet ABR, um zu einer beliebigen zulässigen Bitrate basierend auf der Bandbreite zu wechseln. Dies kann zu einem leichten Wiedergabefehler führen, sollte jedoch nur geringe Auswirkungen haben.

1. Wenn die Aktualisierung erfolgreich ist, sendet das Browser TVSDK eine `MediaPlayerItemEvent.MASTER_UPDATED` -Ereignis.
1. Wenn die Aktualisierung nicht erfolgreich ist, wird die Wiedergabe mit der Einrichtung von vor dieser Aktualisierung fortgesetzt.

## Beispiel 1 {#example_DB55F2B9D98741628C9B973E47A0B6A0}

Die folgenden Bitraten werden live übertragen:

* 500k
* 900k
* 2100k

Der 2100.000-Stream weist einige Probleme auf, daher muss er neu gestartet werden. Das Mastermanifest wird aktualisiert und enthält nur 500.000 und 900.000 Zeichen. Kurz danach werden die Nutzer, die dieses Programm mit 2100.000 ansehen, einen Bit-Rate-Wechsel auf 900.000 sehen. Die Benutzer, die 900.000 Uhr anschauen, sehen sich weiterhin 900.000 Uhr an. Später wird der 2100.000-Stream fortgesetzt und wieder zum Master-Manifest hinzugefügt. Eine Weile später werden die Benutzer, die sich um 900.000 Uhr anschauen und die Bandbreite nutzen, auf 2100.000 umgestellt.

### Beispiel 2 {#example_485E9A9F373D454CADE5395DEC734E5D}

Die folgenden Bitraten werden live übertragen:

* 500k
* 900k
* 2100k

Alle diese Bitraten müssen neu gestartet werden. Dazu gibt es zwei zeitliche Streams, 400.000 und 1500.000. Die Benutzer werden auf 400.000 umgestellt, was der niedrigsten Bitrate der neuen Konfiguration entspricht. Einige Benutzer werden auf 1500.000 umgestellt, wenn ihre Bandbreite ausreicht. Später werden die drei Bitraten gesichert und das Master-Manifest aktualisiert. Benutzer wechseln automatisch zurück und sehen sich bei 500.000 an, was der niedrigsten Bandbreite im überarbeiteten (ursprünglichen) Manifest entspricht. Nach einiger Zeit werden die Benutzer auf die höchste Bandbreite (900.000 oder 1.200.000) umgestellt, die ihr Netzwerk zulässt.

<!-- 

WRITER: Add relref to api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#MASTER_UPDATED

 -->
