---
description: Sie können Adobe Primetime DRM verwenden, um Zertifikatsperrlisten zu erstellen, die die von Adobe veröffentlichte Computer-Zertifikatsperrliste ergänzen.
seo-description: Sie können Adobe Primetime DRM verwenden, um Zertifikatsperrlisten zu erstellen, die die von Adobe veröffentlichte Computer-Zertifikatsperrliste ergänzen.
seo-title: Erstellen von Zertifikatsperrlisten als Ergänzung zu den von Adobe veröffentlichten
title: Erstellen von Zertifikatsperrlisten als Ergänzung zu den von Adobe veröffentlichten
uuid: 0cc4254d-20a0-4e05-9c5b-0b84a5c833cb
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Erstellen von Zertifikatsperrlisten als Ergänzung zu den von Adobe veröffentlichten{#generating-crls-to-supplement-those-published-by-adobe}

Sie können Adobe Primetime DRM verwenden, um Zertifikatsperrlisten zu erstellen, die die von Adobe veröffentlichte Computer-Zertifikatsperrliste ergänzen.

Das Primetime-DRM-SDK prüft und erzwingt die Adobe-Zertifikatsperrlisten. Sie können jedoch zusätzliche Clientcomputer deaktivieren, indem Sie eine Zertifikatsperrliste erstellen, die zusätzliche Computeranmeldeinformationen widerruft, indem Sie die Zertifikatsperrliste an das Primetime-DRM-SDK übergeben. Wenn Sie eine Lizenz ausstellen, überprüft das SDK die Adobe-Zertifikatsperrliste und Ihre Zertifikatsperrliste.

Informationen zum Generieren von Zertifikatsperrlisten finden Sie unter [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).
