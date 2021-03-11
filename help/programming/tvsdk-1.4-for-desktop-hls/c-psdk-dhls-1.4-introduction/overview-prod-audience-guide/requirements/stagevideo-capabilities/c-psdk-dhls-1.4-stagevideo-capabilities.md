---
description: Auf Geräten, die die GPU-Beschleunigung (Hardware) unterstützen, können Sie ein flash.media.StageVideo-Objekt verwenden, um Videos auf der Gerätehardware zu verarbeiten. Die Verfügbarkeit von StageVideo hängt von den Versionen und Funktionen verschiedener Systemteile ab, einschließlich Flash Player, Videohardware, Betriebssystem, Treiber, Browser, Netzwerkverbindung und Anzeigekontext.
title: StageVideo-Funktionen und -Einschränkungen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# Übersicht {#stagevideo-capabilities-and-restrictions-overview}

Auf Geräten, die die GPU-Beschleunigung (Hardware) unterstützen, können Sie ein flash.media.StageVideo-Objekt verwenden, um Videos auf der Gerätehardware zu verarbeiten. Die Verfügbarkeit von StageVideo hängt von den Versionen und Funktionen verschiedener Systemteile ab, einschließlich Flash Player, Videohardware, Betriebssystem, Treiber, Browser, Netzwerkverbindung und Anzeigekontext.

Mit der `StageVideo`-Klasse können Sie die Hardwarebeschleunigung nutzen, um Videos auf dem höchstmöglichen Leistungsniveau für ein Gerät anzuzeigen. Die Verfügbarkeit und Leistung von `StageVideo` wird durch folgende Faktoren beeinflusst:

* **Hardwarebeschleunigung** : Wenn Hardwarebeschleunigung verfügbar ist, werden Videos auf der Hardware des Geräts  `StageVideo` verarbeitet. Wenn die Hardwarebeschleunigung nicht verfügbar ist, hängt die Antwort von der auszuführenden Version des Flashs ab:`StageVideo`

   * *Flash 15 und höher* : Wenn die Hardwarebeschleunigung nicht verfügbar ist,  `StageVideo` fällt die Software zurück, und Sie müssen nichts tun.

      >[!TIP]
      >
      >Wenn keine Hardwarebeschleunigung verfügbar ist, kann die Leistung erheblich beeinträchtigt werden.

   * *Flash 14 und früher* : Wenn die Hardwarebeschleunigung nicht verfügbar ist,  `StageVideo` ist sie nicht verfügbar. In kleinen Konfigurationen, bei denen die Hardwarebeschleunigung vom Browser oder GPU nicht unterstützt wird oder im Flash Player ausgeschaltet ist, schlägt die Videoanzeige mit dem TVSDK HLS-Stapel fehl. In der Pipeline *HDS* können Sie von `StageVideo` zu einer Alternative wechseln, z. B. dem Video-Objekt, das Video in der CPU verarbeitet.

* **Präsentationskontext** : Während der Vollbildanzeige  `StageVideo` ist immer verfügbar und die Leistung wird auf der maximalen Ebene auf dem Gerät verfügbar sein. Wenn die Videodarstellung nicht im Vollbildmodus angezeigt wird, fällt sie unter den Kontext des Browsers, in dem die Einstellungen und Funktionen des Browsers verwendet werden.

* **wmode**  - Im Browser-Kontext ist die  `wmode` Einstellung für die Leistung entscheidend. Adobe empfiehlt, `wmode` auf `direct` einzustellen, um die bestmögliche Leistung im Browserkontext sicherzustellen.

   >[!NOTE]
   >
   >Die Kombination von Faktoren wie `wmode`, `StageVideo` und Flash führt zu unterschiedlichen Funktionen und Einschränkungen, je nachdem, wie schnell Ihre Hardware ausgeführt wird und welche Version des Flashs Sie verwenden.

   * *Flash 15 und höher*  -  `StageVideo` ist mit allen verfügbaren  `wmode` Einstellungen verfügbar. Wenn Sie `wmode` jedoch auf eine andere Einstellung als `direct` setzen, ist die Leistung niedriger.

   * *Flash 14 und früher* : Wenn Sie  `wmode` eine andere Einstellung als  `direct`festlegen,  `StageVideo` ist dies nicht in allen Browsern verfügbar.

