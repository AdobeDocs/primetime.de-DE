---
title: Erstellen Sie Zertifikatsperrlisten, um die von der Adobe veröffentlichten zu ergänzen.
description: Erstellen Sie Zertifikatsperrlisten, um die von der Adobe veröffentlichten zu ergänzen.
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Erstellen Sie Zertifikatsperrlisten, um die von der Adobe veröffentlichten zu ergänzen.{#generate-crls-to-supplement-those-published-by-adobe}

Mit Adobe Access können Sie Zertifikatsperrlisten erstellen, um die von der Adobe veröffentlichte Zertifikatsperrliste zu ergänzen. Adobe Access SDK überprüft und erzwingt die Zertifikatsperrlisten der Adobe. Sie können jedoch zusätzliche Clientcomputer deaktivieren, indem Sie eine Zertifikatsperrliste erstellen, die zusätzliche Computeranmeldeinformationen widerruft. Dazu müssen Sie die Zertifikatsperrliste an das Adobe Access SDK übergeben. Bei der Lizenzerteilung überprüft das SDK dann sowohl die Zertifikatsperrliste der Adobe als auch Ihre eigene Zertifikatsperrliste.

Weitere Informationen zum Generieren von Zertifikatsperrlisten finden Sie unter `RevocationListFactory` in *Adobe Access API Reference*.
