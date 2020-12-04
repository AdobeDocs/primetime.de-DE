---
seo-title: Anonyme Domänenregistrierung implementieren
title: Anonyme Domänenregistrierung implementieren
uuid: 330d32fd-8c23-40f9-949b-635e5a9acc86
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---


# Anonyme Domänenregistrierung implementieren{#implement-anonymous-domain-registration}

1. Erstellen Sie eine DRM-Richtlinie, die angibt, dass eine Domänenregistrierung erforderlich ist.
1. Geben Sie die URL des Domänenservers an als:

   ```
   https://[host:port]/flashaccess/domainserver/domainname/
   ```

1. Anonyme Authentifizierung erforderlich machen.

   Legen Sie in der Datei [!DNL .properties] Folgendes fest:

   ```
   policy.domain.anonymous=true 
   ```
