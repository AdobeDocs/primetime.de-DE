---
description: Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter, wie z. B. Adobe Primetime und die Entscheidungsfindung, Konfigurationswerte eingeben, um Ihre Verbindung zum Anbieter zu aktivieren.
seo-description: Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter, wie z. B. Adobe Primetime und die Entscheidungsfindung, Konfigurationswerte eingeben, um Ihre Verbindung zum Anbieter zu aktivieren.
seo-title: Anzeigeneinfügemetadaten
title: Anzeigeneinfügemetadaten
uuid: f40ed53b-eba1-4f70-a29c-90cac51e8a9a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# Übersicht {#ad-insertion-metadata}

Damit der Anzeigenauflöser funktionieren kann, müssen Anzeigenanbieter, wie z. B. Adobe Primetime und die Entscheidungsfindung, Konfigurationswerte eingeben, um Ihre Verbindung zum Anbieter zu aktivieren.

TVSDK enthält die Primetime-Bibliothek für Anzeigenentscheidungen. Damit Ihre Inhalte Werbung vom Primetime-Anzeigen-Entscheidungsserver enthalten, muss Ihre Anwendung die folgenden `AuditudeSettings`-Informationen bereitstellen:

* `mediaID`, was eine eindeutige ID für das abzuspielende Video darstellt.

   Der Herausgeber weist das `mediaID` zu, wenn Videoinhalte und Anzeigeninformationen an den Adobe Primetime-Ad-Decision-Server gesendet werden. Diese ID wird von der Primetime-Anzeigenentscheidung verwendet, um verwandte Werbeinformationen für das Video vom Server abzurufen.

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