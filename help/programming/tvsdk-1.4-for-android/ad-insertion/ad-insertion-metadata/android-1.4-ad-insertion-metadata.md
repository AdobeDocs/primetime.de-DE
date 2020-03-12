---
description: Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte benötigen, um Ihre Verbindung zum Anbieter zu aktivieren.
seo-description: Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte benötigen, um Ihre Verbindung zum Anbieter zu aktivieren.
seo-title: Anzeigeneinfügemetadaten
title: Anzeigeneinfügemetadaten
uuid: f40ed53b-eba1-4f70-a29c-90cac51e8a9a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Übersicht {#ad-insertion-metadata}

Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte benötigen, um Ihre Verbindung zum Anbieter zu aktivieren.

TVSDK enthält die Primetime-Bibliothek für Anzeigenentscheidungen. Damit Ihre Inhalte Werbung vom Primetime-Anzeigen-Entscheidungsserver enthalten, muss Ihre Anwendung die folgenden erforderlichen `AuditudeSettings` Informationen bereitstellen:

* `mediaID`, was eine eindeutige ID für das abzuspielende Video darstellt.

   Der Herausgeber weist die `mediaID` beim Senden von Videoinhalten und Anzeigeninformationen an den Adobe Primetime-Ad-Decision-Server zu. Diese ID wird von der Primetime-Anzeigenentscheidung verwendet, um verwandte Werbeinformationen für das Video vom Server abzurufen.

* (Optional) `defaultMediaId`, der die Anzeigen angibt, die bereitgestellt werden, wenn folgende Bedingungen erfüllt sind:

   * Ihre Anfrage an den Anzeigen-Server ist ungültig oder der Inhalt ist falsch konfiguriert.
   * Bei der Primetime-Anzeigenentscheidung treten Verzögerungen bei der Datenübertragung auf.
   * Einer der Back-End-Prozesse der Primetime-Anzeigenentscheidung funktioniert nicht oder ist nicht verfügbar.
   >[!TIP]
   >
   >Adobe empfiehlt die Verwendung `defaultMediaId`.

* Ihre von Adobe zugewiesene `zoneID`Firma oder Website wird von Ihnen identifiziert.
* Die Domäne des zugewiesenen Anzeigenservers.
* Andere Targeting-Parameter.

   Sie können diese Parameter abhängig von Ihren Anforderungen und den Anforderungen des Anzeigenanbieters einbeziehen.