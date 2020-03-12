---
description: Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der PTSDKConfig-Klasse konfigurieren.
seo-description: Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der PTSDKConfig-Klasse konfigurieren.
seo-title: Methoden der Config-Klasse für Tags
title: Methoden der Config-Klasse für Tags
uuid: 27f1df0a-bbd3-4d80-820e-b659f2f33069
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Methoden der Config-Klasse für Tags {#config-class-methods-for-tags}

Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der PTSDKConfig-Klasse konfigurieren.

TVSDK wendet die globale Konfiguration automatisch auf jeden Medienstream an, der keine Stream-spezifische Konfiguration angibt.

`PTSDKConfig` stellt die folgenden Methoden zur Verwaltung der benutzerdefinierten Tags bereit:

| **Abonnieren bestimmter benutzerdefinierter Tags** |  |
|---|---|
| `subscribedTags` | Ruft die aktuelle Liste der abonnierten Tags ab. |
| `setSubscribedTags` | Legt die Liste der abonnierten Tags fest, die der Anwendung angezeigt werden. |
| **Anpassen der vom Standard-Opportunitätsdetektor verwendeten Anzeigen-Tags** |
| `adTags` | Ruft die aktuelle Liste der Anzeigen-Tags ab. |
| `setAdTags` | Legt die Liste der Anzeigen-Tags fest, die vom standardmäßigen Opportunitätsgenerator verwendet werden. |


Beachten Sie Folgendes:

* Die set-Methoden lassen nicht zu, dass der Parameter tags Null-Werte enthält.
* Der benutzerdefinierte Tag-Name muss das #-Präfix enthalten.

   Beispielsweise ist #EXT-X-ASSET ein richtiger benutzerdefinierter Tag-Name, EXT-X-ASSET ist jedoch nicht korrekt.
* Sie können die Konfiguration nach dem Laden des Medienstreams nicht mehr ändern.