---
title: Erste Schritte mit Adobe Primetime Ad Insertion
description: Erste Schritte mit Adobe Primetime Ad Insertion
translation-type: tm+mt
source-git-commit: 2a9bb089cda2b315f91b30d5cab0db9b3e372799
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---


# Erste Schritte mit Adobe Primetime Ad Insertion {#ptai-get-started}

Primetime Ad Insertion koordiniert die Systeme, die Inhalte und Anzeigen bereitstellen, um personalisierte, Stream-Anzeigenerlebnisse zu erstellen und dann die Anzeigenwiedergabe für Ihre Werbekunden zu verfolgen.

Primetime-Ad Insertion interagiert mit Video-Versand-Clientanwendungen, indem Videomanifeste neu geschrieben werden, um zielgerichtete Anzeigen und personalisierte Erlebnisse für jeden Viewer bereitzustellen. Diese Manifeste kombinieren Inhalte und Anzeigen, die von einem Anzeigen-Server bereitgestellt werden, und können optional Metadaten mit detaillierten Anleitungen zur Anzeigenverfolgung enthalten. Primetime Ad Insertion unterstützt sowohl clientseitige als auch serverseitige Anzeigenverfolgung.

Nachdem das System ordnungsgemäß eingerichtet wurde, könnte ein typischer Workflow wie folgt aussehen:

1. Die Clientanwendung generiert eine [Bootstrap-URL](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md) mit Informationen zum Videostream und sendet eine GET an Primetime Ad Insertion.

1. Primetime Ad Insertion reagiert, indem das Inhaltsmanifest vom CDN des Herausgebers zurück an die Clientanwendung gesendet wird.

1. Die Clientanwendung wählt geeignete Streams im erstellten Manifest zur Wiedergabe aus und sendet Anfragen an Primetime Ad Insertion.

1. Primetime-Ad Insertion ruft die angeforderten Streams aus dem Content CDN ab, analysiert/liest Cue-Informationen, ruft den Anzeigenserver auf und ersetzt bei Bedarf Werbeunterbrechungen.

1. Primetime-Ad Insertion normalisiert das Manifest, indem Ressourcen-URLs umgeschrieben und festgestellt wird, ob für Werbeinhalte Transkodierung erforderlich ist. <!-- see [Just-in-time ad transcoding](just-in-time-transcoding.md) and [packaging](just-in-time-repackaging.md).-->

1. Primetime-Ad Insertion ruft die erforderlichen Anzeigenkreative ab und fügt die entsprechenden Fragmente in die Manifeste ein.

1. Primetime Ad Insertion liefert die endgültigen gehefteten Manifeste einschließlich Anzeigen zur Wiedergabe an die Clientanwendung.

1. Der Versand und die Sichtbarkeit der Anzeige können entweder über die clientseitige oder serverseitige Anzeigenverfolgung gemessen werden (siehe [Einrichten der Anzeigenverfolgung](set-up-ad-tracking.md)).

Primetime Ad Insertion unterstützt die meisten Clientkonfigurationen für HLS/DASH.
