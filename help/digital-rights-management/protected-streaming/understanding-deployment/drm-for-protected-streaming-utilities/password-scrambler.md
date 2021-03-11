---
description: Das Dienstprogramm Password Scrambler verschlüsselt ein Kennwort für den Adobe Primetime DRM-Server für Konfigurationsdateien für geschütztes Streaming.
title: Password crambler
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# Password crambler {#password-scrambler}

Das Dienstprogramm Password Scrambler verschlüsselt ein Kennwort für den Adobe Primetime DRM-Server für Konfigurationsdateien für geschütztes Streaming.

Geben Sie Folgendes ein, um den Scheuerschutz auszuführen:

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

Alle Kennwörter, die Sie in den Dateien [!DNL flashaccess-global.xml] und [!DNL flashaccess-tenant.xml] angegeben haben, müssen verschlüsselt sein.

>[!NOTE]
>
>Das Dienstprogramm Password Scrambler im Primetime DRM Server for Protected Streaming ist nicht mit dem Programm, das mit dem Referenz-Implementierungslizenzserver bereitgestellt wird, austauschbar.