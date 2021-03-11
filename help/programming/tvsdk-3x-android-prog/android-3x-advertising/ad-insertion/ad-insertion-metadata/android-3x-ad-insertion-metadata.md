---
description: Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter, wie z. B. Adobe Primetime und die Entscheidungsfindung, Konfigurationswerte eingeben, um Ihre Verbindung zum Anbieter zu aktivieren.
title: Anzeigeneinfügemetadaten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---


# Übersicht {#ad-nsertion-metadata-overview}

Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter, wie z. B. Adobe Primetime und die Entscheidungsfindung, Konfigurationswerte eingeben, um Ihre Verbindung zum Anbieter zu aktivieren.

TVSDK enthält die Primetime-Entscheidungsbibliothek. Damit Ihre Inhalte Werbung vom Primetime-Anzeigen-Entscheidungsserver enthalten, muss Ihre Anwendung die folgenden `AuditudeSettings`-Informationen bereitstellen:

* `mediaID`, was eine eindeutige ID für das abzuspielende Video darstellt.

   Der Herausgeber weist die mediaID beim Senden von Videoinhalten und Anzeigeninformationen an den Adobe Primetime-Ad-Decision-Server zu. Diese ID wird von Primetime-Anzeigenentscheidungen verwendet, um verwandte Werbeinformationen für das Video vom Server abzurufen.

* (Optional) `defaultMediaId`, der die Anzeigen angibt, die bereitgestellt werden, wenn die folgenden Bedingungen erfüllt sind:

   * Ihre Anfrage an den Anzeigen-Server ist ungültig oder der Inhalt ist falsch konfiguriert.
   * Bei der Primetime-Anzeigenentscheidung treten Verzögerungen bei der Datenübertragung auf.
   * Einer der Back-End-Prozesse der Primetime-Anzeigenentscheidung funktioniert nicht oder ist nicht verfügbar.

   >[!TIP]
   >
   >Adobe empfiehlt die Verwendung von `defaultMediaId`.

* Ihre `zoneID`, die der Adobe zugeordnet ist, kennzeichnet Ihre Firma oder Website.
* Die Domäne des zugewiesenen Anzeigenservers.
* Andere Targeting-Parameter.

   Sie können diese Parameter abhängig von Ihren Anforderungen und den Anforderungen des Anzeigenanbieters einbeziehen.