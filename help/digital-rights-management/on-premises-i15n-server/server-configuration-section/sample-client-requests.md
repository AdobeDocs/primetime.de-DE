---
title: Beispiel-Clientanforderungen
description: Beispiel-Clientanforderungen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 1%

---


# Beispiel-Clientanforderungen{#sample-client-requests}

Sie können eine Bibliothek mit Beispiel-Clientanforderungen mit Werkzeugen wie Charles Proxy oder Wireshark erfassen. Sie sollten Clientanforderungen nach Einrichtung des Individualisierungsservers mit der Berechtigung &quot;Individualisierungstransport&quot;erfassen. Anschließend können Sie diese Clientanforderungen (über *curl* oder ein anderes Tool) an den Endpunkt des Individualisierungsservers senden, um sicherzustellen, dass der Server ordnungsgemäß funktioniert. Beispiel:

```
curl https://<<yourindivserver:port>>/flashaccess/i15n/v5 -­data-binary  
@sample_client_request.bin > sample_client_response.ber
```

Sie können diese Anforderungen auch nach jeder Änderung der Serverkonfiguration oder nach ECI-/CRL-Aktualisierungen erneut senden.

Außerdem sollten Sie die Seite &quot;Personalisierungsstatistik&quot;mit erfolgreichen Individualisierungstransaktionen entsprechend aktualisieren.
