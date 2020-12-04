---
description: Die Referenzimplementierung zeigt, wie Sie den Player für Anzeigen einrichten. Dazu gehören das Einrichten von Videometadaten für das Einfügen von Anzeigen und das Auflösen der Pre-, Mid- und Post-Roll-Anzeigen in VOD- oder Live-/Lineare-Videostreams. Es zeigt auch, wie mit anklickbaren Anzeigen umzugehen ist.
seo-description: Die Referenzimplementierung zeigt, wie Sie den Player für Anzeigen einrichten. Dazu gehören das Einrichten von Videometadaten für das Einfügen von Anzeigen und das Auflösen der Pre-, Mid- und Post-Roll-Anzeigen in VOD- oder Live-/Lineare-Videostreams. Es zeigt auch, wie mit anklickbaren Anzeigen umzugehen ist.
seo-title: Anzeigeneinfügung
title: Anzeigeneinfügung
uuid: 75c1d77a-a7ff-4cb6-ad7f-7c83a950b7cb
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Anzeigeneinfügung {#ad-insertion}

Die Referenzimplementierung zeigt, wie Sie den Player für Anzeigen einrichten. Dazu gehören das Einrichten von Videometadaten für das Einfügen von Anzeigen und das Auflösen der Pre-, Mid- und Post-Roll-Anzeigen in VOD- oder Live-/Lineare-Videostreams. Es zeigt auch, wie mit anklickbaren Anzeigen umzugehen ist.

Das Einrichten eines Players zum Einfügen von Anzeigen umfasst Folgendes:

* **Input-Feed:** Füllen eines Eingabefeds mit Anzeigenmetadaten. Siehe [Katalogformat](../set-up-dev-environment/exploring-code/catalog-format.md).
* **Referenz-Implementierungs-Feed-Adapter:** Analysieren des Eingabefelds zum Füllen eines Ad-Metadatenobjekts.
* **AdsManager:AdsManager** verwenden, um die Anzeigenmetadaten abzurufen und den entsprechenden AdProvider zu erstellen.