---
seo-title: Verpacken von Inhalten
title: Verpacken von Inhalten
uuid: 366c8470-b7ef-4a39-83c2-151ba9be9a32
translation-type: tm+mt
source-git-commit: 1547eb3dd220fafc08df923f40504736c16a866c

---


# Verpacken von Inhalten{#packaging-content}

Verwenden Sie beim Verpacken von Inhalten für Remote-Key-Versand eine Richtlinie, die angibt, dass Remote-Key-Versand erforderlich sind. Die Key Server-URL muss für den HLS-Inhalt in die M3U8 (Manifestdatei) eingeschlossen werden. Die Primetime-URL des DRM-Schlüsselservers hat das folgende Format:

```
https://key-server-host:port/faxsks/tenant-name/key
```

Beispiel: Für den Hostnamen des Schlüsselservers, der auf Port 443 [!DNL mykeyserver.com] überwacht wird, und einen Mandanten mit dem Namen `tenant1`, lautet die in M3U8 anzugebende wichtige Server-URL:

```
https://mykeyserver.com:443/faxsks/tenant1/key
```

Für iOS- und Xbox 360-Clients kann dieselbe URL verwendet werden. Wenn der Server für jeden Clienttyp mit separaten Mietern konfiguriert ist, können auch andere URLs verwendet werden.

Derselbe Inhalt kann auf Clients ohne Schlüsselserver wiedergegeben werden, solange die URL des Lizenzservers auf einen ordnungsgemäß konfigurierten, ausgeführten Lizenzserver verweist.
