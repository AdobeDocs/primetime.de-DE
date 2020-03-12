---
description: Wenn Sie Inhalte verpacken, müssen Sie die URL des Lizenzservers angeben.
seo-description: Wenn Sie Inhalte verpacken, müssen Sie die URL des Lizenzservers angeben.
seo-title: Verpacken von Inhalten
title: Verpacken von Inhalten
uuid: 2e47a9a2-bbc6-4995-8ce5-6ca6b116349b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verpacken von Inhalten{#packaging-content}

Wenn Sie Inhalte verpacken, müssen Sie die URL des Lizenzservers angeben.

Die Adobe Primetime DRM Server-URL verwendet das folgende Format:

```
http(s)://<license-server-host:port>/flashaccessserver/<tenant-name>
```

Beispiel: Für den Hostnamen des Lizenzservers, `mylicenseserver.com` der den Anschluss 8080 überwacht, und einen Mandanten namens *`tenant1`*, verwenden Sie die folgende Syntax für die URL des Lizenzservers, die Sie zum Zeitpunkt des Pakets von Inhalten angeben:

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

Wenn jeder Mieter einen anderen Lizenzserver und eine andere Transportberechtigung verwendet, stellen Sie sicher, dass Sie im Packager das richtige Zertifikat des Mandanten angeben.

Wenn Sie sicherstellen möchten, dass der Server Lizenzen nur für Inhalte bekannter Packager ausstellt, müssen Sie das Zertifikat des Packagers in die Whitelist des Pachtagers der Konfigurationsdatei aufnehmen.
