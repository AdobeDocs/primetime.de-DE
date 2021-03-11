---
title: Passwörter mithilfe von Ant vorbereiten
description: Passwörter mithilfe von Ant vorbereiten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 0%

---


# Vorbereiten von Kennwörtern mit Ant{#prepare-passwords-using-ant}

Verwenden Sie Ant, um Ihr Kennwort zu verschlüsseln:

1. Navigieren Sie zu `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/`
1. Legen Sie die Eigenschaft `sdkdir` in [!DNL build-refimpl.xml] so fest, dass sie auf den Ordner verweist, der das Primetime DRM Java SDK enthält.
1. Führen Sie den folgenden Befehl aus:

   ```
   ant -f build-refimpl.xml
   ```

