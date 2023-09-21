---
description: Auf Geräten, die die GPU-Beschleunigung (Hardware) unterstützen, können Sie ein flash.media.StageVideo-Objekt verwenden, um Videos auf der Gerätehardware zu verarbeiten. Die Verfügbarkeit von StageVideo hängt von den Versionen und Funktionen verschiedener Systemteile ab, einschließlich Flash Player, Videohardware, Betriebssystem, Treiber, Browser, Netzwerkverbindung und Anzeigekontext.
title: StageVideo-Funktionen und -Einschränkungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Übersicht {#stagevideo-capabilities-and-restrictions-overview}

Auf Geräten, die die GPU-Beschleunigung (Hardware) unterstützen, können Sie ein flash.media.StageVideo-Objekt verwenden, um Videos auf der Gerätehardware zu verarbeiten. Die Verfügbarkeit von StageVideo hängt von den Versionen und Funktionen verschiedener Systemteile ab, einschließlich Flash Player, Videohardware, Betriebssystem, Treiber, Browser, Netzwerkverbindung und Anzeigekontext.

Die `StageVideo` -Klasse ermöglicht Ihnen, die Hardware-Beschleunigung zu nutzen, um Videos auf dem höchstmöglichen Leistungsniveau für ein Gerät darzustellen. Verfügbarkeit und Leistung von `StageVideo` sind von folgenden Faktoren betroffen:

* **Hardwarebeschleunigung** - Wenn die Hardwarebeschleunigung verfügbar ist, `StageVideo` verarbeitet Videos auf der Gerätehardware. Wenn die Hardwarebeschleunigung nicht verfügbar ist, wird die `StageVideo` Die Antwort hängt davon ab, welche Flash-Version Sie ausführen:

   * *Flash 15 und höher* - Wenn die Hardwarebeschleunigung nicht verfügbar ist, `StageVideo` zurück auf die Software, und Sie müssen nichts tun.

     >[!TIP]
     >
     >Wenn die Hardwarebeschleunigung nicht verfügbar ist, kann sich die Leistung erheblich verschlechtern.

   * *Flash 14 und früher* - Wenn die Hardwarebeschleunigung nicht verfügbar ist, `StageVideo` wird nicht verfügbar. Bei einer kleinen Anzahl von Konfigurationen, bei denen die Hardwarebeschleunigung vom Browser oder von der GPU nicht unterstützt oder im Flash Player deaktiviert ist, schlägt die Videoanzeige mit dem TVSDK-HLS-Stack fehl. Im *HDS* Pipeline können Sie von `StageVideo` zu einem alternativen Objekt, z. B. dem Video-Objekt, das Video in der CPU verarbeitet.

* **Präsentationskontext** - Während der Vollbildanzeige, `StageVideo` ist immer verfügbar und die Leistung wird auf der maximalen Ebene liegen, die auf dem Gerät verfügbar ist. Wenn Sie den Vollbildmodus nicht anzeigen, fällt die Videopräsentation unter den Kontext des Browsers, in dem die Einstellungen und Funktionen des Browsers verwendet werden.

* **wmode** - Im Browserkontext wird die `wmode` -Einstellung ist für die Leistung von entscheidender Bedeutung. Adobe empfiehlt, dass Sie `wmode` auf `direct` , um die bestmögliche Leistung im Browserkontext sicherzustellen.

  >[!NOTE]
  >
  >Die Kombination von Faktoren, die `wmode`, `StageVideo`, und Flash führen zu unterschiedlichen Funktionen und Einschränkungen, je nachdem, wie schnell Ihre Hardware läuft und welche Flash-Version Sie verwenden.

   * *Flash 15 und höher* - `StageVideo` ist verfügbar mit allen verfügbaren `wmode` -Einstellungen. Wenn Sie jedoch `wmode` auf eine andere Einstellung als `direct`, wird die Leistung geringer sein.

   * *Flash 14 und früher* - Wenn Sie `wmode` auf eine andere Einstellung als `direct`, `StageVideo` ist nicht in allen Browsern verfügbar.
