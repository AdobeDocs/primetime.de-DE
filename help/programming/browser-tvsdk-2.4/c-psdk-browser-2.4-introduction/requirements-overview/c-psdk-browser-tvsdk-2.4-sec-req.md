---
description: Für Browser TVSDK gibt es einige Sicherheitserwägungen.
seo-description: Für Browser TVSDK gibt es einige Sicherheitserwägungen.
seo-title: Sicherheitsaspekte
title: Sicherheitsaspekte
uuid: 78edf2b0-363c-4ab6-b588-ab4748ee6096
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Sicherheitsaspekte{#security-considerations}

Für Browser TVSDK gibt es einige Sicherheitserwägungen.

* **Adobe Flash Player**

   * Flash Player erlaubt keinen Zugriff auf Daten, die sich außerhalb der Domäne befinden, von der die SWF stammt.

      Um Zugriff zuzulassen, hosten Sie eine domänenübergreifende Richtliniendatei mit den entsprechenden Berechtigungen im Stammordner des Servers, auf dem die Daten gehostet werden. Im Flash Fallback-Modus in Browser TVSDK (Flash Player Version 23 und höher) benötigen Sie das Autorisierungstoken für Ihre Domäne. Wenden Sie sich zum Generieren des Tokens an Ihren Adobe-Kundenbetreuer.

* **JavaScript**

   * JavaScript folgt derselben Herkunft und verhindert den Zugriff auf Ressourcen über Domänengrenzen hinweg.

      Um den Zugriff auf diese Ressourcen zu ermöglichen, muss der Header Access-Control-Allow-Herkunft (CORS) auf den Ressourcen eingestellt werden, die auf anderen Herkünfte als dem Player gehostet werden. Wenn der Inhalt optional mithilfe von Bytebereichen angegeben wird, muss in der CORS-Anfrage für die Preflight-Optionen angegeben werden, dass diese Anforderungen von der Herkunft zulässig sind.

* **Browser und gemischte Inhalte**

   * Browser erfordern, dass verschlüsselte AES-128-Inhalte über sichere Herkunft gehostet werden (z. B. HTTPS).

      Da die meisten Browser keine gemischten Inhalte zulassen, empfehlen wir, dass der Player, der Inhalt und die zugehörigen Assets wie Schlüssel-/WebVTT-Dateien auch über eine sichere Herkunft gehostet werden.

      >[!IMPORTANT]
      >
      >Ab Version 2.4.5 wandelt Browser TVSDK die HTTP-Aufrufe bei Verwendung der MSE-Technologie in HTTPS um, wenn der Player über HTTPS gehostet wird.

