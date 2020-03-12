---
description: Auf Geräten, die die GPU-Beschleunigung (Hardware) unterstützen, können Sie ein flash.media.StageVideo-Objekt verwenden, um Videos auf der Gerätehardware zu verarbeiten. Die Verfügbarkeit von StageVideo hängt von den Versionen und Funktionen verschiedener Teile Ihres Systems ab, einschließlich Flash Player, Videohardware, Betriebssystem, Treiber, Browser, Netzwerkverbindung und Anzeigekontext.
seo-description: Auf Geräten, die die GPU-Beschleunigung (Hardware) unterstützen, können Sie ein flash.media.StageVideo-Objekt verwenden, um Videos auf der Gerätehardware zu verarbeiten. Die Verfügbarkeit von StageVideo hängt von den Versionen und Funktionen verschiedener Teile Ihres Systems ab, einschließlich Flash Player, Videohardware, Betriebssystem, Treiber, Browser, Netzwerkverbindung und Anzeigekontext.
seo-title: StageVideo-Funktionen und -Einschränkungen
title: StageVideo-Funktionen und -Einschränkungen
uuid: 7556f30b-4b9f-4258-beb6-2a4ce8f05d1a
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Übersicht {#stagevideo-capabilities-and-restrictions-overview}

Auf Geräten, die die GPU-Beschleunigung (Hardware) unterstützen, können Sie ein flash.media.StageVideo-Objekt verwenden, um Videos auf der Gerätehardware zu verarbeiten. Die Verfügbarkeit von StageVideo hängt von den Versionen und Funktionen verschiedener Teile Ihres Systems ab, einschließlich Flash Player, Videohardware, Betriebssystem, Treiber, Browser, Netzwerkverbindung und Anzeigekontext.

Mit der `StageVideo` Klasse können Sie die Hardwarebeschleunigung nutzen, um Videos auf dem höchstmöglichen Leistungsniveau für ein Gerät anzuzeigen. Die Verfügbarkeit und Leistung von `StageVideo` Inhalten wird durch folgende Faktoren beeinflusst:

* **Hardwarebeschleunigung** : Wenn die Hardwarebeschleunigung verfügbar ist, wird das `StageVideo` Video auf der Gerätehardware verarbeitet. Wenn die Hardwarebeschleunigung nicht verfügbar ist, hängt die `StageVideo` Antwort davon ab, welche Flash-Version Sie ausführen:

   * *Flash 15 und höher* - Wenn die Hardwarebeschleunigung nicht verfügbar ist, wird die Software `StageVideo` verwendet, und Sie müssen nichts tun.

      >[!TIP]
      >
      >Wenn keine Hardwarebeschleunigung verfügbar ist, kann die Leistung erheblich beeinträchtigt werden.

   * *Flash 14 und früher* - Wenn die Hardwarebeschleunigung nicht verfügbar ist, ist sie nicht mehr verfügbar `StageVideo` . In einer kleinen Gruppe von Konfigurationen, bei denen die Hardwarebeschleunigung vom Browser oder GPU nicht unterstützt wird oder im Flash Player ausgeschaltet ist, schlägt die Videoanzeige mit dem TVSDK HLS-Stapel fehl. In der *HDS* -Pipeline können Sie von einem alternativen Objekt wie dem Video-Objekt, das Video in der CPU verarbeitet, `StageVideo` zu einem anderen wechseln.

* **Präsentationskontext** : Während der Vollbildanzeige ist `StageVideo` immer verfügbar und die Leistung wird auf der maximalen Ebene auf dem Gerät verfügbar sein. Wenn die Videodarstellung nicht im Vollbildmodus angezeigt wird, fällt sie unter den Kontext des Browsers, in dem die Einstellungen und Funktionen des Browsers verwendet werden.

* **wmode** - Im Browserkontext ist die `wmode` Einstellung für die Leistung entscheidend. Adobe empfiehlt, dass Sie `wmode` so eingestellt sind, dass im Browserkontext die bestmögliche Leistung gewährleistet `direct` ist.

   >[!NOTE]
   >
   >Die Kombination von Faktoren wie `wmode`, `StageVideo`und Flash führt zu unterschiedlichen Funktionen und Einschränkungen, je nachdem, wie schnell Ihre Hardware ausgeführt wird und welche Flash-Version Sie verwenden.

   * *Flash 15 und höher* - `StageVideo` ist mit allen verfügbaren `wmode` Einstellungen verfügbar. Wenn Sie jedoch `wmode` eine andere Einstellung als `direct`festlegen, ist die Leistung niedriger.

   * *Flash 14 und früher* - Wenn Sie `wmode` eine andere Einstellung als `direct`festlegen, `StageVideo` ist dies nicht in allen Browsern verfügbar.

