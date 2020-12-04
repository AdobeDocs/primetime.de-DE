---
seo-title: Beispiel-Clientanforderungen
title: Beispiel-Clientanforderungen
uuid: 330d5e3c-1711-4375-bd11-e7702f0cde31
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
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
