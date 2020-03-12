---
description: TVSDK kann geänderte Wiedergabeinformationen in Master-m3u8-Manifests für Live-Streaming erkennen und die Wiedergabeinformationen während der Wiedergabe des Streams aktualisieren. TVSDK unterstützt einen dynamischen Satz von Bitrate-Profilen, wenn die Profile im Master-Manifest angezeigt oder ausgeblendet werden, einschließlich nicht überlappender Profil-Bitraten zwischen Updates.
seo-description: TVSDK kann geänderte Wiedergabeinformationen in Master-m3u8-Manifests für Live-Streaming erkennen und die Wiedergabeinformationen während der Wiedergabe des Streams aktualisieren. TVSDK unterstützt einen dynamischen Satz von Bitrate-Profilen, wenn die Profile im Master-Manifest angezeigt oder ausgeblendet werden, einschließlich nicht überlappender Profil-Bitraten zwischen Updates.
seo-title: Aktualisierung des Live-Master-Manifests
title: Aktualisierung des Live-Master-Manifests
uuid: 44f8adc2-0538-4c5d-8e39-55f661d8540b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Aktualisierung des Live-Master-Manifests{#live-master-manifest-update}

TVSDK kann geänderte Wiedergabeinformationen in Master-m3u8-Manifests für Live-Streaming erkennen und die Wiedergabeinformationen während der Wiedergabe des Streams aktualisieren. TVSDK unterstützt einen dynamischen Satz von Bitrate-Profilen, wenn die Profile im Master-Manifest angezeigt oder ausgeblendet werden, einschließlich nicht überlappender Profil-Bitraten zwischen Updates.

Die folgenden Funktionen werden unterstützt:

* Anzahl der Profil (Erhöhen oder verringern)
* Bitraten im Profil (Überschneidung oder Nichtüberschneidung)
* Profil mit URLs auf demselben (oder anderen) Server
* Jede Failover-Struktur

Alle folgenden Bedingungen müssen erfüllt sein:

* Stream ist live.
* Sowohl die Uhrzeit als auch das Tag ändern sich.
* Alle Darstellungsinformationen bleiben gleich (mit der Ausnahme, dass URLs variieren können).
* Die DRM-Zugriffsinformationen bleiben unverändert.
* Segmente werden in einem kleinen Fehlerbereich um dieselben PTS- und Frame-Begrenzungen gepackt.

## Live-Master-Manifest-Aktualisierungsarchitektur {#section_32254A0F684B4960ACC33BF6B1AEF6F1}

Im Folgenden finden Sie einige Informationen und Beispiele, wie das TVSDK aktualisierte Master-Manifeste einbezieht.

Standardmäßig ist diese Funktion deaktiviert. Wenn Ihre Anwendung die Anwendung durch Festlegen einer Aktualisierungshäufigkeit in Minuten aktiviert, werden nach jedem Aktualisierungsintervall die folgenden Schritte ausgeführt:

1. Das TVSDK prüft, ob die Datei aktualisiert wurde, die letzte Änderungszeit und das letzte Tag des Mastermanifests.

   Wenn sich Zeit und Tag geändert haben, gilt die Datei als geändert.
1. Das TVSDK analysiert und analysiert das neue Manifest und ergreift entsprechend der Art des Updates geeignete Maßnahmen.
1. Wenn die aktuelle Wiedergabe-Bitrate mit der Bitrate des modifizierten Manifests übereinstimmt, wechselt das TVSDK zum neuen Profil.

   Das neue Profil kann mit derselben Bitrate von einem anderen Server oder vom gleichen Server stammen. In diesem Fall ist die Transition glatt.
1. Wenn die aktuelle Wiedergabe-Bitrate nicht mehr im neuen Manifest vorhanden ist, versucht TVSDK, eine Bitrate im aktuellen Profil zu finden, die auch im neuen Manifest vorhanden ist.

   * Wenn eine Übereinstimmung gefunden wird, wechselt der Player zunächst zum entsprechenden Bitrate-Profil im vorhandenen Manifest und wechselt zum entsprechenden Bitrate-Profil im aktualisierten Manifest. Dadurch wird sichergestellt, dass die Transition glatt ist.
   * Wenn es keine gemeinsame Bitrate zwischen dem vorherigen Manifest und dem neuen Manifest gibt oder wenn das TVSDK nicht zu der passenden Bitrate wechseln kann, wechselt das TVSDK direkt zum niedrigsten Bitrate-Profil des neuen Manifests und verwendet ABR, um zu einer beliebigen zulässigen Bitrate basierend auf der Bandbreite zu wechseln. Dies kann bei der Wiedergabe zu einem leichten Fehler führen, sollte jedoch nur geringe Auswirkungen haben.

1. Wenn die Aktualisierung erfolgreich war, löst das TVSDK ein `MediaPlayerItemEvent.MASTER_UPDATED` Ereignis aus.
1. Wenn die Aktualisierung nicht erfolgreich ist, wird die Wiedergabe mit der Einrichtung vor dieser Aktualisierung fortgesetzt.

### Beispiel 1 {#example_DB55F2B9D98741628C9B973E47A0B6A0}

Die folgenden Bitraten werden live übertragen:

* 500k
* 900k
* 2100k

Der 2100k-Stream hat einige Probleme, daher muss er neu gestartet werden. Das Master-Manifest wird aktualisiert und enthält nur 500k und 900k. Kurz darauf werden die Benutzer, die dieses Programm mit 2100 k ansehen, einen Bitratenwechsel auf 900 k erleben. Die Benutzer, die bei 900.000 Uhr schauen, sehen sich weiterhin bei 900.000 Uhr an. Später wird der 2100-k-Stream wieder aufgenommen und wieder im Master-Manifest hinzugefügt. Eine Weile später werden die Benutzer, die mit 900k schauen und die Bandbreite haben, auf 2100k umgestellt.

### Beispiel 2 {#example_485E9A9F373D454CADE5395DEC734E5D}

Die folgenden Bitraten werden live übertragen:

* 500k
* 900k
* 2100k

All diese Bitraten müssen neu gestartet werden. Dafür gibt es zwei zeitliche Streams mit 400 und 1500 k. Die Benutzer werden auf 400k umgestellt, was der niedrigsten Bitrate der neuen Konfiguration entspricht. Einige Benutzer werden auf 1500k umgestellt, wenn ihre Bandbreite ausreicht. Später werden die drei Bitraten gesichert und das Master-Manifest aktualisiert. Benutzer wechseln automatisch zurück, um mit 500k zu sehen, was die niedrigste Bandbreite im überarbeiteten (ursprünglichen) Manifest ist. Eine Weile später werden die Benutzer auf die höchste Bandbreite (900k oder 1200k) umgestellt, die ihr Netzwerk zulässt.

## Live-Master-Manifestaktualisierung verwenden {#section_34AC4A9751DB4B7C8561302C6A59A1C4}

Sie können diese Funktion aktivieren und auf zugehörige Ereignis prüfen.

1. Um Live-Master-Manifestaktualisierungen zu aktivieren, legen Sie die Aktualisierungshäufigkeit (in Minuten) fest, indem Sie die `NetworkConfiguration.masterUpdateInterval` Eigenschaft festlegen.
1. Optional können Sie erfolgreiche Manifestaktualisierungen verfolgen, indem Sie auf das `MediaPlayerItemEvent.MASTER_UPDATED` Ereignis warten.

