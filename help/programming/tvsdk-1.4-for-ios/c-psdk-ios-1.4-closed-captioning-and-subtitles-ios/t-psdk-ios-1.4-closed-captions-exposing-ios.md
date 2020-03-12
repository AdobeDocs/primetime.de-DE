---
description: Um Untertitel für Ihren Client-Player verfügbar zu machen, müssen Sie diese aktivieren. Der Benutzer kann Untertitel aktivieren oder deaktivieren und die Formatierung auswählen.
seo-description: Um Untertitel für Ihren Client-Player verfügbar zu machen, müssen Sie diese aktivieren. Der Benutzer kann Untertitel aktivieren oder deaktivieren und die Formatierung auswählen.
seo-title: Untertitel verfügbar machen
title: Untertitel verfügbar machen
uuid: 209b34ca-f14e-499e-af5f-2d8c7b359ef8
translation-type: tm+mt
source-git-commit: 25a0dfef12ecf10ba939500c4ba539468c41ee1b

---


# Untertitel verfügbar machen {#expose-closed-captions}

Um Untertitel für Ihren Client-Player verfügbar zu machen, müssen Sie diese aktivieren. Der Benutzer kann Untertitel aktivieren oder deaktivieren und die Formatierung auswählen.

So stellen Sie Bildunterschriften bereit:

1. Legen Sie im `PTMediaPlayer` Objekt die `closedCaptionDisplayEnabled` Eigenschaft fest.

   Wenn der Benutzer Untertitel aktiviert hat, wird in diesem Schritt der Text angezeigt.

   >[!NOTE]
   >
   >Der Clientbenutzer aktiviert bzw. deaktiviert Untertitel mithilfe der iOS-Barrierefreiheitseinstellungen. Diese Einstellungen bieten auch Formatierungsoptionen.

   >[!NOTE]
   >
   >`closedCaptionDisplayEnabled` -Eigenschaft nicht mehr unterstützt. Verwenden Sie `subtitlesOptions` die Eigenschaft von `PTMediaPlayerItem`. Siehe Untertitel [für](../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-closed-captioning-and-subtitles-ios/t-psdk-ios-1.4-subtitles-exposing-ios.md) die Verwendung von Untertiteln verfügbar machen.