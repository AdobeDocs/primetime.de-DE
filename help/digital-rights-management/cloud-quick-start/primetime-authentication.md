---
seo-title: Adobe Primetime-Authentifizierung (optional)
title: Adobe Primetime-Authentifizierung (optional)
uuid: fa6225d6-e0e5-4fcc-ac26-4ff54f9f334a
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Adobe Primetime-Authentifizierung (optional) {#adobe-primetime-authentication-optional}

Wenn die DRM-Richtlinie, die zum Verpacken des Inhalts verwendet wird, eine anonyme Richtlinie ist, wird eine Lizenz für alle Lizenzanforderungen erteilt. Optional unterstützt Primetime Cloud DRM auch die Authentifizierung über die Adobe Primetime-Authentifizierung. Wenn diese Funktion aktiviert ist, wird eine Lizenz nur dann erteilt, wenn das Client-Gerät zum ersten Mal ein Primetime-Authentifizierungstoken erworben und es lokal über die entsprechende Client-API ( `setAuthenticationToken`) zum Festlegen benutzerdefinierter Authentifizierungstoken festgelegt hat. Weitere Informationen zur Integration der Primetime-Authentifizierung in Ihren Authentifizierungsarbeitsablauf finden Sie unter: [Adobe Primetime-Authentifizierung.](https://tve.helpdocsonline.com/home)

Wenn die DRM-Richtlinie bei der Lizenzerfassung vorsieht, dass eine Pri-metime-Authentifizierung erforderlich ist, analysiert und validiert der Lizenzserver das Primetime-Authentifizierungstoken für Kurzmedien. Wenn die DRM-Richtlinie eine `ResourceID` oder `RequestorID`angibt, validiert der Lizenzserver auch das Token mit diesen Eigenschaften. Wenn sie nicht festgelegt sind, gibt der Lizenzserver die Eigenschaften während der Token-Überprüfung als &quot;null&quot;an. Nur wenn die Token-Validierung erfolgreich ist, wird eine Lizenz erteilt. Andernfalls wird ein 3328 DRMErrorEvent mit einem 305-Unterfehlercode (Benutzer nicht autorisiert) vom Client gesendet.

Die Parameter für die Primetime-Authentifizierung müssen in der Richtlinie angegeben werden, die zum Verpacken der Inhalte verwendet wird, für die eine Primetime-Authentifizierung erforderlich ist.

Die relevanten Eigenschaften sind:

```
#policy.customProp.1=adobePass.required=<TRUE or FALSE> 
#policy.customProp.1=adobePass.requestorID=<Requestor ID String> 
#policy.customProp.1=adobePass.resourceID=<Resource ID String>
```

>[!NOTE]
>
>Beachten Sie bei der Verwendung der Primetime-Authentifizierung in Verbindung mit der DRM-Funktion zur Lizenzdrehung, dass das Primetime-Authentifizierungs-Kurzmedientoken (SMT) eine kurze Gültigkeitsdauer hat. Wenn Ihre Anwendung Lizenzrotation verwenden möchte (z. B. um den *Blackouts* -Verwendungsfall zu unterstützen), muss die Anwendung dies berücksichtigen und ihr Primetime-Authentifizierungs-Short-Media-Token aktualisieren, bevor sie die Lizenz rotieren kann.