---
description: Sie können das standardmäßige Anzeigenverhalten verwenden.
seo-description: Sie können das standardmäßige Anzeigenverhalten verwenden.
seo-title: Verwenden des standardmäßigen Wiedergabeverhaltens
title: Verwenden des standardmäßigen Wiedergabeverhaltens
uuid: 36f76c42-4c6c-4620-9b47-ec97519a642a
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Verwenden des standardmäßigen Wiedergabeverhaltens {#use-the-default-playback-behavior}

Sie können das standardmäßige Anzeigenverhalten verwenden.

1. Führen Sie eine der folgenden Aufgaben aus, um Standardverhalten zu verwenden:

   * Wenn Sie Ihre eigene `AdvertisingFactory` Klasse implementieren, geben Sie null für `createAdPolicySelector`zurück.

   * Wenn Sie keine benutzerdefinierte Implementierung für die `AdvertisingFactory` Klasse haben, verwendet TVSDK eine standardmäßige Anzeigenrichtlinien-Auswahl.

## Einrichten der benutzerdefinierten Wiedergabe {#set-up-customized-playback}

Sie können Anzeigenverhalten anpassen oder außer Kraft setzen.

Bevor Sie Anzeigenrichtlinien anpassen oder außer Kraft setzen können, registrieren Sie die Anzeigenrichtlinieninstanz mit .
Führen Sie zum Anpassen des Anzeigenverhaltens einen der folgenden Schritte aus:

* Implementieren Sie die `AdPolicySelector` Schnittstelle und alle zugehörigen Methoden.

   Diese Option wird empfohlen, wenn Sie **alle** standardmäßigen Werbeverhaltensweisen außer Kraft setzen müssen.

* Erweitern Sie die `DefaultAdPolicySelector` Klasse und stellen Sie Implementierungen nur für die Verhaltensweisen bereit, die angepasst werden müssen.

   Diese Option wird empfohlen, wenn Sie nur **einige** der Standardverhaltensweisen außer Kraft setzen müssen.

So passen Sie Anzeigenverhalten an:

1. Implementieren Sie die `AdPolicySelector` Schnittstelle und alle zugehörigen Methoden.
1. Weisen Sie die Richtlinieninstanz zu, die von TVSDK über die Werbefabrik verwendet werden soll.

>[!NOTE]
>class CustomContentFactory extended ContentFactory {
>...
>@override
>public AdPolicySelector retrieveAdPolicySelector>>(MediaPlayerItem mediaPlayerItem) {
>return new CustomAdPolicySelector(mediaPlayerItem);
>}
>...
>}
>// Registrieren der benutzerdefinierten Inhaltsfactory mit dem Medienplayer
>MediaPlayerItemConfig config = new MediaPlayerItemConfig();
>config.setAdvertisingFactory(new CustomContentFactory());
>// diese Konfiguration sollte später weitergegeben werden, während Sie >die Ressource laden
>mediaPlayer.replaceCurrentResource(resource, config);

1. Implementieren Sie Ihre Anpassungen.