---
description: Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter, wie z. B. Adobe Primetime und die Entscheidungsfindung, Konfigurationswerte eingeben, um Ihre Verbindung zum Anbieter zu aktivieren.
seo-description: Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter, wie z. B. Adobe Primetime und die Entscheidungsfindung, Konfigurationswerte eingeben, um Ihre Verbindung zum Anbieter zu aktivieren.
seo-title: Anzeigeneinfügemetadaten
title: Anzeigeneinfügemetadaten
uuid: 676e81b9-4c2b-487e-bc68-74879ca2966b
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '245'
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