---
description: Das Dienstprogramm SWF Hash Calculator berechnet den Digest einer SWF-Anwendung, die sich in einer Datei befindet.
title: SWF-Hash-Rechner
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---


# SWF-Hash-Rechner{#swf-hash-calculator}

Das Dienstprogramm SWF Hash Calculator berechnet den Digest einer SWF-Anwendung, die sich in einer Datei befindet.

Geben Sie Folgendes ein, um den Hasher auszuführen:

```
Hasher.bat 
<i class="+ topic ph hi-d="" i "="">
  filename.swf
</i class="+ topic>
```

oder

```
java -jar libs/flashaccess-hasher.jar 
<i class="+ topic ph hi-d="" i "="">
  filename.swf
</i class="+ topic>
```

Das Dienstprogramm zeigt die folgende Meldung an:

```
SWF Hash: 
<i class="+ topic ph hi-d="" i "="">
  hash-of-swf
</i class="+ topic>
```

Mit diesem Wert können Sie die SWF-Zusammenfassung in [!DNL flashaccess-tenant.xml] angeben.
