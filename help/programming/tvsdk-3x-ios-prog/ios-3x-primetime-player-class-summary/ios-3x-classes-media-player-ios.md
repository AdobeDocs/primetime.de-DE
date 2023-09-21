---
description: Sie können die Objective-C-API des Primetime-Players verwenden, um das Verhalten des Players anzupassen.
title: Media Player-Klassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Media Player-Klassen {#media-player-classes}

Sie können die Objective-C-API des Primetime-Players verwenden, um das Verhalten des Players anzupassen.

Diese Klassen beschreiben Ihren Medienplayer und seine Ressourcen.

| Klasse | Beschreibung |
|---|---|
| PTABRControlParameters | Umfasst alle Kontrollparameter für die adaptive Bit-Rate. Folgende Parameter werden unterstützt:<ul><li>minBitRate</li><li>maxBitRate</li><li>initialBitRate</li></ul> |
| PTDefaultMediaPlayerClientFactory | Standardimplementierung von PTMediaPlayerClientFactory im TVSDK. Es stellt die Instanzen availablePTOportunityResolver, PTContentResolver und PTAdPolicySelector bereit. |
| PTMediaPlayer | Definiert die Stammkomponente für das Primetime Player-Framework. Anwendungen erstellen eine Instanz dieser Klasse, um ein Medium wiederzugeben. Diese Komponente sendet Benachrichtigungen, um Ihrer Anwendung den Status des Players jederzeit mitteilen zu können. |
| PTMediaPlayerClientFactory | Protokoll, das die Methoden beschreibt, die eine benutzerdefinierte Medienplayer-Client-Factory implementieren sollte, um die verfügbaren PTOportunityResolver-, PTContentResolver- und PTAdPolicySelector-Instanzen bereitzustellen. |
| PTMediaPlayerItem | Stellt ein bestimmtes Audio-Video-Medium dar. |
| PTMediaPlayerView | Verwaltet die Ansichtskomponente des Primetime Player-Frameworks. |
| PTMediaProfile | Stellt das Profil eines einzelnen Streams in der Wiedergabeliste dar. |
| PTMediaSelectionOption | Stellt eine audiovisuelle Medienressource dar, die verschiedene Sprachvoreinstellungen, Barrierefreiheitsanforderungen oder benutzerdefinierte Anwendungskonfigurationen unterstützt. Gültige Optionstypen:<ul><li>Untertitel (PTMediaSelectionOptionTypeSubtitle)</li><li>Alternatives Audio (PTMediaSelectionOptionTypeAudio)</li><li>Geschlossene Untertitel (PTMediaSelectionOptionTypeCC)</li><li>Undefiniert (PTMediaSelectionOptionTypeUndefined)</li></ul> |
| PTOportunityResolver class,PTOpportunityResolver-Protokoll | Klasse, die für die Verarbeitung von In-Manifest-Hinweisen verwendet wird, die als Platzierungen für den Adobe Primetime-Anzeigenentscheidungsprozess verwendet werden. |
| PTOportunityResolverDelegate | Protokoll, das die Methoden beschreibt, die der benutzerspezifische Opportunity-Resolver ( PTOportunityResolver ) verwenden sollte, um dem Delegaten den Status der Lösung der Chance zu kommunizieren. |
| PTSDK | Beschreibt die Version des TVSDK und seine Funktionen. |
| PTSDKConfig | Stellt globale TVSDK-Einstellungen bereit und ermöglicht es einer Anwendung, benutzerdefinierte HLS-Tags zu abonnieren. |
| PTTextStyleRule | Definiert Konstanten, die Attributschlüssel des Textstils darstellen, die das Wörterbuch der Regeln bilden. |
