---
title: Adobe Primetime-Authentifizierung (optional)
description: Adobe Primetime-Authentifizierung (optional)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Adobe Primetime-Authentifizierung (optional) {#adobe-primetime-authentication-optional}

Wenn es sich bei der DRM-Richtlinie, die zum Verpacken des Inhalts verwendet wird, um eine anonyme Richtlinie handelt, wird eine Lizenz für alle Lizenzanfragen erteilt. Optional unterstützt Primetime Cloud DRM auch die Authentifizierung über die Adobe Primetime-Authentifizierung. Wenn diese Funktion aktiviert ist, wird eine Lizenz nur dann erteilt, wenn das Client-Gerät zunächst ein Primetime-Authentifizierungstoken erworben und über die entsprechende Client-API lokal festgelegt hat ( `setAuthenticationToken`) zum Festlegen von benutzerdefinierten Authentifizierungstoken. Weitere Informationen zur Integration der Primetime-Authentifizierung in Ihren Authentifizierungs-Workflow finden Sie unter: [Adobe Primetime-Authentifizierung.](https://tve.helpdocsonline.com/home)

Wenn während der Lizenzakquise die DRM-Richtlinie festlegt, dass eine Pri-metime-Authentifizierung erforderlich ist, analysiert und validiert der Lizenzserver das Primetime-Authentifizierungs-Short-Media-Token. Wenn die DRM-Richtlinie eine `ResourceID` oder `RequestorID`, validiert der Lizenzserver das Token auch anhand dieser Eigenschaften. Wenn sie nicht festgelegt sind, gibt der Lizenzserver die Eigenschaften während der Token-Validierung als &quot;null&quot;an. Nur wenn die Token-Validierung erfolgreich ist, wird eine Lizenz erteilt. Andernfalls wird vom Client ein 3328 DRMErrorEvent mit einem 305-Unterfehlercode (Benutzer nicht autorisiert) gesendet.

Die Parameter für die Primetime-Authentifizierung müssen in der Richtlinie angegeben werden, die zum Verpacken des Inhalts verwendet wird, der für die Primetime-Authentifizierung vorgesehen ist.

Die relevanten Eigenschaften sind:

```
#policy.customProp.1=adobePass.required=<TRUE or FALSE> 
#policy.customProp.1=adobePass.requestorID=<Requestor ID String> 
#policy.customProp.1=adobePass.resourceID=<Resource ID String>
```

>[!NOTE]
>
>Beachten Sie bei der Verwendung der Primetime-Authentifizierung in Verbindung mit der Funktion zum Rotieren von (DRM)-Lizenzen, dass das Primetime-Authentifizierungs-Short-Media-Token (SMT) ein kurzes Gültigkeitsdatum hat. Wenn Ihre Anwendung die Lizenzrotation (z. B. zur Unterstützung der *Blackouts* -Anwendungsfall), muss die Anwendung dies beachten und ihr Primetime-Authentifizierungs-Short-Media-Token aktualisieren, bevor sie ihre Lizenz rotiert.
