---
title: Generieren von Zertifikatsperrlisten zur Ergänzung der von Adobe veröffentlichten
description: Generieren von Zertifikatsperrlisten zur Ergänzung der von Adobe veröffentlichten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Generieren von Zertifikatsperrlisten zur Ergänzung der von Adobe veröffentlichten{#generate-crls-to-supplement-those-published-by-adobe}

Mit Adobe Access können Sie Zertifikatsperrlisten erstellen, um die von Adobe veröffentlichte Zertifikatsperrliste der Maschine zu ergänzen. Adobe Access SDK überprüft und erzwingt die Adobe-Zertifikatsperrlisten. Sie können jedoch zusätzliche Clientcomputer deaktivieren, indem Sie eine Zertifikatsperrliste erstellen, die zusätzliche Computeranmeldeinformationen widerruft. Dazu müssen Sie die Zertifikatsperrliste an das Adobe Access SDK übergeben und dann bei der Lizenzerteilung prüft das SDK sowohl die Adobe-Zertifikatsperrliste als auch Ihre eigene Zertifikatsperrliste.

Weitere Informationen zum Generieren von Zertifikatsperrlisten finden Sie unter `RevocationListFactory` in *Adobe Access API-Referenz*.
