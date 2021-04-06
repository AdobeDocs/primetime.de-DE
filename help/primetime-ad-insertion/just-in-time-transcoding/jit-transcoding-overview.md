---
title: Just-in-time-Transkodierung
description: Just-in-time-Transkodierung
copied-description: true
exl-id: 9577e1d5-1462-49d6-9d24-94e74dc9c019
translation-type: tm+mt
source-git-commit: 3e63c187f12d1bff53370bbcde4d6a77f58f3b4f
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# Just-in-time-Transkodierung {#just-in-time-transcoding}

Primetime Ad Insertion bietet Just-in-time-Transkodierung und -Verpackung, um sicherzustellen, dass inkompatible Werbeinhalte in Inhaltsströmen korrekt wiedergegeben werden können. Es kann auch ID3-Pakete in Anzeigenfragmente injizieren, die bei der clientseitigen Anzeigenverfolgung verwendet werden können.
Ein typischer Workflow ist:

1. Adobe Primetime Ad Insertion ruft Anzeigen/kreative Elemente vom Anzeigen-Server des Kunden ab.

1. Wenn das kreative Format einer Anzeige nativ mit dem Inhaltsstream kompatibel ist, wird das kreative Element in das Manifest eingefügt.

1. Wenn das kreative Format einer Anzeige nicht nativ kompatibel ist (z. B. .mp4, .mov, .webm), sucht Primetime Ad Insertion nach einer vorab transkodierten Version der Anzeige aus einem angegebenen CDN. Wird eine Anzeige gefunden, wird diese eingefügt. Andernfalls wird die Anzeige zur Transkodierung in die Warteschlange gestellt.

1. Nachdem das Werbegeschöpf transkodiert wurde, ordnet Primetime Ad Insertion alle nachfolgenden Anforderungen für dieses Anzeigenelement in die Manifeste ein.

Primetime Ad Insertion unterstützt Transkodierung bei den meisten Video- und linearen Formaten. Die kreative Transkodierung von Anzeigen erfolgt in der Regel innerhalb von drei Minuten. Weitere Informationen erhalten Sie von Ihrem Primetime-Support-Mitarbeiter.
