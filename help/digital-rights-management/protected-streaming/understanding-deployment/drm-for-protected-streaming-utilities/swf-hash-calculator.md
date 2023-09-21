---
description: Das SWF Hash Calculator-Dienstprogramm berechnet den Digest einer SWF-Anwendung, die sich in einer Datei befindet.
title: SWF Hash Rechner
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# SWF Hash Rechner{#swf-hash-calculator}

Das SWF Hash Calculator-Dienstprogramm berechnet den Digest einer SWF-Anwendung, die sich in einer Datei befindet.

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

Mit diesem Wert können Sie den SWF-Digest in [!DNL flashaccess-tenant.xml].
