---
description: Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte benötigen, um Ihre Verbindung zum Anbieter zu aktivieren.
seo-description: Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte benötigen, um Ihre Verbindung zum Anbieter zu aktivieren.
seo-title: Anzeigeneinfügemetadaten
title: Anzeigeneinfügemetadaten
uuid: 8848c939-1f12-4145-8025-453b4fe79aae
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Übersicht {#ad-insertion-metadata-overview}

Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte benötigen, um Ihre Verbindung zum Anbieter zu aktivieren.

Browser TVSDK enthält die Adobe Primetime-Bibliothek für Anzeigenentscheidungen. Damit Ihre Inhalte Werbung vom Adobe Primetime-Anzeigen-Entscheidungsserver enthalten, muss Ihre Anwendung die folgenden erforderlichen AudidtudeSettings-Informationen bereitstellen:

* `mediaID`, was eine eindeutige ID für das abzuspielende Video darstellt.

   Der Herausgeber weist die mediaID beim Senden von Videoinhalten und Anzeigeninformationen an den Adobe Primetime-Ad-Entscheidungsserver zu. Diese ID wird von der Adobe Primetime-Anzeigenentscheidung verwendet, um zugehörige Werbeinformationen für das Video vom Server abzurufen.

* (Optional) `defaultMediaId`, der die Anzeigen angibt, die bereitgestellt werden, wenn folgende Bedingungen erfüllt sind:

   * Ihre Anfrage an den Anzeigen-Server ist ungültig oder der Inhalt ist falsch konfiguriert.
   * Bei der Adobe Primetime-Anzeigenentscheidung treten Verzögerungen bei der Datenübertragung auf.
   * Einer der Back-End-Prozesse von Adobe Primetime und die Entscheidungsfindung ist fehlerhaft oder nicht verfügbar.
   >[!TIP]
   >
   >Adobe empfiehlt die Verwendung `defaultMediaId`.

* Ihre von Adobe zugewiesene `zoneID`Firma oder Website wird von Ihnen identifiziert.
* Die Domäne des zugewiesenen Anzeigenservers.
* Andere Targeting-Parameter.

   Sie können diese Parameter abhängig von Ihren Anforderungen und den Anforderungen des Anzeigenanbieters einbeziehen.