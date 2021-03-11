---
description: Diese Klassen bieten Metadaten für Werbung, Namensraum und Verfolgung.
title: Metadaten-Klassen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---


# Metadatenklassen{#metadata-classes}

Diese Klassen bieten Metadaten für Werbung, Namensraum und Verfolgung.

Paket: [com.adobe.mediacore.metadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/package-summary.html)

| Name | Beschreibung |
|---|---|
| [AdvertisingMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html) | Klasse, die Eigenschaften bereitstellt, die für die Auflösung von Anzeigen für ein bestimmtes Medienelement konfiguriert werden sollten. Alle erforderlichen Eigenschaften müssen festgelegt werden, um den Player für die erfolgreiche Auflösung von Anzeigen zu konfigurieren. |
| AuditudeMetadata | Veraltet. Verwenden Sie AuditudeSettings. |
| [AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AuditudeSettings.html) | Klasse, die Java `AdvertisingMetadata` speziell für Phrase erweitert. Stellt Eigenschaften bereit, die für die Auflösung von Phrase-Anzeigen für ein bestimmtes Medienelement konfiguriert werden. Sie müssen alle erforderlichen Eigenschaften festlegen, einschließlich Zonen-ID, Medien-ID und Anzeigen-Server-URL, um den Player für die erfolgreiche Auflösung von Anzeigen zu konfigurieren. |
| [Metadaten](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/Metadata.html) | Definiert die allgemeine Schnittstelle zum Konfigurieren aller verfügbaren Metadaten für Ihren Player und für weitere Objekte. |
| [MetadataNode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/MetadataNode.html) | Generische datenstrukturähnliche Klasse zum Speichern beliebiger Schlüssel/Wert-Paare. |
| [TimedMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/TimedMetadata.html) | Klasse für die Rohdarstellung der in einen Medienstream eingefügten Metadaten. |