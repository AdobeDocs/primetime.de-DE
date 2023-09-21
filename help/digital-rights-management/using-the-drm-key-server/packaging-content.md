---
title: Verpacken von Inhalten
description: Verpacken von Inhalten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Verpacken von Inhalten{#packaging-content}

Verwenden Sie beim Verpacken von Inhalten für die Remote-Schlüsselbereitstellung eine Richtlinie, die angibt, dass eine Remote-Schlüsselbereitstellung erforderlich ist. Die Key Server URL muss in der M3U8 (Manifestdatei) für den HLS-Inhalt enthalten sein. Die Primetime-URL des DRM-Schlüsselservers hat das Format:

```
https://key-server-host:port/faxsks/tenant-name/key
```

Beispiel: Hostname des Schlüsselservers [!DNL mykeyserver.com] Listening auf Port 443 und einem Mandanten namens `tenant1`lautet die wichtige Server-URL, die in M3U8 angegeben werden soll:

```
https://mykeyserver.com:443/faxsks/tenant1/key
```

Dieselbe URL kann für iOS- und Xbox 360-Clients verwendet werden. Oder wenn der Server für jeden Client-Typ mit separaten Mandanten konfiguriert ist, können unterschiedliche URLs verwendet werden.

Derselbe Inhalt kann auf Clients wiedergegeben werden, die keinen Schlüsselserver benötigen, sofern die URL des Lizenzservers auf einen ordnungsgemäß konfigurierten laufenden Lizenzserver verweist.
