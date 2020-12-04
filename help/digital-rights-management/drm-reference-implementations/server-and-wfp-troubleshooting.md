---
description: 'null'
seo-description: 'null'
seo-title: Fehlerbehebung
title: Fehlerbehebung
uuid: 06b86067-1ff6-4b4e-922f-7f968260ba19
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '98'
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

