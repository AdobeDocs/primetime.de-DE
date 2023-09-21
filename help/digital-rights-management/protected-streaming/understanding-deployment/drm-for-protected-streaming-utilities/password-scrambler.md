---
description: Das Dienstprogramm Password Scrambler verschlüsselt ein Kennwort für den Adobe Primetime DRM-Server für geschützte Streaming-Konfigurationsdateien.
title: Passwort-Absender
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# Passwort-Absender {#password-scrambler}

Das Dienstprogramm Password Scrambler verschlüsselt ein Kennwort für den Adobe Primetime DRM-Server für geschützte Streaming-Konfigurationsdateien.

Geben Sie Folgendes ein, um den Schuster auszuführen:

```
Scrambler.bat  
<i class="+ topic ph hi-d="" i "="">
  password 
</i class="+ topic>
```

oder

```
java -jar libs/flashaccess-scrambler.jar  
<i class="+ topic ph hi-d="" i "="">
  password  
</i class="+ topic>
```

Das Dienstprogramm zeigt die folgende Meldung an:

```
Encrypted password:  
<i class="+ topic ph hi-d="" i "="">
  scrambled-password 
</i class="+ topic>
```

Alle Kennwörter, die Sie in der [!DNL flashaccess-global.xml] und [!DNL flashaccess-tenant.xml] -Dateien müssen verschlüsselt sein.

>[!NOTE]
>
>Das Dienstprogramm Password Scrambler im Primetime DRM Server für geschütztes Streaming ist nicht mit dem Schuster austauschbar, der mit dem Referenz-Implementierungs-Lizenzserver bereitgestellt wird.
