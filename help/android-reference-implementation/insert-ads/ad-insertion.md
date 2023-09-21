---
description: Die Referenzimplementierung zeigt, wie Sie den Player für Anzeigen einrichten. Dazu gehören das Einrichten von Videometadaten für das Einfügen von Anzeigen und das Auflösen der Pre-, Mid- und Post-Roll-Anzeigen in VOD- oder Live-/Linear-Videostreams. Es zeigt auch, wie anklickbare Anzeigen verarbeitet werden.
title: Anzeigeneinfügung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Anzeigeneinfügung {#ad-insertion}

Die Referenzimplementierung zeigt, wie Sie den Player für Anzeigen einrichten. Dazu gehören das Einrichten von Videometadaten für das Einfügen von Anzeigen und das Auflösen der Pre-, Mid- und Post-Roll-Anzeigen in VOD- oder Live-/Linear-Videostreams. Es zeigt auch, wie anklickbare Anzeigen verarbeitet werden.

Die Einrichtung eines Players für das Einfügen von Anzeigen umfasst Folgendes:

* **Input Feed:** Füllen eines Eingabe-Feeds mit Anzeigenmetadaten. Siehe [Katalogformat](../set-up-dev-environment/exploring-code/catalog-format.md).
* **Referenz-Implementierungs-Feed-Adapter:** Analysieren des Eingabe-Feeds zum Ausfüllen eines Anzeigenmetadatenobjekts.
* **AdsManager:** Verwenden des AdsManager zum Abrufen der Anzeigenmetadaten und Erstellen des entsprechenden AdProvider.
