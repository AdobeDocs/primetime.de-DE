---
seo-title: Verpacken von Inhalten
title: Verpacken von Inhalten
uuid: 5d1d4b9d-f241-4291-9577-e9de5a8b92be
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Verpacken von Inhalten{#packaging-content}

Beim Verpacken von Inhalten muss die URL des Lizenzservers angegeben werden. Die Adobe Access Server-URL hat das folgende Format:

```
http(s):// license-server-host:port/flashaccessserver/tenant-name
```

Beispiel: Für den Hostnamen des Lizenzservers &quot;mylicenseserver.com&quot;, der auf Port 8080 und einem Mandanten mit dem Namen &quot;tenant1&quot;überwacht wird, lautet die URL des Lizenzservers, die zum Zeitpunkt der Verpackung angegeben wird:

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Wenn jeder Mieter einen anderen Lizenzserver und eine andere Transportberechtigung verwendet, stellen Sie sicher, dass Sie im Packager das richtige Zertifikat des Mandanten angeben.

Um sicherzustellen, dass der Server Lizenzen nur für Inhalte ausgibt, die von bekannten Packagern verpackt wurden, fügen Sie das Paket-Zertifikat in die zulassungsliste-Datei &quot;packager&quot;der Mietkonfigurationsdatei ein.
