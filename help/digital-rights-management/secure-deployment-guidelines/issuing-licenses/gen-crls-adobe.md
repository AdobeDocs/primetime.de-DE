---
description: Sie können Adobe Primetime DRM verwenden, um Zertifikatsperrlisten zu erstellen, die die von der Adobe veröffentlichte Zertifikatsperrliste ergänzen.
seo-description: Sie können Adobe Primetime DRM verwenden, um Zertifikatsperrlisten zu erstellen, die die von der Adobe veröffentlichte Zertifikatsperrliste ergänzen.
seo-title: Generieren von Zertifikatsperrlisten zur Ergänzung der von der Adobe veröffentlichten
title: Generieren von Zertifikatsperrlisten zur Ergänzung der von der Adobe veröffentlichten
uuid: 0cc4254d-20a0-4e05-9c5b-0b84a5c833cb
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 0%

---


# Generieren von Zertifikatsperrlisten zur Ergänzung der von der Adobe veröffentlichten{#generating-crls-to-supplement-those-published-by-adobe}

Sie können Adobe Primetime DRM verwenden, um Zertifikatsperrlisten zu erstellen, die die von der Adobe veröffentlichte Zertifikatsperrliste ergänzen.

Das Primetime-DRM-SDK prüft und erzwingt die Zertifikatsperrlisten der Adobe. Sie können jedoch zusätzliche Clientcomputer deaktivieren, indem Sie eine Zertifikatsperrliste erstellen, die zusätzliche Computeranmeldeinformationen widerruft, indem Sie die Zertifikatsperrliste an das Primetime-DRM-SDK übergeben. Wenn Sie eine Lizenz ausstellen, prüft das SDK die Zertifikatsperrliste und die Zertifikatsperrliste der Adobe.

Informationen zum Generieren von Zertifikatsperrlisten finden Sie unter [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).
