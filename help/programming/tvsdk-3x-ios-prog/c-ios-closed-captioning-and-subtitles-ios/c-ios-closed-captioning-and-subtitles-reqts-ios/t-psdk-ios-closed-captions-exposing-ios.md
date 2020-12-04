---
description: Um Untertitel für Ihren Client-Player verfügbar zu machen, müssen Sie diese aktivieren. Der Benutzer kann Untertitel aktivieren oder deaktivieren und die Formatierung auswählen.
seo-description: Um Untertitel für Ihren Client-Player verfügbar zu machen, müssen Sie diese aktivieren. Der Benutzer kann Untertitel aktivieren oder deaktivieren und die Formatierung auswählen.
seo-title: Untertitel verfügbar machen
title: Untertitel verfügbar machen
uuid: 7057014a-b14a-4790-8f7f-37d7a1fb8194
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Freigeben von Untertiteln {#expose-closed-captions}

Um Untertitel für Ihren Client-Player verfügbar zu machen, müssen Sie diese aktivieren. Der Benutzer kann Untertitel aktivieren oder deaktivieren und die Formatierung auswählen.

So stellen Sie Bildunterschriften bereit:

1. Legen Sie im `PTMediaPlayer`-Objekt die Eigenschaft `closedCaptionDisplayEnabled` fest.

   Wenn der Benutzer Untertitel aktiviert hat, wird in diesem Schritt der Text angezeigt.

   >[!NOTE]
   >
   >Der Clientbenutzer aktiviert bzw. deaktiviert Untertitel mithilfe der iOS-Barrierefreiheitseinstellungen. Diese Einstellungen bieten auch Formatierungsoptionen.

   >[!NOTE]
   >
   >`closedCaptionDisplayEnabled` -Eigenschaft nicht mehr unterstützt. Verwenden Sie die Eigenschaft `subtitlesOptions` von `PTMediaPlayerItem`. Siehe [Untertitel offen legen](../../../tvsdk-3x-ios-prog/c-ios-closed-captioning-and-subtitles-ios/c-ios-closed-captioning-and-subtitles-reqts-ios/t-ios-subtitles-exposing-ios.md), um Untertitel zu verwenden.