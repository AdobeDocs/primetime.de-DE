---
description: Wenn Sie Inhalte verpacken, müssen Sie die URL des Lizenzservers angeben.
seo-description: Wenn Sie Inhalte verpacken, müssen Sie die URL des Lizenzservers angeben.
seo-title: Verpacken von Inhalten
title: Verpacken von Inhalten
uuid: 2e47a9a2-bbc6-4995-8ce5-6ca6b116349b
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '141'
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
