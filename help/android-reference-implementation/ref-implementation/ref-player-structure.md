---
description: Die Funktionenmanager dienen als Wrapper rund um die TVSDK-Bibliothek.
seo-description: Die Funktionenmanager dienen als Wrapper rund um die TVSDK-Bibliothek.
seo-title: Referenz-Implementierungsstruktur
title: Referenz-Implementierungsstruktur
uuid: ae347a97-1500-476a-9fc8-c99e6b2ab8de
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Referenz-Implementierungsstruktur {#reference-implementation-structure}

Die Funktionenmanager dienen als Wrapper rund um die TVSDK-Bibliothek.

In Java sind Klassen in einer Hierarchie strukturiert. So befinden sich beispielsweise der gesamte Code für die Benutzeroberfläche unter `com.adobe.primetime.reference.ui` und alle Funktionsmanager unter `com.adobe.primetime.reference.manager`.

Die Primetime-Referenzimplementierung enthält die folgenden Pakete:

| Paket | Beschreibung |
|--- |--- |
| [com.adobe.primetime.reference](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/PrimetimeReference.html) | Diese Klasse erweitert android.app.Application. |
| [com.adobe.primetime.reference.advertising](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/advertising/package-summary.html) | Enthält Code für benutzerdefinierte Anzeigen. |
| [com.adobe.primetime.reference.config](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html) | Enthält den Code der Benutzeroberfläche, der zum Konfigurieren der Feature Manager erforderlich ist. |
| [com.adobe.primetime.reference.drm](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/drm/package-summary.html) | Enthält Hilfsklassen für DRM. |
| [com.adobe.primetime.reference.feeds](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/feeds/package-summary.html) | Die Adapter und Elementadapter für die Benutzeroberfläche, Plattform und Referenzinformationen. Enthält auch den Code FeedAdapterFactory, ContentRenditionInfo und XMLParserHelper. |
| [com.adobe.primetime.reference.logging](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/logging/package-summary.html) | Stellt Klassen für die lokale und remote Protokollierung bereit. |
| [com.adobe.primetime.reference.manager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/package-summary.html) | Hier finden Sie die Funktionenmanager sowie die ManagerFactory. Für optionale Funktionen, die Sie aktivieren oder deaktivieren können, gibt es zwei Funktionsmanager: <ul><li>Ein Funktionsmanager, der den Namen der Funktion darstellt, z. B. CCManager. Dieser Funktionsmanager ist deaktiviert und bietet das Standardverhalten.</li><li>Ein Funktionsmanager, an den der Name des Funktionsmanagers An angehängt ist, z. B. CCManagerOn. Dieser Funktionsmanager bietet Beispielcode für die aktivierte Funktion.</li></ul> |
| [com.adobe.primetime.reference.ui.catalog](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/catalog/package-summary.html) | Enthält UI-Code für den Katalog. |
| [com.adobe.primetime.reference.ui.log](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/log/package-summary.html) | Enthält Benutzeroberflächencode für das Protokoll. |
| [com.adobe.primetime.reference.ui.player](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/package-summary.html) | Enthält UI-Code für den Player. |
| [com.adobe.primetime.reference.ui.settings](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/settings/package-summary.html) | Enthält UI-Code für Einstellungen. |
| [com.adobe.primetime.reference.utils](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/utils/package-summary.html) | Enthält allgemeine Dienstprogrammklassen. |
| [com.adobe.primetime.reference.utils.http](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/utils/http/package-summary.html) | Enthält `HTTP-specific` Dienstprogrammklassen. |
