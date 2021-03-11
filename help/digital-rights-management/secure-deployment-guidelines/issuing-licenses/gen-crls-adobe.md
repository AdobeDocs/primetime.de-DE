---
description: Sie können Adobe Primetime DRM verwenden, um Zertifikatsperrlisten zu erstellen, die die von der Adobe veröffentlichte Zertifikatsperrliste ergänzen.
title: Generieren von Zertifikatsperrlisten zur Ergänzung der von der Adobe veröffentlichten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Generieren von Zertifikatsperrlisten zur Ergänzung der von der Adobe veröffentlichten{#generating-crls-to-supplement-those-published-by-adobe}

Sie können Adobe Primetime DRM verwenden, um Zertifikatsperrlisten zu erstellen, die die von der Adobe veröffentlichte Zertifikatsperrliste ergänzen.

Das Primetime-DRM-SDK prüft und erzwingt die Zertifikatsperrlisten der Adobe. Sie können jedoch zusätzliche Clientcomputer deaktivieren, indem Sie eine Zertifikatsperrliste erstellen, die zusätzliche Computeranmeldeinformationen widerruft, indem Sie die Zertifikatsperrliste an das Primetime-DRM-SDK übergeben. Wenn Sie eine Lizenz ausstellen, prüft das SDK die Zertifikatsperrliste und die Zertifikatsperrliste der Adobe.

Informationen zum Generieren von Zertifikatsperrlisten finden Sie unter [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).
