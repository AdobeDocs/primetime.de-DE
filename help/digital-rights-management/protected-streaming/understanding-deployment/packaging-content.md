---
description: Wenn Sie Inhalte verpacken, müssen Sie die URL des Lizenzservers angeben.
title: Verpacken von Inhalten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Verpacken von Inhalten{#packaging-content}

Wenn Sie Inhalte verpacken, müssen Sie die URL des Lizenzservers angeben.

Die Adobe Primetime DRM Server-URL verwendet das folgende Format:

```
http(s)://<license-server-host:port>/flashaccessserver/<tenant-name>
```

Beispiel: für den Hostnamen des Lizenzservers `mylicenseserver.com` , der auf Port 8080 lauscht, und ein Mandant namens *`tenant1`* verwenden Sie die folgende Syntax für die Lizenzserver-URL, die Sie zum Zeitpunkt des Pakets von Inhalten angeben:

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Wenn jeder Mandant eine andere Lizenz für Server und Transport Credential verwendet, stellen Sie sicher, dass Sie im Packager das richtige Zertifikat des Mandanten angeben.

Wenn Sie sicherstellen möchten, dass der Server Lizenzen nur für Inhalte von bekannten Paketen ausgibt, müssen Sie das Zertifikat des Packagers in die Paketkonfigurationsdatei der Mandantenkonfigurationsdatei aufnehmen.
