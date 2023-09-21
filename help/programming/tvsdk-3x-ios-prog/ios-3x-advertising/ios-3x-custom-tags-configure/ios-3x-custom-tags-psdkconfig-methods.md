---
description: Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der PTSDKConfig -Klasse konfigurieren.
title: Konfigurationsklassenmethoden für Tags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Konfigurationsklassenmethoden für Tags {#config-class-methods-for-tags}

Sie können benutzerdefinierte Tag-Namen in TVSDK global mit der PTSDKConfig -Klasse konfigurieren.

TVSDK wendet die globale Konfiguration automatisch auf alle Medien-Streams an, die keine Stream-spezifische Konfiguration angeben.

`PTSDKConfig` stellt diese Methoden zum Verwalten der benutzerdefinierten Tags bereit:

| **Abonnieren bestimmter benutzerdefinierter Tags** |  |
|---|---|
| `subscribedTags` | Ruft die aktuelle Liste der abonnierten Tags ab. |
| `setSubscribedTags` | Legt die Liste der abonnierten Tags fest, die der Anwendung angezeigt werden. |
| **Anpassen der Anzeigen-Tags, die vom standardmäßigen Opportunity-Detektor verwendet werden** |
| `adTags` | Ruft die aktuelle Liste der Anzeigen-Tags ab. |
| `setAdTags` | Legt die Liste der Anzeigen-Tags fest, die vom standardmäßigen Opportunity-Generator verwendet werden. |


Beachten Sie Folgendes:

* Die Setter-Methoden erlauben nicht, dass der Tag-Parameter Nullwerte enthält.
* Der benutzerdefinierte Tag-Name muss das #-Präfix enthalten.

  Beispielsweise ist #EXT-X-ASSET ein richtiger benutzerdefinierter Tag-Name, aber EXT-X-ASSET ist falsch.
* Sie können die Konfiguration nach dem Laden des Medien-Streams nicht mehr ändern.
