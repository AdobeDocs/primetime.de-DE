---
description: Sie können das standardmäßige Anzeigenverhalten verwenden.
title: Verwenden des standardmäßigen Wiedergabe-Verhaltens
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Verwenden des standardmäßigen Wiedergabe-Verhaltens {#use-the-default-playback-behavior}

Sie können das standardmäßige Anzeigenverhalten verwenden.

1. Führen Sie eine der folgenden Aufgaben aus, um Standardverhalten zu verwenden:

   * Wenn Sie Ihre eigene `AdvertisingFactory` class, return null for `createAdPolicySelector`.

   * Wenn Sie keine benutzerdefinierte Implementierung für die `AdvertisingFactory` -Klasse verwendet TVSDK einen standardmäßigen Anzeigenrichtlinienselektor.

## Einrichten der benutzerdefinierten Wiedergabe {#set-up-customized-playback}

Sie können Anzeigenverhalten anpassen oder überschreiben.

Bevor Sie Anzeigenverhalten anpassen oder überschreiben können, registrieren Sie die Anzeigenrichtlinieninstanz bei .
Führen Sie einen der folgenden Schritte aus, um das Anzeigenverhalten anzupassen:

* Implementieren des `AdPolicySelector` -Schnittstelle und all ihre Methoden.

  Diese Option wird empfohlen, wenn Sie **all** Standardverhalten der Anzeige.

* Erweitern Sie die `DefaultAdPolicySelector` -Klasse und stellen Implementierungen nur für jene Verhaltensweisen bereit, die angepasst werden müssen.

  Diese Option wird empfohlen, wenn Sie nur **some** des Standardverhaltens.

So passen Sie das Anzeigenverhalten an:

1. Implementieren des `AdPolicySelector` -Schnittstelle und all ihrer Methoden.
1. Weisen Sie die Richtlinieninstanz zu, die von TVSDK über die Werbefactory verwendet werden soll.

   >[!NOTE]
   >
   >Klasse CustomContentFactory erweitert ContentFactory &amp;lbrace;
   >...
   >@override
   >public AdPolicySelector retrieveAdPolicySelector>>(MediaPlayerItem mediaPlayerItem) &amp;lbrace;
   >gibt neues CustomAdPolicySelector(mediaPlayerItem) zurück;
   >&amp;rbrace;
   >...
   >&amp;rbrace;
   >// Registrieren Sie die benutzerdefinierte Inhaltsfactory mit dem Medienplayer.
   >MediaPlayerItemConfig config = new MediaPlayerItemConfig();
   >config.setAdvertisingFactory(new CustomContentFactory());
   >// Diese Konfiguration sollte später beim Laden der Ressource übergeben werden
   >mediaPlayer.replaceCurrentResource(resource, config);

1. Implementieren Sie Ihre Anpassungen.
