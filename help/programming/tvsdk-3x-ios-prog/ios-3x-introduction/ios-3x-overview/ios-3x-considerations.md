---
description: Um TVSDK am effektivsten zu verwenden, sollten Sie bestimmte Details seines Betriebs berücksichtigen und bestimmte Best Practices befolgen.
title: Überlegungen und Best Practices
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Überlegungen und Best Practices {#considerations-and-best-practices}

Um TVSDK am effektivsten zu verwenden, sollten Sie bestimmte Details seines Betriebs berücksichtigen und bestimmte Best Practices befolgen.

## Überlegungen {#section_tvsdk_considerations}

Beachten Sie bei Verwendung von TVSDK die folgenden Informationen:

* Adobe Primetime funktioniert nicht mit iOS-Simulatoren.

  Sie müssen echte Geräte zum Testen verwenden.

* Die Wiedergabe wird nur für HLS-Inhalte (HTTP Live Streaming) unterstützt.

* Hauptvideoinhalte können durch Multiplexing gesteuert werden, wobei Video- und Audio-Streams sich in derselben Ausgabedarstellung befinden oder nicht durch einen Multiplexing gekennzeichnet sind, wobei Video- und Audio-Streams in separaten Ausgabedarstellungen enthalten sind.

* Die TVSDK-API wird in Objective-C implementiert.

* Für die Videowiedergabe ist das native Apple AV Foundation-Framework erforderlich. Dies wirkt sich darauf aus, wie und wann auf Medienressourcen wie Untertitel und Zeitpläne zugegriffen werden kann:

   * Zeitleistenanpassungen können nach der Ersteinrichtung nicht mehr geändert werden.

     Beispielsweise kann eine Anzeige nicht aus der Timeline entfernt werden, nachdem sie wiedergegeben wurde. Wenn der Benutzer zur Präsentation zurückkehrt, wird dieselbe Anzeige wiedergegeben, selbst wenn die Richtlinie darin bestanden hätte, die Anzeige zu entfernen.

   * Abhängig von der Genauigkeit des Kodierers unterscheidet sich die tatsächliche kodierte Mediendauer möglicherweise von der Dauer, die im Stream-Ressourcen-Manifest aufgezeichnet wird.

     Es gibt keine zuverlässige Methode, um zwischen der idealen virtuellen Timeline und der tatsächlichen Wiedergabescheitleiste neu zu synchronisieren. Das Fortschritts-Tracking der Stream-Wiedergabe für die Anzeigenverwaltung und Video Analytics muss die tatsächliche Wiedergabedauer verwenden, sodass bei der Berichterstellung und dem Verhalten der Benutzeroberfläche die Medien- und Werbeinhalte möglicherweise nicht genau verfolgt werden.

   * Der eingehende Benutzeragent für alle HTTP-Anfragen von TVSDK auf dieser Plattform wird durch das Gerät und die iOS-Version bestimmt, die auf dem Gerät ausgeführt wird.

     Der Wert der Benutzeragenten-Zeichenfolge entspricht standardmäßig dem vom Betriebssystem zugewiesenen Wert.

## Best Practices {#section_tvsdk_best_practices}

Hier finden Sie empfohlene Vorgehensweisen für TVSDK:

* Verwenden Sie HLS Version 3.0 oder höher für Programminhalte.

* Verwenden Sie das Tool mediastreamvalidator von Apple, um VOD-Streams zu validieren.

* Die PTSDKConfig-Klasse stellt Methoden zum Durchsetzen von SSL für Anfragen bereit, die an Primetime-Anzeigenentscheidungen, DRM- und Video Analytics-Server gesendet werden.

Weitere Informationen finden Sie in den Methoden forceHTTPS und isForcingHTTPS in dieser Klasse.

>[!IMPORTANT]
>
>Anforderungen an Drittanbieter-Domänen wie Anzeigenverfolgungspixel, Inhalts- und Anzeigen-URLs und ähnliche Anforderungen werden nicht geändert. Die Bereitstellung von URLs, die über HTTPS unterstützt werden, liegt in der Verantwortung der Inhaltsanbieter und Adserver.
