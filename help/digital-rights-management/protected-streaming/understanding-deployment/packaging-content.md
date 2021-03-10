---
description: Wenn Sie Inhalte verpacken, müssen Sie die URL des Lizenzservers angeben.
title: Verpacken von Inhalten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# Verpacken von Inhalt{#packaging-content}

Wenn Sie Inhalte verpacken, müssen Sie die URL des Lizenzservers angeben.

Die Adobe Primetime DRM Server-URL verwendet das folgende Format:

```
http(s)://<license-server-host:port>/flashaccessserver/<tenant-name>
```

Beispiel: Für den Lizenzserver-Hostnamen `mylicenseserver.com`, der den Anschluss 8080 überwacht, und den Mieter *`tenant1`* verwenden Sie die folgende Syntax für die Lizenzserver-URL, die Sie zum Zeitpunkt des Pakets von Inhalten angegeben haben:

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Wenn jeder Mieter einen anderen Lizenzserver und eine andere Transportberechtigung verwendet, stellen Sie sicher, dass Sie im Packager das richtige Zertifikat des Mandanten angeben.

Wenn Sie sicherstellen möchten, dass der Server Lizenzen nur für Inhalte bekannter Packager ausstellt, müssen Sie das Paketzertifikat in die Packager-Zulassungsliste der Mietkonfigurationsdatei aufnehmen.
