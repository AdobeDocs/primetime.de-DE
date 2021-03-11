---
description: Um Untertitel für Ihren Client-Player verfügbar zu machen, müssen Sie diese aktivieren. Der Benutzer kann Untertitel aktivieren oder deaktivieren und die Formatierung auswählen.
title: Untertitel verfügbar machen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '114'
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