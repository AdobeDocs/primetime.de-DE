---
description: Mit der MediaPlayerItemConfig-Klasse können Sie benutzerdefinierte Tag-Namen in TVSDK global konfigurieren.
seo-description: Mit der MediaPlayerItemConfig-Klasse können Sie benutzerdefinierte Tag-Namen in TVSDK global konfigurieren.
seo-title: Methoden der Config-Klasse für Tags
title: Methoden der Config-Klasse für Tags
uuid: b75aebac-4b94-4c42-bed4-3c17ad989cd1
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---


# Methoden der Config-Klasse für Tags {#config-class-methods-for-tags}

Mit der MediaPlayerItemConfig-Klasse können Sie benutzerdefinierte Tag-Namen in TVSDK global konfigurieren.

TVSDK wendet die globale Konfiguration automatisch auf jeden Medienstream an, der keine Stream-spezifische Konfiguration angibt.

`MediaPlayerItemConfig` stellt die folgenden Methoden zur Verwaltung der benutzerdefinierten Tags bereit:

**Abonnieren bestimmter benutzerdefinierter Tags**

| <b>Methode</b> | <b>Beschreibung</b> |
|--- |--- |
| `public final String[] getSubscribedTags` | Ruft die aktuelle Liste der abonnierten Tags ab. |
| `public final void setSubscribedTags(String[] tags);` | Legt die Liste der abonnierten Tags fest, die der Anwendung angezeigt werden.  Ihre Anwendung wird auch automatisch für alle Tags abonniert, die über `setAdTags` übertragen werden. |

**Anpassen der vom Standard-Opportunitätsdetektor verwendeten Anzeigen-Tags**

| <b>Methode</b> | <b>Beschreibung</b> |
|--- |--- |
| `public final String[] getAdTags;` | Ruft die aktuelle Liste der Anzeigen-Tags ab. |
| `public final void setAdTags(String[] tags);` | Legt die Liste der Anzeigen-Tags fest, die vom standardmäßigen Opportunitätsgenerator verwendet werden. |

Beachten Sie Folgendes:

* Die set-Methoden lassen nicht zu, dass der Parameter tags Null-Werte enthält.

   Wenn TVSDK gefunden, wird ein `IllegalArgumentException` ausgegeben.
* Der benutzerdefinierte Tag-Name muss das Präfix `#` enthalten.

   `#EXT-X-ASSET` ist beispielsweise ein korrekter benutzerdefinierter Tag-Name, `EXT-X-ASSET` ist jedoch nicht korrekt.

* Sie können die Konfiguration nach dem Laden des Medienstreams nicht mehr ändern.