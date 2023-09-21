---
description: Diese Klassen bieten Metadaten für Werbung, Namespaces und Tracking.
title: Metadatenklassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Metadatenklassen{#metadata-classes}

Diese Klassen bieten Metadaten für Werbung, Namespaces und Tracking.

Package: [com.adobe.mediacore.metadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/package-summary.html)

| Name | Beschreibung |
|---|---|
| [AdvertisingMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html) | Klasse, die Eigenschaften bereitstellt, die für die Auflösung von Anzeigen für ein bestimmtes Medienelement konfiguriert werden sollen. Alle erforderlichen Eigenschaften müssen festgelegt sein, um den Player für die erfolgreiche Auflösung von Anzeigen zu konfigurieren. |
| AuditudeMetadata | Veraltet. Verwenden Sie AuditudeSettings. |
| [AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AuditudeSettings.html) | Klasse, die Java erweitert `AdvertisingMetadata` speziell für Wortgruppe. Stellt Eigenschaften bereit, die für die Auflösung von Phrase-Anzeigen für ein bestimmtes Medienelement konfiguriert werden. Sie müssen alle erforderlichen Eigenschaften festlegen, einschließlich Zone ID, Medien-ID und Anzeigen-Server-URL, um den Player für die erfolgreiche Auflösung von Anzeigen zu konfigurieren. |
| [Metadaten](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/Metadata.html) | Definiert die generische Benutzeroberfläche zum Konfigurieren aller verfügbaren Metadaten für Ihren Player und weiterer Objekte. |
| [MetadataNode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/MetadataNode.html) | Generische datenstrukturähnliche Klasse zum Speichern beliebiger Schlüssel-Wert-Paare. |
| [TimedMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/TimedMetadata.html) | Klasse für die Rohdarstellung der zeitgesteuerten Metadaten, die in einen Medien-Stream eingefügt werden. |
