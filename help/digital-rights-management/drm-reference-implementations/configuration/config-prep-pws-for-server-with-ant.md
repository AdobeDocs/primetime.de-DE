---
title: Vorbereiten von Kennwörtern mit Ant
description: Vorbereiten von Kennwörtern mit Ant
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 0%

---

# Vorbereiten von Kennwörtern mit Ant{#prepare-passwords-using-ant}

Verwenden Sie Ant zum Verschlüsseln Ihres Kennworts:

1. Navigieren Sie zu `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/`
1. Legen Sie die `sdkdir` -Eigenschaft in [!DNL build-refimpl.xml] , um auf das Verzeichnis zu verweisen, das das Primetime DRM Java SDK enthält.
1. Führen Sie den folgenden Befehl aus:

   ```
   ant -f build-refimpl.xml
   ```
