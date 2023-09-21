---
title: Beispiel-Client-Anforderungen
description: Beispiel-Client-Anforderungen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Beispiel-Client-Anforderungen{#sample-client-requests}

Sie können eine Bibliothek mit Beispiel-Client-Anforderungen mit Tools wie Charles Proxy oder Wireshark erfassen. Sie sollten Clientanforderungen erfassen, nachdem der Individualisierungsserver eingerichtet wurde. Verwenden Sie dazu die Berechtigung Individualization Transport . Diese Clientanfragen können dann gesendet werden (über *curl* oder ein anderes Tool) zum Endpunkt des Individualisierungsservers hinzu, um zu überprüfen, ob der Server ordnungsgemäß ausgeführt wird. Beispiel:

```
curl https://<<yourindivserver:port>>/flashaccess/i15n/v5 -­data-binary  
@sample_client_request.bin > sample_client_response.ber
```

Sie können diese Anfragen auch nach jeder Änderung der Serverkonfiguration oder ECI-/CRL-Aktualisierungen erneut senden.

Außerdem sollten Sie die Seite Individualisierungsstatistiken entsprechend mit erfolgreichen Individualisierungstransaktionen aktualisieren.
