---
seo-title: SWF Hash Calculator
title: SWF Hash Calculator
uuid: c1823208-92d9-47c5-b550-f9cc370b543d
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9

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

Dieser Wert kann verwendet werden, um den SWF-Digest in anzugeben [!DNL flashaccess-tenant.xml].
