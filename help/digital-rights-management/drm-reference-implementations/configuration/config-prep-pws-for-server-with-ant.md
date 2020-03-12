---
description: 'null'
seo-description: 'null'
seo-title: Passwörter mithilfe von Ant vorbereiten
title: Passwörter mithilfe von Ant vorbereiten
uuid: 9419ab0d-b448-4881-9d26-35c00f0b13bc
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Passwörter mithilfe von Ant vorbereiten{#prepare-passwords-using-ant}

Verwenden Sie Ant, um Ihr Kennwort zu verschlüsseln:

1. Navigieren zu `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/`
1. Legen Sie die `sdkdir` Eigenschaft in fest, [!DNL build-refimpl.xml] um auf den Ordner zu verweisen, der das Primetime DRM Java SDK enthält.
1. Führen Sie den folgenden Befehl aus:

   ```
   ant -f build-refimpl.xml
   ```

