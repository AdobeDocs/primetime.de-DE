---
title: Verpacken von Inhalten
description: Verpacken von Inhalten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# Verpacken von Inhalt{#packaging-content}

Beim Verpacken von Inhalten muss die URL des Lizenzservers angegeben werden. Die Adobe Access Server-URL hat das folgende Format:

```
http(s):// license-server-host:port/flashaccessserver/tenant-name
```

Beispiel: Für den Hostnamen des Lizenzservers &quot;mylicenseserver.com&quot;, der auf Port 8080 und einem Mandanten mit dem Namen &quot;tenant1&quot;überwacht wird, lautet die URL des Lizenzservers, die zum Zeitpunkt der Verpackung angegeben wird:

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Wenn jeder Mieter einen anderen Lizenzserver und eine andere Transportberechtigung verwendet, stellen Sie sicher, dass Sie im Packager das richtige Zertifikat des Mandanten angeben.

Um sicherzustellen, dass der Server Lizenzen nur für Inhalte ausgibt, die von bekannten Packagern verpackt wurden, schließen Sie das Paket-Zertifikat in die Packager-Zulassungsliste der Mietkonfigurationsdatei ein.
