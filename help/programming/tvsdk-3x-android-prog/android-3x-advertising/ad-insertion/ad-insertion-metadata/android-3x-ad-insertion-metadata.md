---
description: Damit der Anzeigenauflöser funktioniert, erfordern Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte, um Ihre Verbindung zum Provider zu ermöglichen.
title: Anzeigeneinfüge-Metadaten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Übersicht {#ad-nsertion-metadata-overview}

Damit der Anzeigenauflöser funktioniert, erfordern Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte, um Ihre Verbindung zum Provider zu ermöglichen.

TVSDK enthält die Primetime-Bibliothek für Anzeigenentscheidungen. Damit Ihre Inhalte Werbung vom Primetime-Anzeigen-Decisioning-Server enthalten, muss Ihre Anwendung die folgenden erforderlichen Informationen bereitstellen `AuditudeSettings` Information:

* `mediaID`: eine eindeutige Kennung für das abzuspielende Video.

  Der Herausgeber weist die mediaID beim Senden von Videoinhalten und Anzeigeninformationen an den Adobe Primetime-Ad Decisioning-Server zu. Diese ID wird von Primetime-Anzeigenentscheidungen verwendet, um verwandte Werbeinformationen für das Video vom Server abzurufen.

* (Optional) `defaultMediaId`, der die Anzeigen angibt, die bereitgestellt werden, wenn die folgenden Bedingungen erfüllt sind:

   * Ihre Anfrage an den Anzeigen-Server ist ungültig oder der Inhalt ist falsch konfiguriert.
   * Bei der Primetime- und Entscheidungsfindung treten Verzögerungen bei der Datenübertragung auf.
   * Einer der Back-End-Prozesse der Primetime-Anzeigenentscheidung funktioniert nicht oder ist nicht verfügbar.

  >[!TIP]
  >
  >Adobe empfiehlt, `defaultMediaId`.

* Ihre `zoneID`, die von Adobe zugewiesen wird, identifiziert Ihr Unternehmen oder Ihre Website.
* Die Domäne Ihres zugewiesenen Anzeigenservers.
* Andere Targeting-Parameter.

  Sie können diese Parameter entsprechend Ihren Anforderungen und den Anforderungen des Anzeigenanbieters einbeziehen.
