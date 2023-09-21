---
title: Fehlerbehebung
description: Fehlerbehebung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# Fehlerbehebung {#troubleshooting}

Im Folgenden finden Sie allgemeine Probleme und Lösungen für die Implementierung:

* Wenn der folgende Fehler angezeigt wird:

  ```
      "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
      javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
  ```

  Stellen Sie sicher, dass das Kennwort mit dem bereitgestellten `ScrambleUtil` -Klasse.

* Wenn der folgende Fehler angezeigt wird:

  ```
      "Unable to load credential from file.pfx -- possibly wrong password."
  ```

  Stellen Sie sicher, dass Sie das richtige verschlüsselte Kennwort für die PFX-Datei angegeben haben.

* Wenn der folgende Fehler angezeigt wird:

  ```
      "javax.crypto.BadPaddingException: Given final block not properly padded"
  ```

  Vergewissern Sie sich, dass Sie die mit der Referenzimplementierung bereitgestellte Passwort-Schuster-Klasse verwendet haben (dieses Schuster-Dienstprogramm unterscheidet sich von dem mit dem Adobe® Access™-Server für geschütztes Streaming bereitgestellten Dienstprogramm).
