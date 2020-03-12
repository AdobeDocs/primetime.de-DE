---
seo-title: Generieren von Zertifikatsperrlisten als Ergänzung zu den von Adobe veröffentlichten
title: Generieren von Zertifikatsperrlisten als Ergänzung zu den von Adobe veröffentlichten
uuid: 4e93f6d3-5a04-44e9-9e6b-e878798b68f5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Generieren von Zertifikatsperrlisten als Ergänzung zu den von Adobe veröffentlichten{#generate-crls-to-supplement-those-published-by-adobe}

Mit Adobe Access können Sie Zertifikatsperrlisten erstellen, um die von Adobe veröffentlichte Computer-Zertifikatsperrliste zu ergänzen. Adobe Access SDK überprüft und erzwingt die Adobe-Zertifikatsperrlisten. Sie können jedoch zusätzliche Clientcomputer deaktivieren, indem Sie eine Zertifikatsperrliste erstellen, die zusätzliche Computeranmeldeinformationen widerruft. Dazu müssen Sie die Zertifikatsperrliste an das Adobe Access-SDK übergeben und dann bei der Lizenzerteilung überprüft das SDK sowohl die Adobe-Zertifikatsperrliste als auch Ihre eigene Zertifikatsperrliste.

Weitere Informationen zum Generieren von Zertifikatsperrlisten finden Sie `RevocationListFactory` in der *Adobe Access-API-Referenz*.
