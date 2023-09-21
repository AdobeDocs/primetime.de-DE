---
title: Fehlerbehebung
description: Fehlerbehebung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Fehlerbehebung{#troubleshooting}

Im Folgenden finden Sie einige Probleme und Lösungen, auf die Sie während der Bereitstellung stoßen können.

* Wenn die folgende Fehlermeldung angezeigt wird:

  ```
  "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
      javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
  ```

  Stellen Sie sicher, dass das Kennwort mit dem `ScrambleUtil` -Klasse.

* Wenn die folgende Fehlermeldung angezeigt wird:

  ```
  "Unable to load credential from file.pfx -- possibly wrong password."
  ```

  Vergewissern Sie sich, dass Sie in der PFX-Datei das richtige verschlüsselte Kennwort angegeben haben.

* Wenn die folgende Fehlermeldung angezeigt wird:

  ```
  "javax.crypto.BadPaddingException: Given final block not properly padded"
  ```

  Stellen Sie sicher, dass Sie die Kennwortbeschriftungsklasse verwenden *, das mit der Referenzimplementierung bereitgestellt wurde*. Dieses Programm unterscheidet sich von dem, das mit dem Adobe Primetime DRM Server für geschütztes Streaming bereitgestellt wurde.
