---
seo-title: Einrichten eines Domänenservers
title: Einrichten eines Domänenservers
uuid: b262ea86-f465-4ed1-b278-122d4dafc881
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Einrichten eines Domänenservers {#set-up-a-domain-server}

So konfigurieren Sie den Domänenserver bei einer vorhandenen Lizenzserverinstallation:

1. Öffnen Sie die [!DNL flashaccess-refimpl.properties] Datei unter [!DNL tomcat/lib].

1. Geben Sie unter der `Domain CA certificate` Option die Details zum CA-Zertifikat der Domäne ein. Dieses Zertifikat wird für die Annahme der Domänentoken verwendet.
1. Geben Sie unter der `Domain CA credential` Option die `Domain CA credential certificate (PFX)` Details ein. Dieses Zertifikat wird zum Signieren von Domänenzertifikaten und -Token verwendet.

1. Geben Sie den Wert für `DomainServerlURL`. Wenn dieser Wert NULL ist, kann die Domänenauthentifizierung erfolgreich sein. Beim Betreten der Domäne wird jedoch ein Fehler wegen einer Verbindungsdomäne ausgegeben.

