---
description: Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der PTSDKConfig-Klasse konfigurieren.
seo-description: Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der PTSDKConfig-Klasse konfigurieren.
seo-title: Methoden der Config-Klasse für Tags
title: Methoden der Config-Klasse für Tags
uuid: 1d3651a0-3b70-4d3a-8ced-663a9dad7205
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# Methoden der Config-Klasse für Tags{#config-class-methods-for-tags}

Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der PTSDKConfig-Klasse konfigurieren.

TVSDK wendet die globale Konfiguration automatisch auf jeden Medienstream an, der keine Stream-spezifische Konfiguration angibt.

`PTSDKConfig` stellt die folgenden Methoden zur Verwaltung der benutzerdefinierten Tags bereit:

| **Abonnieren bestimmter benutzerdefinierter Tags** |
|---|
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

