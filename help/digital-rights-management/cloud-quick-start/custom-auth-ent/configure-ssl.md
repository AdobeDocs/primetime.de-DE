---
seo-title: SSL auf dem BEES-Server konfigurieren
title: SSL auf dem BEES-Server konfigurieren
uuid: 041a106e-8b21-4018-815d-b7ea48c3de03
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
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
