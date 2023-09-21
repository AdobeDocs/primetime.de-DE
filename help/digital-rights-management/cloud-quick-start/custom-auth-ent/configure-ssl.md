---
title: SSL auf Ihrem BEES-Server konfigurieren
description: SSL auf Ihrem BEES-Server konfigurieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# SSL auf Ihrem BEES-Server konfigurieren {#configure-ssl-on-your-bees-server}

1. Stellen Sie Ihr Server-SSL-Zertifikat Ihrem Adobe-Ansprechpartner zur Verfügung, der diese Software bereitgestellt hat.

   Das Zertifikat wird dem Primetime Cloud DRM Trust Store als vertrauenswürdiges Zertifikat hinzugefügt.
1. Aktivieren der Client-Authentifizierung für die SSL-Verbindung (in dieser Version deaktiviert):
   1. Fügen Sie die `[!DNL clouddrm-transport.cer]` und `[!DNL AdobeFlashAccessIntermediateCA.cer]` Zertifikate zum Trust Store, der für die Client-Authentifizierung verwendet wird.
   1. Aktivieren Sie die Client-Authentifizierung in Ihrer SSL-Konfiguration.
