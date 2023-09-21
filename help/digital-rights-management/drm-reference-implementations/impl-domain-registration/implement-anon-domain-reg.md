---
title: Anonyme Domänenregistrierung implementieren
description: Anonyme Domänenregistrierung implementieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---

# Anonyme Domänenregistrierung implementieren{#implement-anonymous-domain-registration}

1. Erstellen Sie eine DRM-Richtlinie, die angibt, dass eine Domänenregistrierung erforderlich ist.
1. Geben Sie die URL des Domänenservers wie folgt an:

   ```
   https://[host:port]/flashaccess/domainserver/domainname/
   ```

1. Anonyme Authentifizierung erforderlich machen.

   In der [!DNL .properties] -Datei, festlegen:

   ```
   policy.domain.anonymous=true 
   ```
