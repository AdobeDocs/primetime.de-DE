---
title: SWF Hash Calculator
description: SWF Hash Calculator
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---

# SWF Hash Calculator{#swf-hash-calculator}

Das SWF Hash Calculator-Dienstprogramm berechnete den Digest einer SWF-Anwendung in einer Datei. Um den Hasher auszuführen, führen Sie den Befehl aus:

```
Hasher.bat filename.swf
```

oder den Befehl:

```
java -jar libs/flashaccess-hasher.jar filename.swf
```

Das Dienstprogramm gibt die folgende Meldung aus:

```
SWF Hash: hash-of-swf
```

Dieser Wert kann verwendet werden, um den SWF-Digest in [!DNL flashaccess-tenant.xml].
