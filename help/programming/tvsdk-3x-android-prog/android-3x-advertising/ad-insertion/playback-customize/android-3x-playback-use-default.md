---
description: Sie können das standardmäßige Anzeigenverhalten verwenden.
seo-description: Sie können das standardmäßige Anzeigenverhalten verwenden.
seo-title: Verwenden des standardmäßigen Wiedergabeverhaltens
title: Verwenden des standardmäßigen Wiedergabeverhaltens
uuid: 36f76c42-4c6c-4620-9b47-ec97519a642a
translation-type: tm+mt
source-git-commit: 6da7d597503d98875735c54e9a794f8171ad408b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---


# Verwenden Sie das standardmäßige Wiedergabeverhalten {#use-the-default-playback-behavior}

Sie können das standardmäßige Anzeigenverhalten verwenden.

1. Führen Sie eine der folgenden Aufgaben aus, um Standardverhalten zu verwenden:

   * Wenn Sie Ihre eigene `AdvertisingFactory`-Klasse implementieren, geben Sie null für `createAdPolicySelector` zurück.

   * Wenn Sie keine benutzerdefinierte Implementierung für die `AdvertisingFactory`-Klasse haben, verwendet TVSDK einen standardmäßigen Anzeigenrichtlinien-Selektor.

## Einrichten der benutzerdefinierten Wiedergabe {#set-up-customized-playback}

Sie können Anzeigenverhalten anpassen oder außer Kraft setzen.

Bevor Sie Anzeigenrichtlinien anpassen oder außer Kraft setzen können, registrieren Sie die Anzeigenrichtlinieninstanz mit .
Führen Sie zum Anpassen des Anzeigenverhaltens einen der folgenden Schritte aus:

* Implementieren Sie die `AdPolicySelector`-Schnittstelle und alle zugehörigen Methoden.

   Diese Option wird empfohlen, wenn Sie **alle**-Standardanzeigeverhalten außer Kraft setzen müssen.

* Erweitern Sie die `DefaultAdPolicySelector`-Klasse und stellen Sie Implementierungen nur für die Verhaltensweisen bereit, die angepasst werden müssen.

   Diese Option wird empfohlen, wenn Sie nur **einige** der Standardverhaltensregeln außer Kraft setzen müssen.

So passen Sie Anzeigenverhalten an:

1. Implementieren Sie die `AdPolicySelector`-Schnittstelle und alle zugehörigen Methoden.
1. Weisen Sie die Richtlinieninstanz zu, die von TVSDK über die Werbefabrik verwendet werden soll.

   >[!NOTE]
   >
   >Klasse CustomContentFactory erweitert ContentFactory&amp;lbrace;
   >...
   >@override
   >public AdPolicySelector retrieveAdPolicySelector>>(MediaPlayerItem mediaPlayerItem) &amp;lbrace;
   >return new CustomAdPolicySelector(mediaPlayerItem);
   >&amp;rbrace;
   >...
   >&amp;rbrace;
   >// Registrieren der benutzerdefinierten Inhaltsfactory mit dem Medienplayer
   >MediaPlayerItemConfig config = new MediaPlayerItemConfig();
   >config.setAdvertisingFactory(new CustomContentFactory());
   >// diese Konfiguration sollte später weitergegeben werden, während Sie >die Ressource
   >mediaPlayer.replaceCurrentResource(resource, config);

1. Implementieren Sie Ihre Anpassungen.
