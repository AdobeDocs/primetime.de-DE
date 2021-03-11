---
description: Für Browser TVSDK gibt es einige Sicherheitserwägungen.
title: Sicherheitsaspekte
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---


# Sicherheitsaspekte{#security-considerations}

Für Browser TVSDK gibt es einige Sicherheitserwägungen.

* **Adobe Flash Player**

   * Flash Player erlaubt keinen Zugriff auf Daten, die sich außerhalb der Domäne befinden, von der die SWF stammt.

      Um Zugriff zuzulassen, hosten Sie eine domänenübergreifende Richtliniendatei mit den entsprechenden Berechtigungen im Stammordner des Servers, auf dem die Daten gehostet werden. Im Flash-Fallback-Modus in Browser TVSDK (Flash Player Version 23 und höher) benötigen Sie das Autorisierungstoken für Ihre Domäne. Wenden Sie sich an Ihren Kundenbetreuer, um das Token zu generieren.

* **JavaScript**

   * JavaScript folgt derselben Herkunft und verhindert den Zugriff auf Ressourcen über Domänengrenzen hinweg.

      Um den Zugriff auf diese Ressourcen zu ermöglichen, muss der Header Access-Control-Allow-Herkunft (CORS) auf den Ressourcen eingestellt werden, die auf anderen Herkünfte als dem Player gehostet werden. Wenn der Inhalt optional mithilfe von Bytebereichen angegeben wird, muss in der CORS-Anfrage für die Preflight-Optionen angegeben werden, dass diese Anforderungen von der Herkunft zulässig sind.

* **Browser und gemischte Inhalte**

   * Browser erfordern, dass verschlüsselte AES-128-Inhalte über sichere Herkunft gehostet werden (z. B. HTTPS).

      Da die meisten Browser keine gemischten Inhalte zulassen, empfehlen wir, dass der Player, der Inhalt und die zugehörigen Assets wie Schlüssel-/WebVTT-Dateien auch über eine sichere Herkunft gehostet werden.

      >[!IMPORTANT]
      >
      >Ab Version 2.4.5 wandelt Browser TVSDK die HTTP-Aufrufe bei Verwendung der MSE-Technologie in HTTPS um, wenn der Player über HTTPS gehostet wird.

