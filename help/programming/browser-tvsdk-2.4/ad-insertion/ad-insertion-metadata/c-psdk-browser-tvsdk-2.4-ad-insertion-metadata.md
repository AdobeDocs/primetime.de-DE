---
description: Damit der Anzeigenauflöser funktioniert, erfordern Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte, um Ihre Verbindung zum Provider zu ermöglichen.
title: Anzeigeneinfüge-Metadaten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Übersicht {#ad-insertion-metadata-overview}

Damit der Anzeigenauflöser funktioniert, erfordern Anzeigenanbieter wie Adobe Primetime und die Entscheidungsfindung Konfigurationswerte, um Ihre Verbindung zum Provider zu ermöglichen.

Browser TVSDK enthält die Adobe Primetime-Bibliothek für Anzeigenentscheidungen. Damit Ihre Inhalte Werbung vom Adobe Primetime-Adentscheidung-Server enthalten, muss Ihre Anwendung die folgenden erforderlichen AudidtudeSettings-Informationen bereitstellen:

* `mediaID`: eine eindeutige Kennung für das abzuspielende Video.

  Der Herausgeber weist die mediaID beim Senden von Videoinhalten und Anzeigeninformationen an den Adobe Primetime-Ad Decisioning-Server zu. Diese ID wird von Adobe Primetime-Anzeigenentscheidungen verwendet, um verwandte Werbeinformationen für das Video vom Server abzurufen.

* (Optional) `defaultMediaId`, der die Anzeigen angibt, die bereitgestellt werden, wenn die folgenden Bedingungen erfüllt sind:

   * Ihre Anfrage an den Anzeigen-Server ist ungültig oder der Inhalt ist falsch konfiguriert.
   * Adobe Primetime-Anzeigenentscheidungen verzögern die Datenübertragung.
   * Einer der Backend-Prozesse der Adobe Primetime-Anzeigenentscheidung funktioniert nicht oder ist nicht verfügbar.

  >[!TIP]
  >
  >Adobe empfiehlt, `defaultMediaId`.

* Ihre `zoneID`, die von Adobe zugewiesen wird, identifiziert Ihr Unternehmen oder Ihre Website.
* Die Domäne Ihres zugewiesenen Anzeigenservers.
* Andere Targeting-Parameter.

  Sie können diese Parameter entsprechend Ihren Anforderungen und den Anforderungen des Anzeigenanbieters einbeziehen.
