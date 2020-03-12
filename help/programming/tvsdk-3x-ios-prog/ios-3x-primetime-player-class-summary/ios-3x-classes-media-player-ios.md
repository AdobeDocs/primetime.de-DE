---
description: Sie können die Objective-C API des Primetime Player verwenden, um das Verhalten des Players anzupassen.
seo-description: Sie können die Objective-C API des Primetime Player verwenden, um das Verhalten des Players anzupassen.
seo-title: Media Player-Klassen
title: Media Player-Klassen
uuid: 705c71b6-4e5e-46b5-a59d-13df977b04f2
translation-type: tm+mt
source-git-commit: b13f2d3f083a6ca333a4edba1c8d7261f7d448ad

---


# Media Player-Klassen {#media-player-classes}

Sie können die Objective-C API des Primetime Player verwenden, um das Verhalten des Players anzupassen.

Diese Klassen beschreiben Ihren Medienplayer und seine Ressourcen.

| Class | Beschreibung |
|---|---|
| PTABRControlParameters | Kapselt alle Kontrollparameter für die adaptive Bitrate. Folgende Parameter werden unterstützt:<ul><li>minBitRate</li><li>maxBitRate</li><li>initialBitRate</li></ul> |
| PTDefaultMediaPlayerClientFactory | Standardimplementierung von PTMediaPlayerClientFactoryin im TVSDK. Es stellt die Instanzen availablePTOportunityResolver, PTContentResolver und PTAdPolicySelector bereit. |
| PTMediaPlayer | Definiert die Stammkomponente für das Primetime Player-Framework.Anwendungen erstellen eine Instanz dieser Klasse, um ein Medium wiederzugeben. Diese Komponente sendet Benachrichtigungen, um Ihre Anwendung jederzeit über den Status des Players zu informieren. |
| PTMediaPlayerClientFactory | Protokoll, das die Methoden beschreibt, die eine Client-Factory eines benutzerdefinierten Medienplayers implementieren sollte, um die verfügbaren PTOpportunityResolver-, PTContentResolver- und PTAdPolicySelector-Instanzen bereitzustellen. |
| PTMediaPlayerItem | Stellt ein bestimmtes Audio-Video-Medium dar. |
| PTMediaPlayerView | Verwaltet die Ansicht-Komponente des Primetime Player-Frameworks. |
| PTMediaProfile | Stellt das Profil eines einzelnen Streams in der Wiedergabeliste der Variante dar. |
| PTMediaSelectionOption | Stellt eine audiovisuelle Medienressource dar, die verschiedene Spracheinstellungen, Barrierefreiheitsanforderungen oder benutzerdefinierte Anwendungskonfigurationen unterstützt. Gültige Optionsarten:<ul><li>Untertitel (PTMediaSelectionOptionTypeSubtitle)</li><li>Alternativaudio (PTMediaSelectionOptionTypeAudio)</li><li>Untertitel (PTMediaSelectionOptionTypeCC)</li><li>Undefined (PTMediaSelectionOptionTypeUndefined)</li></ul> |
| PTOpportunityResolver-Klasse,PTOpportunityResolver-Protokoll | Klasse, die zur Verarbeitung von In-Manifest-Hinweisen verwendet wird, die als Platzierungen für den Adobe Primetime-Prozess der Anzeigenentscheidung verwendet werden. |
| PTOpportunityResolverDelegate | Protokoll, das die Methoden beschreibt, die der benutzerdefinierte Opportunity-Resolver ( PTOpportunityResolver ) verwenden sollte, um dem Delegaten den Status der Auflösung der Gelegenheit zu kommunizieren. |
| PTSDK | Beschreibt die Version des TVSDK und seine Funktionen. |
| PTSDKConfig | Stellt globale TVSDK-Einstellungen bereit und erlaubt einer Anwendung, benutzerdefinierte HLS-Tags zu abonnieren. |
| PTTextStyleRule | Definiert Konstanten, die Attributschlüssel für Textstile darstellen, die das Wörterbuch der Regeln bilden. |
