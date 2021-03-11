---
title: Fehlerbehebung
description: Fehlerbehebung
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# Fehlerbehebung {#troubleshooting}

Nachstehend sind allgemeine Probleme und Lösungen für die Bereitstellung aufgeführt:

* Wenn der folgende Fehler angezeigt wird:

   ```
       "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
       javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
   ```

   Vergewissern Sie sich, dass das Kennwort mit der bereitgestellten `ScrambleUtil`-Klasse verschlüsselt ist.

* Wenn der folgende Fehler angezeigt wird:

   ```
       "Unable to load credential from file.pfx -- possibly wrong password."
   ```

   Stellen Sie sicher, dass Sie das richtige verschlüsselte Kennwort für die PFX-Datei angegeben haben.

* Wenn der folgende Fehler angezeigt wird:

   ```
       "javax.crypto.BadPaddingException: Given final block not properly padded"
   ```

   Vergewissern Sie sich, dass Sie die mit der Referenz-Implementierung bereitgestellte Password crambler-Klasse verwendet haben (dieses Dienstprogramm unterscheidet sich von dem mit Adobe® Access™ Server für geschütztes Streaming bereitgestellten).

