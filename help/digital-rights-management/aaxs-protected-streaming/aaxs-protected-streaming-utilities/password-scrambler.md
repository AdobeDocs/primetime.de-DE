---
title: Password Scrambler
description: Password Scrambler
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 0%

---

# Password Scrambler {#password-scrambler}

Das Dienstprogramm Password Scrambler verschlüsselt ein Kennwort, damit es in der Adobe Access Server für geschützte Streaming-Konfigurationsdateien verwendet werden kann. Führen Sie den Befehl aus, um den Schuster auszuführen:

```
Scrambler.bat password 
```

oder den Befehl:

```
java -jar libs/flashaccess-scrambler.jar password  
```

Das Dienstprogramm gibt die folgende Meldung aus:

```
Encrypted password: scrambled-password 
```

Alle in &quot;flashaccess-global.xml&quot;und &quot;flashaccess-tenant.xml&quot;angegebenen Kennwörter müssen verschlüsselt sein.

>[!NOTE]
>
>Das Dienstprogramm Password Scrambler in der Adobe Access Server für geschütztes Streaming ist nicht mit dem mit dem Referenz-Implementierungs-Lizenzserver bereitgestellten Dispatcher austauschbar.
