---
title: SSL auf dem BEES-Server konfigurieren
description: SSL auf dem BEES-Server konfigurieren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---


# SSL auf dem BEES-Server {#configure-ssl-on-your-bees-server} konfigurieren

1. Geben Sie Ihr SSL-Serverzertifikat an den Ansprechpartner Ihrer Adobe weiter, der diese Software bereitgestellt hat.

   Das Zertifikat wird als vertrauenswürdiges Zertifikat zum Primetime Cloud DRM Trust Store hinzugefügt.
1. Aktivieren der Clientauthentifizierung für die SSL-Verbindung (in dieser Version deaktiviert):
   1. hinzufügen Sie die Zertifikate `[!DNL clouddrm-transport.cer]` und `[!DNL AdobeFlashAccessIntermediateCA.cer]` in den Trust Store, der für die Clientauthentifizierung verwendet wird.
   1. Aktivieren Sie die Clientauthentifizierung in Ihrer SSL-Konfiguration.
