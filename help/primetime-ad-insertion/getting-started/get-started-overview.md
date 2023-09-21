---
title: Erste Schritte mit Adobe Primetime Ad Insertion
description: Erste Schritte mit Adobe Primetime Ad Insertion
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Erste Schritte mit Adobe Primetime Ad Insertion {#ptai-get-started}

Primetime Ad Insertion koordiniert die Systeme, die Inhalte und Anzeigen bereitstellen, um personalisierte, Stream-Werbeerlebnisse zu erstellen und dann die Anzeigenwiedergabe für Ihre Advertiser zu verfolgen.

Primetime Ad Insertion interagiert mit Client-Anwendungen, die Video-Sendungen bereitstellen, indem es Videommanifeste neu schreibt, um zielgerichtete Anzeigen und personalisierte Erlebnisse für jeden Betrachter bereitzustellen. Diese Manifeste kombinieren Inhalte und Anzeigen, die von einem Anzeigen-Server bereitgestellt werden, und können optional Metadaten mit detaillierten Anleitungen zum Anzeigen-Tracking enthalten. Primetime Ad Insertion unterstützt sowohl clientseitige als auch serverseitige Anzeigenverfolgung.

Nachdem das System ordnungsgemäß eingerichtet wurde, kann ein typischer Workflow wie folgt aussehen:

1. Die Clientanwendung generiert eine [Bootstrap-URL](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) mit Informationen zum Video-Stream und sendet eine GET-Anfrage an Primetime Ad Insertion.  Primetime Ad Insertion unterstützt HLS und DASH mit einer Vielzahl von Anzeigensignalisierungsformaten.

1. Primetime Ad Insertion antwortet, indem das Inhaltsmanifest vom CDN des Herausgebers zurück an die Clientanwendung gesendet wird.

1. Die Client-Anwendung wählt geeignete Streams im generierten Manifest zur Wiedergabe aus und sendet Anfragen an Primetime Ad Insertion.

1. Primetime-Ad Insertion ruft die angeforderten Streams aus dem Content CDN ab, analysiert/liest alle Cue-Informationen, führt Aufrufe an den Anzeigen-Server durch und ersetzt bei Bedarf Werbeunterbrechungen.

1. Primetime Ad Insertion normalisiert das Manifest, indem Ressourcen-URLs neu geschrieben werden und erkennt, ob Anzeigenkreative eine Transkodierung erfordern. Siehe [Just-in-time-Anzeigentranskodierung](/help/primetime-ad-insertion/just-in-time-transcoding/jit-transcoding-overview.md).

1. Primetime Ad Insertion ruft die erforderlichen Anzeigenkreativen ab und fügt die entsprechenden Fragmente in die Manifeste ein.

1. Primetime Ad Insertion stellt die endgültigen zugeordneten Manifeste, einschließlich Anzeigen, zur Wiedergabe in der Clientanwendung bereit.

1. Die Bereitstellung und Sichtbarkeit von Anzeigen kann entweder über Client- oder Server-seitiges Anzeigen-Tracking gemessen werden, siehe [Einrichten der Anzeigenverfolgung](/help/primetime-ad-insertion/getting-started/set-up-ad-tracking.md).

Primetime Ad Insertion unterstützt die meisten HLS/DASH-Client- und Player-Konfigurationen. Weitere Informationen zu den unterstützten Anzeigensignaturformaten finden Sie unter [Unterstützte Cue-Formate](/help/primetime-ad-insertion/getting-started/ad-insertion-live-linear-stream.md).
