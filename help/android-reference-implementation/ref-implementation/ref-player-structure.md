---
description: Die Funktions-Manager dienen als Wrapper um die TVSDK-Bibliothek.
title: Referenz-Implementierungsstruktur
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Referenz-Implementierungsstruktur {#reference-implementation-structure}

Die Funktions-Manager dienen als Wrapper um die TVSDK-Bibliothek.

In Java sind Klassen in einer Hierarchie strukturiert. Beispielsweise der gesamte benutzeroberflächenbezogene Code unter `com.adobe.primetime.reference.ui` und alle Feature Manager befinden sich unter `com.adobe.primetime.reference.manager`.

Die Primetime-Referenzimplementierung enthält die folgenden Pakete:

| Paket | Beschreibung |
|--- |--- |
| [com.adobe.primetime.reference](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/PrimetimeReference.html) | Diese Klasse erweitert android.app.Application. |
| [com.adobe.primetime.reference.advertising](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/advertising/package-summary.html) | Enthält Code für benutzerdefinierte Anzeigen. |
| [com.adobe.primetime.reference.config](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html) | Enthält den Code der Benutzeroberfläche, der zum Konfigurieren der Feature Manager erforderlich ist. |
| [com.adobe.primetime.reference.drm](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/drm/package-summary.html) | Enthält Hilfsklassen für DRM. |
| [com.adobe.primetime.reference.feeds](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/feeds/package-summary.html) | Die Adapter und Elementadapter für Schnittstellen-, Plattform- und Referenzinformationen. Enthält auch den Code FeedAdapterFactory, ContentRenditionInfo und XMLParserHelper . |
| [com.adobe.primetime.reference.logging](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/logging/package-summary.html) | Stellt Klassen für die lokale und Remote-Protokollierung bereit. |
| [com.adobe.primetime.reference.manager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/package-summary.html) | Hier finden Sie die Funktionsmanager sowie die ManagerFactory. Für optionale Funktionen, die Sie aktivieren oder deaktivieren können, gibt es zwei Feature Manager: <ul><li>Ein Feature Manager, der den Namen der Funktion darstellt, z. B. CCManager. Dieser Feature Manager ist deaktiviert und bietet das standardmäßige Aus-Verhalten.</li><li>Ein Feature Manager, an den An an den Namen des Feature Manager angehängt ist, z. B. CCManagerOn. Dieser Feature Manager stellt Beispielcode für die aktivierte Funktion bereit.</li></ul> |
| [com.adobe.primetime.reference.ui.catalog](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/catalog/package-summary.html) | Enthält Benutzeroberflächencode für den Katalog. |
| [com.adobe.primetime.reference.ui.log](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/log/package-summary.html) | Enthält Benutzeroberflächencode für das Protokoll. |
| [com.adobe.primetime.reference.ui.player](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/package-summary.html) | Enthält Benutzeroberflächencode für den Player. |
| [com.adobe.primetime.reference.ui.settings](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/settings/package-summary.html) | Enthält Benutzeroberflächencode für Einstellungen. |
| [com.adobe.primetime.reference.utils](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/utils/package-summary.html) | Enthält allgemeine Dienstprogrammklassen. |
| [com.adobe.primetime.reference.utils.http](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/utils/http/package-summary.html) | Enthält `HTTP-specific` Dienstprogrammklassen. |
