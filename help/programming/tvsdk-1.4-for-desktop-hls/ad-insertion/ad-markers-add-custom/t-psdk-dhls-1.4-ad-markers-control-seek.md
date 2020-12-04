---
description: Sie können das Standardverhalten für die Suche von TVSDK nach Anzeigen überschreiben, wenn Sie benutzerdefinierte Anzeigenmarken verwenden.
seo-description: Sie können das Standardverhalten für die Suche von TVSDK nach Anzeigen überschreiben, wenn Sie benutzerdefinierte Anzeigenmarken verwenden.
seo-title: Steuern des Wiedergabeverhaltens für die Suche nach benutzerdefinierten Anzeigenmarken
title: Steuern des Wiedergabeverhaltens für die Suche nach benutzerdefinierten Anzeigenmarken
uuid: 926299c6-9c23-457d-b836-08432e4e169e
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Steuern des Wiedergabeverhaltens für die Suche nach benutzerdefinierten Anzeigenmarken{#control-playback-behavior-for-seeking-over-custom-ad-markers}

Sie können das Standardverhalten für die Suche von TVSDK nach Anzeigen überschreiben, wenn Sie benutzerdefinierte Anzeigenmarken verwenden.

Standardmäßig überspringt TVSDK die Anzeigen, wenn ein Benutzer in Abschnitte der Anzeige, die sich aus der Platzierung benutzerspezifischer Anzeigenmarken ergeben, einspringt oder sie vergangene Abschnitte durchsucht. Dies kann sich von dem aktuellen Wiedergabeverhalten bei Standard-Werbeunterbrechungen unterscheiden.

Sie können TVSDK anweisen, die Abspielleiste an den Anfang der zuletzt übersprungenen benutzerdefinierten Anzeige zu verschieben, wenn der Benutzer nach einer oder mehreren benutzerdefinierten Anzeigen sucht.

1. Konfigurieren Sie eine Metadateninstanz mit der Auflistung `DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED`, die auf den Zeichenfolgenwert &quot;true&quot;gesetzt ist (nicht als boolescher Wert `true`).

1. Erstellen und konfigurieren Sie eine `MediaResource`-Instanz und übergeben Sie die zusätzlichen Konfigurationsoptionen an `TimeRangeCollection.toMetadata`. Diese Methode erhält zusätzliche Konfigurationsoptionen über eine andere generische Metadatenstruktur.

