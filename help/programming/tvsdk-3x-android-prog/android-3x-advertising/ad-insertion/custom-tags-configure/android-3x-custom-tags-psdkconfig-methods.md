---
description: Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der MediaPlayerItemConfig -Klasse konfigurieren.
title: Konfigurationsklassenmethoden für Tags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Konfigurationsklassenmethoden für Tags {#config-class-methods-for-tags}

Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der MediaPlayerItemConfig -Klasse konfigurieren.

TVSDK wendet die globale Konfiguration automatisch auf alle Medien-Streams an, die keine Stream-spezifische Konfiguration angeben.

`MediaPlayerItemConfig` stellt diese Methoden zum Verwalten der benutzerdefinierten Tags bereit:

**Abonnieren bestimmter benutzerdefinierter Tags**

| <b>Methode</b> | <b>Beschreibung</b> |
|--- |--- |
| `public final String[] getSubscribedTags` | Ruft die aktuelle Liste der abonnierten Tags ab. |
| `public final void setSubscribedTags(String[] tags);` | Legt die Liste der abonnierten Tags fest, die der Anwendung angezeigt werden.  Ihre Anwendung wird auch automatisch für alle Tags angemeldet, die über `setAdTags`. |

**Anpassen der Anzeigen-Tags, die vom standardmäßigen Opportunity-Detektor verwendet werden**

| <b>Methode</b> | <b>Beschreibung</b> |
|--- |--- |
| `public final String[] getAdTags;` | Ruft die aktuelle Liste der Anzeigen-Tags ab. |
| `public final void setAdTags(String[] tags);` | Legt die Liste der Anzeigen-Tags fest, die vom standardmäßigen Opportunity-Generator verwendet werden. |

Beachten Sie Folgendes:

* Die Setter-Methoden erlauben nicht, dass der Tag-Parameter Nullwerte enthält.

  Wenn festgestellt, gibt TVSDK eine `IllegalArgumentException`.
* Der benutzerdefinierte Tag-Name muss die Variable `#` -Präfix.

  Beispiel: `#EXT-X-ASSET` ist ein korrekter benutzerdefinierter Tag-Name, aber `EXT-X-ASSET` ist falsch.

* Sie können die Konfiguration nach dem Laden des Medien-Streams nicht mehr ändern.
