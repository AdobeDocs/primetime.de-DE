---
title: SWF Hash Calculator
description: SWF Hash Calculator
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# SWF Hash Calculator{#swf-hash-calculator}

Das Dienstprogramm SWF Hash Calculator berechnete den Digest einer SWF-Anwendung in einer Datei. Führen Sie den Befehl aus, um den Hasher auszuführen:

```
Hasher.bat filename.swf
```

oder Befehl:

```
java -jar libs/flashaccess-hasher.jar filename.swf
```

Das Dienstprogramm gibt folgende Meldung aus:

```
SWF Hash: hash-of-swf
```

Dieser Wert kann verwendet werden, um den SWF-Digest in [!DNL flashaccess-tenant.xml] anzugeben.
