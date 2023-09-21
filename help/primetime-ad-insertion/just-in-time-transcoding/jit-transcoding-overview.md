---
title: Just-in-Time-Transkodierung
description: Just-in-Time-Transkodierung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# Just-in-Time-Transkodierung {#just-in-time-transcoding}

Primetime Ad Insertion bietet Just-in-time-Transkodierung und -Verpackung, um sicherzustellen, dass inkompatible Werbeinhalte in Inhaltsströmen ordnungsgemäß wiedergegeben werden können. Es kann auch ID3-Pakete in Anzeigenfragmente einfügen, die beim clientseitigen Anzeigen-Tracking verwendet werden können.
Ein typischer Workflow sieht wie folgt aus:

1. Adobe Primetime Ad Insertion ruft Anzeigen/kreative Inhalte vom Werbeserver des Kunden ab.

1. Wenn das kreative Format einer Anzeige nativ mit dem Inhalts-Stream kompatibel ist, wird das Kreativelement in das Manifest eingefügt.

1. Wenn das kreative Format einer Anzeige nativ nicht kompatibel ist (z. B. .mp4, .mov, .webm), sucht Primetime Ad Insertion nach einer vorab transkodierten Version der Anzeige von einem angegebenen CDN. Wird eine Anzeige gefunden, wird diese eingefügt. Andernfalls wird die Anzeige zur Transkodierung in die Warteschlange gestellt.

1. Nachdem das Anzeigenmotiv transkodiert wurde, ordnet Primetime Ad Insertion alle nachfolgenden Anfragen für dieses Anzeigen-Asset in die Manifeste zu.

Primetime Ad Insertion unterstützt die Transkodierung für die meisten Video- und Linearformate. Die Transkodierung von Werbeinformationen erfolgt in der Regel in weniger als drei Minuten. Weitere Informationen erhalten Sie von Ihrem Primetime-Support-Mitarbeiter.
