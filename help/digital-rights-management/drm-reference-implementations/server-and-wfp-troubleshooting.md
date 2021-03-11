---
title: Fehlerbehebung
description: Fehlerbehebung
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# Fehlerbehebung{#troubleshooting}

Im Folgenden finden Sie einige Probleme und Lösungen, auf die Sie möglicherweise während der Bereitstellung stoßen.

* Wenn die folgende Fehlermeldung angezeigt wird:

   ```
   "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
       javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
   ```

   Stellen Sie sicher, dass das Kennwort mit der `ScrambleUtil`-Klasse verschlüsselt wurde.

* Wenn die folgende Fehlermeldung angezeigt wird:

   ```
   "Unable to load credential from file.pfx -- possibly wrong password."
   ```

   Vergewissern Sie sich, dass Sie das richtige verschlüsselte Kennwort in der PFX-Datei angegeben haben.

* Wenn die folgende Fehlermeldung angezeigt wird:

   ```
   "javax.crypto.BadPaddingException: Given final block not properly padded"
   ```

   Vergewissern Sie sich, dass Sie die mit der Referenz-Implementierung *bereitgestellte Kennwort-Klasse* verwenden. Dieses Programm unterscheidet sich von dem, das mit dem Adobe Primetime DRM Server für geschütztes Streaming bereitgestellt wurde.

