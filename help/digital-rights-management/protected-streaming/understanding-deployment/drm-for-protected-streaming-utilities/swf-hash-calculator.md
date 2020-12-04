---
description: Das Dienstprogramm SWF Hash Calculator berechnet den Digest einer SWF-Anwendung, die sich in einer Datei befindet.
seo-description: Das Dienstprogramm SWF Hash Calculator berechnet den Digest einer SWF-Anwendung, die sich in einer Datei befindet.
seo-title: SWF-Hash-Rechner
title: SWF-Hash-Rechner
uuid: 0cf972c1-4717-4d78-a594-b27178ece512
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '86'
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
