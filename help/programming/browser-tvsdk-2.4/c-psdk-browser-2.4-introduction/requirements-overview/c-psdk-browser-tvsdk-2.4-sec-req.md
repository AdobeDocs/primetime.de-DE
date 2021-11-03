---
description: Für das Browser TVSDK müssen einige Sicherheitsüberlegungen beachtet werden.
title: Sicherheitsaspekte
exl-id: bc98890a-082a-4e2d-b927-ecb3bd878de9
source-git-commit: 78be1575cc7bd6630a7bf85faa061327e5c414d7
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Sicherheitsaspekte{#security-considerations}

Für das Browser TVSDK müssen einige Sicherheitsüberlegungen beachtet werden.

* **Adobe Flash Player**

   * Flash Player gestattet keinen Zugriff auf Daten, die außerhalb der Domäne liegen, von der die SWF stammt.

      Um den Zugriff zuzulassen, hosten Sie eine domänenübergreifende Richtliniendatei mit den entsprechenden Berechtigungen im Stammverzeichnis des Servers, der die Daten hostet. Im Flash-Fallback-Modus im Browser TVSDK (Flash Player Version 23 und höher) benötigen Sie das Autorisierungstoken für Ihre Domäne. Wenden Sie sich zum Generieren des Tokens an Ihren Adobe-Support-Mitarbeiter.

* **JavaScript**

   * JavaScript folgt derselben Ursprungsrichtlinie und verhindert den Zugriff auf Ressourcen über Domänengrenzen hinweg.

      Um den Zugriff auf diese Ressourcen zu ermöglichen, muss die Kopfzeile Access-Control-Allow-Origin (CORS) für die Ressourcen festgelegt werden, die auf anderen Quellen als dem Player gehostet werden. Wenn der Inhalt optional mithilfe von Byte-Bereichen angegeben wird, muss die CORS-Anfrage für Preflight-Optionen angeben, dass diese Anforderungen von der Quelle zulässig sind.

* **Browser und gemischte Inhalte**

   * Browser erfordern, dass verschlüsselte AES-128-Inhalte über sicheren Ursprung gehostet werden (z. B. HTTPS).

      Da die meisten Browser keine gemischten Inhalte zulassen, empfehlen wir, den Player, den Inhalt und die zugehörigen Assets wie Schlüssel-/WebVTT-Dateien ebenfalls über sicherem Ursprung zu hosten.

      >[!IMPORTANT]
      >
      >Ab Version 2.4.5 konvertiert Browser TVSDK bei über HTTPS gehosteten Players die HTTP-Aufrufe bei Verwendung der MSE-Technologie in HTTPS.
