---
seo-title: Verpacken von Inhalten
title: Verpacken von Inhalten
uuid: 5d1d4b9d-f241-4291-9577-e9de5a8b92be
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
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
