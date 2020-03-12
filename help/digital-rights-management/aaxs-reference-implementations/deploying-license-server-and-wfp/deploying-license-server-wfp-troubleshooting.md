---
seo-title: Fehlerbehebung
title: Fehlerbehebung
uuid: db76d6a4-c285-4d86-95a1-4f1a85ed3743
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Fehlerbehebung {#troubleshooting}

Nachstehend sind allgemeine Probleme und Lösungen für die Bereitstellung aufgeführt:

* Wenn der folgende Fehler angezeigt wird:

   ```
       "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
       javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
   ```

   Vergewissern Sie sich, dass das Kennwort mit der bereitgestellten `ScrambleUtil` Klasse verschlüsselt ist.

* Wenn der folgende Fehler angezeigt wird:

   ```
       "Unable to load credential from file.pfx -- possibly wrong password."
   ```

   Stellen Sie sicher, dass Sie das richtige verschlüsselte Kennwort für die PFX-Datei angegeben haben.

* Wenn der folgende Fehler angezeigt wird:

   ```
       "javax.crypto.BadPaddingException: Given final block not properly padded"
   ```

   Vergewissern Sie sich, dass Sie die mit der Referenz-Implementierung bereitgestellte Kennwort-Verschachtelungsklasse verwendet haben (dieses Programm unterscheidet sich von dem mit Adobe® Access™ Server für geschütztes Streaming bereitgestellten Dienstprogramm).

