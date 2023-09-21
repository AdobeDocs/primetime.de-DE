---
title: Verpacken von Inhalten
description: Verpacken von Inhalten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Verpacken von Inhalten{#packaging-content}

Beim Verpacken von Inhalten muss die URL des Lizenzservers angegeben werden. Die Adobe Access Server-URL hat das Format:

```
http(s):// license-server-host:port/flashaccessserver/tenant-name
```

Beispiel: Für den Lizenzserver-Hostnamen &quot;mylicenseserver.com&quot;, der auf Port 8080 lauscht, und einen Mandanten mit dem Namen &quot;tenant1&quot;, lautet die URL des Lizenzservers, die zum Zeitpunkt der Verpackung angegeben wird:

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Wenn jeder Mandant einen anderen Lizenzserver und eine andere Transportberechtigung verwendet, geben Sie im Packager das Zertifikat des richtigen Mandanten an.

Um sicherzustellen, dass die Serverausgabe nur Lizenzen für Inhalte ausgibt, die von bekannten Packagern verpackt wurden, fügen Sie das Zertifikat des Packager in die Paketkonfigurationsdatei der Mandantenkonfigurationsdatei ein.
