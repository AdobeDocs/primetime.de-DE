---
description: Um TVSDK am effektivsten zu verwenden, sollten Sie bestimmte Details zu seiner Funktionsweise berücksichtigen und bestimmte Best Practices befolgen.
title: Überlegungen und Best Practices
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---


# Überlegungen und Best Practices{#considerations-and-best-practices}

Um TVSDK am effektivsten zu verwenden, sollten Sie bestimmte Details zu seiner Funktionsweise berücksichtigen und bestimmte Best Practices befolgen.

## Überlegungen {#section_tvsdk_considerations}

Beachten Sie bei Verwendung von TVSDK die folgenden Informationen:

* Adobe Primetime funktioniert nicht auf iOS-Simulatoren.

   Sie müssen echte Geräte zum Testen verwenden.
* Die Wiedergabe wird nur für HLS-Inhalte (HTTP Live Streaming) unterstützt.
* Hauptvideoinhalte können im Multiplex-Modus dargestellt werden, wobei Video- und Audiostreams in derselben Darstellung oder nicht im Multiplexverfahren vorliegen, wobei Video- und Audiostreams in separaten Darstellungen dargestellt werden.
* Die TVSDK API wird in Objective-C implementiert.
* Für die Videowiedergabe ist das native Apple AV Foundation-Framework erforderlich. Dies wirkt sich darauf aus, wie und wann auf Medienressourcen, einschließlich Bildunterschriften und Zeitschienen, zugegriffen werden kann:

   * Zeitleistenanpassungen können nach der ersten Einrichtung nicht mehr geändert werden.

      Beispielsweise kann eine Werbung nicht mehr aus der Zeitleiste entfernt werden, nachdem sie wiedergegeben wurde. Wenn der Benutzer in der Präsentation die Suche zurückführt, wird dieselbe Anzeige erneut wiedergegeben, selbst wenn die Richtlinie darin bestand, die Anzeige zu entfernen.
   * Abhängig von der Genauigkeit des Encoder kann die tatsächliche Dauer der kodierten Medien von der Dauer abweichen, die im Stream-Ressourcenmanifest aufgezeichnet wird.

      Es gibt keine zuverlässige Methode, um zwischen der idealen virtuellen Zeitleiste und der tatsächlichen Wiedergabedauer neu zu synchronisieren. Die Fortschrittsverfolgung der Stream-Wiedergabe für die Anzeigenverwaltung und Video Analytics muss die tatsächliche Wiedergabedauer verwenden, sodass das Verhalten von Berichte und Benutzeroberfläche die Medien- und Anzeigeninhalte möglicherweise nicht genau verfolgen kann.
   * Der eingehende Benutzeragent für alle HTTP-Anforderungen von TVSDK auf dieser Plattform wird vom Gerät und der auf dem Gerät ausgeführten iOS-Version bestimmt.

      Der Wert der Benutzeragenten-Zeichenfolge ist standardmäßig vom Betriebssystem zugewiesen.

## Bewährte Verfahren {#section_tvsdk_best_practices}

Hier finden Sie empfohlene Vorgehensweisen für TVSDK:

* Verwenden Sie HLS Version 3.0 oder höher für Programm-Inhalte.
* Verwenden Sie das Media-Validator-Tool von Apple, um VOD-Streams zu validieren.
* Die `PTSDKConfig`-Klasse stellt Methoden zum Erzwingen von SSL für Anforderungen bereit, die an Primetime-Anzeigen, DRM- und Video Analytics-Servern gesendet werden.

   Weitere Informationen finden Sie in den Methoden `forceHTTPS` und `isForcingHTTPS` in dieser Klasse.

   >[!IMPORTANT]
   >
   >Anforderungen an Drittanbieter-Domänen wie Anzeigenverfolgungspixel, Inhalts- und Anzeigen-URLs und ähnliche Anforderungen werden nicht geändert. Es liegt in der Verantwortung der Inhaltsanbieter und Anzeigenserver, URLs bereitzustellen, die über HTTPS unterstützt werden.

