---
description: Um Ihrem Client-Player Untertitel zur Verfügung zu stellen, müssen Sie diese aktivieren. Der Benutzer kann Untertitel ein- oder ausschalten und die Formatierung auswählen.
title: Untertitel anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# Untertitel anzeigen {#expose-closed-captions}

Um Ihrem Client-Player Untertitel zur Verfügung zu stellen, müssen Sie diese aktivieren. Der Benutzer kann Untertitel ein- oder ausschalten und die Formatierung auswählen.

So zeigen Sie geschlossene Untertitel an:

1. In `PTMediaPlayer` -Objekt, legen Sie die `closedCaptionDisplayEnabled` -Eigenschaft.

   Wenn der Benutzer Untertitel aktiviert hat, wird in diesem Schritt der Text angezeigt.

   >[!NOTE]
   >
   >Der Client-Benutzer aktiviert bzw. deaktiviert die Untertitelung mithilfe der Einstellungen für die Barrierefreiheit von iOS. Diese Einstellungen bieten auch Formatierungsoptionen.

   >[!NOTE]
   >
   >`closedCaptionDisplayEnabled` -Eigenschaft wird nicht mehr unterstützt. Verwendung `subtitlesOptions` Eigenschaft von `PTMediaPlayerItem`. Siehe [Untertitel verfügbar machen](../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-closed-captioning-and-subtitles-ios/t-psdk-ios-1.4-subtitles-exposing-ios.md) zum Verwenden von Untertiteln.
