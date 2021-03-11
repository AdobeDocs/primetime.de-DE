---
title: Verpacken von Inhalten
description: Verpacken von Inhalten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Verpacken von Inhalt{#packaging-content}

Verwenden Sie beim Verpacken von Inhalten für Remote-Key-Versand eine Richtlinie, die angibt, dass Remote-Key-Versand erforderlich sind. Die Key Server-URL muss für den HLS-Inhalt in die M3U8 (Manifestdatei) eingeschlossen werden. Die Primetime-URL des DRM-Schlüsselservers hat das folgende Format:

```
https://key-server-host:port/faxsks/tenant-name/key
```

Beispiel: Für den Hostnamen des Schlüsselservers [!DNL mykeyserver.com], der auf Port 443 und einem Pächter mit dem Namen `tenant1` überwacht wird, lautet die URL des Schlüsselservers, die in M3U8 angegeben werden soll:

```
https://mykeyserver.com:443/faxsks/tenant1/key
```

Für iOS- und Xbox 360-Clients kann dieselbe URL verwendet werden. Wenn der Server für jeden Clienttyp mit separaten Mietern konfiguriert ist, können auch andere URLs verwendet werden.

Derselbe Inhalt kann auf Clients ohne Schlüsselserver wiedergegeben werden, solange die URL des Lizenzservers auf einen ordnungsgemäß konfigurierten, ausgeführten Lizenzserver verweist.
